---
title: Sunucusuz işlevlerden yararlanma
description: Bulutta yerel uygulamalarda sunucusuz ve Azure Işlevlerini kullanma
ms.date: 05/13/2020
ms.openlocfilehash: 53a0fdd29630b2a4368f3aa37ddfc5f93df10a24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613869"
---
# <a name="leveraging-serverless-functions"></a>Sunucusuz işlevlerden yararlanma

Bulut yeteneklerini kullanmak için fiziksel makineleri yönetme ucundan, sunucusuz çok daha az çaba yaşar. Yalnızca sizin sorumluluğunuzdadır ve kodunuz çalışırken ödeyin. Azure Işlevleri, bulutta yerel uygulamalarınız için sunucusuz yetenekler oluşturmanın bir yolunu sunar.

## <a name="what-is-serverless"></a>Sunucusuz nedir?

Sunucusuz, bulut bilgi işlemin görece yeni bir hizmet modelidir. Bu, sunucuların isteğe bağlı olduğu anlamına gelmez; kodunuz bir yerde sunucu üzerinde hala çalışır. Ayrım, uygulama ekibinin sunucu altyapısını yönetme ile artık ilgilenmesidir. Bunun yerine, bulut satıcısı bu sorumluluğa aittir. Geliştirme ekibi, müşterilere iş çözümleri sunarak üretkenliğini artırır.

Sunucusuz bilgi işlem, hizmetlerinizi barındırmak için olay tarafından tetiklenen durum bilgisi olmayan kapsayıcılar kullanır. Gerektiğinde, talebe göre ve isteğe bağlı olarak uygun şekilde ölçeklenebilirler. Azure Işlevleri gibi sunucusuz platformlar, kuyruklar, olaylar ve depolama gibi diğer Azure hizmetleriyle sıkı bir tümleştirme özelliğine sahiptir.

## <a name="what-challenges-are-solved-by-serverless"></a>Sunucusuz tarafından hangi sorunlar çözüldü?

Sunucusuz platformlar, zaman alan ve pahalı kaygıların çoğunu ele alır:

- Makineler ve yazılım lisansları satın alma
- Makineleri ve bunların ağ, güç ve A/C gereksinimlerini Muhafazası, güvenli hale getirme, yapılandırma ve sürdürme
- İşletim sistemlerini ve yazılımlarını düzeltme ve yükseltme
- Web sunucularını veya makine hizmetlerini uygulama yazılımını barındıracak şekilde yapılandırma
- Uygulama yazılımını platformu içinde yapılandırma

Birçok şirket, donanım altyapısı sorunlarını desteklemek için büyük bütçeler ayırır. Buluta geçiş bu maliyetlerin azalmasına yardımcı olabilir; uygulamaları sunucusuz olarak kaydırma, bunları ortadan kaldırmaya yardımcı olabilir.

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>Mikro hizmet ve sunucusuz bir işlev arasındaki fark nedir?

Genellikle, bir mikro hizmet, çevrimiçi bir eticaret sitesi için bir alışveriş sepeti gibi iş yeteneklerini kapsar. Kullanıcının kendi alışveriş deneyimlerini yönetmesini sağlayan birden çok işlem sunar. Ancak, bir işlev, bir olaya yanıt olarak tek amaçlı bir işlem yürüten küçük, hafif bir kod bloğudur.
Mikro hizmetler genellikle isteklere, genellikle bir arabirimden yanıt vermek için oluşturulur. İstekler HTTP REST veya gRPC tabanlı olabilir. Sunucusuz hizmetler olaylara yanıt verir. Olay odaklı mimari, kısa süreli çalışan, arka plan görevlerini işlemek için idealdir.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Sunucusuz için hangi senaryolar uygun?

Sunucusuz, bir tetikleyiciye yanıt olarak çağrılan tek başına kısa süreli işlevleri kullanıma sunar. Bu, arka plan görevlerinin işlenmesi için ideal hale getirir.

Bir uygulamanın bir iş akışında bir adım olarak e-posta gönderebilmesi gerekebilir. Bildirimi, mikro hizmet isteğinin bir parçası olarak göndermek yerine, ileti ayrıntılarını bir kuyruğa yerleştirin. Bir Azure Işlevi iletiyi sıradan alabilir ve e-postayı zaman uyumsuz olarak gönderebilir. Bunun yapılması, mikro hizmetin performansını ve ölçeklenebilirliğini iyileştirebilir. E-postaların gönderilmesi ile ilgili performans sorunlarını önlemek için [kuyruk tabanlı yük dengeleme](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) uygulanabilir. Ayrıca, bu tek başına hizmet birçok farklı uygulama üzerinde yardımcı program olarak yeniden kullanılabilir.

Kuyruklardan ve konulardan zaman uyumsuz mesajlaşma, sunucusuz işlevleri tetiklemek için kullanılan yaygın bir modeldir. Ancak Azure Işlevleri, Azure Blob depolamada yapılan değişiklikler gibi diğer olaylar tarafından tetiklenebilir. Görüntü yüklemelerini destekleyen bir hizmetin, görüntü boyutunu iyileştirmekten sorumlu bir Azure Işlevi olabilir. İşlev, Azure Blob depolama alanına eklenerek doğrudan tetiklenebilir ve mikro hizmet işlemlerinden karmaşıklığı ortadan kaldırılabilir.

Birçok hizmet, iş akışlarının bir parçası olarak uzun süredir çalışan işlemlere sahiptir. Genellikle bu görevler, kullanıcının uygulamayla etkileşimi kapsamında yapılır. Bu görevler, kullanıcıyı beklemeye zorlayabilir, deneyimlerini olumsuz yönde etkileyebilir. Sunucusuz bilgi işlem, daha yavaş görevleri Kullanıcı etkileşimi döngüsünün dışına taşımak için harika bir yol sağlar. Bu görevler, tüm uygulamanın ölçeklendirilmesi gerekmeden talebe göre ölçeklendirebilir.

## <a name="when-should-you-avoid-serverless"></a>Sunucusuz ne zaman kaçınmalıyım?

Sunucusuz çözümler sağlama ve isteğe bağlı ölçekleme. Yeni bir örnek çağrıldığında, soğuk başlar yaygın bir sorundur. Soğuk bir başlangıç, bu örneği sağlamak için gereken süredir. Normalde, bu gecikme birkaç saniye olabilir, ancak çeşitli faktörlere bağlı olarak daha fazla olabilir. Sağlandıktan sonra, tek bir örnek, düzenli istekleri aldığı sürece etkin tutulur. Ancak, bir hizmet daha az sıklıkta çağrılırsa Azure bu hizmeti bellekten kaldırabilir ve yeniden çağrıldığında soğuk bir başlatma gerektirebilir. Bir işlev yeni bir örneğe ölçeklendirilirken soğuk başlar de gereklidir.

Şekil 3-10, soğuk başlangıç modelini gösterir. Uygulama soğuk olduğunda gereken ek adımlara göz önünde edin.

![Soğuk, sıcak başlangıç ](./media/cold-start-warm-start.png)
 **şekli 3-10**. Soğuk başlatma ve sıcak başlangıç.

Soğuk tamamen başlamasını önlemek için bir [Tüketim planından adanmış plana](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)geçebilirsiniz. Premium plan yükseltmesine sahip bir veya daha fazla [önceden çarpımış örnek](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) de yapılandırabilirsiniz. Bu durumlarda, başka bir örnek eklemeniz gerektiğinde, zaten çalışır durumda ve gönderilmeye hazırız. Bu seçenekler, sunucusuz bilgi işlem ile ilişkili soğuk başlatma sorununu azaltmaya yardımcı olabilir.

Bulut sağlayıcıları, işlem yürütme süresi ve tüketilen bellek temelinde sunucusuz için faturalandırılır. Uzun süre çalışan işlemler veya yüksek bellek tüketim iş yükleri sunucusuz için her zaman en iyi adaydır. Sunucusuz işlevler hızla tamamlayabilirler küçük iş öbeklerini tercih edebilir. Çoğu sunucusuz platform, birkaç dakika içinde tek tek işlevlerin tamamlanmasını gerektirir. Azure Işlevleri varsayılan olarak 5 dakikalık bir zaman aşımı süresine sahiptir ve bu süre 10 dakikaya kadar yapılandırılabilir. Azure Işlevleri Premium planı, bu sorunu da hafifletmenize olanak sağlar. bu da, yapılandırılan zaman aşımı süresini, sınırsız daha yüksek bir sınıra sahip 30 dakikaya kadar azaltır. İşlem süresi takvim zamanı değil. [Azure dayanıklı işlevler çerçevesini](https://docs.microsoft.com/azure/azure-functions/durable/durable-functions-overview?tabs=csharp) kullanan daha gelişmiş işlevler, yürütmeyi birkaç güne ait bir kurs üzerinden duraklatabilir. Faturalandırma gerçek yürütme zamanına göre yapılır-işlev ne zaman uyandırılır ve işlemeyi sürdürür.

Son olarak, uygulama görevleri için Azure Işlevleri 'nden yararlanmak karmaşıklık sağlar. Uygulamanızı modüler ve gevşek olarak bağlanmış bir tasarımla ilk kez mimarın. Daha sonra, avantajlar sunucusuz olup olmadığını ve ek karmaşıklığın nasıl olacağını belirleyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](leverage-containers-orchestrators.md) 
> [Sonraki](combine-containers-serverless-approaches.md)
