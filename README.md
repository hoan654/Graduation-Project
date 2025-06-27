# Phân tích yếu tố tác động đến giá nhà tại Mỹ và dự báo giá nhà

## 1. Mục tiêu dự án  
- Xác định những yếu tố ảnh hưởng mạnh nhất đến giá bán nhà (số phòng ngủ, diện tích, grade, view, vị trí, v.v.).  
- Xây dựng mô hình hồi quy tuyến tính đa biến để dự báo giá nhà với độ chính xác cao (R², RMSE).  
- Đề xuất chiến lược định giá và cải tạo bất động sản cho nhà đầu tư, người mua và người bán.

## 2. Nguồn dữ liệu sử dụng  
- **House Sales in King County, USA** (21.613 dòng, 21 cột) từ Kaggle.  
- Tài liệu đề xuất dự án và brief tốt nghiệp: `Proposal_KhaiHoan.docx`, `Graduation Project Brief.docx`.

## 3. Tổng quan dữ liệu  
- **Mô tả chung**: Dữ liệu giao dịch bán nhà tại King County (Washington State), bao gồm thông tin kỹ thuật và vị trí.  
- **Cấu trúc bảng**:  
  - `id`: mã giao dịch  
  - `date`: ngày bán  
  - `price`: giá bán (USD)  
  - `bedrooms`, `bathrooms`: số phòng ngủ, số phòng tắm  
  - `sqft_living`, `sqft_lot`: diện tích sử dụng trong nhà và diện tích đất (sqft)  
  - `floors`: số tầng  
  - `waterfront`: view mặt nước (0/1)  
  - `view`, `condition`, `grade`: đánh giá góc nhìn, tình trạng, chất lượng xây dựng  
  - `sqft_above`, `sqft_basement`: diện tích trên mặt đất và diện tích tầng hầm  
  - `yr_built`, `yr_renovated`: năm xây, năm cải tạo  
  - `lat`, `long`: toạ độ kinh độ và vĩ độ
  - `zipcode`: mã vùng
  - `sqft_living15`, `sqft_lot15`: diện tích trung bình của 15 ngôi nhà xung quanh

## 4. Công cụ và công nghệ áp dụng  
- **Ngôn ngữ**: Python (Jupyter Notebook)  
- **Xử lý & phân tích**: `pandas`, `numpy`  
- **Trực quan hóa**: `matplotlib`, `seaborn`  
- **Mô hình hóa**: `statsmodels`, `scikit-learn`  
- **Môi trường**: Google Colab

## 5. Các insight chính  
1. **Diện tích sử dụng** (`sqft_living`) và **grade** có tương quan mạnh nhất với giá bán.  
2. Bất động sản có `waterfront = 1` thường có giá cao hơn trung bình khoảng 20–30%.  
3. Tỷ lệ diện tích trên phòng ngủ (sqft_living/bedroom) phản ánh tối ưu không gian, giúp mô hình ổn định và giảm hệ số âm bất hợp lý.

## 6. Giả thuyết dựa trên các insight  
- **Tăng 1 điểm grade** kỳ vọng kéo giá bán tăng X% khi giữ nguyên các yếu tố khác.  
- **Waterfront premium**: Nhà gần mặt nước luôn bán với giá cao hơn do tính khan hiếm và view.  
- **Cải tạo gần đây** (yr_renovated) làm tăng giá bán so với nhà chưa cải tạo.  
- **Tỷ lệ diện tích/phòng ngủ cao** đem lại giá trị gia tăng vì không gian sống thoải mái hơn.

## 7. Khuyến nghị dựa trên kết quả phân tích  
- **Nhà đầu tư**: Ưu tiên mua/sửa chữa tại khu vực waterfront và nâng cấp grade để tối đa hóa lợi nhuận.  
- **Người bán**: Đầu tư cải tạo, sơn sửa, nâng cấp grade và khai thác tính view để tăng curb appeal.  
- **Người mua**: Lưu ý cân bằng giữa số phòng ngủ và diện tích mỗi phòng, ưu tiên nhà có waterfront nếu ngân sách cho phép.
