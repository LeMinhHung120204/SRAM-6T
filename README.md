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
| 2      | 22521198      | Đoàn Đăng Quang        |Thành viên |[QuangTheGreat](https://github.com/QuangTheGreat) |22521198@gm.uit.edu.vn   |

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
![read_operation](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/ReadOperation.png?raw=true)

Trước khi đọc, hai đường bitline (BL và BLB) được sạc đầy lên mức cao (V<sub>DD</sub>).
Giả sử bitcell đang lưu giá trị logic '0', tức điểm Q = LOW, Q̅ = HIGH. Trong trạng thái này, các transistor N4, N2, P1 và N3 đang dẫn.

Khi wordline được kích hoạt, bitline BL sẽ được nối với điểm Q thông qua transistor truy cập N4.
Do chênh lệch điện áp giữa BL (HIGH) và Q (LOW), sẽ xuất hiện một xung tăng điện áp nhỏ ∆V tại Q (tức điểm lưu logic '0').

Trong khi đó, điểm Q̅ vẫn giữ nguyên mức HIGH do không có dòng chảy qua N3.
Để đảm bảo giá trị lưu trữ không bị lật trong quá trình đọc, biên độ ∆V tại Q phải nhỏ hơn ngưỡng kích dẫn của NMOS (∆V < V<sub>tn</sub>).

Dựa trên điều kiện này, phương trình mô tả dòng điện trong quá trình đọc có thể được thiết lập, từ đó suy ra tỉ lệ kích thước (sizing) phù hợp giữa transistor pull-down và access – còn được gọi là cell ratio (Eq.1): 

![Eq.1](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/Eq-1.jpeg?raw=true)

## Write Operation
![write_operation](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/WriteOperation.png?raw=true)

Giả sử bitcell đang lưu giá trị logic '0', tức điểm Q = LOW, Q̅ = HIGH.

Trong trạng thái này, các transistor N4, N2, P1 và N3 đang dẫn.

![write_operation](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/WriteOperation2.png?raw=true)

Để ghi vào giá trị logic ‘1’, các đường bitline được thiết lập: BL = HIGH, BLB = LOW.

Trong quá trình này, tại điểm Q (ban đầu = LOW), xuất hiện một xung tăng điện áp nhỏ ∆V < V<sub>tn</sub>, không đủ để làm lật bitcell.

Tuy nhiên, tại điểm Q̅ (ban đầu = HIGH), do được nối với BLB = LOW thông qua transistor truy cập, xuất hiện điện áp giảm ∆V₂ sao cho ∆V₂ > V<sub>tn</sub>. Điều này khiến transistor pull-down (N1) bật dẫn và kéo điểm Q̅ xuống mức LOW, dẫn đến bitcell bị lật.

Dựa trên điều kiện này, phương trình mô tả dòng điện trong quá trình ghi có thể được thiết lập, từ đó suy ra tỉ lệ kích thước (sizing) phù hợp giữa transistor pull-up và access – còn gọi là pull-up ratio (xem Eq.2):

![Eq.2](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/Eq-2.jpeg?raw=true)

---
# Waveform result

![waveform](https://github.com/LeMinhHung120204/SRAM-6T/blob/main/images/waveform.png?raw=true)

SRAM hoạt động ổn định ở tần số 1.52 GHz, cho thấy thiết kế đạt được độ tin cậy cao trong điều kiện mô phỏng.

---
# Reference

[1] Y. Alekhya and J. Sudhakar, “Design Analysis of SRAM Cell with Improved 
Noise Margin based on Aspect Ratio Adjustments,” 2017, doi: 
10.29042/2018-2645-2650.  

[2] N. H. E. Weste and D. M. Harris, CMOS VLSI Design: A Circuits and Systems 
Perspective, 4th ed., Boston, MA, USA: Addison-Wesley, 2010.   

[3] D. Dutt, P. Mittal, B. Rawat, and B. Kumar, “Design and Performance Analysis of 
High-Performance Low Power Voltage Mode Sense Amplifier for Static RAM,”.

[4] GitHub repository: [6T-SRAM Cell Design by Gautam19499](https://github.com/gautam19499/6T-SRAM_cell_design.git)