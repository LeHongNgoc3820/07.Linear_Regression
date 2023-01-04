# Linear Regression

## 1. Regression Analysis
+ **Regression analysis** là một dạng của kỹ thuộc mô hình tiên đoán **(predictive modelling technique)**, nó điều tra mối quan hệ giữa **dependent (target)** và các **independent variable (predictor).**
+ Kỹ thuật này được **sử dụng để dự báo (forecasting)**, mô hình hoá chuỗi thời gian (time series) và tìm mối quan hệ giữa các biến.
+ Regression analysis là một công cụ quan trọng cho việc lập mô hình và phân tích dữ liệu.

**Mục tiêu:** dự đoán giá trị số (number) từ input variables.

**Đặc điểm:**
+ Dự đoán number từ input variables
+ Regression là supervised task
+ Target variable là giá trị số

**Ví dụ:** 
+ Ước tính giá nhà trung bình cho một khu vực
+ Xác định nhu cầu cho một sản phẩm mới
+ Dự đoán mức sử dụng năng lượng

### Xây dựng và áp dụng model
**Training Phase**
+ Điều chỉnh tham số model (model parameter)
+ Sử dụng dữ liệu huấn luyện (training data)

**Testing Phase**
+ Áp dụng mô hình (learned model)
+ Sử dụng dữ liệu mới (new data)

### Một số thuật toán Regression
+ Linear regression
+ Polynomial regression
+ Regression Trees & Random Forest
+ ...

## 2. Linear Regression
### 2.1 Giới thiệu
+ Linear Regression là một thuật toán thuộc nhóm Supervised Learning được sử dụng cho regression.
+ Là một trong những mô hình kỹ thuật được sử dụng rộng rãi.
+ Là một trong những chủ đề đầu tiên cần biết khi học về mô hình tiên đoán dữ liệu (learning predictive modeling).

**Ví dụ sử dụng Linear Regression:**
+ Hệ thống quản lý rủi ro hoặc chấm điểm tín dụng của các ngân hàng: để quyết định hạn mức thẻ Credit card của khách hàng, hệ thống sẽ sử dụng LR để tính toán dựa trên các thông tin khách hàng cung cấp như mức lương hiện tại, độ tuổi, giới tính, công việc đang làm, ...
+ Dự báo tài chính
+ Dự đoán chi phí phần mềm, chi phí đảm bảo chất lượng phần mềm

### 2.2 Ý tưởng
+ Tìm mối quan hệ giữa numerical output và input variables.
+ Dêpndent variable có thể liên tục hoặc rời rạc
+ Mối quan hệ được mô hình hoá dưới dạng tuyến tính (linear).
+ Mô hình có thể được "phù hợp" bằng cách sử dụng least squares

### 2.3 Phân loại
**a. Simple Linear Regression**
+ Simple Linear Regression là phương pháp giúp chúng ta hiểu mối quan hệ giữa hai biến:
    + X: Biến độc lập (predictor/independent variable)
    + Y: Biến phụ thuộc (response/dependent variable) là biến mà chúng ta muốn dự đoán.
+ Kết quả của Linear Regression là một hàm tuyến tính (linear function) dự đoán biến phụ thuộc từ biến độc lập.

**b. Multiple Linear Regression**
+ Nếu chúng ta muốn sử dụng nhiều biến hơn trong mô hình để dự đoán (Y), chúng ta có thể sử dụng Multiple Linear Regression.
+ Multiple Linear Regression rất giống với Simple Linear Regression, nhưng phương pháp này được sử dụng để giải thích mối quan hệ giữa một biến phụ thuộc và hai (hoặc nhiều) biến độc lập.
+ Hầu hết các mô hình hồi quy (regression model) trong thực tế liên quan đến nhiều yếu tố dự đoán.

### 2.3 Ưu điểm và hạn chế của Linear Regression
**Ưu điểm:**
+ Thuật toán dễ hiểu
+ Độ phổ biến cao
+ Tốc độ giải thuật nhanh
+ Thực hiện mô hình thống kê, khi các mối quan hệ giữa các biến độc lập và biến phụ thuộc gần như tuyến tính => cho thấy kết quả tối ưu

**Hạn chế:**
+ Hạn chế đầu tiên của Linear Regression là nó rất nhạy cảm với nhiễu - outlier (sensitive to noise), do đó trước khi thực hiện thuật toán này cần phải loại bỏ nhiễu.
+ Hạn chế tiếp theo là không biểu diễn được các mô hình phức tạp.
+ Không thích hợp để mô hình hoá các mối quan hệ phi tuyến tính.

### 2.4 Các bước thực hiện
+ Chọn model sẽ sử dụng là **Linear Regression**
+ tạo ra một tập dữ liệu input và một tập output
+ Chia dữ liệu cho việc train và test theo tỷ lệ training data : testing data là (80:20), (75:25) hoặc (70:30)
+ Huấn luyện model với traning data
+ Kiểm tra model với testing data
+ So sánh R-square của train và test để biết model có bị overfitting hay underfitting hay không

> **Overfitting:** Training tốt, Testing tệ

> **Underfitting:** Training tệ, Testing tốt

+ Tính mean squared error (MSE) của output test và output predict
+ Vẽ biểu đồ trực quan hoá kết quả và đưa ra nhận xét

Áp dụng, ta sử dụng thư viện sklearn: `linear_model.LinearRegression()`

### 2.5 Đánh giá mô hình
Với việc kiểm tra/đánh giá mô hình (**model evaluation**), ta có thể sử dụng trực quan hoá dữ liệu để đánh giá (dùng matplotlib hoặc seaborn, ...)

**Regression Plot**
+ Khi nói đến simple linear regression, một cách tốt nhất để hình dung sự phù hợp của mô hình là sử dụng các biểu đồ hồi quy hay **regression plot**.
+ Biểu đồ này sẽ hiển thị kết hợp các điểm dữ liệu phân tán (scatter plot) cũng như đường hồi quy tuyến tính được tạo thành đi qua dữ liệu. Điều này sẽ cho chúng ta một ước tính hợp lý về mối quan hệ giữa hai biến, sức mạnh của mối tương quan (correlation) cũng như hướng tác động (positive/negative correlation)

**Residual Plot**
+ Một cách tốt để trực quan phương sai của dữ liệu là sử dụng residual plot
> **Residual (phần dư) là gì?**  
> Sự khác biệt giữa giá trị quan sát (y) và giá trị dự đoán (y_hat) được gọi là phần dư (e). Khi chúng ta xem xét một biểu đồ hồi quy, phần dư là khoảng cách từ điểm dữ liệu đến đường hồi quy (regression line) được fit.
+ **Residual plot là gì?** 
> Biểu đồ phần dư là biểu đồ hiển thị phần dư trên trục y và biến độc lập trên trục x.

**Vậy chúng ta cần chú ý gì khi xem residual plot?**
+ Chúng ta xem xét sự lây lan của residual (phần dư)
+ Nếu các điểm trong một residual plot được trải ngẫu nhiên xung quanh trục x, thì mô hình tuyến tính phù hợp với dữ liệu.
+ Lí do: Vì ngẫu nhiễn trải residual có nghĩa là phương sai không đổi và do đó mô hình tuyến tính phù hợp với dữ liệu này.

**Distribution plot**
+ Làm thế nào để chúng ta trực quan hoá một mô hình cho Multiple Linear Regression? Điều này trở nên phức tạp hơn vì ta không thể hình dung nó bằng regression/residual plot.
+ Một cách để xem xét sự phù hợp của mô hình là bằng cách quan sát **Distribution plot** (biểu đồ phân phối): có thể xem xét phân phối của các giá trị được dự đoán từ mô hình và so sánh nó với các giá trị thực tế.

Ngoài ra, để đánh giá mô hình có tốt hay không thì còn phải dựa trên các giá trị định lượng là **MSE, R-squared.**

> **MSE**: khi so sánh các mô hình, mô hình có giá trị MSE nhỏ hơn phù hợp hơn với dữ liệu

> **R-squared**: khi so sánh các mô hình, mô hình có giá trị R-squared cao hơn sẽ phù hợp hơn với dữ liệu.


## 3. Polynomial Regression
+ Polynomial regression (hồi quy đa thức) là một trường hợp cụ thể của general linear regression model (mô hình hồi quy tuyến tính tổng quát) hoặc nhiều multiple linear regression model.
+ Chúng ta có được các non-linear relationship (mối quan hệ phi tuyến) bằng cách bình phương hoặc đặt các biến dự đoán ở bậc cao hơn.

## 4. Hiện tượng đa cộng tuyến trong mô hình hồi quy

### 4.1 Multicollinearity (đa cộng tuyến)

+ Hiện tượng đa cộng tuyến: là hiện tượng các biến độc lập trong mô hình phụ thuộc lẫn nhau và thể hiện được dưới dạng hàm số.

**Ví dụ:** Có hai biến độc lập A và B, khi ta tgawng A thì B tặng, A giảm thì B giảm...thì đó là một dấu hiệu của đa cộng tuyến.

+ Nói một cách khác là hai biến độc lập có quan hệ rất mạnh với nhau, đúng ra hai biến này phải là 1 biến nhưng thực tế trong mô hình lại tách làm 2 biến.
+ Hiện tượng đa cộng tuyến vi phạm giả định của mô hình hồi quy tuyến tính cổ điển là các biến độc lập không có mối quan hệ tuyến tính với nhau.

### 4.2 Nguyên nhân

+ Thường thì cộng tuyến về cơ bản là vấn đề thiếu dữ liệu (data deficiency)
+ hoặc do khi lập bảng khảo sát, chúng ta xây dựng nên các yếu tố không khác biệt nhau nhiều về tính chất, ý nghĩa. Ví dụ: tiền lượng và thu nhập/sở thích và điều quan tâm, ...
+ Hoặc do đặc trưng của chính môi trường được khảo sát gây nên hiện tượng đa cộng tuyến.

### 4.3 Hậu quả

+ Sai số chuẩn của các hệ số sẽ lớn
+ Khoảng tin cậy lớn và thống kê t ít ý nghĩa
+ Đưa một biến cộng tuyến vào mô hình hồi quy được chọn có thể làm thay đổi các giá trị của hệ số của các biến khác trong mô hình.
+ Các ước lượng không chính xác

**Tóm lại:** Khi các biến độc lập cộng tuyến, suy diễn thống kê trở nên không vững chắc, đặc biệt là khi có cộng tuyến gần hoàn hảo. Nếu hai biến có cộng tuyến cao thì rất khó tách biệt tác động riêng của từng biến lên biến phụ thuộc.

### 4.4 Nhận biết multicollinearity

+ Dựa vào hệ số tương quan (correlation - theo Pearson): để biết có hay không tương quan tuyến tính mạnh giữa các biến độc lập (kiểm tra hệ số tương quan giữa các cặp biến (pairwise correlations): 
    + **corr > 0.5 (hay < -0.5):** có hiện tượng tương quan
    + **corr > 0.7 (hay -0.7):** tương quan mạnh
    + **corr -1 hay 1:** tương quan hoàn hảo

### 4.5 Cách khắc phục

+ Thu thập thêm dữ liệu
+ Loại biến đa cộng tuyến ra khỏi mô hình trong trường hợp biến không cần thiết và có hệ số tương quan rất cao so với các biến khác.
+ Chấp nhận đa cộng tuyến nếu như chắc chắn rằng các biến đưa vào mô hình đều là những biến cần thiết và quan trọng, được đảm bảo trên một nền tảng lý thuyết chắc chắn thì chúng ta không cần phải làm gì cả trong trường hợp này.
+ Sử dụng phương pháp giảm chiều dữ liệu.
