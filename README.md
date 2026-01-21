# Grid Balanced Trading V2 - MetaTrader 5

## 📋 Mô tả

**Grid Balanced Trading V2** là phiên bản nâng cấp của Expert Advisor (EA) cho MetaTrader 5 được thiết kế để thực hiện chiến lược giao dịch lưới (Grid Trading) với hệ thống cân bằng lưới tự động. EA tự động đặt các lệnh pending (Buy Limit, Buy Stop, Sell Limit, Sell Stop) tại các mức giá được xác định trước dựa trên khoảng cách lưới.

## 📌 Thông tin phiên bản

- **Tên file**: `GridBalancedTradingV2.mq5`
- **Phiên bản**: 2.00
- **Ngôn ngữ**: MQL5 (MetaTrader 5)
- **Trạng thái**: Phiên bản nâng cấp với nhiều tính năng mới

## ✨ Tính năng chính

- **Hệ thống lưới tự động**: Tự động tạo và quản lý các lệnh tại các mức giá được tính toán sẵn
- **Cân bằng lưới**: Đảm bảo mỗi mức giá chỉ có tối đa 1 lệnh Buy và 1 lệnh Sell để tránh mất cân bằng
- **Cấu hình riêng biệt**: Bật/tắt và cấu hình độc lập cho từng loại lệnh (Buy Limit, Sell Limit, Buy Stop, Sell Stop)
- **Lot size và TP riêng**: Mỗi loại lệnh có lot size và Take Profit riêng
- **Gấp thếp (Martingale)**: Hỗ trợ gấp thếp riêng cho từng loại lệnh với hệ số tùy chỉnh
- **Ghi nhớ lot size**: Tự động ghi nhớ lot size theo mức lưới khi đạt TP và bổ sung lại với đúng lot size đó
- **TP tổng**: 3 loại TP tổng (lệnh mở, phiên, tích lũy) với tùy chọn Reset hoặc Dừng EA
- **Tự động bổ sung lệnh**: Tùy chọn tự động tạo lại lệnh khi lệnh cũ bị đóng
- **Magic Number**: Quản lý lệnh riêng biệt với Magic Number

## 🛠️ Cài đặt

1. Sao chép file `GridBalancedTradingV2.mq5` vào thư mục `MQL5/Experts/` của MetaTrader 5
2. Khởi động lại MetaTrader 5 hoặc làm mới Navigator (F5)
3. Kéo và thả EA vào biểu đồ mong muốn
4. Cấu hình các tham số theo nhu cầu
5. Bật chế độ AutoTrading

## ⚙️ Tham số cấu hình

### Cài đặt lưới

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `GridDistancePips` | Khoảng cách giữa các mức giá trong lưới (pips) | 20.0 |
| `MaxGridLevels` | Số lượng mức lưới tối đa mỗi phía (trên và dưới giá cơ sở) | 10 |
| `AutoRefillOrders` | Tự động bổ sung lệnh khi lệnh cũ bị đóng | true |

### Cài đặt lệnh Buy Limit

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `EnableBuyLimit` | Cho phép lệnh Buy Limit | true |
| `LotSizeBuyLimit` | Khối lượng Buy Limit (mức 1) | 0.01 |
| `TakeProfitPipsBuyLimit` | Take Profit Buy Limit (pips, 0=off) | 30.0 |
| `EnableMartingaleBuyLimit` | Bật gấp thếp Buy Limit | false |
| `MartingaleMultiplierBuyLimit` | Hệ số gấp thếp Buy Limit (mức 2=x2, mức 3=x4...) | 2.0 |

### Cài đặt lệnh Sell Limit

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `EnableSellLimit` | Cho phép lệnh Sell Limit | true |
| `LotSizeSellLimit` | Khối lượng Sell Limit (mức 1) | 0.01 |
| `TakeProfitPipsSellLimit` | Take Profit Sell Limit (pips, 0=off) | 30.0 |
| `EnableMartingaleSellLimit` | Bật gấp thếp Sell Limit | false |
| `MartingaleMultiplierSellLimit` | Hệ số gấp thếp Sell Limit (mức 2=x2, mức 3=x4...) | 2.0 |

### Cài đặt lệnh Buy Stop

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `EnableBuyStop` | Cho phép lệnh Buy Stop | true |
| `LotSizeBuyStop` | Khối lượng Buy Stop (mức 1) | 0.01 |
| `TakeProfitPipsBuyStop` | Take Profit Buy Stop (pips, 0=off) | 30.0 |
| `EnableMartingaleBuyStop` | Bật gấp thếp Buy Stop | false |
| `MartingaleMultiplierBuyStop` | Hệ số gấp thếp Buy Stop (mức 2=x2, mức 3=x4...) | 2.0 |

### Cài đặt lệnh Sell Stop

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `EnableSellStop` | Cho phép lệnh Sell Stop | true |
| `LotSizeSellStop` | Khối lượng Sell Stop (mức 1) | 0.01 |
| `TakeProfitPipsSellStop` | Take Profit Sell Stop (pips, 0=off) | 30.0 |
| `EnableMartingaleSellStop` | Bật gấp thếp Sell Stop | false |
| `MartingaleMultiplierSellStop` | Hệ số gấp thếp Sell Stop (mức 2=x2, mức 3=x4...) | 2.0 |

### TP Tổng

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `TotalProfitTPOpen` | TP tổng lệnh đang mở (USD, 0=off) | 0.0 |
| `ActionOnTotalProfitOpen` | Hành động khi đạt TP tổng lệnh mở (0=Dừng EA, 1=Reset EA) | Reset EA |
| `TotalProfitTPSession` | TP tổng phiên (USD, 0=off) | 0.0 |
| `ActionOnTotalProfitSession` | Hành động khi đạt TP tổng phiên (0=Dừng EA, 1=Reset EA) | Reset EA |
| `TotalProfitTPAccumulated` | TP tổng tích lũy (USD, 0=off) | 0.0 |

### Cài đặt chung

| Tham số | Mô tả | Giá trị mặc định |
|---------|-------|------------------|
| `MagicNumber` | Magic Number để nhận diện lệnh của EA | 123456 |
| `CommentOrder` | Comment được gắn vào mỗi lệnh | "Grid Balanced V2" |

## 📊 Cách hoạt động

### 1. Khởi tạo lưới
Khi EA được khởi động, nó sẽ:
- Lấy giá hiện tại (BID) làm giá cơ sở
- Tạo một mảng các mức giá cố định dựa trên `GridDistancePips` và `MaxGridLevels`
- Tổng số mức = `MaxGridLevels * 2 + 1` (bao gồm cả trên và dưới giá cơ sở)
- Mức 1 là gần giá cơ sở nhất, mức 2 xa hơn, v.v.

### 2. Quản lý lệnh
Trên mỗi tick:
- EA kiểm tra tất cả các mức giá trong lưới
- Đối với mỗi mức giá:
  - Nếu mức giá ở **phía trên** giá hiện tại:
    - Đặt lệnh **Buy Stop** (nếu `EnableBuyStop = true`)
    - Đặt lệnh **Sell Limit** (nếu `EnableSellLimit = true`)
  - Nếu mức giá ở **phía dưới** giá hiện tại:
    - Đặt lệnh **Buy Limit** (nếu `EnableBuyLimit = true`)
    - Đặt lệnh **Sell Stop** (nếu `EnableSellStop = true`)

### 3. Cân bằng lưới
- EA đảm bảo mỗi mức giá chỉ có tối đa 1 lệnh Buy và 1 lệnh Sell
- Tránh đặt lệnh trùng lặp tại cùng một mức giá
- Bỏ qua các mức giá quá gần giá hiện tại (nhỏ hơn 5 pips)

### 4. Gấp thếp (Martingale)
- Mức 1: Lot size cơ bản (không gấp)
- Mức 2: Lot size × Multiplier (ví dụ: x2)
- Mức 3: Lot size × Multiplier² (ví dụ: x4)
- Mức n: Lot size × Multiplier^(n-1)

**Ví dụ:** Lot = 0.01, Multiplier = 2.0
- Mức 1: 0.01 lot
- Mức 2: 0.02 lot (x2)
- Mức 3: 0.04 lot (x4)
- Mức 4: 0.08 lot (x8)

### 5. Ghi nhớ lot size theo mức lưới
- Khi một lệnh đạt TP, EA ghi nhớ lot size của lệnh đó tại mức lưới đó
- Khi bổ sung lệnh lại (nếu `AutoRefillOrders = true`), EA sử dụng đúng lot size đã lưu thay vì tính toán lại
- Đảm bảo tính nhất quán trong chiến lược gấp thếp

### 6. TP Tổng

#### TP Tổng Lệnh Đang Mở
- Tính tổng profit của tất cả lệnh đang mở (floating profit)
- Khi đạt mức USD đặt → Reset EA hoặc Dừng EA

#### TP Tổng Phiên
- Tính: **Vốn hiện tại - Vốn ban đầu** (lãi)
- Vốn hiện tại = Equity (Balance + Floating Profit/Loss)
- Vốn ban đầu = Equity khi EA khởi động hoặc reset
- Khi đạt mức USD đặt → Reset EA (reset phiên về 0) hoặc Dừng EA

#### TP Tổng Tích Lũy
- Tích lũy profit qua các lần reset
- Mỗi lần reset, profit phiên được cộng vào tích lũy
- Khi đạt mức USD đặt → Dừng EA vĩnh viễn

### 7. Reset EA
Khi reset:
- Đóng tất cả pending orders
- Đóng tất cả positions đang mở
- Reset basePrice về giá hiện tại
- Reset grid levels
- Reset lot sizes đã lưu
- Reset phiên (tổng phiên về 0)
- Cập nhật vốn ban đầu mới
- EA tiếp tục hoạt động với cấu hình mới

### 8. Dừng EA
Khi dừng:
- Đóng tất cả pending orders
- Đóng tất cả positions đang mở
- Set flag dừng EA
- EA không quản lý lệnh nữa
- EA không mở thêm lệnh nào

## ⚠️ Cảnh báo rủi ro

- **Giao dịch lưới có rủi ro cao**: Chiến lược này có thể tạo ra nhiều lệnh đồng thời, làm tăng yêu cầu ký quỹ
- **Gấp thếp tăng rủi ro**: Gấp thếp có thể làm tăng lot size nhanh chóng, cần quản lý ký quỹ cẩn thận
- **Thị trường trending**: Lưới có thể hoạt động kém hiệu quả trong thị trường có xu hướng mạnh một chiều
- **Yêu cầu ký quỹ**: Đảm bảo tài khoản có đủ ký quỹ để chịu được nhiều lệnh cùng lúc, đặc biệt khi sử dụng gấp thếp
- **Kiểm thử kỹ**: Luôn test EA trên tài khoản demo trước khi sử dụng trên tài khoản thật
- **Không có đảm bảo lợi nhuận**: Trading luôn có rủi ro, không có chiến lược nào đảm bảo 100% lợi nhuận

## 📝 Lưu ý kỹ thuật

- **File EA**: `GridBalancedTradingV2.mq5`
- EA được viết cho **MetaTrader 5** (MQL5), không tương thích với MT4
- Sử dụng thư viện `Trade.mqh` để thực hiện giao dịch
- Tất cả giá được chuẩn hóa theo số chữ số thập phân của symbol
- EA tự động tính toán chuyển đổi pips sang giá dựa trên symbol
- Không sử dụng Stop Loss (đã được loại bỏ trong V2)
- Lot size được chuẩn hóa về 2 chữ số thập phân

## 🔍 Ví dụ cấu hình

### Cấu hình thận trọng (Conservative)
```
GridDistancePips = 30.0
MaxGridLevels = 5
LotSizeBuyLimit = 0.01
LotSizeSellLimit = 0.01
LotSizeBuyStop = 0.01
LotSizeSellStop = 0.01
TakeProfitPipsBuyLimit = 40.0
TakeProfitPipsSellLimit = 40.0
TakeProfitPipsBuyStop = 40.0
TakeProfitPipsSellStop = 40.0
EnableMartingaleBuyLimit = false
EnableMartingaleSellLimit = false
EnableMartingaleBuyStop = false
EnableMartingaleSellStop = false
TotalProfitTPSession = 50.0
ActionOnTotalProfitSession = Reset EA
```

### Cấu hình tích cực (Aggressive)
```
GridDistancePips = 15.0
MaxGridLevels = 15
LotSizeBuyLimit = 0.05
LotSizeSellLimit = 0.05
LotSizeBuyStop = 0.05
LotSizeSellStop = 0.05
TakeProfitPipsBuyLimit = 25.0
TakeProfitPipsSellLimit = 25.0
TakeProfitPipsBuyStop = 25.0
TakeProfitPipsSellStop = 25.0
EnableMartingaleBuyLimit = true
MartingaleMultiplierBuyLimit = 2.0
EnableMartingaleSellLimit = true
MartingaleMultiplierSellLimit = 2.0
TotalProfitTPSession = 100.0
ActionOnTotalProfitSession = Reset EA
```

### Cấu hình chỉ Buy Limit với gấp thếp
```
EnableBuyLimit = true
EnableSellLimit = false
EnableBuyStop = false
EnableSellStop = false
LotSizeBuyLimit = 0.01
TakeProfitPipsBuyLimit = 30.0
EnableMartingaleBuyLimit = true
MartingaleMultiplierBuyLimit = 2.0
```

## 🔄 So sánh V1 và V2

| Tính năng | V1 | V2 |
|-----------|----|----|
| Bật/tắt loại lệnh | Buy/Sell chung | Riêng từng loại (Buy Limit, Sell Limit, Buy Stop, Sell Stop) |
| Lot size | Chung cho tất cả | Riêng cho từng loại lệnh |
| Take Profit | Chung cho tất cả | Riêng cho từng loại lệnh |
| Stop Loss | Có | Không (đã xóa) |
| Gấp thếp | Không | Có (riêng cho từng loại) |
| Ghi nhớ lot size | Không | Có (theo mức lưới) |
| TP tổng | Không | Có (3 loại) |
| Reset EA | Không | Có |
| Dừng EA | Không | Có (đóng tất cả lệnh) |

## 📞 Hỗ trợ

Nếu gặp vấn đề hoặc có câu hỏi về **Grid Balanced Trading V2**, vui lòng:
- Kiểm tra log trong tab "Experts" của MetaTrader 5
- Xác nhận file `GridBalancedTradingV2.mq5` đã được compile thành công (không có lỗi trong tab "Errors")
- Đảm bảo AutoTrading đã được bật
- Kiểm tra Magic Number để đảm bảo không trùng với EA khác
- Kiểm tra log debug để theo dõi profit và trạng thái EA

## 📜 Giấy phép

EA này được cung cấp "as-is" không có bất kỳ bảo đảm nào. Sử dụng trên trách nhiệm của bạn.

---

**Lưu ý**: Luôn test kỹ trên tài khoản demo trước khi sử dụng thực tế. Giao dịch có rủi ro, có thể dẫn đến mất vốn. Đặc biệt cẩn thận khi sử dụng tính năng gấp thếp vì có thể làm tăng rủi ro đáng kể.
