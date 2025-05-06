<!-- Banner -->
<p align="center">
  <a href="https://www.uit.edu.vn/" title="Trường Đại học Công nghệ Thông tin" style="border: none;">
    <img src="https://i.imgur.com/WmMnSRt.png" alt="Trường Đại học Công nghệ Thông tin | University of Information Technology">
  </a>
</p>

<h1 align="center"><b>Thiết kế SRAM 6T </b></h1>

# Thành viên nhóm
| STT    | MSSV          | Họ và Tên              |Chức Vụ    | Github                                                  | Email                   |
| ------ |:-------------:| ----------------------:|----------:|--------------------------------------------------------:|-------------------------:
| 1      | 22520506      | Lê Minh Hùng        |Thành viên |[LeMinhHung120204](https://github.com/LeMinhHung120204)            |22520506@gm.uit.edu.vn   |
| 2      | 22521198      | Đoàn Đăng Quang        |Thành viên | |22521198@gm.uit.edu.vn   |

---
# GIỚI THIỆU MÔN HỌC
* **Tên môn học:** Thiết kế vi mạch số
* **Mã môn học:** CE222
* **Mã lớp:** CE222.P21
* **Năm học:** HK2 (2024 - 2025)
* **Giảng viên**: Ngô Hiếu Trường

---
# ĐỒ ÁN
* **Đề tài:** Thiết kế SRAM 6T

---
# Kiến trúc tổng quát SRAM
![SRAM block diagram.](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/block_diagram_new2.png?raw=true)

Ở mức cơ bản, kiến trúc SRAM bao gồm: Mảng ô nhớ (Bit Cell Array), Mạch nạp (Precharge Circuit), Bộ khuếch đại cảm nhận (Sense Amplifier), Bộ điều khiển ghi (Write Driver), Bộ giải mã hàng (Decoder).

---
# Kiến trúc bit cell
![Bit cell circuit.](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/Bitcell.png?raw=true)

Cấu trúc ô nhớ gồm 4 transistor tạo thành một cặp inverter mắc chéo (cross-coupled inverters) nhằm duy trì trạng thái lưu trữ ổn định, và 2 transistor truyền (access transistors) được điều khiển bởi tín hiệu Word Line (WL) để kết nối cell với các đường Bit Line (BL và BLB) trong quá trình đọc và ghi dữ liệu.

Để cell có thể đọc và không bị mất dữ liệu, và có thể lật giá trị trong cell trong lúc ghi thì kích thước của các transistor trong cell phải tuân theo tỉ lệ nhất định.

## Read Operation:
![read_operation]()