---
title: Orta Katman İstemci Uygulamaları
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 667cc98f46b131fe91e17f3b1b16af429dc597ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174089"
---
# <a name="middle-tier-client-applications"></a>Orta Katman İstemci Uygulamaları
Bu konu, Windows Communication Foundation (WCF) kullanan Orta katman istemci uygulamaları için belirli çeşitli sorunlar ele alınmıştır.  
  
## <a name="increasing-middle-tier-client-performance"></a>Orta katman istemci performansını artırma  
 Kullanarak Web Hizmetleri gibi önceki iletişimi teknolojilerine kıyasla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], bir WCF istemcisi örneği oluşturulmasını WCF zengin özellik kümesi nedeniyle daha karmaşık olabilir. Örneğin, bir <xref:System.ServiceModel.ChannelFactory%601> nesnesinin açıldığı güvenli bir oturum hizmetiyle istemci örneği için başlangıç süresini artıran bir yordam oluşturabilirsiniz. WCF istemcisini çeşitli çağrılar yapar ve ardından kapatır genellikle, bu ek özellik yetenekleri istemci uygulamaları önemli ölçüde etkilemez.  
  
 Orta katman istemci uygulamaları, ancak birçok WCF istemci nesne hızlı bir şekilde oluşturabilir ve, sonuç olarak, artan başlatma gereksinimleri karşılaşırsınız. Hizmetleri çağırırken orta katman uygulamalarının performansını artırmak için iki ana yaklaşım vardır:  
  
-   WCF istemci nesnesini önbelleğe ve mümkün olduğunda sonraki çağrılar için indirilebilir.  
  
-   Oluşturma bir <xref:System.ServiceModel.ChannelFactory%601> nesne ve o nesnenin kanal nesneler her çağrı için yeni bir WCF istemcisi oluşturmak için kullanın.  
  
 Bu yaklaşımların kullanırken dikkat etmeniz gereken sorunlar şunlardır:  
  
-   Hizmet istemci özel durumu bir oturumu kullanarak koruma, hizmet durumu, orta katman istemci bağlı olmadığından birden çok istemci katmanı isteklerle orta katman WCF istemcisini yeniden kullanamazsınız.  
  
-   Hizmet istemci başına temelinde kimlik doğrulaması gerçekleştirmesi gerekiyorsa, çünkü orta katman WCF istemcisi (veya WCF istemci kanal nesnesi) yeniden kullanmak yerine orta katman her gelen istek için yeni bir istemci oluşturmalısınız orta katman istemci kimlik bilgileri WCF istemcisi sonra değiştirilemez (veya <xref:System.ServiceModel.ChannelFactory%601>) oluşturuldu.  
  
-   Kanallar ve istemcilerin kanalları tarafından oluşturulan iş parçacığı açısından güvenli olsa da, bunlar için kablo, eşzamanlı olarak birden fazla ileti yazma desteklemiyor olabilir. Büyük iletileri gönderiyorsanız, özellikle akış, gönderme işlemi tamamlamak başka bir göndermek için bekleme engelleyebilir. Bu iki tür sorunlara neden olur: bir eşzamanlılık ve denetim akışını kanal yeniden hizmete döndürürse kilitlenme olasılığını eksikliği (diğer bir deyişle, paylaşılan istemci bir hizmet olan kod yolu sonuçları paylaşılan istemciye bir geri çağırma içinde çağırır). Bu yeniden WCF istemci türü ne olursa olsun doğrudur.  
  
-   Kanal paylaştığınız bağımsız olarak hatalı kanal işlemesi gerekir. Kanalları yeniden kullanılır, ancak hatalı kanal birden fazla bekleyen istek aşağı olması ya da gönderebilir.  
  
 Bir istemci birden çok istek için yeniden kullanmak için en iyi yöntemleri gösteren bir örnek için bkz: [bir ASP.NET istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Ayrıca, seri hale getirilebilir kullanarak veri türleri kullanan bu istemciler için başlatma performansını artırabilir <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve yavaş başlatma performansı düşürebilir çalışma zamanında bu veri türleri için serileştirme kodu derleyin. [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) derlenmiş bütünleştirilmiş uygulama için gerekli serileştirme kod oluşturarak bu uygulamaları için başlatma performansını geliştirebilir. Daha fazla bilgi için [nasıl yapılır: Başlangıç zamanı, istemci XmlSerializer kullanarak WCF uygulamalarının geliştirilmesine](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF İstemcisi Kullanarak Hizmetlere Erişme](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
