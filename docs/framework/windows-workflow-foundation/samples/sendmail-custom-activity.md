---
title: SendMail Özel Etkinliği
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 4dca15bfd3798b9282960663bea827f9323a1266
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547746"
---
# <a name="sendmail-custom-activity"></a>SendMail Özel Etkinliği
Bu örnek, <xref:System.Activities.AsyncCodeActivity> bir iş akışı uygulaması içinde kullanılmak üzere SMTP kullanarak posta göndermek için öğesinden türetilen özel bir etkinliğin nasıl oluşturulacağını gösterir. Özel etkinlik, <xref:System.Net.Mail.SmtpClient> e-postayı zaman uyumsuz olarak göndermek ve kimlik doğrulamasıyla posta göndermek için yeteneklerini kullanır. Ayrıca, test modu, belirteç değiştirme, dosya şablonları ve test bırakma yolu gibi bazı son kullanıcı özellikleri de sağlar.  
  
 Aşağıdaki tabloda etkinliğin bağımsız değişkenlerinin ayrıntıları verilmiştir `SendMail` .  
  
|Ad|Tür|Description|  
|-|-|-|  
|Ana bilgisayar|Dize|SMTP sunucusu konağının adresi.|  
|Bağlantı noktası|Dize|Konaktaki SMTP hizmetinin bağlantı noktası.|  
|EnableSsl|bool|<xref:System.Net.Mail.SmtpClient>Bağlantının, bağlantıyı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanıp kullanmadığını belirtir.|  
|UserName|Dize|Gönderen özelliğinin kimlik doğrulaması için kimlik bilgilerini ayarlamak üzere Kullanıcı adı <xref:System.Net.Mail.SmtpClient.Credentials%2A> .|  
|Parola|Dize|Gönderen özelliğinin kimlik doğrulaması için kimlik bilgilerini ayarlamak için parola <xref:System.Net.Mail.SmtpClient.Credentials%2A> .|  
|Konu|<xref:System.Activities.InArgument%601>\<string>|İletinin konusu.|  
|Gövde|<xref:System.Activities.InArgument%601>\<string>|İletinin gövdesi.|  
|Ekler|<xref:System.Activities.InArgument%601>\<string>|Bu e-posta iletisine eklenen verileri depolamak için kullanılan ek koleksiyonu.|  
|Kaynak|<xref:System.Net.Mail.MailAddress>|Bu e-posta iletisinin Kimden adresi.|  
|Amaç|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisinin alıcılarını içeren adres toplama.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için karbon kopyası (CC) alıcılarını içeren adres toplama.|  
|ALÝCÝ|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Bu e-posta iletisi için gizli bilgi kopyası (gızlı) alıcılarını içeren adres toplama.|  
|Belirteçler|<xref:System.Activities.InArgument%601><IDictionary\<string, string>>|Gövdede değiştirilecek belirteçler. Bu özellik, kullanıcıların gövdede daha sonra bu özellik kullanılarak girilen belirteçlerle değiştirilebilmesi için bazı değerler belirlemesine izin verir.|  
|BodyTemplateFilePath|Dize|Gövde şablonunun yolu. `SendMail`Etkinlik bu dosyanın içeriğini Body özelliğine kopyalar.<br /><br /> Şablon, belirteçler özelliğinin içeriğiyle değiştirilmiş belirteçleri içerebilir.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adrese gönderilir.<br /><br /> Bu özellik iş akışlarını test ederken kullanılmak üzere tasarlanmıştır. Örneğin, tüm e-postaların gerçek alıcılara gönderilmeksizin gönderilmesini sağlamak istediğinizde.|  
|TestDropPath|Dize|Bu özellik ayarlandığında, tüm e-postalar da belirtilen dosyaya kaydedilir.<br /><br /> Bu özellik, giden e-postaların biçiminin ve içeriğinin uygun olduğundan emin olmak için iş akışlarını test ederken veya hata ayıklarken kullanılmak üzere tasarlanmıştır.|  
  
## <a name="solution-contents"></a>Çözüm Içeriği  
 Çözüm iki proje içerir.  
  
|Proje|Açıklama|Önemli dosyalar|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail etkinliği|1. SendMail.cs: ana etkinlik için uygulama<br />SendMail etkinliği için 2. SendMailDesigner. xaml ve SendMailDesigner.xaml.cs: Designer<br />3. MailTemplateBody.htm: gönderilecek e-postanın şablonu.|  
|SendMailTestClient|SendMail etkinliğini test etmek için istemci.  Bu proje, SendMail etkinliğini çağırmanın iki yolunu gösterir: bildirimli ve programlı olarak.|1. Sequence1. xaml: SendMail etkinliğini çağıran iş akışı.<br />2. Program.cs: Sequence1 çağırır ve ayrıca SendMail kullanan programlı bir iş akışı oluşturur.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>SendMail etkinliğinin daha fazla yapılandırması  
 Örnekte gösterilmese de, kullanıcılar SendMail etkinliğinin ek yapılandırmasını gerçekleştirebilir. Sonraki üç bölümde bunun nasıl yapılacağı gösterilmektedir.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Gövdede belirtilen belirteçleri kullanarak e-posta gönderme  
 Bu kod parçacığı, gövdedeki belirteçlerle nasıl e-posta gönderebileceğinizi gösterir. Gövde özelliğinde belirteçlerin nasıl sağlandığını fark edin. Bu belirteçlerin değerleri belirteçler özelliğine sağlanır.  
  
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
 Bu kod parçacığında, gövdedeki bir şablon belirteçlerini kullanarak e-posta gönderme gösterilmektedir. `BodyTemplateFilePath`Gövde özelliği için değer sağlamak zorunda olduğumuz özelliği ayarlarken (şablon dosyasının içeriği gövdeye kopyalanacaktır) dikkat edin.  
  
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
  
### <a name="sending-mails-in-testing-mode"></a>Sınama modunda postaları gönderme  
 Bu kod parçacığı, iki test özelliklerinin nasıl ayarlanacağını gösterir: ayarına göre `TestMailTo` , tüm iletiler için gönderilir `john.doe@contoso.con` (Kime, CC, gizli değerleri olmadan). TestDropPath ' i ayarlayarak tüm giden e-postalar da, belirtilen yola kaydedilir. Bu özellikler bağımsız olarak ayarlanabilir (ilişkili değildir).  
  
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
 Bu örnek için bir SMTP sunucusuna erişim gerekir.  
  
 SMTP sunucusu kurma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.  
  
- [SMTP hizmetini yapılandırma (IIS 6,0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7,0: SMTP e-postasını Yapılandırma](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [SMTP hizmetini nasıl yükleyeceğiniz](/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 Üçüncü taraflar tarafından sağlanan SMTP öykünücüleri indirilebilir.  
  
##### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1. Visual Studio 2010 kullanarak SendMail. sln çözüm dosyasını açın.  
  
2. Geçerli bir SMTP sunucusuna erişiminiz olduğundan emin olun. Bkz. kurulum yönergeleri.  
  
3. Programı sunucu adresinizle ve Kimden e-posta adreslerinden yapılandırın.  
  
     Bu örneği doğru bir şekilde çalıştırmak için, ' ın ve e-posta adresleri ve Program.cs içindeki SMTP sunucusunun adresi ve dizi. xaml içindeki adresini yapılandırmanız gerekebilir. Program postayı iki farklı şekilde gönderdiğinden, her iki konumdaki adresi de değiştirmeniz gerekir  
  
4. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
5. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
