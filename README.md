# BÀI TẬP VỀ NHÀ TRÍ TUỆ NHÂN TẠO
## Chủ đề bài tập
- Xây dựng AI Agent.
- Thực hành và hiểu các thuật toán tìm kiếm: Có thông tin và không có thông tin.
  + Có thông tin: BFS, DFS, IDS, ...
  + Không có thông tin: Greedy,...

## Cách sử dụng
- Mỗi bài tập được thực hiện trong file ipynb.
- Có thể nhiều bài tập gộp chung trong 1 file.
- Khi sử dụng, hãy nhấn "Run All" để có thể tải thư viện và chạy code.

## Giao diện
<img width="1517" height="883" alt="image" src="https://github.com/user-attachments/assets/31d4186c-3eec-4f64-8e06-cd7e67118e2d" />

- Chọn thuật toán cần sử dụng.
- Ấn RUN.
- Các hành động của Agent sẽ được ghi lại trong Logs.
- Bàn cờ hiện tại đang là tạo ngẫu nhiên nên có thể xảy ra việc không tìm được đường đi, ấn "Trạng thái mới" để đổi bàn cờ.
- Ấn quay lại ban đầu để có thể sử dụng lại bàn cờ ban đầu để chạy thuật toán khác (so sánh hoạt động giữa các thuật toán)

## Các thuật toán tìm kiếm
# 1. Uninformed Search Algorithms (Thuật toán tìm kiếm không có thông tin)

Đây là nhóm thuật toán tìm kiếm chỉ dựa vào cấu trúc của không gian trạng thái mà không sử dụng bất kỳ thông tin ước lượng nào về vị trí của trạng thái đích. Thuật toán sẽ duyệt các trạng thái theo một quy tắc nhất định cho đến khi tìm được lời giải.

## 1.1. Breadth-First Search (BFS)

Breadth-First Search mở rộng các nút theo từng mức độ sâu từ gốc. Thuật toán sử dụng cấu trúc dữ liệu hàng đợi (FIFO - First In First Out), đảm bảo rằng tất cả các trạng thái ở cùng một mức được duyệt trước khi chuyển sang mức tiếp theo.

**Ưu điểm:**

* Đảm bảo tìm được lời giải nếu tồn tại.
* Tìm được đường đi ngắn nhất khi chi phí các cạnh là như nhau.

**Nhược điểm:**

* Tiêu tốn nhiều bộ nhớ do phải lưu toàn bộ các nút ở biên tìm kiếm.

## 1.2. Depth-First Search (DFS)

Depth-First Search ưu tiên mở rộng sâu nhất có thể trên một nhánh trước khi quay lui để khảo sát các nhánh khác. Thuật toán thường được cài đặt bằng ngăn xếp (LIFO - Last In First Out).

**Ưu điểm:**

* Tiết kiệm bộ nhớ hơn BFS.

**Nhược điểm:**

* Có thể mắc kẹt trong các nhánh rất sâu hoặc vòng lặp.
* Không đảm bảo tìm được lời giải tối ưu.

## 1.3. Iterative Deepening Search (IDS)

IDS kết hợp ưu điểm của BFS và DFS bằng cách thực hiện DFS với giới hạn độ sâu tăng dần. Mỗi lần tìm kiếm thất bại, giới hạn độ sâu được tăng thêm và thuật toán bắt đầu lại từ gốc.

**Ưu điểm:**

* Đảm bảo tối ưu như BFS.
* Tiết kiệm bộ nhớ như DFS.

## 1.4. Uniform Cost Search (UCS)

Uniform Cost Search mở rộng nút có tổng chi phí từ trạng thái gốc nhỏ nhất. Thuật toán sử dụng hàng đợi ưu tiên để lựa chọn nút tiếp theo.

**Ưu điểm:**

* Tìm được đường đi có chi phí thấp nhất nếu mọi chi phí đều không âm.

---

# 2. Informed Search Algorithms (Thuật toán tìm kiếm có thông tin)

Khác với nhóm trước, các thuật toán trong nhóm này sử dụng hàm heuristic để ước lượng khoảng cách từ trạng thái hiện tại đến đích. Nhờ đó, quá trình tìm kiếm thường hiệu quả hơn đáng kể.

## 2.1. Greedy Best-First Search

Thuật toán luôn ưu tiên mở rộng trạng thái có giá trị heuristic nhỏ nhất.

[
f(n)=h(n)
]

Trong đó:

* (h(n)): chi phí ước lượng từ trạng thái hiện tại đến đích.

**Ưu điểm:**

* Tốc độ nhanh.

**Nhược điểm:**

* Không đảm bảo tìm được lời giải tối ưu.

## 2.2. A* Search

A* sử dụng đồng thời chi phí đã đi và chi phí ước lượng:

[
f(n)=g(n)+h(n)
]

Trong đó:

* (g(n)): chi phí thực tế từ trạng thái gốc đến nút hiện tại.
* (h(n)): chi phí ước lượng từ nút hiện tại đến đích.

**Ưu điểm:**

* Tìm được lời giải tối ưu nếu heuristic thỏa điều kiện admissible.

## 2.3. Iterative Deepening A* (IDA*)

IDA* hoạt động tương tự IDS nhưng sử dụng ngưỡng trên giá trị (f(n)) thay vì độ sâu.

**Ưu điểm:**

* Giữ được tính tối ưu của A*.
* Tiêu thụ ít bộ nhớ hơn A* truyền thống.

---

# 3. Local Search Algorithms (Thuật toán tìm kiếm cục bộ)

Các thuật toán tìm kiếm cục bộ chỉ tập trung vào trạng thái hiện tại và các trạng thái lân cận của nó. Chúng không cần lưu toàn bộ cây tìm kiếm nên rất phù hợp với các bài toán tối ưu hóa quy mô lớn.

## 3.1. Hill Climbing

### 3.1.1. Simple Hill Climbing

Chọn trạng thái lân cận đầu tiên tốt hơn trạng thái hiện tại và di chuyển đến đó.

### 3.1.2. Steepest-Ascent Hill Climbing

Đánh giá toàn bộ các trạng thái lân cận và chọn trạng thái tốt nhất.

### 3.1.3. Random Hill Climbing

Lựa chọn ngẫu nhiên một trạng thái lân cận. Nếu trạng thái đó tốt hơn hiện tại thì di chuyển tới nó.

### 3.1.4. Random Restart Hill Climbing

Khi bị mắc kẹt tại cực trị địa phương, thuật toán khởi tạo lại từ một trạng thái ngẫu nhiên khác và tiếp tục quá trình tìm kiếm.

## 3.2. Local Beam Search

Thuật toán duy trì đồng thời (k) trạng thái tốt nhất. Tại mỗi bước, tất cả các trạng thái kế cận được sinh ra và chỉ giữ lại (k) trạng thái có chất lượng cao nhất.

## 3.3. Simulated Annealing

Thuật toán mô phỏng quá trình làm nguội kim loại. Ở giai đoạn đầu, thuật toán có thể chấp nhận các bước đi kém hơn để thoát khỏi cực trị địa phương. Khi nhiệt độ giảm dần, thuật toán trở nên ổn định và ưu tiên các bước cải thiện lời giải.

---

# 4. Search in Complex Environments (Tìm kiếm trong môi trường phức tạp)

Nhóm thuật toán này được thiết kế cho các môi trường mà thông tin không đầy đủ hoặc có tính bất định.

## 4.1. Blind-Environment Search

### 4.1.1. Blind-Start Search

Trạng thái khởi đầu không được xác định rõ ràng. Thuật toán phải thực hiện các hành động thăm dò để suy luận vị trí hiện tại.

### 4.1.2. Blind-Goal Search

Đích đến không được mô tả cụ thể. Thuật toán chỉ có thể xác nhận khi đã tiếp cận hoặc đạt được trạng thái mục tiêu.

## 4.2. Partial-Environment Search

Áp dụng trong các môi trường chỉ quan sát được một phần. Bản đồ hoặc mô hình môi trường được cập nhật dần trong quá trình tìm kiếm.

## 4.3. And-Or Graph Search

Được sử dụng trong các môi trường có nhiều khả năng xảy ra cho cùng một hành động. Thuật toán xây dựng kế hoạch cho nhiều kịch bản khác nhau thông qua cây AND-OR.

---

# 5. Constraint Satisfaction Problem Search (Tìm kiếm với bài toán thỏa mãn ràng buộc)

Trong nhóm này, mục tiêu không phải là tìm đường đi mà là tìm một cấu hình giá trị thỏa mãn toàn bộ các ràng buộc được đặt ra.

## 5.1. Backtracking

Backtracking gán giá trị cho từng biến theo từng bước. Nếu phát hiện không còn giá trị hợp lệ cho biến tiếp theo, thuật toán sẽ quay lui và thử lựa chọn khác.

**Đặc điểm:**

* Dễ cài đặt.
* Là nền tảng của nhiều thuật toán CSP hiện đại.

## 5.2. Forward Checking

Forward Checking cải tiến Backtracking bằng cách kiểm tra trước các biến chưa được gán. Sau mỗi lần gán giá trị, các lựa chọn không còn hợp lệ trong tương lai sẽ bị loại bỏ ngay lập tức.

**Ưu điểm:**

* Phát hiện ngõ cụt sớm.
* Giảm đáng kể số lượng trạng thái cần duyệt.

---

# Hướng dẫn sử dụng chương trình

## Bước 1

Tải source code về máy và mở tệp chứa hàm `main()`. Thay đổi giá trị của biến `initial` thành trạng thái khởi tạo mong muốn, sau đó thực hiện lệnh **Run All**.

## Bước 2

Sau khi chương trình khởi động, giao diện trực quan sẽ xuất hiện. Chọn thuật toán cần sử dụng từ danh sách có sẵn, sau đó nhấn **PLAY** để bắt đầu quá trình tìm kiếm.

Trong quá trình chạy:

* Trạng thái hiện tại của bài toán sẽ được hiển thị trực quan trên màn hình.
* Các bước chuyển trạng thái sẽ được mô phỏng theo thời gian thực.
* Danh sách hành động từ trạng thái ban đầu đến trạng thái hiện tại sẽ được cập nhật liên tục.


## Hướng dẫn
![DEMO](video/demo.gif) 

