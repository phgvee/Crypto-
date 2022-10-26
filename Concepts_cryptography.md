# [Crypto] Một Số Khái Niệm Cơ Bản Trong Mật Mã Học
## 1. Cryptography
Cryptography ( mật mã học) là ngành khoa học nghiên cứu về mã hóa và giải mã thông tin với mục đích nghiên cứu các phương pháp, cách thức để chuyển đổi một thông tin từ dạng “đọc hiểu” sang dạng “đọc nhưng không hiểu” và ngược lại.

Các chức năng chính của mật mã có thể được kể đến:
*  Tính bảo mật (quyền riêng tư): đảm bảo không ai có thể đọc và hiểu được tin nhắn ngoại trừ người nhận dự bị.
* Tính xác thực: quá trình xác minh danh tính của một người.
* Tính toàn vẹn: đảm bảo tin nhắn khi đến tay người nhận không bị thay đổi theo bất kỳ hình thức nào so với bản gốc
* Không thoái thác: đây là cơ chế nhằm chứng minh rằng người gửi đã thực sự gửi tin nhắn này.
* Trao đổi khóa: phương thức chia sẻ các khóa mật mã giữa người gửi và người nhận.

## 2. Crytanalysics
Cryptanalysis là giải mã và phân tích các mã, mật mã hoặc văn bản được mã hóa. Cryptanalysis sử dụng công thức toán học để tìm kiếm các lỗ hổng thuật toán và đột nhập vào hệ thống an ninh mật mã hoặc thông tin.

![](https://i.imgur.com/kDiyX8P.png)

Một ví dụ dễ hiểu cho Cryptanalysics chính là kỹ thuật phân tích tần suất được áp dụng thành công cho các thuật toán mã hóa cổ điển.  bằng cách tính tần suất các ký tự hoặc nhóm ký tự trong bản mã và so sánh với tần suất thực tế trong các văn bản thường.
## 3. Encode / Decode
Encode là cách thức chuyển hóa dữ liệu của các bạn thành 1 dạng khác mà có thể tiêu thụ được trên các hệ thống khác nhau, và tất nhiên Encode không hề bảo mật. Ta chỉ cần dùng đúng thuật toán encode là có thể giải mã ngược lại mà không cần một key nào

ví dụ : chuyển một kí tự sang bit : A -> 1000001 ( dựa vào ASCII)

Và quá trình chuyển từ 1000001 -> A chính là Decode, ngược lại so với Encode

Dưới đây là một ví dụ minh họa cho việc Decode từ một số nguyên lớn sang dạng bytes :
```python=
from Crypto.Util.number import *
l = 11515195063862318899931685488813747395775516287289682636499965282714637259206269
print(long_to_bytes(l))
#crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
```
## 4. Encryption / Decryption
Encryption là thuật ngữ chỉ đến quá trình mã hóa thông tin từ đọc hiểu sang đọc được nhưng không hiểu được. Encryption mang tính bảo mật hơn vì đi kèm với nó chính là 1 secret-key mà chỉ người gửi và người nhận biết

![](https://i.imgur.com/lg6FH6h.png)

Decryption là thuật ngữ chỉ đến quá trình giải mã nhằm lấy lại thông tin ban đầu. Nó ngược lại với quá trình Encryption, nghĩa là chuyển từ cái không hiểu sang cái đọc hiểu được. Để có thể Decrypt được thì cần đủ 3 yếu tố sau:

1. Đầu tiên chắc chắn là đoạn dữ liệu đã bị mã hóa
2. Thuật toán dùng để mã hóa
3. Cuối cùng quan trọng nhất vẫn là key mật mà người tạo đã sử dụng.

Những ví dụ minh họa của Encrytion và Decryption sẽ được mình liệt kê trong những khái niệm tiếp theo.
## 5. Symmetric Cryptography
Là những hệ mật được sử dụng chung 1 khóa trong quá trình mã hóa và giải mã. Do đó khóa phải được giữ bí mật tuyện đối.

Một số hệ mật mã khóa đối xứng hiện đại mà mình thấy hay được sử dụng là DES, AES, RC4, RC5,…

![](https://i.imgur.com/26yYUVT.png)

. Cách hoạt động của khóa đối xứng có thể được hiểu như sao :
* . Bạn A muốn gửi thông điệp( M) cho bạn B , nhưng A không muốn những đứa khác xem được nên A quyết đinh mã hóa nó bằng một hàm mã hóa ( gọi là hàm E), một khóa K ( tất nhiên là cái khóa này chỉ mỗi A và B biết :>)
* . Giờ thì cái thông điệp sau khi mã hóa ( gọi là C) C = D(M,K)
* . A gửi C cho B mà ko cần sợ đứa nào khác đọc được
* . B bắt được thông điệp thì B dùng cái K để giải mã thông qua hàm giải mã ( gọi là D) D(C,K) = M , giờ thì thu được thông điệp M đúng như cái mà A đã gửi .

Nhưng do hệ mật mã khóa đối xứng còn nhiều hạn chế nên chúng ta có thêm một hệ mật mã mới : hệ mật mã khóa bất đối xứng

## 6. Asymmetric Cryptography
Hệ mật mã khóa bất đối xứng sẽ có hai khóa là public-key và Private Key

Tiêu biểu cho hệ mật này chính là mã hóa RSA :tada: : 
![](https://i.imgur.com/Hy7HzKl.png)

Hệ mật sẽ bao gồm:
* Bản rõ (plaintext-M): bản tin được sinh ra bởi bên gửi
* Bản mật (ciphertext-C): bản tin che giấu thông tin của bản rõ, được gửi tới bên nhận qua một kênh không bí mật
* Khóa: Bên nhận có 1 cặp khóa:
* Khóa công khai (Kub) : công bố cho tất cả mọi người biết (kể cả hacker)
* Khóa riêng (Krb) : bên nhận giữ bí mật, không chia sẻ cho bất kỳ ai
* Mã hóa (encrypt-E): C = E(Kub, M)
* Giải mã (decrypt): M = D(Krb, C) = D(Krb, E(Kub, M))

Dưới đây là minh họa cho RSA , về cách hoạt động thì các cậu có thể search google :smiley_cat: 

```python=
from audioop import mul
from operator import invert
from Crypto.Util.number import *
from gmpy2 import *
n = 882564595536224140639625987659416029426239230804614613279163
q = 857504083339712752489993810777
p = 1029224947942998075080348647219
e = 65537
c = 77578995801157823671636298847186723593814843845525223303932 # cipher
phi = mul(q-1,p-1)
d = invert(e,phi)
m = pow(c,d,n)
print(m)
# m =13371337
```
 
## 7. Block Cipher

Mật mã khối (block cipher) là một phương pháp mã hóa dữ liệu trong các khối (block) để tạo ra bản mã (ciphertext) bằng cách sử dụng một khóa mật mã (cryptographic key) và thuật toán (algorithm). Mật mã khối (block cipher xử lý đồng thời các khối có kích thước cố định

 Hầu hết các mật mã khối (block cipher) hiện đại được thiết kế để mã hóa dữ liệu trong các khối có kích thước cố định là 64 hoặc 128 bit.

*Dưới đây là mã hóa AES mode CBC:*
![](https://i.imgur.com/CPdxftI.png)

Mật mã khối (block cipher) sử dụng một khóa đối xứng (symmetric key) và thuật toán để mã hóa (encrypt) và giải mã (decrypt) một khối dữ liệu. Mật mã khối yêu cầu (block cipher) một vectơ khởi tạo (initialization vector – IV) được thêm vào bản rõ (plaintext) đầu vào để tăng không gian khóa (keyspace) của mật mã (cipher) và khiến việc sử dụng brute force để phá khóa (key) khó khăn hơn. IV có nguồn gốc từ trình tạo số ngẫu nhiên (random number generator), được kết hợp với văn bản trong khối đầu tiên và khóa để đảm bảo tất cả các khối tiếp theo tạo ra văn bản mã không khớp với văn bản của khối mã hóa đầu tiên.

 ## 8. Stream Cipher
 Với các hệ mã dòng (stream cipher), ta sẽ xử lý trên từng bit của bản rõ. Một hệ mã dòng rất nổi tiếng đó là One Time Pad (OTP), lưu ý các bạn đừng nhầm lẫn với One Time Password. Với bản rõ m và khóa k có cùng độ dài theo bit, One-Time-Pad được xác định như sau:
```python=
E(m, k) = m XOR k = c
D(c, k) = c XOR k = (m XOR k) XOR k = m
```
* Với OTP, khóa k phải đáp ứng 3 điều kiện sau đây:
* Độ dài của khóa phải bằng kích thước bản rõ.
* Khóa phải được chọn hoàn toàn ngẫu nhiên (truly random)
* Và khóa chỉ được sử dụng một lần.

Nếu thỏa mãn 3 điều kiện trên, hệ mã OTP sẽ là an toàn tuyệt đối ([perfect security](https://en.wikipedia.org/wiki/One-time_pad#Perfect_secrecy)) theo định lý của [Clause Shannon](https://en.wikipedia.org/wiki/Claude_Shannon), tức là kẻ tấn công sẽ không thể biết được thông tin gì của bản rõ m chỉ từ bản mã c.

## 9. Hash Function
Hash Function hay hàm băm là 1 hàm mã hóa trong máy tính, hàm này được dùng để mã hóa các dữ liệu với dung lượng bất kỳ về một loại dữ liệu khác với dung lượng nhất định

Giả dụ, bạn tải một video trên Youtube về, sau đó cho nó chạy qua hàm băm có tên MD5 sẽ trả về một chuỗi dài 32 ký tự, hoặc bạn tải một bức ảnh trên mạng về, cho chạy qua hàm MD5, thứ bạn nhận được vẫn là một chuỗi dài 32 ký tự. Thậm chí, nếu bạn cho chạy từ “apple” qua hàm hash MD5 kia, kết quả sẽ là:

“1f3870be274f6c49b3e31a0c6728957f”

Lại là một chuỗi có 32 ký tự. Những thuật toán băm khác cũng hoạt động tương tự như vậy, bạn cho bất kỳ thứ gì vào hàm, đầu ra sẽ luôn là một chuỗi có độ dài nhất định.

![](https://i.imgur.com/5km64yV.png)

 Một số tính chất của hàm băm :face_with_monocle: 
* Không thể đảo ngược ( có nghĩa là từ giá trị sau khi băm không thể suy ra giá trị ban đầu)
* Tính tránh va chạm (xảy ra khi hai giá trị khác nhau nhưng khi chạy qua hàm băm lại trả về hai kết quả giống nhau)
* Tính hiệu quả (thời gian tính toán những giá trị băm phải nhanh)
* Tính nhạy cảm (chỉ cần sự thay đổi nhỏ trong giá trị ban đầu có thể thay đổi hoàn toàn giá trị băm).

