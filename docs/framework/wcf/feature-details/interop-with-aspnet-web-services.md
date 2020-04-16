---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464087"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ASP.NET Web hizmetleri ile Windows Communication Foundation (WCF) Web hizmetleri arasında birlikte çalışabilirlik, her iki teknoloji kullanılarak uygulanan hizmetlerin WS-I Temel Profil 1.1 belirtimine uygun olmasını sağlayarak elde edilebilir. WS-I Temel Profil 1.1'e uygun ASP.NET Web hizmetleri, <xref:System.ServiceModel.BasicHttpBinding>WCF sistemi tarafından sağlanan bağlama kullanılarak WCF istemcileri ile birlikte çalışabilir.  
  
 ASP.NET 2.0 seçeneğini kullanarak <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> sınıfyerine arabirime ve öznitelikleri ekleme ve aşağıdaki örnek kodda gösterildiği gibi arabirimi uygulamak için bir sınıf yazma seçeneğini kullanın.  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 Öznitelik ile <xref:System.Web.Services.WebService> arabirim farklı şekillerde aynı sözleşmeyi uygulayabilir çeşitli sınıflar ile yeniden kullanılabilir hizmet tarafından gerçekleştirilen işlemler için bir sözleşme oluşturduğundan, bu seçeneğin kullanılması tercih edilir.  
  
 İletilerin <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> `SOAPAction` HTTP üstbilgiyerine SOAP iletisinin gövde öğesinin tam nitelikli adını temel alan yöntemlere yönlendirilmiş olması için özniteliği kullanmaktan kaçının. WCF iletileri yönlendirme için `SOAPAction` HTTP üstbilgisini kullanır.  
  
 Bir türü varsayılan <xref:System.Xml.Serialization.XmlSerializer> olarak serileştiren XML, XML'in ad alanının açıkça tanımlanması koşuluyla, bir türü <xref:System.Runtime.Serialization.DataContractSerializer> serileştirdiği XML ile anlamsal olarak aynıdır. WCF'yi benimseme beklentisiyle ASP.NETWeb hizmetlerinde kullanılmak üzere bir veri türü tanımlarken aşağıdakileri yapın:  
  
- XML Şeması yerine .NET Framework sınıflarını kullanarak türü tanımlayın.  
  
- Türü için <xref:System.SerializableAttribute> ad <xref:System.Xml.Serialization.XmlRootAttribute> alanını açıkça tanımlamak için ikincisini kullanarak yalnızca ve sınıfa ekleyin. .NET Framework sınıfının <xref:System.Xml.Serialization> XML'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.  
  
- Bu yaklaşımı benimseyerek, .NET sınıflarını daha sonra veri sözleşmelerine ekleyerek <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> ve sınıfların iletim için seri hale getirildiği XML'yi önemli ölçüde değiştirmeden yapabilmeniz gerekir. ASP.NET Web hizmetleri tarafından iletilerde kullanılan türler, WCF uygulamaları tarafından veri sözleşmeleri olarak işlenebilir ve wcf uygulamalarında diğer avantajların yanı sıra daha iyi performans sağlar.  
  
 Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçeneklerini kullanmaktan kaçının. WCF istemcileri bunları desteklemez. Bir hizmetin güvence altına alınması gerekiyorsa, bu seçenekler sağlam olduğundan ve standart protokollere dayandığından WCF tarafından sağlanan seçenekleri kullanın.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HttpModule'in yüklenmesinden kaynaklanan performans etkisi  
 .NET Framework 3.0'da, `HttpModule` WCF root Web.config dosyasına her ASP.NET uygulamanın WCF etkin olduğunu yüklenmiş. Bu performansı etkileyebilir, böylece `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için kaldırabilirsiniz.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
