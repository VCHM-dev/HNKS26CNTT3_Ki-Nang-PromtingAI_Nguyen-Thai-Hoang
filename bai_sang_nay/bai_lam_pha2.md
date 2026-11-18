## 4.2. Trích xuất tin nhắn đặt vé ra JSON

**KET QUA AI**

```text
[
  {
    "ma_goi": "SVT",
    "ngay_su_kien": "2026-12-20",
    "nguoi_lon": 2,
    "tre_em": 1,
    "loai_ve": "thuong",
    "ghi_chu": null
  },
  {
    "ma_goi": "FZ",
    "ngay_su_kien": "2027-01-05",
    "nguoi_lon": 3,
    "tre_em": 0,
    "loai_ve": "thuong",
    "ghi_chu": "hỗ trợ xe lăn"
  },
  {
    "ma_goi": "VIP",
    "ngay_su_kien": null,
    "nguoi_lon": 4,
    "tre_em": 0,
    "loai_ve": "vip",
    "ghi_chu": "hỗ trợ tìm chỗ cho người khiếm thị"
  }
]
```

**Link trò chuyện:** https://share.gemini.google/Aci1RHZQHt2e

## 4.3. Báo giá vé bằng Chain-of-Thought

**KET QUA AI**

```text
```python
price_adult = 1200000
num_adults = 5
adult_total = num_adults * price_adult

# 2 children (8 and 10 years old -> 5 to 11 -> 70%)
# 1 child (3 years old -> under 5 -> free)
price_child_5_11 = price_adult * 0.7
child_total = 2 * price_child_5_11 + 1 * 0

ticket_total = adult_total + child_total

# Group discount: >= 5 adults -> 5% off ticket_total
discount = ticket_total * 0.05
ticket_after_discount = ticket_total - discount

# Priority seat surcharge: 300,000 per person (1 adult)
surcharge = 1 * 300000

grand_total = ticket_after_discount + surcharge

print(f"adult_total: {adult_total:,.0f}")
print(f"child_total: {child_total:,.0f}")
print(f"ticket_total: {ticket_total:,.0f}")
print(f"discount: {discount:,.0f}")
print(f"ticket_after_discount: {ticket_after_discount:,.0f}")
print(f"surcharge: {surcharge:,.0f}")
print(f"grand_total: {grand_total:,.0f}")


```

```text
adult_total: 6,000,000
child_total: 1,680,000
ticket_total: 7,680,000
discount: 384,000
ticket_after_discount: 7,296,000
surcharge: 300,000
grand_total: 7,596,000


```

1. **Tiền người lớn:** Nhóm mua gói SVT (1.200.000 đồng/người lớn) cho 5 người lớn:
$5 \times 1.200.000 = 6.000.000$ đồng.
2. **Tiền trẻ em:** Có 2 trẻ em từ 5 đến 11 tuổi (8 tuổi và 10 tuổi) tính 70% giá vé người lớn và 1 bé 3 tuổi (dưới 5 tuổi) được miễn phí:
$2 \times (1.200.000 \times 70\%) + 1 \times 0 = 2 \times 840.000 + 0 = 1.680.000$ đồng.
3. **Tiền vé:** Tổng tiền vé của người lớn và trẻ em:
$6.000.000 + 1.680.000 = 7.680.000$ đồng.
4. **Giảm giá nhóm:** Vì nhóm có từ 5 người lớn trở lên nên được giảm 5% trên tiền vé:
$7.680.000 \times 5\% = 384.000$ đồng (Tiền vé sau giảm: $7.680.000 - 384.000 = 7.296.000$ đồng).
5. **Phụ thu:** Có 1 người lớn chọn khu ghế ưu tiên (300.000 đồng/người, không giảm giá):
$1 \times 300.000 = 300.000$ đồng.
6. **Tổng tiền:** Tiền vé sau giảm cộng với phụ thu:
$7.296.000 + 300.000 = 7.596.000$ đồng.

[RESULT: 7.596.000 đồng]
```

**Link trò chuyện:** https://share.gemini.google/9NvomtAc1Vcp

### b) Kiểm tra kết quả AI

AI Đúng

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
```json
{
  "loai_su_co": "sai_khu_vuc",
  "so_khach": 2,
  "so_hiep_bi_anh_huong": 2,
  "tom_tat": "Khán giả mua vé gói SVT bị xếp sai sang khu vực không mái che trong 2 hiệp đầu trời mưa."
}

```
```

**Link trò chuyện:** https://share.gemini.google/o8W5qS7cEVvG
