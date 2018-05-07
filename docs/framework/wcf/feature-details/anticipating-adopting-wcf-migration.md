---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma
Yeni ASP.NET uygulamaları WCF için daha kolay gelecekteki geçişini sağlamak için aşağıdaki önerileri yanı sıra önceki önerileri izleyin.  
  
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
  
 WCF SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uyumludur iletileri farklı uç noktalar kullanarak Git gerektirdiğinden Bunun yapılması önerilir. Hizmet SOAP 1.1 ve SOAP olamaz sonra varsayılan yapılandırmadır 1.2 desteklemek üzere yapılandırıldığı ASP.NET 2.0 Web kesinlikle olacak özgün adresinde tek bir WCF uç noktası için İleri geçirdiyseniz tüm ASP.NET Web ile uyumlu olması hizmetin mevcut istemciler. Ayrıca 1.1 yerine SOAP 1.2 seçme hizmet clientele daha ciddi bir şekilde kısıtlar.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 WCF hizmet sözleşmeleri uygulayarak tanımlamanıza izin verir <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri ya sınıfları sağlar. Bunu yaptığınızda bu nedenle herhangi bir sayıda sınıfları teknolojiye uygulanabileceği bir sözleşme tanımının oluşturduğundan arabirime yerine bir sınıfa öznitelik uygulamak için önerilir. ASP.NET 2.0 destekler, uygulamanın seçeneği <xref:System.Web.Services.WebService> öznitelik sınıfları yanı sıra arabirimleri. Ancak, önceden belirtildiği gibi yok ASP.NET 2. 0'da, bir üründe, Namespace parametresinin <xref:System.Web.Services.WebService> özniteliği hiçbir etkisi bu özniteliği bir sınıf yerine bir arabirim uygulandığında. Varsayılan değer alanından bir hizmet ad alanı değiştirmek için genellikle önerilir olduğundan http://tempuri.org, Namespace parametresini kullanarak <xref:System.Web.Services.WebService> öznitelik, bir devam etmelidir ASP.NET Web Hizmetleri uygulayarak tanımlama <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya sınıfları özniteliği.  
  
-   Bu arabirimleri tanımlanan yöntemler mümkün olduğunca küçük koda sahip. İşlerini başka sınıfların temsilci sağlayın. Yeni WCF hizmet türleri, bu sınıfların substantive iş de atayabilirsiniz.  
  
-   Kullanarak hizmet işlemleri için açık adlar sağlayan `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     ASP.NET işlemleri için varsayılan adlar WCF tarafından sağlanan varsayılan adlarından farklı olduğu için Bunun yapılması önemlidir. Açık adları sağlayarak, varsayılan değerleri bağlı kaçının.  
  
-   WCF biçimli yöntemleriyle uygulama işlemlerini desteklemediğinden, ASP.NET Web hizmeti işlemleri çok biçimli yöntemleriyle kullanılmaz.  
  
-   Kullanım <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> tarafından hangi HTTP isteklerinin yöntemlere yönlendirilecek SOAPAction HTTP üstbilgilerinin açık değerlerini sağlamak için.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Bu yaklaşımı, varsayılan ASP.NET ve WCF aynı anda tarafından kullanılan SOAPAction değerleri kullanan gerek kalmadan atlama.  
  
-   SOAP uzantılarını kullanmaktan kaçının. SOAP uzantılarını gerekirse, bunlar kabul amacı WCF tarafından zaten sağlanan bir özellik olup olmadığını belirler. Ardından, gerçekten durumda, WCF hemen benimsemeyi değil seçimi alan.  
  
## <a name="state-management"></a>Durum Yönetimi  
 Hizmetleri'ndeki durumunu korumak üzere olmamasına özen gösterin. Yalnızca durum koruma uygulama ölçeklenebilirliğini tehlikeye eğilimindedir yapar, ancak WCF ASP.NET mekanizmaları ASP.NET uyumluluk modunda desteklese de, ASP.NET ve WCF durumu yönetimi mekanizmaları çok farklı.  
  
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
  
 Bu özel durum sınıfları WCF ile kolayca yeniden kullanılabilir<xref:System.ServiceModel.FaultException%601> yeni bir özel durum sınıfı `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Güvenlik  
 Bazı güvenlik önerileri verilmiştir.  
  
-   Kaçının kullanarak olarak ASP.NET 2.0 profilleri kullanılarak kısıtlamak ASP.NET tümleştirme modu kullanımını hizmet için WCF geçirdiyseniz.  
  
-   Hizmetlere erişim için ASP.NET Web Hizmetleri destekleyen Internet Information Services (IIS) kullanarak ACL'ler denetlemek için ACL kullanmaktan kaçının, WCF yok; çünkü ASP.NET Web hizmetlerini barındırmak için IIS üzerinde bağlı ve WCF mutlaka yok IIS'de barındırılması.  
  
-   Bir hizmet kaynaklara erişim yetkisi vermek için ASP.NET 2.0 rol sağlayıcıları kullanmayı düşünün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
