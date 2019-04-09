---
title: Eş Kanal Senaryoları
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: 610668e5f3625c638fc1e814e0116df87970773b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147062"
---
# <a name="peer-channel-scenarios"></a>Eş Kanal Senaryoları
Eş kanal API'leri aşağıdaki geliştirme senaryolarını destekler.  
  
## <a name="publicationsubscription-messaging"></a>Yayımlama/abonelik Mesajlaşma  
 Yayımlama/abonelik uygulamalar (örneğin, yürütebilmektedir ve haber başlıklarını yayımcıları Spor puanları ve hava durumu raporları) derleme şirketler eş kanalı sunucusuz uygulamalar için kullanabilirsiniz. Örneğin, kullanıcılar bir ortak ağ (veya grup istemciler) katılarak en son Spor puanlarını almak ve güncel oyun verilerini, büyük bir miktarını, sunucu iş yükü artırmadan yayar. Bu, sunucu tabanlı teknolojiler yatırım artırmadan önemli ölçüde daha yüksek kalitede hizmet vermek için veri sağlayıcısı yardımcı olur.  
  
## <a name="collaboration"></a>İş Birliği  
 Bağımsız yazılım satıcılarına (ISV), kişilere eşler arası etkinlikleri katılım için sıkı grupları oluşturma uygulamalar oluşturabilirsiniz. Örneğin, bu resmi paylaşım arkadaşlar, diğer planlama etkinlikleri ve daha fazla arasında işbirliğine dayalı projeler üzerinde çalışan ekipler içerebilir. Geleneksel olarak, bu etkinlikler, sunucular her zaman içerir; Ancak, eş kanaldan maliyet açısından daha verimli bir şekilde kolayca geleneksel sunucusu istemci modeli altında uygulanmaz ve çevrimdışı erişimi senaryoları etkinleştirerek bunu bir yol sağlar.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Dağıtılan işleme ve hesaplama kümeleri  
 Genellikle işlem kümeleri ve dağıtılan işleme finansal/modelleme ve İnsan DNA kod çözme hava durumu gibi büyük ölçekli hesaplamalar için kullanılır. Genellikle, bu sunucuları hesaplama Kümeye katılan tüm istemcileri tek tek Görevler atayın sağlanarak gerçekleştirilir. Bu sunucular, ek taleplerin da olabilir; Örneğin, tüm görevler, belirli bir süre içinde her görev için birden fazla makine gerektiren tamamlanmış olması gerekebilir. Ayrıca, bir görevi çalıştırma herhangi bir istemci kalırsa, başka bir istemci, görev alabilir ve üzerinde çalışmayı gerçekleştirmek mümkün olması gerekir. Benzer şekilde, birden fazla istemci, tutarlı sonuçlar alınması aynı görevi çalıştırmanız gerekebilir. Bu tür bir istemci koordinasyon sunucuları çalıştırabilirsiniz, ancak burada bir görev bağımsız olarak alma istemciler görev geçici sunucu gereksinimleri belirlemek ve işlem kafes bu görevin nasıl tamamlanacağını belirlemek için bir eşler arası çözüm oluşturabilirsiniz.  
  
## <a name="gaming"></a>Oyun  
 Eş kanalı kullanarak, uygulama geliştiricilerin sunucusuz oyun taşır burada ve için gönderilen bir eşler arası mekanizması yerine bir merkezi sunucu üzerinden diğer ouyncularla eşitlenmiş oyunlarını sürümleri oluşturabilirsiniz. Küçük ISV'ler için bu dağıtımı, Bakımı ve merkezi sunucuların bakımı ile ilgili işletim maliyetlerini kaldırmaya yardımcı olur. Eşler arası mimari kullanılarak yazılmış oyunlar, Internet üzerinden veya kablolu veya kablosuz yerel ağ çalınabilir. Giriş ve oyun içi sohbet gibi ikincil oyun etkinlikleri bir eşler arası ağ ile geliştirilmiş olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Kavramları](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
