# Chương 8: Overfitting

## Overfitting

Trong cái mô hình Supervised Learning, cần đi tìm hàm số f. Ta sẽ đi tìm các tham số mô hình (model parameter) của f sao cho việc xấp xỉ có sai số càng nhỏ càng tốt. Điều ngày nghĩa là mô hình càng fit với mô hình các tốt. Tuy nhiên nếu một mô hình quá fit với dữ liệu thì nó sẽ gây ra phản tác dụng. Hiện tượng quá fit trong Machine Learning được gọi là overfitting  (khi xây dưng mô hình chúng ta cần tránh)

Overfitting là hiện tượng mô hình tìm được *quá khớp* với dữ liệu training. Việc *quá khớp* này có thể dẫn đến việc dự đoán nhầm nhiễu, và chất lượng mô hình không còn tốt trên dữ liệu test nữa. (Dữ liệu test được giả sử là không biết trước, và không được sử dụng để xây dựng các mô hình)

VD: 

Hãy xem xét một trường hợp sử dụng trong đó mô hình máy học phải phân tích hình ảnh và xác định những bức ảnh có hình các chú chó. Nếu được đào tạo trên một tập dữ liệu chứa đa số những bức ảnh về các chú chó ở ngoài công viên, mô hình máy học có thể sẽ học cách sử dụng cỏ làm đặc điểm phân loại và không nhận ra một chú chó ở trong phòng.

**(câu hỏi) Khi nào xảy ra hiện tượng overfitting?** - Overfitting xảy ra khi mô hình quá phức tạp để mô phỏng training data. Đặc biệt xảy ra khi lượng dữ liệu training data quá nhỏ kho độ phức tạp của mô hình quá cao. 

**(câu hỏi) Vây có những kỹ thuật toán giúp tránh overfitiing?**

Có 2 đại lượng: 

- Train error

![m](https://github.com/toe25/Image/blob/main/Machine%20Learning/Screenshot%20from%202024-01-27%2017-36-47.png?raw=true)

- Test error

![m](https://github.com/toe25/Image/blob/main/Machine%20Learning/Screenshot%20from%202024-01-27%2017-36-53.png?raw=true)

**(kết luận)** 

- **Một mô hình được coi là tốt (fit) nếu cả *train error* và *test error* đều thấp.**
- **Nếu *train error* thấp nhưng *test error* cao, mô hình bị overfitting.**
- **Nếu *train error* cao và *test error* cao, mô hình bị underfitting.**

## Validation

### Validation

**(câu hỏi) Làm cách nào để biết được chất lượng của mô hình với *unseen data* (tức dữ liệu chưa nhìn thấy bao giờ)?**

Phương pháp đơn giản nhất là *trích* từ tập training data ra một tập con nhỏ và thực hiện việc đánh giá mô hình trên tập con nhỏ này. Tập con nhỏ **được trích ra từ training set** này được gọi là *validation set (* xuất hiện một khái niệm *validation error)*

Với khái niệm mới này, tìm mô hình sao cho cả *train error* và *validation error* đều nhỏ, qua đó có thể dự đoán được rằng *test error* cũng nhỏ. Phương pháp thường được sử dụng là sử dụng nhiều mô hình khác nhau. Mô hình nào cho *validation error* nhỏ nhất sẽ là mô hình tốt.

**Thông thường, bắt đầu từ mô hình đơn giản, sau đó tăng dần độ phức tạp của mô hình. Tới khi nào *validation error* có chiều hướng tăng lên thì chọn mô hình ngay trước đó. Chú ý rằng mô hình càng phức tạp, *train error* có xu hướng càng nhỏ đi.**

VD: 

Hình dưới đây mô tả ví dụ phía trên với bậc của đa thức tăng từ 1 đến 8. Tập validation bao gồm 10 điểm được lấy ra từ tập training ban đầu.

![m](https://github.com/toe25/Image/blob/main/Machine%20Learning/Screenshot%20from%202024-01-27%2017-58-52.png?raw=true)

### Cross-validation

Nếu lấy quá nhiều dữ liệu trong tập training ra làm dữ liệu validation, phần dữ liệu còn lại của tập training là không đủ để xây dựng mô hình. Lúc này, tập validation phải thật nhỏ để giữ được lượng dữ liệu cho training đủ lớn. 

**(câu hỏi) Khi tập validation quá nhỏ, hiện tượng overfitting lại có thể xảy ra với tập training còn lại. Có giải pháp nào cho tình huống này không?** - Cross-validation

Cross validation là một cải tiến của validation với lượng dữ liệu trong tập validation là nhỏ nhưng chất lượng mô hình được đánh giá trên nhiều tập validation khác nhau. 

Một cách thường đường sử dụng là chia tập training ra k tập con không có phần tử chung, có kích thước gần bằng nhau. Tại mỗi lần kiểm thử , được gọi là run, một trong số k tập con được lấy ra làm validate set. Mô hình sẽ được xây dựng dựa vào hợp của k − 1 tập con còn lại. 

Mô hình cuối được xác định dựa trên trung bình của các train error và validation error. Cách làm này còn có tên gọi là k-fold cross validation.

Khi k = số lượng phần tử trong tập training ban đầu (mỗi tập validation có 1 phần tử) ta được kỹ thuật **leave-one-out**

## Regularization (Cơ chế kiểm soát)

Nhược điểm của cross-calidation là số lượng mô hình sẽ tỉ lệ thuận với k. Có một số trường hợp, việc huấn luyện nhiều mô hình khó khả thi. 

Có một kỹ thuật tránh quá khớp khác giúp giảm số mô hình cần huấn luyện có tên là cơ chế kiểm soát (regularization).


---
(note)

Khi thiết kế một hệ thống dựa trên dữ liệu, cần chú ý:
- lựa chọn tập dữ liệu, để mô hình hoạt động tốt, thì dữ liệu phải chứa nhiều đặc trưng của không gian dữ liệu
- xác định loại của hàm, đối với bài toán này, đầu ra của chúng sẽ như thế nào
- lựa chọn mô hình nào
- chọn thuận toán đễ huấn luyện 
