---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 171a31b375eae4c032849c2a1c2090f5d9ff856f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837407"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma
Yeni ASP.NET uygulamalarını wcf'ye TAŞIMA daha kolay gelecekteki geçişini sağlamak için yukarıdaki öneriler ve bunun yanı sıra aşağıdaki önerileri uygulayın.  
  
## <a name="protocols"></a>Protokolleri  
 ASP.NET 2.0'ın SOAP 1.2 desteği devre dışı bırakın:  
  
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
  
 WCF SOAP 1.1 ve SOAP 1.2 gibi farklı protokollere uyumludur iletileri farklı uç noktaları kullanarak Git gerektirdiğinden Bunun yapılması önerilir. ASP.NET 2.0 Web hizmeti SOAP 1.1 hem olamaz sonra varsayılan yapılandırma, SOAP 1.2 desteklemek üzere yapılandırılmış tek bir WCF uç noktasına kesinlikle olabilecek özgün adresten İleri geçirdiyseniz, tüm ASP.NET Web ile uyumlu olacak hizmetin mevcut istemciler. Ayrıca 1.1 yerine SOAP 1.2 seçme clientele hizmetinin daha ciddi bir şekilde kısıtlar.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 WCF hizmet sözleşmelerini uygulayarak tanımlamanıza izin verir <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya sınıflar. Bunun yapılması, bu nedenle herhangi bir sayıda sınıfları teknolojiye uygulanabilir bir sözleşme tanımı oluşturur çünkü bir arabirim yerine bir sınıf özniteliği uygulamak için önerilir. ASP.NET 2.0 uygulama seçeneğini destekler <xref:System.Web.Services.WebService> öznitelik sınıflarının yanı sıra arabirimleri. Ancak, önceden belirtildiği gibi yoktur, ASP.NET 2. 0'da, bir hata Namespace parametresi <xref:System.Web.Services.WebService> özniteliği bu öznitelik, bir sınıf yerine bir arabirim uygulandığında hiçbir etkiye sahiptir. Varsayılan değer, bir hizmet ad alanı değiştirmek için genellikle tavsiye olduğundan `http://tempuri.org`, Namespace parametresini kullanarak <xref:System.Web.Services.WebService> öznitelik, bir çalışmaya devam ASP.NET Web hizmetlerini uygulayarak tanımlama <xref:System.ServiceModel.ServiceContractAttribute> arabirimleri veya Sınıf özniteliği.  
  
-   Bu arabirimleri tarafından tanımlanan yöntemler olabildiğince küçük kod sahip. Çalışmalarını diğer sınıflar için temsilci sağlayın. Yeni bir WCF Hizmeti türleri, bu sınıfların substantive işlerini de atayabilirsiniz.  
  
-   Kullanarak bir hizmet işlemleri için açık adlar sağlayan `MessageName` parametresinin <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     ASP.NET'te işlemleri için varsayılan adlar WCF tarafından sağlanan varsayılan adları farklı olduğundan Bunun yapılması önemlidir. Açık bir ad sağlayarak, varsayılan değerleri bağlı olan kaçının.  
  
-   WCF polimorfik yöntemlerle uygulama işlemlerini desteklemediğinden, ASP.NET Web hizmeti işlemleri çok biçimli yöntemleriyle kullanılmaz.  
  
-   Kullanım <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> açık değerler tarafından hangi HTTP isteklerinin yöntemlere yönlendirilecek SOAPAction HTTP üst bilgilerini sağlamak için.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Bu yaklaşımı, varsayılan ASP.NET ve WCF aynı anda tarafından kullanılan SOAPAction değerleri kullanan gerek kalmadan aşmak.  
  
-   SOAP uzantıları kullanmaktan kaçının. SOAP uzantıları gerekiyorsa, bunlar kabul amacı zaten WCF tarafından sağlanan bir özellik olup olmadığını belirler. Ardından, aslında durumda, WCF hemen benimsemeye değil seçimi yeniden gözden geçir.  
  
## <a name="state-management"></a>Durum Yönetimi  
 Hizmetleri'nde durumunu korumak üzere yapmamaya Yalnızca durum koruma uygulamasının ölçeklenebilirliğini aşmaya eğilimli yapar, ancak WCF ASP.NET mekanizmaları ASP.NET uyumluluk modunda desteklese de ASP.NET ve WCF durumu yönetim sistemleri çok farklı.  
  
## <a name="exception-handling"></a>Özel Durum İşleme  
 Gönderilen ve alınan bir hizmet tarafından aktarılacak veri türlerini yapıları tasarlarken, ayrıca tek bir hizmet içinde oluşabilecek özel durumları çeşitli türlerini temsil etmek için tasarım yapıları istemciye iletmek isteyebilir.  
  
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
  
 Bu tür sınıflar kendileri için XML seri hale getirme olanağı sağlar:  
  
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
  
 Sınıflar için açıkça durum ayrıntılarını sağlamak için daha sonra kullanılabilir <xref:System.Web.Services.Protocols.SoapException> örnekleri:  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Bu özel durum sınıfları WCF ile kolayca yeniden kullanılabilir olacaktır<xref:System.ServiceModel.FaultException%601> sınıfının yeni bir `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Güvenlik  
 Bazı güvenlik önerileri aşağıda verilmiştir.  
  
-   Önlemek ASP.NET 2.0 profilleri kullanarak olarak sınırlandıracak ASP.NET tümleştirme modu kullanımını hizmet WCF'ye geçirdiyseniz.  
  
-   ASP.NET Web Hizmetleri Internet Information Services (IIS) kullanarak ACL'leri destekler, hizmetlere erişimi denetlemek için ACL'leri kullanmaktan kaçının, WCF desteklemez; çünkü ASP.NET Web hizmetlerini barındırmak için IIS üzerinde bağlıdır ve WCF gerekmeyen gerekmez IIS'de barındırılan.  
  
-   Bir hizmetin kaynaklara erişim yetkisi vermek için ASP.NET 2.0 rol sağlayıcıları kullanmayı düşünün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
