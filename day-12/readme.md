### 200 DAYS TO BECOME A JAVA DEV | DAY 12/200

#### SPRING SECURITY - REGISTRATION & LOGIN PAGE

##### Tutorial Guider

![1709210277454](image/readme/1709210277454.png)

![1709210290159](image/readme/1709210290159.png)

##### Entity

###### Role.class

![1709211713147](image/readme/1709211713147.png)

###### User.class

![1709211742812](image/readme/1709211742812.png)

![1709212606055](image/readme/1709212606055.png)

###### Thymeleaf Data Transfer

**Enpoint /register**

![1709313093005](image/readme/1709313093005.png)

> Ta tạo một đối tượng userDto và thêm vào phần view register, đối tượng này sẽ được binding và nhận các giá trị (thuộc tính) từ  form khi người dùng nhập.

**Xử lí form trong thymeleaf.**

![1709312844258](image/readme/1709312844258.png)

> Ta cần quan tâm đên một số attributes quan trọng khi xử  form.
>
> 1. th:action : Đây là một attribute dùng để điều hướng đến URL Enpoint xử lí form khi click vào button Submit (3).
> 2. th:object : Đây là object được binding từ lớp controller và object này sẽ được dùng để truyền vào Enpoint được khai báo trong th:action="@{/register/save}"

**Enpoint "/register/save"**

![1709313529708](image/readme/1709313529708.png)

> @ModelAttribute("user") UserDto userDto : đây là một annotation dùng để binding dữ liệu từ object có tên "user"  từ  View sang Controller.



###### Thymeleaf Param enpoint

**Enpoint**

![1709346035777](image/readme/1709346035777.png)

**register.html**

![1709346103435](image/readme/1709346103435.png)

**UI**

![1709346224821](image/readme/1709346224821.png)

![1709346196352](image/readme/1709346196352.png)


###### Validation Form 

**Result**

![1709348316717](image/readme/1709348316717.png)

**UserDto** 

> Thêm các Annotation Validation cho các field 

![1709348367493](image/readme/1709348367493.png)

**AuthController**

> 1. Ta sử dụng các annotation như @Valid để check validation cho các trường của lớp UserDto.
> 2. Ta sử dụng lớp DataBinding để lưu các kết quả (lỗi) khi xử lí validation.

![1709348212498](image/readme/1709348212498.png)

**register.html**

![1709348662410](image/readme/1709348662410.png)

> Ta sử dụng th:errors="*{firstName}" để trả về lỗi cho trường firstName khi có lỗi xảy ra.
>
> th:if="${#fields.hasErrors('firstName')}" sẽ check lỗi cho trường firstName.


###### Spring Security

![1709355067929](image/readme/1709355067929.png)

**SecurityConfig**

![1709390446445](image/readme/1709390446445.png)

> Ta có thể viết ngắn gọn như dưới thay vì 

![1709390368704](image/readme/1709390368704.png)

**login.html**

> Ta lưu ý rằng trong 2 thẻ input khi customize trang login thì attribute "name", "id" dùng để spring boot lấy giá trị nên không đc bỏ qua. 

![1709390543297](image/readme/1709390543297.png)
