---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation benimsemeyi bekleme benimseme: gelecekteki tümleştirme kolaylaştırıcı'
title: "Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma"
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 512e35e8a4cd6057c96e96a1474f393c3f006525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643884"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Tümleştirmeyi Kolaylaştırma

ASP.NET bugün kullanıyorsanız ve gelecekte WCF kullanmayı düşünüyorsanız, bu konuda yeni ASP.NET Web hizmetlerinin WCF uygulamalarıyla birlikte iyi şekilde çalışmasını sağlamak için rehberlik sağlanmıştır.  
  
## <a name="general-recommendations"></a>Genel öneriler  

 Tüm yeni hizmetler için ASP.NET 2,0 benimseyin. Bu işlem, yeni sürümün geliştirmeleri ve geliştirmeleri için erişim sağlar. Ancak, ASP.NET 2,0 bileşenlerini aynı uygulamadaki WCF bileşenleriyle birlikte kullanma olasılığa de izin verir.  
  
## <a name="protocols"></a>Protokoller  

 ASP.NET 2.0 'ın, WS-ı temel profil 1,1 ile uyumluluğunu doğrulamak için yeni tesis kullanın:  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 WS-ı temel profil 1,1 ile uyumlu olan ASP.NET Web Hizmetleri, WCF istemcileri ile önceden tanımlanmış WCF kullanılarak birlikte çalışabilir <xref:System.ServiceModel.BasicHttpBinding> .  
  
## <a name="service-development"></a>Hizmet geliştirme  

 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute>SOAPACTION http üstbilgisi yerıne soap iletisinin gövde öğesinin tam adına bağlı olarak yöntemlere yönlendirilmek için özniteliğini kullanmaktan kaçının. WCF iletileri yönlendirmek için SOAPAction HTTP üstbilgisini kullanır.  
  
## <a name="data-representation"></a>Veri gösterimi  

 <xref:System.Xml.Serialization.XmlSerializer>Bir türü varsayılan olarak seri hale getirilen XML, bir türü seri hale getirilen XML ile aynıdır, bu, <xref:System.Runtime.Serialization.DataContractSerializer> XML için ad alanı açıkça tanımlanmış olarak belirtilmelidir. Daha sonra WCF 'yi benimseme olasılığına 'de ASP.NET Web Hizmetleri ile kullanmak için bir veri türü tanımlarken, şunları yapın:  
  
1. Türü, XML şeması yerine .NET Framework sınıfları kullanarak tanımlayın.  
  
2. <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.XmlRootAttribute> Türü için ad alanını açıkça tanımlamak için, ikincisini kullanarak yalnızca ve öğesini sınıfına ekleyin. <xref:System.Xml.Serialization>.NET Framework SıNıFıNıN XML 'e nasıl çevrileceğini denetlemek için ad alanından ek öznitelikler eklemeyin.  
  
 Bu yaklaşımı benimseerek, daha sonra, <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıflarının iletilmek üzere SERILEŞTIRILDIĞI XML 'yi önemli ölçüde değiştirmeksizin, .NET sınıflarını daha sonra ve ' nin eklenmesiyle veri sözleşmeleri halinde yapabilmelisiniz. ASP.NET Web hizmetlerine göre iletilerde kullanılan türler, WCF uygulamalarında veri sözleşmeleri, diğer avantajlar arasında, WCF uygulamalarında daha iyi performans olarak işlenebilecektir.  
  
## <a name="security"></a>Güvenlik  

 Internet Information Services (IIS) tarafından sunulan kimlik doğrulama seçeneklerini kullanmaktan kaçının. WCF istemcileri bunları desteklemez. Bir hizmetin güvenliğinin sağlanması gerekiyorsa, bu seçenekler daha zengin ve standart protokollerin temel aldığı için WCF tarafından sağlanan seçenekleri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation'ı Benimsemeyi Bekleme: Gelecekteki Geçişi Kolaylaştırma](anticipating-adopting-wcf-migration.md)
