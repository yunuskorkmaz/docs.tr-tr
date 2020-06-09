---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: b43f509bd49ebe89d7ed0be4c37b3ed179aaeb8c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576505"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma
Yeni ASP.NET uygulamalarının WCF 'ye daha kolay bir şekilde geçişini sağlamak için, önceki önerilere ve aşağıdaki önerilere uyun.  
  
## <a name="protocols"></a>Protokoller  
 SOAP 1,2 için ASP.NET 2.0 desteğini devre dışı bırakın:  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>
      </webServices>  
     </system.web>
</configuration>  
```  
  
 WCF, SOAP 1,1 ve SOAP 1,2 gibi farklı protokollerle uyumlu iletiler gerektirdiğinden farklı uç noktalar kullanarak devam etmek önerilir. Bir ASP.NET 2,0 Web hizmeti, varsayılan yapılandırma olan hem SOAP 1,1 hem de SOAP 1,2 'ı destekleyecek şekilde yapılandırıldıysa, özgün adresteki tüm ASP.NET Web hizmeti 'nin mevcut istemcileriyle uyumlu olacak şekilde tek bir WCF uç noktasına geçiş yapılamaz. Ayrıca, 1,2 1,1 yerine SOAP ' i seçtiğinizde hizmetin Clientele daha ciddi bir şekilde kısıtlanacaktır.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 WCF, arabirimleri veya sınıfları uygulayarak hizmet sözleşmeleri tanımlamanızı sağlar <xref:System.ServiceModel.ServiceContractAttribute> . Özniteliği, bir sınıf yerine bir arabirime uygulamanız önerilir, çünkü bunu yapmak, herhangi bir sayıda sınıf tarafından variously uygulanabilecek bir sözleşmenin tanımını oluşturur. ASP.NET 2,0, <xref:System.Web.Services.WebService> sınıfları arayüzlerin yanı sıra sınıflara uygulama seçeneğini destekler. Ancak, zaten bahsedildiği gibi, ASP.NET 2,0 ' de bir hata vardır, bu özniteliğin ad alanı parametresinin <xref:System.Web.Services.WebService> bir sınıf yerine bir arabirime uygulandığında hiçbir etkisi yoktur. Genellikle, bir hizmetin ad alanını varsayılan değerden değiştirmek önerilir, `http://tempuri.org` öznitelik ad alanı parametresini kullanarak, <xref:System.Web.Services.WebService> bir, <xref:System.ServiceModel.ServiceContractAttribute> özniteliği arabirimlere veya sınıflara uygulayarak ASP.NET Web hizmetlerini tanımlamaya devam etmelidir.  
  
- Bu arabirimlerin tanımlandığı metotlarda olabildiğince az kod olması gerekir. Çalışmalarını diğer sınıflara devretmek. Yeni WCF hizmet türleri, daha sonra bu sınıflara birlikte çalışan işlerini de devredebilir.  
  
- Parametresinin parametresini kullanarak bir hizmetin işlemlerine yönelik açık adlar sağlayın `MessageName` <xref:System.Web.Services.WebMethodAttribute> .  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Bu, ASP.NET içindeki işlemlerin varsayılan adları WCF tarafından sağlanan varsayılan adlardan farklı olduğundan, bunun yapılması önemlidir. Açık adlar sağlayarak varsayılan olanlara bağlı kalmaktan kaçının.  
  
- WCF, çok biçimli yöntemlerle uygulama işlemlerini desteklemediğinden, ASP.NET Web hizmeti işlemlerini polimorfik yöntemlerle uygulamayın.  
  
- <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>Http isteklerinin yöntemlere yönlendirileceği SOAPACTION http üst bilgilerine yönelik açık değerler sağlamak için öğesini kullanın.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Bu yaklaşımın alınması, ASP.NET tarafından kullanılan varsayılan SOAPAction değerlerini ve WCF 'nin aynı olduğunu aşmak için bir yaklaşım sağlar.  
  
- SOAP uzantıları kullanmaktan kaçının. SOAP uzantıları gerekliyse, kabul edildiği amacının WCF tarafından zaten sağlanmış olan bir özellik olup olmadığını saptayın. Bu durum gerçekten büyük bir durumdur, daha sonra WCF 'yi hemen benimseme seçeneğini yeniden değerlendirin.  
  
## <a name="state-management"></a>Durum yönetimi  
 Hizmetlerde durumu sürdürmek zorunda kalmaktan kaçının. Bir uygulamanın ölçeklenebilirliğini tehlikeye atmak için yalnızca durumun korunmasıyla kalmaz, ASP.NET ve WCF 'nin durum yönetimi mekanizmaları çok farklıdır, ancak WCF, ASP.NET uyumluluk modundaki ASP.NET mekanizmalarını destekler.  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 Bir hizmet tarafından gönderilecek ve alınacak veri türlerinin yapılarını tasarlarken, bir hizmette bir istemciye iletmek isteyebileceğiniz farklı özel durum türlerini temsil etmek için de tasarım yapıları.  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 Bu tür sınıflara, kendilerini XML 'e serileştirme yeteneği verin:  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 Sınıflar daha sonra açıkça oluşturulan örneklerin ayrıntılarını sağlamak için kullanılabilir <xref:System.Web.Services.Protocols.SoapException> :  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Bu özel durum sınıfları, <xref:System.ServiceModel.FaultException%601> Yeni bir hata oluşturması IÇIN WCF sınıfıyla birlikte yeniden kullanılabilir`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Güvenlik  
 Aşağıda bazı güvenlik önerileri verilmiştir.  
  
- ASP.NET 2,0 profillerinin kullanmaktan kaçının, bu hizmet WCF 'ye geçirildiğinde ASP.NET tümleştirme modunun kullanımını kısıtlar.  
  
- ASP.NET Web Hizmetleri, Internet Information Services (IIS) kullanan ACL 'Leri desteklediğinden, WCF, ASP.NET Web Hizmetleri barındırmak için IIS 'ye bağlı olduğundan ve WCF 'nin IIS 'de barındırılması gerekmeyen için, ACL 'Leri kullanmaktan kaçının.  
  
- Bir hizmetin kaynaklarına erişimi yetkilendirmek için ASP.NET 2,0 rol sağlayıcılarını kullanmayı düşünün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](anticipating-adopting-the-wcf-easing-future-integration.md)
