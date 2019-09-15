---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 59ee6412cde152588e8007fe530cc8e5708410e5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991527"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ASP.NET Web Hizmetleri ve Windows Communication Foundation (WCF) Web Hizmetleri arasında birlikte çalışabilirlik, her iki teknolojiyi kullanarak uygulanan hizmetlerin WS-ı temel profil 1,1 belirtimine uyduğundan emin olarak elde edilebilir. WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, <xref:System.ServiceModel.BasicHttpBinding>WCF sistem tarafından sunulan bağlama kullanılarak WCF istemcileriyle birlikte çalışabilir.  
  
 Aşağıdaki örnek kodda gösterildiği gibi, <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> özniteliklerini bir sınıf yerine arabirime eklemek için ASP.NET 2,0 seçeneğini kullanın ve arabirimi uygulamak için bir sınıf yazmak.  
  
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
  
 Bu seçeneğin kullanılması tercih edilir çünkü <xref:System.Web.Services.WebService> özniteliğe sahip arabirim, hizmet tarafından gerçekleştirilen işlemler için, aynı sözleşmeyi farklı yollarla uygulayabilecek çeşitli sınıflarla yeniden kullanılabilen işlemler için bir sözleşme oluşturur.  
  
 `SOAPAction` Http üstbilgisi yerine SOAP iletisinin gövde öğesinin tam adı temelinde yöntemlere yönlendirilmek için özniteliğinikullanmaktankaçının.<xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> WCF, `SOAPAction` iletileri yönlendirme için http üstbilgisini kullanır.  
  
 Bir türü varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> olarak serihalegetirilenXML,birtürüserihalegetirilenXMLileaynıdır,bu,XMLiçinadalanıaçıkçatanımlanmışolarakbelirtilmelidir.<xref:System.Xml.Serialization.XmlSerializer> WCF 'yi benimseme olasılığına içinde ASP. NETWeb Hizmetleri ile kullanmak için bir veri türü tanımlarken, aşağıdakileri yapın:  
  
- Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.  
  
- Türü için ad <xref:System.SerializableAttribute> alanını açıkça <xref:System.Xml.Serialization.XmlRootAttribute> tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin. .NET Framework sınıfının XML 'e nasıl çevrileceğini denetlemek <xref:System.Xml.Serialization> için ad alanından ek öznitelikler eklemeyin.  
  
- Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve sınıflarının iletilmek üzere serileştirildiği XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' <xref:System.Runtime.Serialization.DataMemberAttribute> nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz. ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar ve WCF uygulamalarında daha iyi performans gibi işlenebilir.  
  
 Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının. WCF istemcileri bunları desteklemez. Bir hizmetin güvenliğinin sağlanması gerekiyorsa WCF tarafından sağlanan seçenekleri kullanın, çünkü bu seçenekler sağlam ve standart protokolleri temel alır.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HttpModule yüklemesi nedeniyle performans etkisi  
 .NET Framework 3,0 ' de, WCF `HttpModule` , kök Web. config dosyasında her ASP.NET uygulamasının WCF etkin olduğu gibi yüklenmiştir. Bu, aşağıdaki örnekte gösterildiği gibi Web. config `ServiceModel` dosyasını kaldırabilmeniz için performansı etkileyebilir.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WCF hizmetini ASP.NET Web hizmeti Istemcileriyle birlikte çalışmak üzere yapılandırma](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
