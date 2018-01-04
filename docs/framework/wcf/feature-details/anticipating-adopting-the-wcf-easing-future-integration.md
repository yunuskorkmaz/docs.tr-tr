---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dbb50af9d5655a76abb3827cd2f512eab0fd662
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma
ASP.NET bugün kullanıyorsanız ve kullanarak düşündüğünüz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelecekte bu konuda yeni ASP.NET Web hizmetleri de ile birlikte çalışacağından emin olmak için yönergeler sağlanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
## <a name="general-recommendations"></a>Genel öneriler  
 ASP.NET 2.0 için yeni hizmetlerin benimser. Bunun yapılması geliştirmeleri ve yeni sürümün geliştirmeleri erişim sağlar. Ancak, bu da ASP.NET 2.0 bileşenleri ile birlikte kullanma olasılığını için sağlayacak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı uygulama bileşenleri.  
  
## <a name="protocols"></a>protokolleri  
 ASP.NET 2. 0'ın yeni tesis ws uygunluk doğrulamak için kullanın-ı temel Profil 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WS uygun ASP.NET Web Hizmetleri-ı temel Profil 1.1 birlikte çalışabilir olacaktır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanarak istemcileri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama, önceden tanımlanmış <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik SOAPAction HTTP üstbilgisi yerine SOAP iletisi body öğesi tam olarak nitelenmiş adını temel alarak. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]SOAPAction HTTP üstbilgisi iletileri yönlendirmek için kullanır.  
  
## <a name="data-representation"></a>Veri temsili  
 Hangi içine XML <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir. Ne zaman kullanmak için bir veri türü ile ASP.NET Web tanımlama izin ver Hizmetleri benimsenmesi bir kapatıldığını içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelecekte, aşağıdakileri yapın:  
  
1.  XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.  
  
2.  Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıfına türünün ad alanını açıkça tanımlamak için ikinci kullanarak. Yapmak hiçbir ek özniteliklerinden Ekle <xref:System.Xml.Serialization> .NET Framework sınıf nasıl XML çevrilmesi denetlemek için ad alanı.  
  
 Bu yaklaşım kabul ederek, daha sonra .NET eklenmesi veri Sözleşmelerle içine sınıflarının gerekir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde değiştirmeden. ASP.NET Web Hizmetleri tarafından mesajlarında türleri tarafından veri sözleşmeleri olarak işlenmesi kuramaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , başka avantajları arasında oluşturan uygulamalar, daha iyi performans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
## <a name="security"></a>Güvenlik  
 Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]istemcileri onları desteklemez. Bir hizmeti güvenli hale gerekiyorsa tarafından sağlanan seçenekleri kullanın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], çünkü bu seçenekler daha zengin ve standart protokollerine dayalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
