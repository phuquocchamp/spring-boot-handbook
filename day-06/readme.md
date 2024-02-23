### 200 DAYS TO BECOME A JAVA DEV - DAY 06/200

[Link Code](https://github.com/phuquocchamp/restapi-webservices)

#### DTO PARTERN

##### Tham khảo:

[Entity, domain model và DTO](https://viblo.asia/p/entity-domain-model-va-dto-sao-nhieu-qua-vay-YWOZroMPlQ0)

[Một số Design Principles trong lập trình](https://viblo.asia/p/mot-so-design-principles-trong-lap-trinh-ma-ban-nen-biet-eW65GvJOlDO#_design-principles-vs-design-patterns-0)

> DTO là một parten, parten này tuân thủ nguyên tắc SoC tức là phân tách dữ liệu ra thành những phần nhỏ nhất sao cho có ít sự liên quan đến nhau.
>
> Điều này xảy ra khi chúng ta muốn ẩn đi nhưng thông tin không cần thiết của các đối tượng.
>
> Ví dụ: Dữ liệu của lớp Person chứ thông tin như (tên, tuổi, email, số điện thoại, ngày sinh ,... ) nhưng khi chúng ta truyền đối tượng cho các layer khác xử lí (ví dụ như ta xây dựng chức năng kết bạn thì lúc này dữ liệu cần được hiển thị cho lớp Person là tên, tuổi, ngày sinh là đủ) thì dữ liệu được truyền đi có những thông tin không cần thiết (nhạy cảm) => DTO giúp giảm bớt các dữ liệu không cần thiết trong các đối tượng.

##### Tutorial Guider

![1708592468771](image/handbook/1708592468771.png)

###### Mapper Class

![1708598438080](image/handbook/1708598438080.png)

Ta thấy rằng trong quá trình convert từ class DTO sang Entity và từ Entity sang DTO sẽ được lặp lại trong quá trình code. Ta có thể thể tạo ra một class Mapper thực hiện viêc chuyển đổi này.

###### ModelMapper Library

[Tham khảo](https://modelmapper.org/getting-started/)

![1708600408742](image/handbook/1708600408742.png)

![1708600447927](image/handbook/1708600447927.png)

**Cách Sử dụng :**

![1708600915292](image/handbook/1708600915292.png)

![1708600857312](image/handbook/1708600857312.png)

##### Mapstruct Library

[Tham khảo](https://mapstruct.org/)

![1708601048377](image/handbook/1708601048377.png)

![1708601071894](image/handbook/1708601071894.png)

#### EXCEPTION HANDLING

[Tham khảo](https://kungfutech.edu.vn/bai-viet/spring-boot/exception-handling-trong-spring-boot)

##### Tutorial Guider

![1708603417876](image/handbook/1708603417876.png)

![1708603593422](image/handbook/1708603593422.png)

>  Khi làm việc với RESTAPI sẽ xảy ra trường hợp xảy ra lỗi khi truy vấn và lúc này server sẽ trả về message error default mặc định, thay vì hiển thị như vậy ta có thể thay đổi cách xử lí output khi gặp lỗi, giúp cho lập trình viên có thể bắt lỗi và fix một cách dễ dàng.

![1708605213939](image/handbook/1708605213939.png)

![1708605270663](image/handbook/1708605270663.png)

##### Phân Tích

**ResourceNotFoundException.class**

![1708606984889](image/handbook/1708606984889.png)

**Bắt lỗi cụ thể với method findById() => nếu không tìm thấy ném ra exception.**

![1708606895743](image/handbook/1708606895743.png)

**Method handleResourceNotFoundException() trong class UserController.class**

> Ta sử dụng annotation *@ExceptionHandler* cho method này, *@ExceptionHandler* là một annotation dùng để xử lí một ngoại lệ cụ thể và gửi một* **custom responses*** trả về phía client.
>
> Workflow : Khi có ngoại lệ xảy ra với class ResourceNotFoundException thì được annotation @ExceptionHandler lắng nghe và xử lí

![1708607131730](image/handbook/1708607131730.png)

**GlobalExceptionHandler.class** 

>  Ta có thể tạo một class Global ExceptionHandler để handle ngoại lệ một cách globally.

![1708608851000](image/handbook/1708608851000.png)


##### Exercises

![1708609048188](image/handbook/1708609048188.png)

> Để kiểm tra xem email được tạo đã tồn tại ở trong database hay chưa ta, tạo một custom query method findByEmail(String email) ở Interface UserRepository. Trong hàm createUser ta kiểm tra Email đã tồn tại hay chưa. Nếu đã tồn tại thì thow một Exception EmailAlreadyExitsException.

**EmailAlreadyExitsException.class**

![1708610762210](image/handbook/1708610762210.png)

**createUser method**

![1708610790061](image/handbook/1708610790061.png)

**handleEmailAlreadyExitsException method**

![1708610589423](image/handbook/1708610589423.png)

##### GlobalException

> Ta thấy rằng lớp Exception chính là lớp cha của các lớp Exception khác nên ta có thể custom một method handleGlobalException bắt lỗi khi có ngoại lệ từ Exception.

![1708611304699](image/handbook/1708611304699.png)

#### VALIDATION 

>  Validation là hoạt động nhằm kiểm tra tính hợp lệ của dữ liệu .

##### Tutorial Guider

![1708611861156](image/handbook/1708611861156.png)

![1708611909478](image/handbook/1708611909478.png)

![1708611987364](image/handbook/1708611987364.png)

![1708612028086](image/handbook/1708612028086.png)


**Sử dụng valicatation library để kiểm ta tính hợp lí của dữ liệu đầu vào.**

> Sử dụng các annotation như @NotEmpty, @Email để validate

![1708612543524](image/handbook/1708612543524.png)

**Thêm annotation @Valid để check dữ liệu DTO từ client**

![1708612608374](image/handbook/1708612608374.png)


##### Phân Tích

**Method handleMethodArgumentNotValid**

![1708613710393](image/handbook/1708613710393.png)

**Khi ta sử dụng validation bằng thư viện thì để cho quá trình bắt lỗi validate diễn ra một cách tự động thì lớp trên rất hữu hiệu.**

![1708613857547](image/handbook/1708613857547.png)

**Ta cũng có thể cusom lại message trả về phía client bằng cách thêm message ở phần validate lớp UserDto.class**

![1708614054158](image/handbook/1708614054158.png)

**Kết Quả:**

![1708614069464](image/handbook/1708614069464.png)
