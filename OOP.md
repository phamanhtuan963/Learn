_ Class là định nghĩa của đối tượng gồm trạng thái(thuộc tính) và hành động(phương thức) của đối tượng đó
+ Phương thức nó rất giống với hàm nên nó cũng có các tính chất như hàm đó chỉ khác là phương thức nằm trong một lớp đối tượng và muốn gọi đến nó phải thông qua lớp đối tượng này.
_ Để truy suất thuộc tính/ phương thức của đối tượng
Trước tiên phải khởi tạo đối tượng:
$object = new Doituong();
Cú pháp: $object->{Thuộc tính}
	$object->{Phương thức}

_ Hàm trong lớp đối tượng gọi đến các thuộc tính của chính mình bằng cú pháp sau:
$this->ten_thuoc_tinh;

_ Tính kế thừa: 
Cú pháp: Class classCon extends classCha{}
Vậy classCon có tất cả thuộc tính, phương thức của classCha nên không cần viết lại
Cách gọi phương thức và thuộc tính của lớp cha
Có 2 cách: từ bên trong lớp con và gọi từ bên ngoài lớp
+ Gọi bên trong lớp con: do kế thừa từ lớp cha nên thuộc tính và phương thức đều xem như là của lớp con nên cách gọi cũng như cách nó gọi các thuộc tính/ phương thức của chính nó, đó là
Cú pháp: $this->thuoctinh, $this->phuong_thuc()
Tuy nhiên để phân biệt hàm nào của cha, hàm nào của con người ta gọi bằng từ khóa:
Cú pháp: parent::thuoctinh, parent::phuong_thuc()
+ Gọi từ bên ngoài lớp: Cách gọi cũng như cách gọi phương thức bên trong lớp con, tuy nhiên không sử dụng được gọi phương thức như trên(Gọi chính hàm gọi lớp cha bên trong lớp con)

_ Mức truy cập private, protected và public
Private: thành phần chỉ dành riêng cho nội bộ của lớp, nghĩa là không thể truy xuất tới thành phần lớp con hoặc bên ngoài lớp
Mức truy cập private thường được sử dụng với:
+ Các thuộc tính nhằm bảo vệ chúng, tránh sự truy cập tự do từ bên ngoài. Các thuộc tính này sẽ có hàm SET và GET gán và lấy dữ liệu.
+ Các phương thức trung gian tính toán trong nội bộ của đối tượng mà ta không muốn bên ngoài có thể can thiệp vào

Protected: cho phép truy xuất nội bộ trong lớp đó và lớp kế thừa, riêng bên ngoài lớp sẽ không truy xuất được. Mức protected thường được dùng cho những phương thức và thuộc tính có khả năng bị lớp con định nghĩa lại.

Public: truy cập tới phương thức và thuộc tính ở bất cứ đâu, dù trong nội bộ của lớp hay ở lớp con hay cả bên ngoài lớp đều được
Khi khai báo thuộc tính là public ta có thể dùng từ khóa "var" để thay thế cho public
Khi khai báo hàm là public nếu ta không đặt từ public ở đầu thì php sẽ tự hiểu hàm này là public

_ Khi nào sử dụng private, protected và public
Dùng hàm Get và SET cho việc gán và lấy dữ liệu cho các thuộc tính để sau này thay đổi chỉ cần vào hai hàm này sửa, không cần thao tác trực tiếp trên thuộc tính
+ Khi nào sử dụng private: thông thường để an toàn dữ liệu các thuộc tính đều ở dạng private, nhưng điều này rất phiền vì phải tạo thêm SET và GET. Tuy nhiên có những trường hợp bắt buộc dùng private để an toàn cho đối tượng
 ++ Những thuộc tính có tính biến đổi dữ liệu khi nhập và lấy dữ liệu như username và password
 ++ Những phương thức chỉ dùng cho nội bộ lớp đó, không có sử dụng bên ngoài lớp

+ Khi nào sử dụng protected: thường được dùng khi biết chắc là có lớp khác sẽ kế thừa lớp này và những phương thức, thuộc tính đó chỉ được dùng trong lớp kế thừa nó

+ Khi nào sử dụng public: dùng để có thể gọi ở mọi nơi từ trong nội bộ lớp đến lớp kế thừa nó, thậm chí cả bên ngoài lớp cũng gọi được. Những hàm được khai báo public thường được dùng để lấy và xuất dữ liệu ra bên ngoài như hàm SET và GET.

Kế thừa lồng:
Các mức độ truy cập trong kế thừa lồng,
Ở dạng public thì tất cả các lớp con dù ở cấp độ nào cũng có thể truy xuất vào được. (kể cả ngoài lớp con)
Ở dạng protected thì tất cả lớp kế thừa nó dù lồng bao nhiêu lần cũng có thể sử dụng
Ở dạng private thì chỉ dùng trong lớp đó.

_ Tính đa hình trong lập trình php được hiểu là Lớp con sẽ viết lại những phương thức (cùng tên) ở lớp cha(overwrite).

_ Tính đóng gói là tính chất không cho phép người dùng hay đối tượng khác thay đổi thuộc tính của đối tượng, nếu muốn thay đổi bên trong đối tượng thì phải được sự chấp thuận của đối tượng đó thông qua mức độ truy cập private, protected và public. (Hoặc hàm GET và SET).

_ Hàm khởi tạo sẽ tự động gọi khi bạn khởi tạo một đối tượng, còn hàm hủy thì sẽ được gọi khi đối tượng bị hủy
+ Hàm khởi tạo cũng là một hàm bình thường nhưng có đặc biệt là nó luôn được gọi tới khi khởi tạo đối tượng. Hàm khởi tạo có thể có các tham số hoặc không tham số, có thể có giá trị trả về hoặc không. Ở hàm bình thường khác có thể gọi lại hàm khởi tạo và hàm khởi tạo cũng có thể gọi một hàm bình thường khác
+ Có 2 cách khai báo tên hàm khởi tạo:
 ++ Khai báo trùng với tên lớp (Cách này sẽ không còn trong phiên bản PHP trong tương lai)
 ++ Khai báo với tên __construct
Hàm khởi tạo cũng có thể có các tham số truyền vào, lúc này khi khởi tạo đối tượng ta sẽ truyền các tham số đó vào trong lớp

+ Hàm khởi tạo trong kế thừa, trường hợp lớp cha và lớp con có hàm khởi tạo, khi khởi tạo đối tượng lớp con thì hàm khởi tạo con sẽ được chạy. Còn nếu lớp con không có hàm khởi tạo thì sẽ chạy hàm khởi tạo của lớp cha.
Trường hợp lớp con có hàm khởi tạo và lớp cha không có, thì sẽ chạy hàm khởi tạo lớp con
Trường hợp cả 2 không có hàm khởi tạo thì sẽ không có hàm khởi tạo nào được chạy khi khởi tạo đối tượng

+ Hàm hủy là hàm tự động gọi khi đối tượng bị hủy, nó thường được sử dụng để giải phóng bộ nhớ chương trình. Trong đối tượng hàm hủy có thể có hoặc không
+ Tương tự hàm khởi tạo ưu tiên hàm hủy lớp con, nếu không có sẽ chạy lớp cha, cón nếu cả 2 không có thì sẽ không chạy hàm hủy nào.

_ Lớp trừu tượng abstract định nghĩa các hàm (phương thức) mà từ đó các lớp con sẽ kế thừa nó và Overwrite lại(tính đa hình). Tất cả phương thức của lớp abstract đều phải khai báo là abstract và phải ở mức protected và public, không được ở mức private. Lớp abstract có thể có thuộc tính nhưng không được khai báo là abstract, và không khởi tạo được đối tượng.
Cú pháp: abstract class Classname{}
+ Không được định nghĩa dòng lệnh nào trong hàm abstract, ngoại trừ __construct, hàm thường
+ Mức truy cập hàm phải ở public hoặc protected để lớp kế thừa có thể định nghĩa lại và các thuộc tính của lớp Abstract không được khai báo abstract
+ Lớp kế thừa lớp abstract phải Rewrite lại tất cả các hàm Abstract, nếu không sẽ bị báo sai

_ Lớp Final là lớp được khai báo là lớp cuối cùng, không một lớp nào có thể kế thừa nó. Tương tự hàm Final trong abstract hoặc trong kế thừa Chỉ có thể gọi ra và dùng, không được Override lại

_ Interface là một template, nó không phải là lớp đối tượng mà khi nhìn vào ta biết được tất cả các hàm của đối tượng implement nó
Để khai báo một Interface ta dùng từ khóa interface để thay cho class. Tất cả các hàm trong interface đều ở dạng khai báo và không được định nghĩa (giống abstract). Nếu một đối tượng implement một interface nó phải khai báo và định nghĩa tất cả các hàm trong Interface (implement cùng cấp độ truy cập)
+ Tính kế thừa interface: tuy không phải là lớp nhưng nó cũng có tính kế thừa,nghĩa là một Interface A có thể kế thừa một Interface B thì lúc này đối tượng nào implement lớp A thì phải định nghĩa tất cả hàm mà A,B đã khai báo

So sánh: + Đa thừa kế: Interface: một class có thể thực hiện nhiều interface(tạm coi là thừa kế)
			Abstract class: không hỗ trợ đa thừa kế
	+Implement mặc định: Interface không thể định nghĩa code xử lý, chỉ có thể khai báo
	 		Abstract có thể định nghĩa thân phương thức, thuộc tính.
	+Phạm vi truy cập: Interface mọi phương thức, thuộc tính đều mặc định là public
			Abtract có thể xác định modifier
	+ Mọi phương thức trong interface cần được thực hiện trong class
	 Abstract không cần thiết (không cần phải override các method thường)





