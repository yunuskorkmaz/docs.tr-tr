---
title: SendMail Özel Etkinliği
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e7cc64e68c3d78b9ee7ec813700e96a52c239141
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182776"
---
# <a name="sendmail-custom-activity"></a>SendMail Özel Etkinliği
Bu örnek, iş akışı uygulamasında kullanılmak üzere <xref:System.Activities.AsyncCodeActivity> SMTP kullanarak posta göndermekten türeyen özel bir etkinliğin nasıl oluşturulacağını göstermektedir. Özel etkinlik, eşit olarak <xref:System.Net.Mail.SmtpClient> e-posta gönderme ve kimlik doğrulaması ile posta gönderme özelliklerini kullanır. Ayrıca test modu, belirteç değiştirme, dosya şablonları ve test bırakma yolu gibi bazı son kullanıcı özellikleri sağlar.  
  
 Aşağıdaki tabloda etkinlik için `SendMail` bağımsız değişkenler ayrıntılı olarak anlatılır.  
  
|Adı|Tür|Açıklama|  
|-|-|-|  
|Host|Dize|SMTP sunucu ana bilgisayarının adresi.|  
|Bağlantı noktası|Dize|SMTP hizmetinin ana bilgisayardaki bağlantı noktası.|  
|Etkinleştirssl|bool|Bağlantıyı şifrelemek <xref:System.Net.Mail.SmtpClient> için Güvenli Soket katmanının (SSL) kullanılıp kullanılmayacağını belirtir.|  
|UserName|Dize|Gönderen <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliğinin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için kullanıcı adı.|  
|Parola|Dize|Gönderen <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliğinin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için parola.|  
|Özne|<xref:System.Activities.InArgument%601>\<dize>|İletinin konusu.|  
|Gövde|<xref:System.Activities.InArgument%601>\<dize>|Mesajın gövdesi.|  
|Ekler|<xref:System.Activities.InArgument%601>\<dize>|Bu e-posta iletisine bağlı verileri depolamak için kullanılan ek koleksiyonu.|  
|Başlangıç|<xref:System.Net.Mail.MailAddress>|Bu e-posta iletisi için adresten.|  
|Alıcı|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisinin alıcılarını içeren adres koleksiyonu.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için karbon kopya (CC) alıcıları içeren adres toplama.|  
|Gizli|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için kör karbon kopya (BCC) alıcıları içeren adres toplama.|  
|Belirteçler|<xref:System.Activities.InArgument%601><IDictionary\<dize, dize>>|Vücutta değiştirilecek belirteçler. Bu özellik, kullanıcıların daha sonra bu özelliği kullanılarak sağlanan belirteçleri ile değiştirilebilir daha gövdede bazı değerleri belirtmenize olanak sağlar.|  
|BodyTemplateFilePath|Dize|Gövde için bir şablonyolu. Etkinlik, `SendMail` bu dosyanın içeriğini gövde özelliğine kopyalar.<br /><br /> Şablon belirteçleri özelliğinin içeriği ile değiştirilen belirteçleri içerebilir.|  
|Testmailto|<xref:System.Net.Mail.MailAddress>|Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adrese gönderilir.<br /><br /> Bu özellik, iş akışlarını sınarken kullanılmak üzere tasarlanmıştır. Örneğin, tüm e-postaların gerçek alıcılara gönderilmeden gönderildiğinden emin olmak istediğinizde.|  
|TestDroppath|Dize|Bu özellik ayarlandığında, tüm e-postalar da belirtilen dosyaya kaydedilir.<br /><br /> Bu özellik, giden e-postaların biçiminin ve içeriğinin uygun olduğundan emin olmak için iş akışlarını test ederken veya hata ayıklarken kullanılmak üzere tasarlanmıştır.|  
  
## <a name="solution-contents"></a>Çözüm İçeriği  
 Çözüm iki proje içerir.  
  
|Project|Açıklama|Önemli Dosyalar|  
|-------------|-----------------|---------------------|  
|Sendmail|SendMail etkinliği|1. SendMail.cs: ana faaliyet için uygulama<br />2. SendMailDesigner.xaml ve SendMailDesigner.xaml.cs: SendMail etkinliği için tasarımcı<br />3. MailTemplateBody.htm: e-postanın gönderilmesi için şablon.|  
|SendMailTestClient|SendMail etkinliğini test etmek için istemci.  Bu proje, SendMail etkinliğini çağırmak için iki yol gösterir: bildirimsel ve programsal olarak.|1. Sequence1.xaml: SendMail etkinliğini çağıran iş akışı.<br />2. Program.cs: Sequence1 çağırır ve aynı zamanda SendMail kullanan bir iş akışı programlı oluşturur.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>SendMail etkinliğinin daha fazla yapılandırması  
 Örnekte gösterilmese de, kullanıcılar SendMail etkinliğinin ek yapılandırmasını gerçekleştirebilir. Sonraki üç bölüm bunun nasıl yapıldığını gösteriyor.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Vücutta belirtilen belirteçleri kullanarak e-posta gönderme  
 Bu kod snippet vücutta belirteçleri ile e-posta gönderebilirsiniz nasıl gösterir. Jetonların gövde mülkünde nasıl sağlandığına dikkat edin. Bu belirteçler için değerler belirteçleri özelliğine sağlanır.  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>Şablon kullanarak e-posta gönderme  
 Bu parçacık, vücuttaki şablon belirteçlerini kullanarak e-postanın nasıl gönderilebildiğini gösterir. `BodyTemplateFilePath` Özelliği ayarlarken Gövde özelliği nin değerini sağlamamıza gerek olmadığını unutmayın (şablon dosyasının içeriği gövdeye kopyalanır).  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>Test Modunda Posta Gönderme  
 Bu kod snippet iki test özellikleri ayarlamak `TestMailTo` için nasıl gösterir: tüm `john.doe@contoso.con` iletileri ayarlayarak (To, Cc, Bcc değerleri ne olursa olsun) gönderilecektir. TestDropPath ayarlayarak tüm giden e-postalar da sağlanan yolda kaydedilir. Bu özellikler bağımsız olarak ayarlanabilir (bunlar ilişkili değildir).  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>Kurulum Yönergeleri  
 Bu örnek için bir SMTP sunucusuna erişim gereklidir.  
  
 Bir SMTP sunucusu ayarlama hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.  
  
- [SMTP Hizmetini Yapılandırma (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7.0: SMTP E-Postayı Yapılandır](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [SMTP Hizmeti Nasıl Yüklenir?](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 Üçüncü şahıslar tarafından sağlanan SMTP emülatörleri indirilebilir.  
  
##### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1. Visual Studio 2010'u kullanarak SendMail.sln çözüm dosyasını açın.  
  
2. Geçerli bir SMTP sunucusuna erişebildiğinizden emin olun. Kurulum yönergelerine bakın.  
  
3. Programı sunucu adresinizle ve E-posta adreslerinize göre yapılandırın.  
  
     Bu örneği doğru çalıştırmak için, Program.cs ve Sequence.xaml'daki SMTP sunucusunun E-posta adreslerinin değerini ve adresini yapılandırmanız gerekebilir. Program posta gönderdiğinden, her iki konumda da adresi değiştirmeniz gerekir  
  
4. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.  
  
5. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
