---
title: ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 8a0737a36989dd8bc6f5d5670555c7b2218798bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
Birlikte çalışabilirlik [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri ve Windows Communication Foundation (WCF) Web hizmetlerini elde edilebilir iki teknolojiyi kullanılarak uygulanan Hizmetleri WS uygun sağlayarak-ı temel Profil 1.1 belirtimini. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web WS uygun Hizmetleri-ı temel Profil 1.1 WCF istemcileriyle birlikte çalışabilir WCF sistem tarafından sağlanan bağlama kullanarak <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Kullanım [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] ekleme seçeneği <xref:System.Web.Services.WebService> ve <xref:System.Web.Services.WebMethodAttribute> öznitelikleri bir arabirime yerine bir sınıf ve aşağıdaki örnek kodda gösterildiği gibi arabirimini uygulayan bir sınıf yazma.  
  
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
  
 Bu seçeneği kullanarak, tercih edilen, çünkü arabirimiyle <xref:System.Web.Services.WebService> özniteliği oluşturduğunu aynı sözleşme farklı şekillerde uygulayabilir çeşitli sınıflarıyla yeniden hizmeti tarafından gerçekleştirilen işlemler için bir sözleşmede.  
  
 Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik tabanlı SOAP iletisi body öğesi tam olarak nitelenmiş adına yerine `SOAPAction` HTTP üstbilgisi. WCF kullanan `SOAPAction` iletileri yönlendirmek için HTTP üstbilgisi.  
  
 Hangi içine XML <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir. İle kullanmak için bir veri türü tanımlarken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web Hizmetleri WCF benimsenmesi, kapatıldığını, aşağıdakileri yapın:  
  
-   XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.  
  
-   Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıfına türünün ad alanını açıkça tanımlamak için ikinci kullanarak. Ek özniteliklerden eklemeyin <xref:System.Xml.Serialization> .NET Framework sınıf nasıl XML çevrilmesi denetlemek için ad alanı.  
  
-   Bu yaklaşım kabul ederek, daha sonra .NET eklenmesi veri Sözleşmelerle içine sınıflarının gerekir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde değiştirmeden. İleti tarafından kullanılan türleri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri, diğer avantajlar arasında WCF uygulamaları daha iyi performans sağlayan, WCF uygulamaları tarafından veri sözleşmeleri işlenebilir.  
  
 Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının. WCF istemcileri onları desteklemez. Bir hizmeti güvenli hale getirilmelidir, çünkü bu seçenekler sağlam ve standart protokollerine dayalıdır WCF tarafından sağlanan seçenekleri kullanın.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HTTP yükleyerek neden performans etkisi  
 .NET Framework 3.0, WCF `HttpModule` kök Web.config dosyasında her ASP.NET uygulama etkin bir WCF olduğu şekilde yüklendi. Kaldırabilmeniz için bu performansını etkileyebilir `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WCF Hizmetini ASP.NET Web Hizmeti İstemcileriyle Birlikte Çalışmak için Yapılandırma](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
