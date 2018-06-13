---
title: Bulut için optimize edilmiş uygulamalara varolan .NET uygulamaları modernize nedenleri
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Bulut için optimize edilmiş uygulamalara varolan .NET uygulamaları modernize nedenleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a874a742f6a5b32e15040ad0a237f0e0fa7908dc
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958235"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Bulut için optimize edilmiş uygulamalara varolan .NET uygulamaları modernize nedenleri

Bulut için iyileştirilmiş bir uygulama ile güvenilir uygulamaların müşterileriniz için hızlı ve art arda sunabilir. Temel çeviklik ve güvenilirlik, uygulamanızın platform işletim karmaşıklığını çoğunu ertelemeyi kazanır.

Hızlı bir şekilde, uygulamanızın sevk zamanına göre pazara uygulamalarınızı erişemiyorsanız hedefleme Pazar gelişim göstermiştir. Ne kadar iyi uygulamayı tasarlanmış mühendislik veya olsun çok geç olabilir. Olabilir başarısız veya uygulama teslimat Pazar ihtiyaçlarını ile eşitleme yapamıyor çünkü tam potansiyelinize ulaşamayabilir.

Sürekli iş yenilik gereksinimini geliştirme ve işlemleri ekipleri sınırla iter. Sürekli iş yenilik ihtiyacınız çeviklik elde etmek için yalnızca kapsayıcıları ve özel bulut için iyileştirilmiş uygulama ilkeleri gibi teknolojileri uygulamalarınızla modernizing tarafından yoludur.

Alt çizgi kuruluş oluşturur ve bulut için iyileştirilmiş olan uygulamaları yönetir, bunu çözümleri müşteriler elinizde er put ve ilgili olduklarında pazara yeni fikirleri Getir olmasıdır.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Bulut için iyileştirilmiş uygulama ilkeleri ve tenets 

Bulutta geliştirmeleri çoğunlukla odaklanmış iki amacı toplantı: maliyetleri azaltır ve iş büyümesi çeviklik geliştirerek artırmak. Bu hedefleri işlemleri basitleştirir ve yayın ve uygulamaları sevk uyuşmazlık azaltma elde edilir.

Bulut iyileştirilmiş can bileşenini bir Çevik diğer şirket içi uygulamalardan sınırlarına uygulamayı şekilde geliştirme ve ardından bırakın, otomatik ölçekli dağıtırsanız, uygulamanızı izlemek ve bulut uygulamanızda sorun giderme.

Anahtar *çeviklik*. Tüm dağıtım için-üretim minimuma azaltmak sürece çeviklik ile birlikte olamaz ve geliştirme ve test ortamı sorunlarını. Kapsayıcılar (özellikle, Docker, gerçek bir standart olarak) ve yönetilen hizmetler özellikle bu amaç için tasarlanmıştır.

Çeviklik elde etmek için ayrıca bulutta ölçeklenebilir platformlar için yayın CI/CD ardışık düzen temel alan otomatik DevOps işlemleri gerekir. Ölçeklenebilir ve esnek bir bulut Platformu (örneğin, Azure App Service, Azure Service Fabric veya Azure Kubernetes hizmet) dağıtmak CI/CD platformlar (Visual Studio Team Services veya Jenkins gibi) bulutta çeviklik elde etmek için anahtar teknolojilerdir.

Aşağıdaki listede ana tenets veya Bulut için iyileştirilmiş uygulamalar için yöntemler açıklanmaktadır. Tüm veya aşamalı veya artımlı bir yaklaşım, bu ilkeler yalnızca bazılarını benimseyebilirsiniz dikkat edin:

-   **Kapsayıcıları**. Kapsayıcılar uygulama ile uygulamanın bağımlılıkları ekleme yeteneği verir. Kapsayıcıyla taşıma hazırlık ortamları test veya üretim ortamlarına dağıttığınızda karşılaşabileceğiniz sorunların sayısını önemli ölçüde azaltır. Sonuç olarak, kapsayıcı uygulama teslim çeviklik geliştirin.

-   **Esnek, ölçeklenebilir ve bulut**. Bulut yönetilen, esnek, ölçeklenebilir ve esnek bir platform sağlar. Bu özelliklere maliyet geliştirmeleri kazanmak ve yüksek oranda kullanılabilir ve güvenilir uygulamaları sürekli bir teslimi sevk etmek için gerekli olan araçlardır. Yönetilen Hizmetleri ister yönetilen veritabanları, yönetilen önbellek hizmeti (CaaS) ve yönetilen depolama uygulamanızın bakım maliyetlerini ortadan kaldırılmasına içinde temel parçalar olarak.

-   **İzleme**. Güvenilir Uygulama algılamak ve özel durumları ve uygulama performans sorunlarını tanılamak için en iyi yolu gerek kalmadan sahip olamaz. Uygulama performansı yönetimi ve anlık analytics eyleme dönüştürülebilir Öngörüler almanız gerekir.

-   **DevOps kültür ve kesintisiz teslim**. DevOps yöntemlerini kullanma takımlar artık bağımsız gruplar halinde çalıştığı bir kültür değişiklik gerektirir. CI/CD ardışık düzen yalnızca geliştirme ve kapsayıcılar ve CI/CD araçları tarafından desteklenen BT işletim ekipleri arasında daha yüksek bir işbirliği olduğunda kullanılabilir.

Şekil 4-2 bulut için iyileştirilmiş bir uygulamanın ana isteğe bağlı ayaklar gösterir. Daha fazla ayaklar uygulayabilir, uygulamanızın müşterilerinizin beklentilerini karşılamak için başarılı olması için readier olacaktır.

> ![Bulut için iyileştirilmiş bir uygulamanın ana ayaklar](./media/image2.png)
>
> **Şekil 4-2.** Bulut için iyileştirilmiş bir uygulamanın ana ayaklar

Özetlemek gerekirse, bulut için iyileştirilmiş bir uygulama modeli kapsayıcıları, yönetilen bir bulut altyapısı, esnek uygulama teknikler birleşimini kullanırken bulut yararlanan oluşturma ve uygulamaları yönetmek için bir yaklaşımdır, İzleme, kesintisiz teslim ve tüm rearchitect ve mevcut uygulamalarınızı recode gerek kalmadan DevOps.

Kuruluşunuz bu teknolojiler ve yaklaşımlar kademeli olarak benimseyebilirsiniz. Bunların, tümünün aynı anda çekirdeğin gerekmez. Kurumsal öncelikleri ve kullanıcı gereksinimlerinize bağlı olarak artımlı olarak, benimseyebilirsiniz.

## <a name="benefits-of-a-cloud-optimized-application"></a>Bulut için iyileştirilmiş bir uygulama yararları

(Bulut için iyileştirilmiş bir uygulama varolan bir uygulamaya bütçeden veya kodlama olmadan) dönüştürerek aşağıdaki faydaları elde edebilirsiniz:

-   **Düşük maliyetler, bulut sağlayıcısı tarafından yönetilen altyapı işlendiğinden**. Bulut için iyileştirilmiş uygulamaları bulutun Giden kutusu esneklik, otomatik ölçeklendirme ve yüksek kullanılabilirlik kullanarak bulutun avantajlarını alın. Avantajları yalnızca işlem özellikleri (VM'ler ve kapsayıcılar) ilişkilidir, ancak aynı zamanda bulut kaynaklarında bağlıdır DBaaS, CaaS ve herhangi bir altyapı gibi bir uygulama gerekli.

-   **Esnek uygulama ve altyapı**. Buluta geçirirken, geçici hataları çekirdeğin gerekir; hataları bulutta meydana gelir. Ayrıca, bulut altyapısı ve donanım "değiştirilebilir," geçici kapalı kalma süresi olanaklarını artıran kullanılabilir. Aynı anda iç bulut özelliklerini ve dayanıklılık uygulamak ve kurtarma otomatikleştirmek belirli uygulama geliştirme teknikleri çok bulutta beklenmeyen hatalar kurtarılır kolaylaştırır.

-   **Uygulama performansı daha ayrıntılı Öngörüler**. Azure Application Insights sistem durumu yönetimi, günlüğe kaydetme ve bildirimler için görselleştirme sağlamak gibi izleme araçları bulut. Denetim günlüklerini uygulamaları hata ayıklama ve denetleme, güvenilir bulut uygulaması için temel kolay hale getirir.

-   **Çevik dağıtımlar ile uygulama taşınabilirliği**. Kapsayıcılar (Docker altyapısını temel Linux veya Windows kapsayıcıları) önleme bulut kilitli bir uygulama için en iyi çözüm sunar. Kapsayıcılar, Docker ana bilgisayarları ve birden çok bulut orchestrators kullanarak kolayca bir ortamdan taşıma veya başka bir bulut. Kapsayıcıları herhangi bir ortamın (aşama/test/üretim) dağıtımları genellikle oluşuyor uyuşmazlık ortadan kaldırır.

Tüm avantajlar sonuçta uçtan uca uygulama yaşam döngünüz için önemli maliyet azaltması sağlayın.

Aşağıdaki bölümlerde bu faydaları daha ayrıntılı olarak açıklanmıştır ve belirli teknolojileri bağlanır.

>[!div class="step-by-step"]
[Önceki](index.md)
[sonraki](microsoft-technologies-in-cloud-optimized-applications.md)
