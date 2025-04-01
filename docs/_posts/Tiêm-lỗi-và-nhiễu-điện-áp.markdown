---
layout: post
title: "Tiêm lỗi và nhiễu điện áp"
date: 2025-04-01
categories: side-channel-attack
---
# Khái niệm
## Tiêm lỗi (Fault-Injection)
Tiêm lỗi là một kỹ thuật tấn công dùng can thiệp vật lý để gây ra lỗi trong hệ thống và từ đó ảnh hưởng đến hành vi của hệ thống. Hiểu đơn giản có nghĩa là thay đổi các giá trị đầu vào của hệ thống để tạo ra lỗi không mong muốn trên hệ thống. Trong trường hợp vi điều khiển hoặc các hệ thống nhúng nói chung, nguồn điện cấp hoặc bộ tạo xung clock trên bảng mạch bị can thiệp vật lý để gây ra các trạng thái lỗi.
## Nhiễu điện áp (Voltage Glitching)
Trong nhiễu điện áp, nguồn điện áp cung cấp cho chip được kéo gần về 0V-GND trong một thời gian rất ngắn (theo đơn vị nanosecond đến vài microsecond) dẫn đến việc chip không còn hoạt động chính xác. Ví dụ, việc ghi hoặc xóa một ô nhớ không thể thực hiện thành công hoặc việc kiểm tra điều kiện bắt buộc trên một đoạn mã bị bỏ qua. 

![Đồ họa mô phỏng sự nhiễu điện áp]({{ "/assets/images/voltage-glitching.webp" | relative_url }})
## Ví dụ cụ thể trên STM32F407VET6
Trong ví dụ này mình sẽ dùng phương pháp nhiễu điện áp để vượt qua câu điều kiện được lập trình trên chip
```
void main() {
    clock_init();
    led_init();
    while(1) {
    // trap code
    }
    blink_led();
}
```
Ví dụ khối code như trên, đèn LED sẽ không bao giờ được nhấp nháy do dòng lập while() luôn đúng, trong trường hợp này mình có thể dùng nhiễu điện áp để bỏ qua vòng lặp while() và đèn LED sẽ nhấp nháy