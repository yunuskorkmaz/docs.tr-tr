---
title: "SendMail özel etkinlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fb8454d3e1e679154bc016e37b83c3ac4ff6768
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="sendmail-custom-activity"></a>SendMail özel etkinlik
Bu örnek, türetilen özel bir etkinlik oluşturmak gösterilmiştir <xref:System.Activities.AsyncCodeActivity> bir iş akışı uygulama içinde kullanmak için SMTP kullanarak posta göndermek için. Özel Etkinlik özelliklerini kullanan <xref:System.Net.Mail.SmtpClient> zaman uyumsuz olarak e-posta göndermek için ve kimlik doğrulaması ile posta göndermek için. Bırakma yolu test ve test modu, belirteç değiştirme, dosya şablonları gibi bazı son kullanıcı özellikler de sağlar.  
  
 Aşağıdaki tabloda bağımsız değişkenleri ayrıntıları `SendMail` etkinlik.  
  
|Ad|Tür|Açıklama|  
|-|-|-|  
|Ana bilgisayar|Dize|SMTP sunucusunun ana bilgisayar adresi.|  
|Bağlantı Noktası|Dize|Ana bilgisayar SMTP hizmetinin bağlantı noktası.|  
|enableSsl|bool|Belirtir olup olmadığını <xref:System.Net.Mail.SmtpClient> Güvenli Yuva Katmanı (SSL) bağlantıyı şifrelemek için kullanır.|  
|UserName|Dize|Gönderenin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için kullanıcı adı <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliği.|  
|Parola|Dize|Gönderenin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için parola <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliği.|  
|Konu|<xref:System.Activities.InArgument%601>\<dize >|İleti konusu.|  
|Gövde|<xref:System.Activities.InArgument%601>\<dize >|İleti gövdesi.|  
|Ekler|<xref:System.Activities.InArgument%601>\<dize >|Bu e-posta iletisine verileri depolamak için kullanılan ek koleksiyonu.|  
|Başlangıç|<xref:System.Net.Mail.MailAddress>|Bu e-posta iletisinin adresinden.|  
|Bitiş|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisinin alıcılarını içeren koleksiyon adres.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için gizli kopya (CC) alıcıları içeren koleksiyon adres.|  
|GİZLİ|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için gizli kopya (gizli) alıcıları içeren koleksiyon adres.|  
|Belirteçler|<xref:System.Activities.InArgument%601>< IDictionary\<dize, dize >>|Gövdesinde değiştirmek için belirteç. Bu özellik, kullanıcıların bu özelliği kullanan sağlanan belirteçleri tarafından daha sonra değiştirilebilir daha bazı değerler gövdesinde belirtmesine izin verir.|  
|BodyTemplateFilePath|Dize|Gövdesi için bir şablon yolu. `SendMail` Etkinlik kendi gövde özelliğine bu dosyanın içeriğini kopyalar.<br /><br /> Şablon belirteçleri özelliği içeriğine göre değiştirilir belirteçleri içerebilir.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adresine gönderilir.<br /><br /> Bu özellik, iş akışları test edilirken kullanılmak üzere tasarlanmıştır. Örneğin, emin olmak istediğinizde tüm e-postalar gerçek alıcılara göndermeden gönderilir.|  
|TestDropPath|Dize|Bu özellik ayarlandığında, tüm e-postalar de belirtilen dosyasında kaydedilir.<br /><br /> Bu özellik biçimini ve giden e-postalar içeriğini uygun olmasını sağlamak için iş akışlarını, test veya geldiğinde kullanılmak üzere tasarlanmıştır.|  
  
## <a name="solution-contents"></a>Çözüm içeriği  
 Çözüm iki proje içerir.  
  
|Project|Açıklama|Önemli dosyaları|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail etkinliği|1.  SendMail.cs: ana etkinlik uygulama<br />2.  SendMailDesigner.xaml ve SendMailDesigner.xaml.cs: SendMail etkinliğinin Tasarımcısı<br />3.  MailTemplateBody.htm: gönderilecek e-posta şablonu.|  
|SendMailTestClient|Test SendMail etkinliği istemci.  Bu proje SendMail etkinlik çağırma iki yolla gösterir: bildirimli olarak ve program aracılığıyla.|1.  Sequence1.XAML: SendMail etkinlik çağıran iş akışı.<br />2.  Program.cs: Sıra1 çağırır ve program aracılığıyla SendMail kullanan bir iş akışı da oluşturur.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Başka bir yapılandırma SendMail etkinliği  
 Aşağıdaki örnekte gösterilmese kullanıcılar SendMail etkinliğin ek yapılandırma gerçekleştirebilir. Sonraki üç bölümde bunun nasıl yapılacağı gösterilmektedir.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Gövdede belirtilen belirteçleri kullanarak bir e-posta gönderme  
 Bu kod parçacığını nasıl gövdesinde belirteçleri içeren e-posta gönderebilirsiniz gösterir. Belirteçleri gövde özelliğinde nasıl sağlanır dikkat edin. Bu belirteçler için değerler belirteçleri özelliğine sağlanır.  
  
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
  
### <a name="sending-an-email-using-a-template"></a>Bir şablonu kullanarak bir e-posta gönderme  
 Bu kod parçacığında gövdesinde bir şablon belirteçleri kullanarak bir e-posta göndermek nasıl gösterir. Ayarlarken dikkat `BodyTemplateFilePath` özelliği biz gerekmez (şablon dosyası içeriğini gövdesine kopyalanacak) gövde özelliği için değer sağlayın.  
  
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
  
### <a name="sending-mails-in-testing-mode"></a>Mod testinde postalar gönderme  
 Bu kod parçacığını iki sınama özelliklerin nasıl ayarlanacağını gösterir: ayarlayarak `TestMailTo` tüm iletileri gönderilir john.doe@contoso.con (bakmadan değerlerinin Kime, bilgi, gizli). TestDropPath ayarlayarak tüm giden e-postalar, aynı zamanda sağlanan yolunda kaydedilir. Bu özellikler bağımsız olarak ayarlanabilir (bunlar birbiriyle ilgili olmayan).  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bir SMTP sunucusu kurma ayarlama, aşağıdaki bağlantılara bakın.  
  
-   [Microsoft Technet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [SMTP Hizmeti (IIS 6.0) yapılandırma](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0: SMTP e-posta yapılandırma](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [SMTP hizmeti nasıl yüklenir?](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Üçüncü taraflar tarafından sağlanan SMTP Öykünücüler indirme için kullanılabilir.  
  
##### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SendMail.sln çözüm dosyasını açın.  
  
2.  Geçerli bir SMTP sunucusuna erişimi olduğundan emin olun. Kurulum yönergelerine bakın.  
  
3.  Program, sunucu adresi ve Kimden ve Kime e-posta adreslerini yapılandırın.  
  
     Bu örnek düzgün çalışması için ilk ve son e-posta adresi ve SMTP sunucusunun adresini değerini Program.cs ve Sequence.xaml yapılandırmanız gerekebilir. Program iki farklı şekilde posta gönderir olduğundan her iki konumda adresi değiştirmeniz gerekir  
  
4.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
5.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`