---
title: Orta Katman İstemci Uygulamaları
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: c50223a55765f211dae710f96bffa7716ce36b32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598820"
---
# <a name="middle-tier-client-applications"></a>Orta Katman İstemci Uygulamaları
Bu konuda Windows Communication Foundation (WCF) kullanan orta katman istemci uygulamalarına özgü çeşitli sorunlar ele alınmaktadır.  
  
## <a name="increasing-middle-tier-client-performance"></a>Orta katman Istemci performansını artırma  
 ASP.NET kullanan Web Hizmetleri gibi önceki iletişim teknolojilerine kıyasla, WCF istemci örneğinin oluşturulması, zengin özellik WCF kümesi nedeniyle daha karmaşık olabilir. Örneğin, bir <xref:System.ServiceModel.ChannelFactory%601> nesne açıldığında, hizmet ile güvenli bir oturum oluşturabilir ve istemci örneği için başlama süresini artıran bir yordamdır. Genellikle, bu ek özellik özellikleri, WCF istemcisi çeşitli çağrılar yaptığından, istemci uygulamalarını önemli ölçüde etkilemez ve sonra kapatır.  
  
 Ancak, orta katman istemci uygulamaları hızlı bir şekilde birçok WCF istemci nesnesi oluşturabilir ve sonuç olarak, daha fazla başlatma gereksinimini ortadan kaldırabilirsiniz. Hizmetleri çağırırken orta katman uygulamaların performansını arttırmaya yönelik iki ana yaklaşım vardır:  
  
- WCF istemci nesnesini önbelleğe alarak mümkün olduğunda sonraki çağrılar için yeniden kullanın.  
  
- Bir <xref:System.ServiceModel.ChannelFactory%601> nesne oluşturun ve ardından bu nesneyi kullanarak her çağrı için yenı WCF istemci kanalı nesneleri oluşturun.  
  
 Bu yaklaşımların kullanılması sırasında göz önünde bulundurulması gereken sorunlar şunlardır:  
  
- Hizmet, bir oturum kullanarak istemciye özgü bir durumu yaşalıyorsa, hizmetin durumu orta katman istemciye bağlı olduğundan, orta katman WCF istemcisini birden çok istemci katmanı isteği ile yeniden kullanamazsınız.  
  
- Hizmetin, istemci başına kimlik doğrulaması gerçekleştirmesi gerekiyorsa, orta katman WCF istemcisini (veya WCF istemci kanalı nesnesini) yeniden kullanmak yerine orta katmandaki her gelen istek için yeni bir istemci oluşturmanız gerekir, çünkü ortadaki katmanın istemci kimlik bilgileri, WCF istemcisi (veya) oluşturulduktan sonra değiştirilemez <xref:System.ServiceModel.ChannelFactory%601> .  
  
- Kanallar tarafından oluşturulan kanallar ve istemciler iş parçacığı açısından güvende olsa da, aynı anda hatta birden fazla ileti yazmayı desteklemeyebilir. Büyük iletiler gönderiyorsanız, özellikle akış ise, gönderme işlemi başka bir göndermenin tamamlanmasını beklemeyi engelleyebilir. Bu, iki tür soruna neden olur: denetim akışı kanalı yeniden kullanan hizmete geri dönerse, eşzamanlılık olmaması ve kilitlenme olasılığını (yani, paylaşılan istemci, kod yolu paylaşılan istemciye geri çağrıya neden olan bir hizmet çağırır) sağlar. Bu, yeniden kullandığınız WCF istemcisi türünden bağımsız olarak geçerlidir.  
  
- Kanalı paylaşıp paylaşmadığına bakılmaksızın hatalı kanalları işlemeniz gerekir. Ancak, kanallar yeniden kullanıldığında, hatalı bir kanal birden fazla bekleyen istek veya gönderme işlemi gerçekleştirebilir.  
  
 Bir istemciyi birden çok istek için yeniden kullanmak üzere en iyi yöntemleri gösteren bir örnek için bkz. [ASP.net Istemcisinde veri bağlama](../samples/data-binding-in-an-aspnet-client.md).  
  
 Ek olarak, <xref:System.Xml.Serialization.XmlSerializer> çalışma zamanında bu veri türleri için Oluştur ve derle serileştirme kodu kullanarak seri hale getirilebilir veri türlerini kullanan istemciler için başlangıç performansını artırabilirsiniz ve bu da yavaş başlangıç performansına yol açabilir. [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , uygulama için derlenmiş derlemelerden gerekli serileştirme kodunu oluşturarak bu uygulamalar için başlangıç performansını iyileştirebilir. Daha fazla bilgi için bkz. [nasıl yapılır: XmlSerializer kullanarak WCF Istemci uygulamalarının başlangıç zamanını geliştirme](startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF İstemcisi Kullanarak Hizmetlere Erişme](accessing-services-using-a-client.md)
