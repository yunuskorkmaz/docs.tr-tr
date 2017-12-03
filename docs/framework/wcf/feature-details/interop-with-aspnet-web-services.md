---
title: "ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd30b2d62d3ecf21027c0225490da6f31113cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="interoperability-with-aspnet-web-services"></a>ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik
Birlikte çalışabilirlik [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri ve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web Hizmetleri elde edilebilir iki teknolojiyi kullanılarak uygulanan Hizmetleri WS uygun sağlayarak-ı temel Profil 1.1 belirtimini. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web WS uygun Hizmetleri-ı temel Profil 1.1 birlikte çalışabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak istemcileri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistem tarafından sağlanan bir bağlamayı, <xref:System.ServiceModel.BasicHttpBinding>.  
  
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
  
 Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik tabanlı SOAP iletisi body öğesi tam olarak nitelenmiş adına yerine `SOAPAction` HTTP üstbilgisi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kullanan `SOAPAction` iletileri yönlendirmek için HTTP üstbilgisi.  
  
 Hangi içine XML <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir. İle kullanmak için bir veri türü tanımlarken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web Hizmetleri benimsenmesi, kapatıldığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], aşağıdakileri yapın:  
  
-   XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.  
  
-   Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıfına türünün ad alanını açıkça tanımlamak için ikinci kullanarak. Ek özniteliklerden eklemeyin <xref:System.Xml.Serialization> .NET Framework sınıf nasıl XML çevrilmesi denetlemek için ad alanı.  
  
-   Bu yaklaşım kabul ederek, daha sonra .NET eklenmesi veri Sözleşmelerle içine sınıflarının gerekir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde değiştirmeden. İleti tarafından kullanılan türleri [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri, veri sözleşmeleri tarafından olarak işlenebilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , başka avantajları arasında oluşturan uygulamalar, daha iyi performans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
 Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]istemcileri onları desteklemez. Bir hizmeti güvenli hale getirilmelidir, tarafından sağlanan seçenekleri kullanın. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], çünkü bu seçenekler sağlam ve standart protokollerine dayalıdır.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>ServiceModel HTTP yükleyerek neden performans etkisi  
 .NET Framework 3.0, WCF `HttpModule` kök Web.config dosyasında her ASP.NET uygulama etkin bir WCF olduğu şekilde yüklendi. Kaldırabilmeniz için bu performansını etkileyebilir `ServiceModel` aşağıdaki örnekte gösterildiği gibi Web.config dosyası için.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WCF hizmetini ASP.NET Web hizmeti istemcileriyle birlikte çalışmak üzere yapılandırma](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
