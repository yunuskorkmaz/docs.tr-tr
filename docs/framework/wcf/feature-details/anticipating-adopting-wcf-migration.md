---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185466"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma
WCF'ye yeni ASP.NET uygulamalarının gelecekte daha kolay geçişini sağlamak için, aşağıdaki önerilerin yanı sıra önceki önerileri de izleyin.  
  
## <a name="protocols"></a>Protokoller  
 SOAP 1.2 için 2.0 desteğiASP.NET devre dışı kalım:  
  
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
  
 WCF, SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uygun iletilerin farklı uç noktaları kullanarak kullanılmasını gerektirdiğinden bunu yapmak tavsiye edilir. Bir ASP.NET 2.0 Web hizmeti, varsayılan yapılandırma olan SOAP 1.1 ve SOAP 1.2'yi destekleyecek şekilde yapılandırılırsa, orijinal adreste kesinlikle tüm ASP.NET Web ile uyumlu olacak tek bir WCF bitiş noktasına geçirilemez. hizmetin mevcut istemcileri. Ayrıca 1.1 yerine SOAP 1.2'yi seçmek, hizmetin müşterilerini daha ciddi bir şekilde kısıtlar.  
  
## <a name="service-development"></a>Hizmet Geliştirme  
 WCF, arabirimlere <xref:System.ServiceModel.ServiceContractAttribute> veya sınıflara uygulayarak hizmet sözleşmelerini tanımlamanıza olanak tanır. Bunu yapmak çeşitli sınıflar herhangi bir sayı tarafından uygulanabilen bir sözleşme tanımı oluşturur, çünkü bu özniteliği bir sınıf yerine bir arabirime uygulamak için önerilir. ASP.NET 2.0, öznitelik in <xref:System.Web.Services.WebService> arabirimlerine ve sınıflara uygulanma seçeneğini destekler. Ancak, daha önce de belirtildiği gibi, ASP.NET 2.0'da bir kusur <xref:System.Web.Services.WebService> vardır ve bu öznitelik bir sınıf yerine arabirime uygulandığında özniteliğin Ad alanı parametresinin hiçbir etkisi yoktur. Bir hizmetin ad alanını varsayılan değerden değiştirmek genellikle tavsiye `http://tempuri.org`edilir, öznitelik Ad alanı <xref:System.Web.Services.WebService> parametresini kullanarak, öznitelik veya sınıflara <xref:System.ServiceModel.ServiceContractAttribute> öznitelik uygulayarak ASP.NET Web Hizmetleri tanımlamaya devam edilmelidir.  
  
- Bu arabirimlerin tanımlandığı yöntemlerde mümkün olduğunca az kod alabildiğiniz kadar az koda sahip olabilir. Çalışmalarını diğer sınıflara devretsinler. Yeni WCF hizmet türleri de bu sınıflara kendi maddi çalışma temsilci olabilir.  
  
- Parametreyi `MessageName` kullanarak bir hizmetin işlemleri için <xref:System.Web.Services.WebMethodAttribute>açık adlar sağlayın.  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     ASP.NET işlemleri için varsayılan adlar WCF tarafından sağlanan varsayılan adlardan farklı olduğundan, bunu yapmak önemlidir. Açık adlar sağlayarak, varsayılan adlara güvenmekten kaçınırsınız.  
  
- WCF çok morfik yöntemlerle işlemleri uygulama desteklemez, çünkü ASP.NET Web hizmet işlemleri çok morfik yöntemlerle uygulamayın.  
  
- SOAPAction <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> HTTP üstbilgilerine, HTTP isteklerinin yöntemlere yönlendirileceği açık değerleri sağlamak için kullanın.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Bu yaklaşımın yanı, ASP.NET ve WCF tarafından kullanılan varsayılan SOAPAction değerlerinin aynı olmasına güvenmek zorunda kalmanın ardından gelecektir.  
  
- SOAP uzantıları kullanmaktan kaçının. SOAP uzantıları gerekiyorsa, değerlendirilme amaçlarının WCF tarafından zaten sağlanan bir özellik olup olmadığını belirleyin. Bu gerçekten durumda, o zaman hemen WCF benimsemek değil seçim yeniden düşünün.  
  
## <a name="state-management"></a>Devlet Yönetimi  
 Hizmetlerde durumu korumak zorunda kalmaktan kaçının. WCF ASP.NET uyumluluk modunda ASP.NET mekanizmaları desteklemesine rağmen, devletin korunması bir uygulamanın ölçeklenebilirliğinden ödün vermekle kalmıyor, aynı zamanda ASP.NET ve WCF'nin devlet yönetim mekanizmaları da çok farklıdır.  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 Bir hizmet tarafından gönderilecek ve alınacak veri türlerinin yapılarını tasarlarken, istemciye iletmek isteyebileceği bir hizmet içinde oluşabilecek çeşitli özel durum türlerini temsil edecek yapılar da tasarlar.  
  
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
  
 Bu tür sınıflara kendilerini XML'e serileştirme olanağı verin:  
  
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
  
 Sınıflar daha sonra açıkça atılan <xref:System.Web.Services.Protocols.SoapException> örnekler için ayrıntıları sağlamak için kullanılabilir:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Bu özel durum sınıfları, WCF <xref:System.ServiceModel.FaultException%601> sınıfı yla kolayca yeniden kullanılabilir hale gelir ve yeni bir`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Güvenlik  
 Aşağıda bazı güvenlik önerileri veremeleri yer alıyor.  
  
- Hizmet WCF'ye geçirilmişse, 2.0 Profillerini ASP.NET kullanmaktan kaçının, çünkü bunları kullanmak ASP.NET Tümleştirme Modu'nun kullanımını kısıtlar.  
  
- ASP.NET Web hizmetleri Internet Information Services (IIS) kullanarak ALA'ları desteklediği için, hizmetlere erişimi denetlemek için ALA'lar kullanmaktan kaçının, çünkü ASP.NET Web hizmetleri barındırma için IIS'ye bağlıdır ve WCF'nin IIS'de barındırılması gerekmez.  
  
- Bir hizmetin kaynaklarına erişim yetkisi vermek için ASP.NET 2.0 Rol Sağlayıcıları kullanmayı düşünün.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
