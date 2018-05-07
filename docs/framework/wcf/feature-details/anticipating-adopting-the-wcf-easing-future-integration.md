---
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma
ASP.NET bugün kullanıyorsanız ve WCF gelecekte kullanarak düşündüğünüz, bu konuda yeni ASP.NET Web hizmetleri de WCF uygulamaları ile birlikte çalıştığından emin olmak için yönergeler sağlar.  
  
## <a name="general-recommendations"></a>Genel öneriler  
 ASP.NET 2.0 için yeni hizmetlerin benimser. Bunun yapılması geliştirmeleri ve yeni sürümün geliştirmeleri erişim sağlar. Ancak, bu da aynı uygulamada ASP.NET 2.0 bileşenlerini WCF bileşenleri ile birlikte kullanma olasılığını için izin verir.  
  
## <a name="protocols"></a>protokolleri  
 ASP.NET 2. 0'ın yeni tesis ws uygunluk doğrulamak için kullanın-ı temel Profil 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WS uygun ASP.NET Web Hizmetleri-ı temel Profil 1.1 bağlama, önceden tanımlanmış WCF kullanarak WCF istemcileriyle birlikte çalışabilir olacağını <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Hizmet geliştirme  
 Kullanmaktan kaçının <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> yöntemlere yönlendirilmiş iletiler için öznitelik SOAPAction HTTP üstbilgisi yerine SOAP iletisi body öğesi tam olarak nitelenmiş adını temel alarak. WCF SOAPAction HTTP üstbilgisi iletileri yönlendirmek için kullanır.  
  
## <a name="data-representation"></a>Veri temsili  
 Hangi içine XML <xref:System.Xml.Serialization.XmlSerializer> serileştiren bir türü varsayılan olarak anlam olarak hangi içine XML aynıdır <xref:System.Runtime.Serialization.DataContractSerializer> ad alanı XML açıkça tanımlanmış için sağlanan bir tür serileştirir. ASP.NET Web Hizmetleri ile kullanmak için bir veri türü kapatıldığını nu benimsemenin WCF gelecekte tanımlarken aşağıdakileri yapın:  
  
1.  XML şeması yerine .NET Framework sınıfları kullanarak türünü tanımlayın.  
  
2.  Yalnızca ekleme <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.XmlRootAttribute> sınıfına türünün ad alanını açıkça tanımlamak için ikinci kullanarak. Yapmak hiçbir ek özniteliklerinden Ekle <xref:System.Xml.Serialization> .NET Framework sınıf nasıl XML çevrilmesi denetlemek için ad alanı.  
  
 Bu yaklaşım kabul ederek, daha sonra .NET eklenmesi veri Sözleşmelerle içine sınıflarının gerekir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> içine sınıfları aktarım için serileştirilir XML önemli ölçüde değiştirmeden. ASP.NET Web Hizmetleri tarafından mesajlarında türleri arasında başka avantajları WCF uygulamaları daha iyi performans sağlayan veri sözleşmeleri WCF uygulamaları tarafından işlenmesi mümkün olacaktır.  
  
## <a name="security"></a>Güvenlik  
 Internet Information Services (IIS) tarafından sağlanan kimlik doğrulama seçenekleri kullanmaktan kaçının. WCF istemcileri onları desteklemez. Bir hizmeti güvenli hale gerekiyorsa, çünkü bu seçenekler daha zengin ve standart protokollerine dayalıdır WCF tarafından sağlanan seçenekleri kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Taşınmayı Kolaylaştırma](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
