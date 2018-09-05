---
title: SendMail özel etkinliği
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e9d27711754c3aa8ff7f68c23f528c9f5c4356f7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533879"
---
# <a name="sendmail-custom-activity"></a>SendMail özel etkinliği
Bu örnek, türetilen özel etkinlik oluşturma işlemini gösterir <xref:System.Activities.AsyncCodeActivity> bir iş akışı uygulaması içinde kullanmak için SMTP kullanarak posta göndermek için. Özel Etkinlik özelliklerini kullanan <xref:System.Net.Mail.SmtpClient> zaman uyumsuz olarak e-posta gönderin ve kimlik doğrulaması içeren e-posta göndermek için. Test modu, belirteç değiştirme, dosya şablonları ve test bırakma yolu gibi bazı son kullanıcı özellikler de sağlar.  
  
 Aşağıdaki tabloda bağımsız değişkenleri için ayrıntıları `SendMail` etkinlik.  
  
|Ad|Tür|Açıklama|  
|-|-|-|  
|Ana bilgisayar|Dize|Hostitel SMTP sunucu adresi.|  
|Bağlantı Noktası|Dize|Konak SMTP hizmetinin bağlantı noktası.|  
|enableSsl|bool|Belirtir olup olmadığını <xref:System.Net.Mail.SmtpClient> Güvenli Yuva Katmanı (SSL) bağlantıyı şifrelemek için kullanır.|  
|UserName|Dize|Kullanıcı adı, gönderenin kimliğini doğrulamak için kimlik bilgilerini ayarlayın <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliği.|  
|Parola|Dize|Gönderenin kimliğini doğrulamak için kimlik bilgilerini ayarlayın parola <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliği.|  
|Konu|<xref:System.Activities.InArgument%601>\<dize >|İletinin konusu.|  
|Gövde|<xref:System.Activities.InArgument%601>\<dize >|İletinin gövdesi.|  
|Ekler|<xref:System.Activities.InArgument%601>\<dize >|Bu e-posta iletisine ekli veri depolamak için kullanılan ek koleksiyonu.|  
|Başlangıç|<xref:System.Net.Mail.MailAddress>|Bu e-posta iletisi için adres.|  
|Bitiş|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisinin alıcıları içeren adres koleksiyonu.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bilgi (CC) alıcılarını bu eposta iletisi için içeren koleksiyon adresi.|  
|GİZLİ|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için gizli kopya (gizli) alıcıları içeren adres koleksiyonu.|  
|Belirteçler|<xref:System.Activities.InArgument%601>< IDictionary\<dize, dize >>|Belirteçleri gövdesinde değiştirin. Bu özellik, kullanıcıların daha sonra bu özelliği kullanarak verilen belirteçleri ile değiştirilebilir daha gövdesinde bazı değerleri belirtmesine izin verir.|  
|BodyTemplateFilePath|Dize|Gövdesi için bir şablon yolu. `SendMail` Etkinliği, bu dosyanın içeriğini kendi gövdesi özelliğine kopyalar.<br /><br /> Şablon belirteçleri özelliğinin içeriğine göre değiştirilir belirteçlerini içerebilir.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Bu özelliği ayarlandığında, tüm e-postaları içinde belirtilen adrese gönderilir.<br /><br /> Bu özellik, iş akışları test ederken kullanılması amaçlanmıştır. Örneğin, emin olmak istediğinizde tüm e-postaları gerçek alıcıya gönderim olmadan gönderilir.|  
|TestDropPath|Dize|Bu özelliği ayarlandığında, tüm e-postaları da belirtilen dosyasında kaydedilir.<br /><br /> Bu özellik, test veya giden e-posta içeriğini ve biçimini uygun olduğunu emin olmak için iş akışlarında hata ayıklama yaparken kullanılmak için tasarlanmıştır.|  
  
## <a name="solution-contents"></a>Çözüm içeriği  
 Çözüm iki proje içerir.  
  
|Proje|Açıklama|Önemli dosya|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail etkinliği|1.  SendMail.cs: ana etkinlik uygulama<br />2.  SendMailDesigner.xaml ve SendMailDesigner.xaml.cs: SendMail etkinliğinin Tasarımcısı<br />3.  MailTemplateBody.htm: gönderilecek e-posta şablonu.|  
|SendMailTestClient|SendMail etkinlik test etmek için istemci.  Bu proje SendMail etkinlik çağrılırken, iki yolunu gösterir: bildirimli ve programlı olarak.|1.  Sequence1.XAML: SendMail etkinlik çağıran iş akışı.<br />2.  Program.cs: Sıra1 çağırır ve aynı zamanda program aracılığıyla SendMail kullanan bir iş akışı oluşturur.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>SendMail etkinlik başka bir yapılandırma  
 Örnekte gösterilmese, kullanıcılar ayrıca yapılandırma SendMail etkinliğin gerçekleştirebilir. Sonraki üç bölümde nasıl yapıldığını gösterir.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Gövdesinde belirtilen belirteçleri kullanarak bir e-posta gönderme  
 Bu kod parçacığı, nasıl gövdesinde e-posta belirteçleri ile gönderebileceğiniz gösterilir. Gövde özelliğinde belirteçlerin nasıl sağlanan dikkat edin. Bu belirteçler için değerler belirteçleri özelliğine sağlanır.  
  
```html  
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
  
### <a name="sending-an-email-using-a-template"></a>Şablon kullanarak bir e-posta gönderme  
 Bu kod parçacığı gövdesinde bir şablon belirteçleri kullanarak bir e-posta gönderme işlemini gösterir. Ayarlarken dikkat `BodyTemplateFilePath` özelliği biz (şablon dosyasının içeriğini gövdesine kopyalanır) gövde özelliği için değer sağlamanız gerekmez.  
  
```  
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
  
### <a name="sending-mails-in-testing-mode"></a>Modu test e-postalar gönderme  
 Bu kod parçacığı, iki test özelliklerini ayarlama işlemi gösterilmektedir: ayarlayarak `TestMailTo` tüm iletileri gönderilir john.doe@contoso.con (bakmadan değerlerinin Kime, bilgi, gizli). TestDropPath ayarlayarak tüm giden e-postaları da sağlanan yolda kaydedilir. Bu özellikler bağımsız olarak ayarlanabilir (bunlar birbiriyle ilgili olmayan).  
  
```  
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
  
 Bir SMTP sunucusu kurma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.  
  
-   [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [SMTP Hizmeti (IIS 6.0) yapılandırma](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0: SMTP e-posta yapılandırma](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [SMTP hizmeti nasıl yüklenir?](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Üçüncü taraflarca sağlanan SMTP öykünücüsünü indirme için kullanılabilir.  
  
##### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SendMail.sln çözüm dosyasını açın.  
  
2.  Geçerli bir SMTP sunucusuna erişimi olduğundan emin olun. Kurulum yönergelerine bakın.  
  
3.  Programı, sunucu adresi ve Kimden ve Kime e-posta adreslerini yapılandırın.  
  
     Doğru Bu örneği çalıştırmak için ilk ve son e-posta adresi ve SMTP sunucusunun adresini değerini program.CS'de Webhostbuilder'a ve Sequence.xaml yapılandırmanız gerekebilir. Program iki farklı şekilde posta gönderen adresi konumlarının her ikisinde de değiştirmek gerekir  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`