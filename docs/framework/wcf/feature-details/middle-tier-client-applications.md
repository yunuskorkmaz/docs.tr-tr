---
title: Orta Katman İstemci Uygulamaları
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 4cca832266b2eb2ab7b1b4eb1a5fe937525db97d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493507"
---
# <a name="middle-tier-client-applications"></a>Orta Katman İstemci Uygulamaları
Bu konu, Windows Communication Foundation (WCF) kullanan Orta katman istemci uygulamaları için özgü çeşitli sorunları açıklar.  
  
## <a name="increasing-middle-tier-client-performance"></a>Orta katman istemci performansı artırma  
 Kullanan Web Hizmetleri gibi önceki iletişimi teknolojileri ile karşılaştırıldığında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], WCF istemci örneğinin oluşturulmasını WCF zengin özellik kümesi nedeniyle daha karmaşık olabilir. Örneğin, bir <xref:System.ServiceModel.ChannelFactory%601> nesne açıldığında hizmeti, istemci örneği için başlangıç zamanı artırır bir yordam ile güvenli bir oturum kurabilirsiniz. WCF istemcisini birkaç çağrı yapar ve sonra kapatır genellikle, bu ek özellikler istemci uygulamaları önemli ölçüde etkilemez.  
  
 Orta katman istemci uygulamaları, ancak birçok WCF istemci nesneleri hızlı bir şekilde oluşturabilir ve, sonuç olarak, artan başlatma gereksinimleri deneyimi. Hizmetleri çağrılırken orta katman uygulamalarının performansını artırmak için iki ana yaklaşım vardır:  
  
-   WCF istemci nesnesini önbelleğe ve sonraki çağrılar için mümkün olduğunca yeniden.  
  
-   Oluşturma bir <xref:System.ServiceModel.ChannelFactory%601> nesne ve yeni WCF istemcisi her çağrı için kanal nesneleri oluşturmak için söz konusu nesne kullanın.  
  
 Bu yaklaşım kullanırken dikkate alınması gereken konular şunlardır:  
  
-   Hizmeti istemci özel durumu bir oturumu kullanarak bakımı, hizmetin durumunu, orta katman istemci bağlıdır çünkü birden çok istemci katmanı isteklerle orta katman WCF istemcisini yeniden kullanamazsınız.  
  
-   Hizmet bir istemci başına temelinde kimlik doğrulaması gerçekleştirmeniz gerekirse, orta katman WCF istemci (veya WCF istemci kanal nesnesi) çünkü yeniden kullanmak yerine orta katman her gelen istek için yeni bir istemci oluşturmalısınız orta katman istemci kimlik bilgileri WCF istemcisi sonra değiştirilemez (veya <xref:System.ServiceModel.ChannelFactory%601>) oluşturuldu.  
  
-   Kanallar ve istemcilerin kanalları tarafından oluşturulan iş parçacığı olsa da, bunlar aynı anda birden fazla ileti kablo için yazma desteklemeyebilir. Büyük iletiler gönderiyorsanız, özellikle akış, gönderme işlemi tamamlamak başka bir gönderme bekleniyor engelleyebilir. Bu iki tür sorunlara neden olur: eşzamanlılık ve denetim akışını kanal yeniden hizmet döndürürse kilitlenme olasılığını eksikliği (diğer bir deyişle, paylaşılan istemci bir hizmet kod yolu sonuçlarını paylaşılan istemciye bir geri çağırma olarak çağırır). Bu yeniden WCF istemci türüne bakılmaksızın geçerlidir.  
  
-   Kanal paylaştığınız bağımsız olarak hatalı kanalları işlemelidir. Kanalları yeniden kullanılır, ancak, hataya neden olan bir kanal birden fazla bekleyen istek aşağı alın veya gönderin.  
  
 Bir istemci birden çok istek için yeniden kullanmak için en iyi yöntemleri gösteren bir örnek için bkz: [bir ASP.NET istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Ayrıca, seri hale getirilebilir kullanarak veri türlerini kullanan bu istemciler için başlangıç performansını artırabilirsiniz <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında veri türleri için seri hale getirme kodu derleyin. [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) başlangıcından bu uygulamalar için uygulama için derlenmiş derlemelerden gerekli serileştirme kod oluşturarak performansı artırabilir. Daha fazla bilgi için bkz: [nasıl yapılır: Başlangıç saati, WCF istemci XmlSerializer kullanarak uygulamaları geliştirmek](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF İstemcisi Kullanarak Hizmetlere Erişme](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
