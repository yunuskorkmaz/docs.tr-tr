---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c6fec1d520cd251473d8840b7b1afe879002a04c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108582"
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
Birlikte çalışabilirliği [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri ve Windows Communication Foundation (WCF) Web hizmetleri hem teknolojiler kullanılarak uygulanan Hizmetleri WS uygun sağlayarak gerçekleştirilebilir-ı Basic Profile 1.1 belirtimi. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web için WS uygun Hizmetleri-ı Basic Profile 1.1 ile WCF istemcileri birlikte çalışabilen WCF sistem tarafından sağlanan bağlama kullanarak <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Kullanım [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] ekleme seçeneği <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> bir arabirim yerine bir sınıf ve arabirim uygulamak için bir sınıf aşağıdaki örnek kodda gösterildiği gibi yazmak için öznitelikler.  
  
```  
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
  
 Bu seçenek kullanılarak tercih edilir, çünkü arabirimiyle <xref:System.Web.Services.WebService> özniteliği aynı sözleşme farklı şekillerde uygulayabilir, çeşitli sınıflarla yeniden kullanılabilir bir hizmet tarafından gerçekleştirilen işlemleri için bir sözleşmeyi oluşturur.  
  
 Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik SOAP iletisinin gövde öğesi tam olarak nitelenmiş adını temel alarak yerine `SOAPAction` HTTP üstbilgisi. WCF kullanan `SOAPAction` iletileri yönlendirmek için HTTP üstbilgisi.  
  
 XML'e <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlamı da XML'e aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir türü seri hale getirir. Bir veri türü ile kullanılmak üzere tanımlarken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web Hizmetleri WCF'nu benimsemenin olasılığına, aşağıdakileri yapın:  
  
-   XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.  
  
-   Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıf türünün ad alanını açıkça tanımlamak için ikinci kullanarak. Ek öznitelikleri eklemeyin <xref:System.Xml.Serialization> nasıl XML'e çevrilmesi için .NET Framework sınıf olduğunu denetlemek için ad alanı.  
  
-   Bu yaklaşım benimseyerek, daha sonra ek olarak veri sözleşmeleri içine .NET sınıfları oluşturmak erişebileceğinizi <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde boyutlandırabiliriz. İleti tarafından kullanılan türleri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri, diğer avantajlar arasında WCF uygulamalarında daha iyi performans sağlayan, WCF uygulamaları tarafından veri sözleşmeleri işlenebilir.  
  
 Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının. WCF istemcileri onları desteklemez. Bir hizmeti güvenli hale getirilmelidir, çünkü bu seçenekler, sağlam ve standardı protokollerine dayalıdır WCF tarafından sağlanan seçenekleri kullanın.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HttpModule yükleyerek nedeniyle performans etkisi  
 .NET Framework 3.0, WCF `HttpModule` kök Web.config dosyasında her bir ASP.NET uygulaması etkinleştirilmiş WCF olduğu şekilde yüklendi. Bu nedenle bu performansını etkileyebilir `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
