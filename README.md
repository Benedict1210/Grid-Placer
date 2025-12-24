# Grid-Placer
![Grid Placer Logo](/Resources/Icon_LightMode.png)

Đặt đồ kiểu tilemap cho Unity3D để thống khổ game dev.

(Phần hướng dẫn ở dưới được dịch bởi AI)

# Cài đặt

Mở cửa sổ **Package Manager**, nhấn nút **+** nhỏ ở góc trên bên trái và chọn **Git URL**.
Hãy đảm bảo bạn sao chép URL từ nút **Code** màu xanh lá, thay vì lấy URL từ thanh địa chỉ của trình duyệt.

# Cửa sổ Grid Placer

Trong **Toolbar**, vào **Tools > Grid Placer** để mở cửa sổ Grid Placer. Tôi khuyên bạn nên dock nó cạnh **Inspector**.
Cửa sổ này bao gồm các thiết lập sau:

* **Grid**

  * **Origin** xác định vị trí gốc của lưới. Có thể dùng để dịch chuyển các ô lưới hoặc thay đổi độ cao của chúng.
  * **Rotation** xác định cách lưới được xoay quanh gốc.
  * **Size X** xác định kích thước ô lưới trên trục x, có xét đến góc xoay của lưới.
  * **Size Z** xác định kích thước ô lưới trên trục z, có xét đến góc xoay của lưới.
* **Height Offset**

  * **Height** xác định độ lệch chiều cao của prefab đang được chọn theo phương vuông góc với lưới.
  * **Small Step** xác định mức thay đổi độ lệch chiều cao khi cuộn chuột trong **Scene View** trong khi giữ **Shift**.
  * **Big Step** xác định mức thay đổi độ cao của lưới khi cuộn chuột trong **Scene View**.
* **Rotation**

  * **Rotation** xác định góc xoay của prefab đang được chọn quanh trục y cục bộ của nó.
  * **Randomize** xác định liệu góc xoay quanh trục y cục bộ của prefab có được ngẫu nhiên hóa sau mỗi lần đặt hay không.
  * **Small Step** xác định mức thay đổi góc xoay khi nhấn **E/Q** trong khi giữ **Shift** trong **Scene View**.
  * **Big Step** xác định mức thay đổi góc xoay khi nhấn **E/Q** trong **Scene View**.
* **Scale**

  * **Scale** xác định tỉ lệ đồng đều (uniform scale) của prefab đang được chọn.
  * **Randomize** xác định liệu tỉ lệ đồng đều của prefab có được ngẫu nhiên hóa sau mỗi lần đặt hay không.

    * **Min Scale** xác định giá trị tỉ lệ đồng đều ngẫu nhiên nhỏ nhất.
    * **Min Scale** xác định giá trị tỉ lệ đồng đều ngẫu nhiên lớn nhất.
* **Grid Snapping**

  * **Center** khiến prefab đang được chọn snap vào tâm của ô lưới đang hoạt động.
  * **Edges** khiến prefab đang được chọn snap vào một trong bốn cạnh của ô lưới đang hoạt động.
  * **Corners** khiến prefab đang được chọn snap vào một trong bốn góc của ô lưới đang hoạt động.
  * **None** tắt hoàn toàn chế độ snapping.
  * Các thiết lập Snap cũng được hiển thị trong **Scene View**.
* **Scene Sampling**

  * **Sample Height Offset** lấy mẫu độ lệch chiều cao hiện tại so với lưới.
  * **Sample Origin Transform** đặt gốc của lưới bằng điểm lấy mẫu và căn chỉnh góc xoay của lưới theo pháp tuyến được lấy mẫu.

    * Khi ở chế độ **Sample Origin Transform**, sẽ có thêm một số tùy chọn
    * **Sample Position** xác định có lấy mẫu vị trí gốc của lưới hay không.
    * **Sample Rotation** xác định có lấy mẫu góc xoay của gốc lưới hay không.
    * **Sample Continuously** xác định có tự động lấy mẫu gốc ở mỗi frame hay không.
  * **Sample Prefab** cố gắng sử dụng đối tượng được lấy mẫu như một prefab để khởi tạo. Chỉ hoạt động với các đối tượng vốn đã là instance của prefab (không áp dụng cho prefab đã unpack).
* **Pool**

  * Để đặt prefab vào scene, chúng cần phải nằm trong **Pool**.
  * Pool có thể chỉ chứa một prefab, hoặc nhiều prefab tùy ý.
  * Khi đặt prefab, chúng sẽ được chọn ngẫu nhiên từ pool. Điều này rất hữu ích khi đặt nhiều biến thể prop khác nhau.
  * Để xóa một prefab cụ thể khỏi **Pool**, chỉ cần nhấp vào nó.
  * **Clear Pool** xóa toàn bộ prefab khỏi pool.
* **Palette**

  * **Instance Parent** – Gán một **Transform** trong scene vào đây để tự động đặt tất cả prefab được tạo làm con của Transform đó.
  * **Drag Prefabs here** để thêm prefab vào palette prefab đang hoạt động.
  * **Clear Palette** xóa toàn bộ prefab khỏi palette đang hoạt động.
  * **Palette Display Mode**

    * **List** hiển thị prefab theo dạng danh sách dọc, kèm thumbnail và tên.
    * **Compact** hiển thị prefab theo dạng lưới, chỉ hiển thị thumbnail.
  * Tất cả prefab trong palette đang hoạt động sẽ được liệt kê bên dưới

    * Nhấp vào **Prefab Thumbnail** để thêm prefab đó vào **Pool**.
    * Các prefab đang nằm trong **Pool** sẽ được đánh dấu màu xanh lá.
    * Nhấp vào **Prefab Thumbnail** màu xanh lá để xóa prefab đó khỏi **Pool**.
    * Nút **X** sẽ xóa prefab này khỏi palette.

# Gizmo trong Scene

Trong **Scene View**, bạn sẽ thấy **Grid Gizmo** luôn theo sát con trỏ chuột.

* Các **đường trắng** hiển thị ô lưới mà con trỏ hiện đang trỏ tới, đồng thời cho biết các ô lân cận.
* **Chấm xanh lá** hiển thị vị trí con trỏ được chiếu lên lưới. Khi tắt snapping, đây cũng là vị trí prefab được chọn sẽ được đặt.
* Các **chấm cam** hiển thị các vị trí snapping khả dụng theo thiết lập Snap hiện tại. Prefab được chọn sẽ được đặt tại chấm cam gần chấm xanh lá nhất.
* Các **đường cam** xuất hiện giữa các đường lưới và vị trí snapping là chỉ báo trực quan cho độ lệch chiều cao khi sử dụng snapping.
* **Đường xanh lá** xuất hiện giữa vị trí con trỏ được chiếu và prefab là chỉ báo trực quan cho độ lệch chiều cao khi không sử dụng snapping.

# Phím tắt

| Phím (Trong Scene View) | Hành động                                                                    |
| ----------------------- | ---------------------------------------------------------------------------- |
| 1                       | Chuyển sang chế độ Snap **Center**                                           |
| 2                       | Chuyển sang chế độ Snap **Edges**                                            |
| 3                       | Chuyển sang chế độ Snap **Corners**                                          |
| 4                       | Tắt snapping                                                                 |
| Scroll                  | Thay đổi **Height** bằng **Big Step**                                        |
| Scroll+Shift            | Thay đổi **Height** bằng **Small Step**                                      |
| E                       | Xoay prefab được chọn theo chiều kim đồng hồ bằng **Big Step**               |
| E+Shift                 | Xoay prefab được chọn theo chiều kim đồng hồ bằng **Small Step**             |
| Q                       | Xoay prefab được chọn ngược chiều kim đồng hồ bằng **Big Step**              |
| Q+Shift                 | Xoay prefab được chọn ngược chiều kim đồng hồ bằng **Small Step**            |
| R                       | Duyệt qua tất cả prefab trong **Pool**                                       |
| R+Shift                 | Duyệt qua tất cả prefab trong **Pool** theo chiều ngược lại                  |
| LMB                     | Đặt prefab được chọn                                                         |
| LMB+Alt                 | Lấy mẫu chiều cao của đối tượng bạn nhấp vào (yêu cầu đối tượng có collider) |

# Prefab Palettes

![Prefab Palette Icon](/Icons/PrefabPalette.png)

**Prefab Palettes** là một loại asset tùy chỉnh dùng để nhóm các prefab. Chúng có thể được kéo vào trường **Drag Prefabs here** trong cửa sổ Grid Placer để thêm toàn bộ prefab chứa trong Prefab Palette vào palette đang hoạt động.

Để tạo một Prefab Palette, nhấp chuột phải trong **Project Browser** > **Create > GridPlacer > Prefab Palette**.
Bạn sẽ thấy giao diện rất giống với giao diện Prefab Palette trong cửa sổ Grid Placer.
Bạn có thể kéo prefab vào trường **Drag Prefabs here** để thêm chúng vào Prefab Palette và nhấp vào thumbnail prefab trong danh sách để xóa chúng.
