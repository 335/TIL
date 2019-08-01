# spring-boot-starter-mail 첨부파일 전송

AWS SES로 첨부파일 포함된 메일 발송기능 개발

```java
public class EmailService {

  private final JavaMailSender mailSender;

  public void sendEmail(SimpleMailMessage simpleMailMessage) {
    mailSender.send(simpleMailMessage);
  }

  public void sendEmail(MimeMessage message) {
    mailSender.send(message);
  }

  public MimeMessage createMimeMessage() {
    return mailSender.createMimeMessage();
  }
}
```

```java
private final EmailService emailService;

public void sendMail() throws MessagingException, IOException {
    File attachment = new File("file");
    try (FileOutputStream outputStream = new FileOutputStream(attachment)) {
      MimeMessage message = emailService.createMimeMessage();
      MimeMessageHelper mimeMessageHelper = new MimeMessageHelper(message, true);
      mimeMessageHelper.setTo("to@to.com");
      mimeMessageHelper.setCc("cc@cc.com");
      mimeMessageHelper.setFrom("no-reply@from.com");
      mimeMessageHelper.setSubject("subject");
      mimeMessageHelper.setText("text");
      mimeMessageHelper.addAttachment("blahblah.xlsx", attachment);
      emailService.sendEmail("message");
    }
```
