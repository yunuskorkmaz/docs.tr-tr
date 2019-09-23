---
title: Sunucusuz işlevleri kullanma
description: Bulutta yerel uygulamalarda sunucusuz ve Azure Işlevlerini kullanma
ms.date: 06/30/2019
ms.openlocfilehash: 61bf4db6d61160c7ec11ffa3f178cc3917ae6cf9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182827"
---
# <a name="leveraging-serverless-functions"></a>Sunucusuz işlevleri kullanma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bulut yeteneklerini kullanmak için tam makineleri ve işletim sistemlerini yönetme yelpazesi içinde sunucusuz, yalnızca sizin sorumlu olduğunuz tek şey kodunuzun olduğu ve yalnızca çalışma sırasında kodunuz için ödeme yaparsınız. Azure Işlevleri, uygulamalarınızda sunucusuz yetenekler oluşturmak için bir yol sağlar. 

## <a name="what-is-serverless"></a>Sunucusuz nedir?

Sunucusuz bilgi işlem, uygulamanızı çalıştırmaya katılan bir sunucu olmadığı anlamına gelmez; kod hala sunucuda çalışır. Ayrım, uygulama geliştirme ekibinin sunucu altyapısını yönetme konusunda artık ilgilenmesini gerektirmez. Azure Işlevleri gibi sunucusuz bilgi işlem çözümleri ekiplerin üretkenliğini artırmasına yardımcı olur ve kuruluşların kaynaklarını iyileştirmelerine ve çözümler sunmaya odaklanmasına olanak tanır.

Sunucusuz bilgi işlem, uygulamanızı veya uygulamanızın bir bölümünü barındırmak için olay tarafından tetiklenen durum bilgisi olmayan kapsayıcılar kullanır. Sunucusuz platformlar, isteğe bağlı olarak talep karşılamak için ölçeği artırma ve azaltma yapabilir. Azure Işlevleri gibi platformlar, kuyruklar, olaylar ve depolama gibi diğer Azure hizmetlerine kolayca doğrudan erişebilir.

## <a name="what-challenges-are-solved-by-serverless"></a>Sunucusuz tarafından hangi sorunlar çözüldü?

Sunucusuz, kendi donanımınızı çalıştırmanın son soyutlamasıdır. Geliştiriciler, kendi sunucularınızı barındırırken gerekli olabilecek aşağıdaki görevlerden herhangi birine gerek kalmadan, iş sorunlarını gidermek için özel olarak kod yazmaya odaklanabilir:

- Makineler ve yazılım lisansları satın alma
- Makineleri ve bunların ağ, güç ve A/C gereksinimlerini Muhafazası, güvenli hale getirme, yapılandırma ve sürdürme
- İşletim sistemlerini ve yazılımlarını düzeltme ve yükseltme
- Web sunucularını veya makine hizmetlerini uygulama yazılımını barındıracak şekilde yapılandırma
- Uygulama yazılımını platformu içinde yapılandırma

Birçok şirket, onlarca personel üyesi ve bu donanım altyapısı sorunlarını desteklemek için büyük bütçeler ayırır. Yalnızca buluta geçmek, bu kaygıları ortadan kaldırır; uygulamaları sunucusuz 'e kadar bir şekilde kaydırma, Rest 'i ortadan kaldırır.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Sunucusuz için hangi senaryolar uygun?

Sunucusuz, bazı tetikleyicisine yanıt olarak çağrılan tek başına kısa süreli işlevleri kullanır. Bu, arka plan görevlerinin işlenmesi için ideal hale getirir.

Örneğin, bir uygulamanın bir isteği işlemenin parçası olarak bir e-posta gönderebilmesi gerekebilir. Web isteğini işlemenin parçası olarak e-postayı göndermek yerine, e-postanın ayrıntıları bir kuyruğa yerleştirilecektir ve iletiyi almak ve e-postayı göndermek için bir Azure Işlevi kullanılabilir. Uygulamanın birçok farklı bölümü veya çok sayıda uygulama, bu aynı Azure Işlevinden yararlanarak uygulamalar için iyileştirilmiş performans ve ölçeklenebilirlik sağlar ve ile ilgili sorunları önlemek için [kuyruk tabanlı yük dengelemeyi](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) kullanabilir e-postalar gönderiliyor.

Uygulamalar ve Azure Işlevleri arasında bir [yayımcı/abonelik düzeni](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) en yaygın düzen olmakla birlikte, diğer desenler de mümkündür. Azure Işlevleri, Azure Blob depolamada yapılan değişiklikler gibi diğer olaylar tarafından tetiklenebilir. Görüntü karşıya yüklemelerini destekleyen bir uygulama, küçük resimler oluşturmaktan veya karşıya yüklenen görüntüleri tutarlı boyutlara yeniden boyutlandırmaktan veya görüntü boyutunu en iyi duruma getirmekten sorumlu bir Azure Işlevine sahip olabilir. Bu işlevlerin tümü, Azure Blob depolama alanına ekleme yaparak doğrudan tetiklenebilir ve karmaşıklık ve iş yükü uygulamanın kendisi tarafından yapılır.

Birçok uygulama, iş akışlarının bir parçası olarak uzun süredir çalışan işlemlere sahiptir. Genellikle bu görevler kullanıcının uygulamayla etkileşimi kapsamında yapılır, böylece Kullanıcı, deneyimlerini bekleyip olumsuz şekilde etkiler. Sunucusuz bilgi işlem, Kullanıcı etkileşimi döngüsünün dışında daha yavaş görevler gerçekleştirmek için harika bir yol sağlar ve bu görevler tüm uygulamanın ölçeklendirilmesine gerek kalmadan isteğe bağlı olarak kolayca ölçeklenebilirler.

## <a name="when-should-you-avoid-serverless"></a>Sunucusuz ne zaman kaçınmalıyım?

Sunucusuz bilgi işlem, Kullanıcı arabirimini engellememe görevleri için en iyi seçenektir. Bu, Web uygulamalarını veya Web API 'Lerini doğrudan barındırmak için ideal olmadıkları anlamına gelir. Bunun ana nedeni sunucusuz çözümlerin talep üzerine sağlandığını ve ölçeklendirilmesine yöneliktir. Bir işlevin yeni bir örneği gerektiğinde, *soğuk başlangıç*olarak bahsedildiğinde, sağlanması zaman alır. Bu süre genellikle birkaç saniyedir, ancak çeşitli faktörlere bağlı olarak daha uzun sürebilir. Tek bir örnek genellikle süresiz olarak korunabilir (örneğin, düzenli aralıklarla bir istek yaparak), ancak her zaman ölçeği bir kez ölçeklendirilmesi gereken örneklerin sayısı varsa soğuk başlatma sorunu kalır.

![Soğuk, sıcak başlangıç](./media/cold-start-warm-start.png)
**şekli 3-10**. Soğuk başlatma ve sıcak başlangıç.

Soğuk tamamen başlamasını gerekmiyorsa, bir [Tüketim planından adanmış plana](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)geçiş yapabilirsiniz. Premium planıyla [bir veya daha fazla önceden çarpımış örnek de yapılandırabilirsiniz](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) , bu nedenle başka bir örnek eklemeniz gerektiğinde, zaten çalışır durumda ve gönderilmeye hazırız olur. Bu seçenekler sunucusuz bilgi işlem ile ilişkili önemli kaygılardan birini hafifletmeye yönelik olabilir.

Ayrıca uzun süre çalışan görevler için sunucusuz da kaçınmalısınız. Bunlar, hızlıca tamamlanalabileceğiniz küçük iş parçaları için idealdir. Çoğu sunucusuz platform, birkaç dakika içinde tek tek işlevlerin tamamlanmasını gerektirir. Azure Işlevleri, varsayılan olarak 5 dakikalık bir zaman aşımı süresine sahiptir (10 dakikaya kadar yapılandırılabilir). Azure Işlevleri Premium planı, bu sorunun yanı sıra 30 dakikalık süreyi en aza indirmenize ve sınırlandırılmamış daha yüksek sınırın yapılandırılmasına izin verebilir.

Son olarak, uygulamanızın içindeki belirli görevler için sunucusuz bir şekilde yararlanmak karmaşıklık ekler. Uygulamanızı öncelikle modüler ve gevşek olarak bağlanmış bir şekilde mimariyi hale getirmek, daha sonra diğer karmaşıklığın daha az olduğunu ve avantajların daha az olup olmadığını belirlemek için en iyi seçenektir. Birçok küçük uygulama, dağıtılmış uygulama mimarisi sunucusuz bilgi işlem için gerekli olmadan, tek bir monoparçalı dağıtımda kusursuz bir şekilde çalışacaktır.

## <a name="references"></a>Referanslar

- [Sunucusuz soğuk başlangıcını anlama](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Önceden çarpımış Azure Işlevleri örnekleri](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Linux üzerinde özel görüntü kullanarak bir işlev oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
>[Önceki](leverage-containers-orchestrators.md)
>[İleri](combine-containers-serverless-approaches.md)
