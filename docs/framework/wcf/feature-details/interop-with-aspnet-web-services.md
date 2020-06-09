---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f38209ffe2161e58528a108b29e730665a65da37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598872"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ASP.NET Web Hizmetleri ve Windows Communication Foundation (WCF) Web Hizmetleri arasında birlikte çalışabilirlik, her iki teknolojiyi kullanarak uygulanan hizmetlerin WS-ı temel profil 1,1 belirtimine uyduğundan emin olarak elde edilebilir. WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, WCF sistem tarafından sunulan bağlama kullanılarak WCF istemcileriyle birlikte çalışabilir <xref:System.ServiceModel.BasicHttpBinding> .  
  
 <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> Aşağıdaki örnek kodda gösterildiği gibi, ve özniteliklerini bir sınıf yerine arabirime eklemek için ASP.NET 2,0 seçeneğini kullanın ve arabirimi uygulamak için bir sınıf yazmak.  
  
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
  
 Bu seçeneğin kullanılması tercih edilir çünkü özniteliğe sahip arabirim, <xref:System.Web.Services.WebService> hizmet tarafından gerçekleştirilen işlemler için, aynı sözleşmeyi farklı yollarla uygulayabilecek çeşitli sınıflarla yeniden kullanılabilen işlemler için bir sözleşme oluşturur.  
  
 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute>Http üstbilgisi yerıne soap iletisinin gövde öğesinin tam adı temelinde yöntemlere yönlendirilmek için özniteliğini kullanmaktan kaçının `SOAPAction` . WCF, `SOAPAction` iletileri yönlendirme için http üstbilgisini kullanır.  
  
 <xref:System.Xml.Serialization.XmlSerializer>Bir türü varsayılan olarak seri hale getirilen XML, bir türü seri hale getirilen XML ile aynıdır, bu, <xref:System.Runtime.Serialization.DataContractSerializer> XML için ad alanı açıkça tanımlanmış olarak belirtilmelidir. WCF 'yi benimseme olasılığına içinde ASP. NETWeb Hizmetleri ile kullanmak için bir veri türü tanımlarken, aşağıdakileri yapın:  
  
- Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.  
  
- <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> Türü için ad alanını açıkça tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin. <xref:System.Xml.Serialization>.NET Framework SıNıFıNıN XML 'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.  
  
- Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıflarının iletilmek üzere SERILEŞTIRILDIĞI XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz. ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar ve WCF uygulamalarında daha iyi performans gibi işlenebilir.  
  
 Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının. WCF istemcileri bunları desteklemez. Bir hizmetin güvenliğinin sağlanması gerekiyorsa WCF tarafından sağlanan seçenekleri kullanın, çünkü bu seçenekler sağlam ve standart protokolleri temel alır.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HttpModule yüklemesi nedeniyle performans etkisi  
 .NET Framework 3,0 ' de, WCF, `HttpModule` kök Web. config dosyasında her ASP.net UYGULAMASıNıN WCF etkin olduğu gibi yüklenmiştir. Bu, `ServiceModel` Aşağıdaki örnekte gösterildiği gibi Web. config dosyasını kaldırabilmeniz için performansı etkileyebilir.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma](config-wcf-service-with-aspnet-web-service.md)
