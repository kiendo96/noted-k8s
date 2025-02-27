# Requirement: Yêu cầu biết cách host một website tĩnh lên S3 bucket
1. Chuẩn bị 1 website tĩnh
2. Thực hiện host website tĩnh sử dụng S3
3. Tạo CloudFront distribution, đăng kí S3 làm Origin
4. Thử truy cập thông qua CloudFront, so sánh tốc độ khi truy cập trực tiếp S3
5. Disable public access cho S3, Tạo OAI cho CloudFront, thiết lập policy chỉ cho phép truy cập resource thông qua CloudFront
6. [Optional] phát hành SSL certificate và sử dụng CloudFront custom domain. Mua 1 tên miền và trỏ sang CloudFront, truy cập thông qua domain đã setting.

```
Steps:
=> Tạo 1 web static bằng s3 bucket
    => CloudFront => Create distribution => Origin domain "Choose a domain" => Origin access "Public" => viewer "choose 1 trong các option - recommend is `redirect HTTP to HTTPS` "
        => Access cloudFront = "distribution domain name" trong phần detail của CloudFront
            VD: abc.cloudfront.net/index.html
            => Access cloudfront => Origins -> Edit origin -> Change Origin Access from "Public" to "Origin access control setting" -> Origin access control: "create control setting" -> Change Signing behavior to "Sign request"  and Origin type "S3"   => Sau khi xong "Copy policy"
                => Back to S3 => Turn on "Block all access" => Edit Bucket Policy and Paste "Policy được create ở CloudFront vào Bucket Policy"
Step 6:
-> Access Certificate Manager (ACM) -> Request a new certificate SSL
    -> Access CloudFront -> Edit Setting -> Alternate domain name (CNAME) "VD: udemy.kiendt.devops.com" -> Custom SSL certificate "choose ACM certificate đã create trước đó"
        -> Access Route 53 -> Vào domain -> Create record -> record name "udemy"    => record type: "CNAME" => value: "copy distribution domain name of CloudFront"
```

# Hướng dẫn chi tiết
### Step 1: Prepare a static website in S3
- For example: https://www.free-css.com/free-css-templates
- Enabling website hosting
- Configuring an index document
- Setting permissions for website access: Clear “Block all public access” configuration, and set S3 bucket policy
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```

### Step 2: Create a CloudFront distribution
- Under Origin Settings, for Origin Domain Name, choose the Amazon S3 bucket that you created earlier.
- We should set the root page for our distribution
