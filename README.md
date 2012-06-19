An easy way to send emails with attachments

**Send attachments**

```go
m := email.NewMessage("Hi", "this is the body")

err := m.AddAttachment("picture.png")
if err != nil {
	log.Println(err)
}

err = email.Send(
	"mail.padelclick.com:25",
	smtp.PlainAuth("", "user", "password", "example.com"),
	"from@example.com",
	[]string{"to@example.com"},
	m)

if err != nil {
	log.Fatal(err)
}
```


**Send without requiring TLS**

```go
err = email.Send(
	"mail.padelclick.com:25",
	email.InsecureAuth("user", "password"),
	"from@example.com",
	[]string{"to@example.com"},
	m)
```
	