# About elastic beanstalk
- Elastic Beanstalk là một dịch vụ của AWS được sử dụng để triển khai, quản lý và mở rộng web app, web service một cách dễ dàng trên môi trường AWS. Elastic Beanstalk cung cấp một nền tảng quản lý tự động cho việc triển khai ứng dụng và điều chỉnh các tài nguyên cần thiết như Server, Network, Database và các dịch vụ liên quan khác
- Elastic Beanstalk đóng vai trò như một PaaS nơi bạn tập trung vào việc phát triển ứng dụng còn AWS sẽ phụ trách phần hạ tầng và deployment. Nó hỗ trợ nhiều ngôn ngữ lập trình và framework phổ biến như Java, .Net, PHP, Node.js, Python và Ruby
- Để triển khai ứng dụng, chỉ cần đóng gói mã nguồn của mình và tải lên Elastic Beanstalk. Dịch vụ sẽ tự động xây dựng và cấu hình môi trường chạy ứng dụng dựa trên các yêu cầu và tùy chọn. Nó cũng tự động quản lý việc scaling tài nguyên dựa trên tải lượng và yêu cầu của ứng dụng
- Elastic Beanstalk cung cấp một giao diện quản lý đơn giản và tùy chọn linh hoạt cho phép tùy chỉnh cấu hình và kiểm soát ứng dụng của mình

# Tính năng của Elastic Beanstalk - Topo
- First step => AWS Elastic Beanstalk: Deploy and scale web applications and service
- Second Step => Use AWS Elastic Beanstalk console: Create an AWS account and answer questions that become inputs to create you environment
- Third Step => [Application code, Elastic Beanstalk platform]: Set up your application(with your code) and runtime (with Elastic Beanstalk platform)
- Step 4  => Deploy environment: Launch resourrces for your environment with AWS cloudformation
- Step 5 => Web application or service


# Tính năng:
- Tự động tạo ra môi trường và các tài nguyên liên quan
- Cung cấp khả năng auto scaling
- Monitoring thông qua giao diện thân thiện giúp theo dõi được tình trạng của app cũng như môi trường
- Hỗ trợ nhiều platform: Java, .NET, Node.js, PHP, Ruby, Python, Go and dockerr
- Đa dạng hình thức deploy
    VD: Console, CLI, vscode, eclipse ... 
- Hỗ trợ deployment policies
    VD: Rolling update, blue-green, canary deploy...
- Tự động update platform version khi cần thiết

# Ưu điểm của Elastic Beanstalk
1. Dễ sử dụng: Elastic Beanstalk cung cấp một giao diện quản lý đơn giản và tương tác trực quan, giúp triển khai và quản lý ứng dụng một cách dễ dàng mà không cần hiểu rõ về cấu hình và quản lý hạ tầng
2. Tự động hóa quy trình triển khai, giúp giảm thời gian và công sức cần thiết cho việc triển khai ứng dụng
3. Quản lý tự động tài nguyên: Elastic Beanstalk tự động quản lý việc mở rộng và thu hẹp tài nguyên dựa trên tải lượng và yêu cầu của ứng dụng
4. Hỗ trợ nhiều ngôn ngữ và framework: Elastic Beanstalk hỗ trợ nhiều ngôn ngữ lập trình và framework phổ biến như java, .NET, Nodejs, python và Ruby

# Nhược điểm
1. Giới hạn tùy chỉnh: Mặc dù Elastic Beanstalk cung cấp các tùy chọn cấu hình và kiểm soát, nhưng nó có thể hạn chế đối với những ứng dụng phức tạp đòi hỏi sự tùy chỉnh cao hơn. Nếu bạn có nhu cầu tùy chỉnh chi tiết hơn, có thể cần sử dụng các dịch vụ khác của AWS như EC2, ECS, EKS
2. Giới hạn của mô hình phân phối: Elastic Beanstalk dựa trên mô hình phân phối dựa trên máy ảo EC2, điều này có thể gây ra một số hạn chế trong việc mở rộng và quản lý tài nguyên trong một số tình huống đặc biệt. Đối với các ứng dụng đòi hỏi mô hình phân phối linh hoạt hơn, có thể cần sử dụng service khác

# Usecase
- Elastic Beanstalk phù hợp với:
    + Hệ thống có backend đơn  giản
    + Team muốn đơn giản hóa quy trình deploy hoặc chưa có nhiều kinh nghiệm với AWS
    + Hệ thống monolithic
- Elastic Beanstalk không phù hợp:
    + Hệ thống có backend phức tạp
        VD: micro service
    + Có nhu cầu customize nhiều


