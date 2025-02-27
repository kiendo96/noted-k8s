# Lab 1- SQS thao tác cơ bản
1. Login vào AWS console, navigate tới dịch vụ SQS
2. Tạo một Queue với các thông số cơ bản
3. Thử gửi và nhận message trên queue
4. Thử xóa một message
5. Thử purge queue (xóa toàn bộ message)
```
-> Create a new SQS queue
  -> visibility timeout (Tối đa 12hours)
    -> Message retention period(Thời gian hết hạn của message: tối đa 14 ngày)
      -> Delivery delay (max: 15 minutes): Được sử dụng để ném message qua target (lambda, ec2, s3...)
        -> Receive message wait time (long polling - max:20s): Nếu không có message thì sau khoảng thời gian long polling nó mới trả lại empty cho client
          *Note: SQS có Access policy
```

### Test queue
```
- Click "Send and receive message"
  -> Type message body: {"name":"kiendt","age":27}  -> send message -> Thử send tiếp 1 số message  -> croll to end of page click "poll for messages"
```

# Lab 2 - SQS thao tác cơ bản
1. Login vào AWS console, navigate tới dịch vụ SQS
2. Tạo thêm một queue với tên gọi "dead-letter-queue"
3. Cấu hình queue lab1 sử dụng queue ở bước trước làm dead letter queue, max receive count = 5
4. Thử gửi một message vào queue chính sau đó poll liên tục 5 lần. Chú ý thông số receive count của message sẽ bị +1 sau mỗi lần poll
5. Poll tới lần thứ 6, message không còn nữa
6. Confirm message đã bị đẩy sang "dead-letter-queue". Chú ý thông số receive count sẽ không bị reset mà được giữ nguyên và tiếp tục cộng +1 lên sau mỗi lần poll
