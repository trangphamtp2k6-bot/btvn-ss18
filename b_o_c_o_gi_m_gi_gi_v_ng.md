# Báo cáo Xây dựng cơ chế giảm giá giờ vàng tự động tại Co.opmart

**Người thực hiện:** Chuyên viên Tối ưu hóa Giá & Dòng tiền Bán lẻ (Dynamic Pricing & Markdown Specialist)
**Đối tượng phân tích:** Tồn kho Rau củ quả hữu cơ lúc 17h30 tại Co.opmart Quang Trung
**Lượng hàng tồn:** 360 kg

---

## Phần 1: Bảng đối chiếu cân đối tài chính chi tiết của 3 kịch bản

Tại thời điểm 17h30, toàn bộ 360 kg rau củ hữu cơ có tổng giá vốn là: $360 \text{ kg} \times 25,000 \text{ VNĐ/kg} = 9,000,000 \text{ VNĐ}$. Đây là khoản "chi phí chìm" (Sunk Cost) đã phát sinh. Mục tiêu hiện tại của việc định giá là tối đa hóa dòng tiền thu hồi và giảm thiểu mức lỗ ròng trước giờ đóng cửa (21h30). 

Dưới đây là bảng đối chiếu tài chính dự kiến của 3 kịch bản:

| Chỉ tiêu tài chính | Kịch bản A (Giữ nguyên giá) | Kịch bản B (Giảm giá 30%) | Kịch bản C (Giảm giá 50%) |
| :--- | :--- | :--- | :--- |
| **Giá bán áp dụng** | 35,000 VNĐ/kg | 24,500 VNĐ/kg | 17,500 VNĐ/kg |
| **Lượng hàng bán được** | 120 kg | 280 kg | 360 kg |
| **Lượng hàng tồn hủy** | 240 kg | 80 kg | 0 kg |
| **Doanh thu thu về** | $4,200,000 \text{ VNĐ}$ | $6,860,000 \text{ VNĐ}$ | $6,300,000 \text{ VNĐ}$ |
| **Giá vốn hàng hủy** | $6,000,000 \text{ VNĐ}$ | $2,000,000 \text{ VNĐ}$ | $0 \text{ VNĐ}$ |
| **Lợi nhuận ròng (Mức lỗ)** | $\mathbf{-4,800,000 \text{ VNĐ}}$ | $\mathbf{-2,140,000 \text{ VNĐ}}$ | $\mathbf{-2,700,000 \text{ VNĐ}}$ |

*(Ghi chú: Mức lỗ ròng = Doanh thu thu về - Tổng giá vốn 9,000,000 VNĐ).*

---

## Phần 2: Luận giải kinh tế học về tư duy "Bán dưới giá vốn để cắt lỗ"

Khi nhìn vào Kịch bản C, việc bán với giá $17,500 \text{ VNĐ/kg}$ (thấp hơn giá vốn $25,000 \text{ VNĐ/kg}$) thoạt nhìn có vẻ phi lý, nhưng so với Kịch bản A (giữ nguyên giá bán ban đầu), đây là một **quyết định kinh doanh thông minh và mang lại hiệu quả vượt trội** vì những lý do sau:

1.  **Tối ưu hóa thu hồi vốn lưu động:** Trong ngành thực phẩm tươi sống, khi sản phẩm qua ngày sẽ mất 100% giá trị (thu hồi $= 0 \text{ VNĐ}$). Giá vốn $9,000,000 \text{ VNĐ}$ lúc này đã trở thành chi phí chìm. Bằng việc giảm giá 50% (Kịch bản C), siêu thị thu hồi ngay được $6,300,000 \text{ VNĐ}$ tiền mặt thay vì chỉ thu được $4,200,000 \text{ VNĐ}$ như Kịch bản A. Mức lỗ ròng được thu hẹp đáng kể từ 4.8 triệu xuống chỉ còn 2.7 triệu VNĐ. 
2.  **Loại bỏ hoàn toàn chi phí ẩn (Hidden Costs):** Việc tiêu hủy 240kg rau củ ở Kịch bản A không chỉ làm mất tiền vốn mà còn phát sinh thêm chi phí nhân công dọn dẹp, chi phí xử lý rác thải môi trường. Kịch bản C bán sạch 100% lượng tồn, giúp quầy kệ trống trải, sạch sẽ để sẵn sàng đón đợt hàng mới vào sáng hôm sau.
3.  **Chiến lược Chim mồi (Loss Leader Strategy):** Khung giờ 18h00 - 21h30 là thời điểm tan tầm. Mức giảm giá sốc 50% ("Giờ vàng Happy Hour") sẽ tạo hiệu ứng FOMO (sợ bỏ lỡ), thu hút lượng lớn khách hàng đến quầy. Dù siêu thị chịu lỗ ở mặt hàng rau củ hữu cơ, nhưng những khách hàng này sẽ có xu hướng mua kèm thêm các sản phẩm có biên lợi nhuận cao khác (như thịt, cá, gia vị, đồ gia dụng), từ đó bù đắp lại mức lỗ chênh lệch (Kịch bản C lỗ nhiều hơn Kịch bản B khoảng $560,000 \text{ VNĐ}$ nhưng lại mang về lượng traffic khách hàng lớn nhất).

---

## Phần 3: Đặc tả quy tắc kích hoạt tự động (Automated Markdown Trigger) trên POS

Để chuyển đổi Insight thành Hành động tức thời (Actionable BI) mà không phụ thuộc vào quyết định thủ công của cửa hàng trưởng, hệ thống ERP/POS cần được thiết lập một bộ quy tắc logic (Trigger Logic). 

Hệ thống sẽ liên tục tính toán **Tốc độ bán trung bình (Run-rate)** và so sánh với **Tồn kho hiện tại** để kích hoạt kịch bản giảm giá.

**Đặc tả mã Logic (Pseudo-code):**

```text
// 1. Định nghĩa các biến số lúc 18:00
SET @CurrentTime = GET_TIME()
SET @ItemCategory = "Organic_Vegetables"
SET @CurrentStock = GET_INVENTORY(@ItemCategory)
SET @SalesVelocityPerHour = CALCULATE_AVG_SALES(@ItemCategory, LAST_2_HOURS)
SET @HoursToClose = 3.5 // (Từ 18:00 đến 21:30)

// 2. Tính toán lượng hàng dự kiến bán được ở mức giá bình thường
SET @ProjectedSales = @SalesVelocityPerHour * @HoursToClose

// 3. Quy tắc kích hoạt Giảm giá tự động (Dynamic Markdown)
IF (@CurrentTime >= "18:00:00") THEN
    
    // Khối lệnh đánh giá rủi ro tồn hủy
    IF (@CurrentStock > @ProjectedSales * 2) THEN
        // Cảnh báo Đỏ: Tồn kho quá cao, nguy cơ hủy lớn -> Kích hoạt Kịch bản C
        TRIGGER_POS_DISCOUNT(@ItemCategory, 0.50) // Giảm 50%
        SEND_NOTIFICATION("Zalo_StoreManager", "Kích hoạt Giảm 50% Rau Hữu Cơ. Xả hàng cắt lỗ!")
        
    ELSE IF (@CurrentStock > @ProjectedSales) THEN
        // Cảnh báo Vàng: Tồn kho vượt mức an toàn -> Kích hoạt Kịch bản B
        TRIGGER_POS_DISCOUNT(@ItemCategory, 0.30) // Giảm 30%
        
    ELSE
        // An toàn: Tốc độ bán hiện tại đủ để tiêu thụ hết hàng -> Kịch bản A
        MAINTAIN_CURRENT_PRICE(@ItemCategory)
        
    END IF
    
END IF
```

**Cơ chế hoạt động:** Đúng 18h00, hệ thống tự động quét dữ liệu. Tại Co.opmart Quang Trung, do `@CurrentStock (360kg) > @ProjectedSales * 2 (105kg * 2 = 210kg)`, hệ thống POS tại tất cả các quầy thu ngân sẽ tự động áp dụng mã giảm giá 50% cho ngành hàng rau củ hữu cơ, đồng thời gửi thông báo qua Zalo cho Quản lý siêu thị để kịp thời in tem giá mới dán lên quầy.