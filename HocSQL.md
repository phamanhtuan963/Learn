_ Select dùng để lấy dữ liệu từ 1 hay nhiều cột từ bảng
VD: Select * from table; //chọn hết
Select column1, column2,... from table; //lấy cụ thể
Select lấy hết dữ liệu từ cột, (From lấy ít nhất 1 table)

_ Và để lọc dữ liệu ta dùng Where conditions, dùng cho Select, Update, Delete, etc
dùng toán tử so sánh như:
+ > lớn hơn
+ < bé hơn
+ = bằng
+ >= lớn hơn hoặc bằng
+ <= bé hơn hoặc bằng
+ LIKE so sánh chuỗi trùng khớp
+ NOT so sánh không giống
Where với hơn một điều kiện: dùng toán tử AND hoặc OR
+ AND trả về true nếu cả 2 đúng, ngược lại false
+ OR trả về true nếu 1 trong 2 đúng (và lấy điều kiện đó), trả về false nếu cả 2 sai
Cú pháp: Where condition1 [AND][OR] condition2

_ Lọc dữ liệu trùng lặp và chỉ để lại một dòng duy nhất sử dụng Distinct (dữ liệu trùng lặp là phải giống ở mọi column)
Cú pháp: SELECT DISTINCT column1, ... columnN FROM table_name

_ Update cập nhật một hay nhiều dữ liệu có sẵn trong 1 bảng. Lệnh này cũng sử dụng where (những row) thỏa điều khiện mới cập nhật
Cú pháp: Update table_name SET column1 = value1,... columnN = valueN Where [Condition];

_ Delete xóa hoàn toàn dữ liệu ra khỏi hệ thống và không thể lấy lại
Cú pháp: DELETE FROM table_name Where [CONDITION];
+ CONDITION là điều khiện để xóa, nếu không nhập CONDITION thì toàn bộ dữ liệu trong bảng sẽ bị xóa
+ Delete chỉ có thể thao tác với một bảng trong một câu truy vấn

_ INSERT thêm một row vào vị trí dưới cùng của danh sách dữ liệu
Cú pháp: INSERT INTO table_name [(column1m, ... columnN)] VALUES (value1m, ... valueN);
hoặc : INSERT INTO table_name VALUES (value1, ... valueN);
Các danh sách column sẽ nhận dữ liệu tương ứng value. Trong trường hợp không truyền column thì tổng giá trị phải bằng tổng số column trong bảng

_ Order By sắp xếp dữ liệu tăng dần hoặc giảm dần, lệnh này được đặt cuối câu Select và có 2 tham số truyền vào
Cú pháp: Select column1, ... columnN
	From table_name
	[Where condition]
	[Order By column1, column2,... columnN] [ASC | DESC]
Ví dụ: Select *
	From Posts
	Order By created_date ASC
Sắp xếp theo nhiều column thì bổ sung vào Order By và cách nhau bởi dấu phẩy
Ví dụ: Select *
	From Posts
	Order By created_date, ID ASC
	
_ UNION dùng để gộp 2 bảng tạm thành một bảng
Cú pháp: Select column_name(s) FROM table1 [Where condition]
	UNION
	Select column_name(s) FROM table2 [Where condition]
	[Order By]
UNION gộp kết quả 2 lệnh Select và loại bỏ những dòng bị trùng lặp chỉ để lại một dòng duy nhất, tuy nhiên không phải lệnh nào cũng gộp được mà phải thỏa điều kiện sau:
+ Tên của các Column phải giống nhau
+ Thứ tự column phải giống nhau
+ Tổng các column phải bằng nhau

_UNION ALL tương tự UNION chỉ có điều là sẽ giữ lại tất cả dữ liệu kể cả bị trùng lặp

_ ALIAS sẽ tạo ra một tên tạm và chỉ tồn tại trong quá trình chạy câu truy vấn, sau đó nó sẽ được giải phóng khỏi bộ nhớ. Sử dụng ALIAS cho column, table hay một tên bất kì, kí hiệu trong SQL là AS
Cú pháp: Select column_name AS column_new_name
	From table_name AS table_new_name

_ Trường có giá trị NULL là trường không có giá trị, chỉ khi trường đó là optional thì khi insert hay update mà không thêm gía trị cho trường này sẽ save là NULL
Trường có giá trị NULL khác với giá trị 0 và trường chứa khoảng trắng. NUll là bị bỏ trống trong quá trình tạo bản ghi.
Không thể kiểm tra giá trị NULL với toán tử so sánh như là =, < hay <>.
Mà dùng IS NULL(tìm giá trị NULL, empty) và IS NOT NULL(tìm giá trị khác NULL, non-empty)
Cú pháp: Select column_names
	From table_name
	Where column_name [IS NULL | IS NOT NULL];

_ LIKE nằm trong mệnh đề where dùng để so khớp một chuỗi đại diện so với chuỗi gốc
Có 2 kí tự đại diện:
+ (_) đại diện cho 1 kí tự bất kỳ
+ (%) đại diện cho zero, 1, hoặc nhiều kí tự bất kì

_ IN dùng để tìm ra nhiều giá trị trong mệnh đề Where,là cách viết tắt của nhiều điều kiện OR
Cú pháp: Select column_list
	FROM table_name
	Where column_name (NOT) IN ("list_value");
+ list_value là tập các giá trị cách nhau bởi dấu phẩy

_ Join dùng để truy vấn lấy dữ liệu từ nhiều bảng dựa trên một mối liên hệ nào đó, thường là dựa trên mối liên hệ khóa ngoại, (lấy những record thỏa điều kiện ở ON)
Cú pháp Inner Join:
 Select columns
 From table1
 (Inner) Join table2
 On table1.column = table2.column
 [Where conditions]

_ LEFT (OUTER) JOIN sẽ ưu tiên chọn tất cả những record thỏa điều kiện ON lẫn không thỏa ON trong bảng phía bên trái
Cú pháp: Select columns from table1 LEFT JOIN table2 ON table1.column = table2.column

_ RIGHT (OUTER) JOIN sẽ ưu tiên chọn tất cả những record thỏa điều kiện ON lẫn không thỏa ON trong bảng phía bên phải, tổng column trả về bằng tổng số column của 2 bảng
Cú pháp: Select columns from table1 RIGHT JOIN table2 ON table1.column = table2.column

_ FULL (OUTER) JOIN trả về hợp record của 2 bảng
Cú pháp: Select column_name(s)
	From table1
	Full OUTER JOIN table2
	ON table1.column_name = table2.column_name
	[Where condition];
	
_ SELF JOIN là phép join trên cùng 1 bảng (khóa ngoại trỏ đến khóa chính trên cùng một bảng)
Cú pháp: Select column_name(s)
	From table1 T1, table2 T2
	[Where condition];

_ Group By gom nhóm dữ liệu theo một hoặc nhiều field nào đó, rất có ích cho báo cáo nhưng ảnh hưởng đề tốc độ xử lý câu truy vấn. Group By gom nhóm dữ liệu và chỉ trả về một record cho một nhóm duy nhất, thường kết hợp với các hàm như SUM, AVG, MAX, MIN và COUNT
Cú pháp: Select columns
	From table
	Where condition
	Group By column1,... columnN
	[Having conditions];

Lưu ý: Group By có khoảng trắng và nằm sau lệnh Where
	Field trong Group By bắt buộc phải có trong Select
Thứ tự chạy Group By: From -> Where -> Select -> Group By -> Having -> Order By -> Limit
_ Dùng Having để lọc (thêm điều kiện) cho Group By (Do Where chạy trước Group By nên điều kiện không thể đặt ở Where được)


