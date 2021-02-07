---
description: 'Daha fazla bilgi edinin: eş kanal senaryoları'
title: Eş Kanal Senaryoları
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: ae21cdb5452864ce3852f2c10892fd082a79fa29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733482"
---
# <a name="peer-channel-scenarios"></a>Eş Kanal Senaryoları

Eş kanal API 'Leri aşağıdaki geliştirme senaryolarını destekler.  
  
## <a name="publicationsubscription-messaging"></a>Yayın/abonelik mesajlaşma  

 Yayın/abonelik uygulamaları oluşturan şirketler (örneğin, hisse senetleri ve haber başlıkları, spor puanları ve hava durumu raporlarının yayımcıları), eş kanalını sunucu-daha az uygulamalar için kullanabilir. Örneğin, kullanıcılar ortak bir ağı (veya istemci grubunu) birleştirerek en son spor puanlarını edinebilir ve sunucu yükünü arttırmadan büyük miktarda güncel oyun verisi yayabilir. Bu, veri sağlayıcısının sunucu tabanlı teknolojilerde yatırımları önemli ölçüde arttırmadan daha yüksek hizmet kalitesi vermesini sağlar.  
  
## <a name="collaboration"></a>İşbirliği  

 Bağımsız yazılım satıcıları (ISV 'Ler), insanların eşler arası etkinliklere katılım için sıkı gruplar oluşturmalarına olanak sağlayan uygulamalar oluşturabilir. Örneğin, bu, işbirliğine dayalı projelerde çalışan takımları, arkadaşlar arasında resim paylaşımı, parti planlama etkinlikleri ve daha fazlasını içerebilir. Geleneksel olarak, bu etkinlikler her zaman sunucular içerir; Bununla birlikte, eş kanal, geleneksel bir sunucu istemci modeli altında kolayca uygulanmayan çevrimdışı erişim senaryolarını etkinleştirerek bunu daha uygun maliyetli bir şekilde yapmanın bir yolunu sunar.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Dağıtılmış Işlem ve Işlem kümeleri  

 İşlem kümeleri ve dağıtılmış işleme genellikle finansal/Hava durumu modelleme ve insan DNA kodu çözme gibi büyük ölçekli hesaplamalar için kullanılır. Genellikle bu işlem, sunucuların hesaplama kümesine katılan tüm istemcilere ayrı ayrı görev atamasını sağlar. Bu sunucularda ek talepler de olabilir; Örneğin, tüm görevlerin belirli bir süre içinde tamamlanması gerekebilir ve her görev için birden fazla makine gerekir. Ayrıca, bir görevi çalıştıran herhangi bir istemci kapalıysa, başka bir istemci bu görevi ele alabilmeli ve üzerinde iş gerçekleştirebilir. Benzer şekilde, birden fazla istemcinin tutarlı sonuçlar sağlamak için aynı görevi çalıştırması gerekebilir. Sunucular bu tür istemci koordinasyonunu çalıştırabilse de, bir görevi alan istemcilerin, görevin bir yanındaki sunucu gereksinimlerini ve bu görevi nasıl tamamlayacağınızı anlamak için bir işlem ağı kullanmasını sağlayan bir eşler arası çözüm oluşturabilirsiniz.  
  
## <a name="gaming"></a>Oyun  

 Eş kanal kullanarak, uygulama geliştiricileri, oyunlarının bir merkezi sunucu yerine eşler arası bir mekanizmaya iletilmesi ve diğer oyunculara aktarılmasıyla eşitlenmesi durumunda sunucu tarafından daha az sürümlerini oluşturabilir. Küçük ISV 'Ler için bu, merkezi sunucuları dağıtma, sürdürme ve hizmet verme ile ilişkili işletimsel maliyetlerin kaldırılmasına yardımcı olur. Eşler arası mimari kullanılarak yazılan Oyunlar Internet 'te veya kablolu veya kablosuz yerel ağlarda çalınabilir. Giriş ve oyun içi sohbet gibi ikincil oyun etkinlikleri, eşler arası bir ağ kullanılarak geliştirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Kavramları](peer-channel-concepts.md)
