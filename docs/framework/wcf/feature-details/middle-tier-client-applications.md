---
title: "Orta Katman İstemci Uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 893fa027d2f1eb4fa3782b9119f6ae2d4a78d700
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="middle-tier-client-applications"></a>Orta Katman İstemci Uygulamaları
Bu konuda kullanan Orta katman istemci uygulamaları için özgü çeşitli sorunları ele alınmıştır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="increasing-middle-tier-client-performance"></a>Orta katman istemci performansı artırma  
 Kullanan Web Hizmetleri gibi önceki iletişimi teknolojileri ile karşılaştırıldığında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], oluşturulmasını bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci örneği nedeniyle zengin özellik kümesi daha karmaşık olabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Örneğin, bir <xref:System.ServiceModel.ChannelFactory%601> nesne açıldığında hizmeti, istemci örneği için başlangıç zamanı artırır bir yordam ile güvenli bir oturum kurabilirsiniz. Genellikle, bu ek özellikler istemci uygulamaları önemli ölçüde beri etkilemez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci birkaç çağrı yapar ve sonra kapatır.  
  
 Orta katman istemci uygulamaları, ancak oluşturabilirsiniz birçok [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci nesneleri hızla ve sonuç olarak, artan başlatma gereksinimleri karşılaşırsınız. Hizmetleri çağrılırken orta katman uygulamalarının performansını artırmak için iki ana yaklaşım vardır:  
  
-   Önbellek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci nesnesi ve sonraki çağrılar için mümkün olduğunca yeniden.  
  
-   Oluşturma bir <xref:System.ServiceModel.ChannelFactory%601> nesne ve yeni oluşturmak için bu nesneyi kullanabilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci kanal nesnelerinin her çağrı için.  
  
 Bu yaklaşım kullanırken dikkate alınması gereken konular şunlardır:  
  
-   Hizmeti istemci özel durumu bir oturumu kullanarak Bakımı sonra orta katmanda tekrar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] birden çok istemci katmanı ile istemci hizmetinin durumunu, orta katman istemci bağlıdır çünkü ister.  
  
-   Hizmet kimlik doğrulaması istemci başına temelinde gerçekleştirmeniz gerekirse, Orta katmanda yeniden kullanmak yerine orta katman her gelen istek için yeni bir istemci oluşturmalısınız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci (veya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci kanal nesnesi) için istemci Orta katman kimlik bilgilerini, sonra değiştirilemez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci (veya <xref:System.ServiceModel.ChannelFactory%601>) oluşturuldu.  
  
-   Kanallar ve istemcilerin kanalları tarafından oluşturulan iş parçacığı olsa da, bunlar aynı anda birden fazla ileti kablo için yazma desteklemeyebilir. Büyük iletiler gönderiyorsanız, özellikle akış, gönderme işlemi tamamlamak başka bir gönderme bekleniyor engelleyebilir. Bu iki tür sorunlara neden olur: eşzamanlılık ve denetim akışını kanal yeniden hizmet döndürürse kilitlenme olasılığını eksikliği (diğer bir deyişle, paylaşılan istemci bir hizmet kod yolu sonuçlarını paylaşılan istemciye bir geri çağırma olarak çağırır). Bu tür bağımsız olarak doğrudur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeniden istemci.  
  
-   Kanal paylaştığınız bağımsız olarak hatalı kanalları işlemelidir. Kanalları yeniden kullanılır, ancak, hataya neden olan bir kanal birden fazla bekleyen istek aşağı alın veya gönderin.  
  
 Bir istemci birden çok istek için yeniden kullanmak için en iyi yöntemleri gösteren bir örnek için bkz: [bir ASP.NET istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Ayrıca, seri hale getirilebilir kullanarak veri türlerini kullanan bu istemciler için başlangıç performansını artırabilirsiniz <xref:System.Xml.Serialization.XmlSerializer> oluşturmak ve bu yavaş başlatma performansının düşmesine neden olabilir çalışma zamanında veri türleri için seri hale getirme kodu derleyin. [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) başlangıcından bu uygulamalar için uygulama için derlenmiş derlemelerden gerekli serileştirme kod oluşturarak performansı artırabilir. Daha fazla bilgi için bkz: [nasıl yapılır: Başlangıç saati, WCF istemci XmlSerializer kullanarak uygulamaları geliştirmek](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir WCF istemcisi kullanarak hizmetlere erişme](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
