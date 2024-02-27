
- [Chương 5: Các khái niệm cơ bản](#chương-5-các-khái-niệm-cơ-bản)
  - [Nhiệm vụ, kinh nghiệm, phép đánh giá](#nhiệm-vụ-kinh-nghiệm-phép-đánh-giá)
  - [Dữ liệu](#dữ-liệu)
  - [Phân nhóm các thuật toán Machine Learning](#phân-nhóm-các-thuật-toán-machine-learning)
    - [Học có giám sát (Supervised Learning)](#học-có-giám-sát-supervised-learning)
    - [Học không giám sát (Unsupervised Learning)](#học-không-giám-sát-unsupervised-learning)
    - [Reinforcement Learning](#reinforcement-learning)
  - [Hàm mất mát với tham số mô hình](#hàm-mất-mát-với-tham-số-mô-hình)

# Chương 5: Các khái niệm cơ bản

## Nhiệm vụ, kinh nghiệm, phép đánh giá

Một chương trình máy tính được gọi là “học tập” từ kinh nghiệm E để hoàn thành nhiệm vụ T với hiệu quả được đo bằng phép đánh giá P , nếu hiệu quả của nó khi thực hiện nhiệm vụ T , khi được đánh giá bởi P , cải thiệntheo kinh nghiệm E.

Để xây dựng một chương trình có khả năng học: 

- Nhiệm vụ (T)
- Các phép đánh giá (P)
- Nguồn dữ liệu huấn luyện (E)

## Dữ liệu

Bộ dữ liệu thường được chia ra làm 3 tập dữ liệu

- Training set ( sử dụng trong việc huấn luyện mô hình)
- Test set (dùng để đánh giá mô hình)
- Validation set

## Phân nhóm các thuật toán Machine Learning

### Học có giám sát (Supervised Learning)

Một thuật toán machine learning được gọi là học có giám sát (supervised learning) nếu việc xây dựng mô hình dự đoán mối quan hệ giữa đầu vào và đầu ra được thực hiện dựa trên các cặp (đầu vào, đầu ra) đã biết trong tập huấn luyện.

![Untitled](https://github.com/toe25/Image/blob/main/Machine%20Learning/Screenshot%20from%202024-01-25%2011-04-34.png?raw=true)

Điển hình trong nhóm học có giám sát: 

- Phân loại
- Hồi quy

### Học không giám sát (Unsupervised Learning)

Khác biệt của học có giám sát là dữ liệu không được gán nhãn. Nói một cách khác, mục tiêu của mô hình này đó chính là trích xuất nhiều thông tin nhất có thể từ tập dữ liệu.

![Untitled](https://github.com/toe25/Image/blob/main/Machine%20Learning/Screenshot%20from%202024-01-25%2011-04-54.png?raw=true)

Các thuật toán giải quyết bài toán phân cụm và giảm chiều dữ liệu là các ví dụ điển hình của nhóm này. Trong bài toán phân cụm, có thể mô hình không trực tiếp dự đoán được đầu ra của dữ liệu nhưng vẫn có khả năng phân các điểm dữ liệu có đặc tính gần giống nhau vào từng nhóm.

### Reinforcement Learning

Có thể không yêu cầu dữ liệu huấn luyện mà mô hình tự ra quyết định bằng cách giao tiếp với môi trường xung quanh. Các thuật toán nhóm này liên tục ra quyết định và nhận phản hồi từ môi trường xung quanh để tự củng cố hành vi. 

## Hàm mất mát với tham số mô hình

Mỗi mô hình được mô tả bởi bộ các **tham số mô hình** (model parameter)

(note)

Tham số mô hình là một biến cấu hình bên trong mô hình và giá trị của nó có thể được ước tính từ dữ liệu

- Chúng được mô hình yêu cầu khi đưa ra dự đoán
- Chúng được ước tính từ dữ liệu
- Thường không được thiết lập bởi con người

(tham khảo) [What is the Difference Between a Parameter and a Hyperparameter?](https://machinelearningmastery.com/difference-between-a-parameter-and-a-hyperparameter/)

Công việc của các thuật toán là tìm ra các tham số mô hình tối ưu cho bài toán sao cho phép đánh giá đạt kết quả cao nhất

- Trong các bài toán phân loại, ít điểm dữ liệu bị phân loại sai
- Trong bài toán hồi quy, sự chênh lệch giữa đầu ra dự đoán và đầu ra thực sự nhỏ nhất

**Hàm mất mát** thể hiện mối quan hệ giữa giá trị thực tế (y) và kết quả dự đoán của model (y*). Hàm số này thường có giá trị nhỏ khi phép đánh giá cho kết quả tốt và ngược lại