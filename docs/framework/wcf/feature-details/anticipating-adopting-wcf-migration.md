---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 375274cd1b67b6dc71d3e66e1c1f063a81db7d8e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma
Yeni ASP.NET uygulamaları için daha kolay gelecekteki geçişini sağlamak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], yukarıdaki öneriler ve bunun yanı sıra aşağıdaki önerileri uygulayın.  
  
## <a name="protocols"></a>protokolleri  
 SOAP 1.2 ASP.NET 2.0'in desteğini devre dışı bırakın:  
  
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
  
 Bunun yapılması önerilir çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] farklı uç noktalar kullanarak Git iletileri SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uyumludur gerektirir. Bir ASP.NET 2.0 Web hizmeti SOAP 1.1 ve SOAP 1.2, varsayılan yapılandırmadır desteklemek üzere yapılandırıldığı sonra İleri tek bir geçirilemez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç nokta olacak özgün adresinde kesinlikle tüm ASP ile uyumlu .NET web Service'in mevcut istemciler. Ayrıca 1.1 yerine SOAP 1.2 seçme hizmet clientele daha ciddi bir şekilde kısıtlar.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hizmet sözleşmeleri uygulayarak tanımlamanıza olanak verir <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri ya sınıfları sağlar. Bunu yaptığınızda bu nedenle herhangi bir sayıda sınıfları teknolojiye uygulanabileceği bir sözleşme tanımının oluşturduğundan arabirime yerine bir sınıfa öznitelik uygulamak için önerilir. ASP.NET 2.0 destekler, uygulamanın seçeneği <xref:System.Web.Services.WebService> öznitelik sınıfları yanı sıra arabirimleri. Ancak, önceden belirtildiği gibi yok ASP.NET 2. 0'da, bir üründe, Namespace parametresinin <xref:System.Web.Services.WebService> özniteliği hiçbir etkisi bu özniteliği bir sınıf yerine bir arabirim uygulandığında. Sonra varsayılan değerden http://tempuri.org, Namespace parametresini kullanarak bir hizmet ad alanı değiştirmek için genellikle önerilir <xref:System.Web.Services.WebService> öznitelik, bir devam etmelidir ASP.NET Web Hizmetleri uygulayarak tanımlama <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya sınıfları özniteliği.  
  
-   Bu arabirimleri tanımlanan yöntemler mümkün olduğunca küçük koda sahip. İşlerini başka sınıfların temsilci sağlayın. Yeni [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet türleri sonra ayrıca temsilci bu sınıfların substantive iş.  
  
-   Kullanarak hizmet işlemleri için açık adlar sağlayan `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Bunun yapılması önemlidir, ASP.NET işlemleri için varsayılan adlar tarafından sağlanan varsayılan adlarından farklı olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Açık adları sağlayarak, varsayılan değerleri bağlı kaçının.  
  
-   ASP.NET Web hizmeti işlemleri çok biçimli yöntemleriyle çünkü kullanılmaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] biçimli yöntemleriyle uygulama işlemlerini desteklemiyor.  
  
-   Kullanım <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> tarafından hangi HTTP isteklerinin yöntemlere yönlendirilecek SOAPAction HTTP üstbilgilerinin açık değerlerini sağlamak için.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Bu yaklaşımı aşmak SOAPAction değerleri ASP.NET tarafından kullanılan varsayılan yararlanmayı sahip ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı anda.  
  
-   SOAP uzantılarını kullanmaktan kaçının. SOAP uzantılarını gerekirse, ardından, bunlar olarak kabul edilir amacı tarafından sağlanan bir özellik olup olmadığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Gerçekten durumda değil benimsemeyi seçimi alan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hemen.  
  
## <a name="state-management"></a>Durum Yönetimi  
 Hizmetleri'ndeki durumunu korumak üzere olmamasına özen gösterin. Yalnızca durum koruma uygulama ölçeklenebilirlik ancak ASP.NET durum yönetimi mekanizmaları tehlikeye eğilimindedir ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çok farklı olan ancak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET ASP.NET uyumluluğu mekanizmaları modu.  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 Gönderilen ve hizmeti tarafından alınan veri türlerinin yapıları tasarlarken, ayrıca bir hizmet içinde oluşabilir ve bir özel durum çeşitli türlerde temsil etmek için tasarım yapıları istemciye iletmek isteyebilir.  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 Bu tür sınıflar kendileri için XML serileştirme olanağı verir:  
  
```  
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
  
 Sınıflar sonra açıkça durum için ayrıntılarını sağlamak için kullanılabilir <xref:System.Web.Services.Protocols.SoapException> örnekleri:  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Bu özel durum sınıfları ile kolayca yeniden kullanılabilir[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.FaultException%601> yeni bir özel durum sınıfı`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Güvenlik  
 Bazı güvenlik önerileri verilmiştir.  
  
-   Kaçının kullanarak olarak ASP.NET 2.0 profillerini kullanarak kısıtlamak ASP.NET tümleştirme modu kullanmak için hizmet geçirildiyse [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   ASP.NET Web hizmetlerini destekleyen olarak Internet Information Services (IIS) kullanarak ACL'ler hizmetlerine erişimi denetlemek için ACL kullanmaktan kaçının [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yok; çünkü ASP.NET Web hizmetlerini barındırmak için IIS üzerinde bağlı ve WCF mutlaka yok IIS'de barındırılması.  
  
-   Bir hizmet kaynaklara erişim yetkisi vermek için ASP.NET 2.0 rol sağlayıcıları kullanmayı düşünün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı benimsemeyi bekleme: gelecekteki tümleştirmeyi kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
