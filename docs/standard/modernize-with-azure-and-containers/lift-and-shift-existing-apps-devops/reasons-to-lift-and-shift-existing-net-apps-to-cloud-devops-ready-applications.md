---
title: "Yükseltme ve bulut DevOps çapında kullanılmaya hazır uygulamalar için .NET uygulamaları varolan shift nedenler"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Yükseltme ve bulut DevOps çapında kullanılmaya hazır uygulamalar için .NET uygulamaları varolan shift nedenler"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 941ca8d8fcb4d69f60282737851ab3e86b5782d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications"></a>Yükseltme ve bulut DevOps çapında kullanılmaya hazır uygulamalar için .NET uygulamaları varolan shift nedenler

Bulut DevOps hazır bir uygulama ile güvenilir uygulamaların müşterileriniz için hızlı ve art arda sunabilir. Temel çeviklik ve güvenilirlik, uygulamanızın platform işletim karmaşıklığını çoğunu ertelemeyi kazanır.

Hızlı bir şekilde, uygulamanızın sevk zamanına göre pazara uygulamalarınızı erişemiyorsanız hedefleme Pazar gelişim göstermiştir. Ne kadar iyi uygulamayı tasarlanmış mühendislik veya olsun çok geç olabilir. Olabilir başarısız veya uygulama teslimat Pazar ihtiyaçlarını ile eşitleme yapamıyor çünkü tam potansiyelinize ulaşamayabilir.

Sürekli iş yenilik gereksinimini geliştirme ve işlemleri ekipleri sınırla iter. Sürekli iş yenilik ihtiyacınız çeviklik elde etmek için yalnızca kapsayıcıları ve özel buluta DevOps hazır uygulama ilkeler gibi teknolojileri uygulamalarınızla modernizing tarafından yoludur.

Alt çizgi kuruluş oluşturur ve bulut DevOps kullanıma hazır olan uygulamaları yönetir, bunu çözümleri müşteriler elinizde er put ve ilgili olduklarında pazara yeni fikirleri Getir verilir.

## <a name="cloud-devops-ready-application-principles-and-tenets"></a>Bulut DevOps hazır uygulama ilkeleri ve tenets 

Bulutta geliştirmeleri çoğunlukla odaklanmış iki amacı toplantı: maliyetleri azaltır ve iş büyümesi çeviklik geliştirerek artırmak. Bu hedefleri işlemleri basitleştirir ve yayın ve uygulamaları sevk uyuşmazlık azaltma elde edilir.

Can bir Çevik bileşenini uygulamanızı buluta DevOps hazır ise sınırlarına diğer uygulamalardan şirket içi, uygulamayı şekilde geliştirme ve ardından bırakın, dağıtma, POP, izlemek ve bulut uygulamanızda sorun giderme.

Anahtar *çeviklik*. Tüm dağıtım için-üretim minimuma azaltmak sürece çeviklik ile birlikte olamaz ve geliştirme ve test ortamı sorunlarını. Kapsayıcılar (özellikle, Docker, gerçek bir standart olarak) ve yönetilen hizmetler özellikle bu amaç için tasarlanmıştır.

Çeviklik elde etmek için ayrıca bulutta ölçeklenebilir platformlar için yayın CI/CD ardışık düzen temel alan otomatik DevOps işlemleri gerekir. Ölçeklenebilir ve esnek bir bulut Platformu (örneğin, Azure Service Fabric veya Kubernetes) dağıtmak CI/CD platformlar (Visual Studio Team Services veya Jenkins gibi) bulutta çeviklik elde etmek için anahtar teknolojilerdir.

Aşağıdaki listede ana tenets veya Bulut DevOps çapında kullanılmaya hazır uygulamalar için yöntemler açıklanmaktadır. Tüm veya aşamalı veya artımlı bir yaklaşım, bu ilkeler yalnızca bazılarını benimseyebilirsiniz dikkat edin:

-   **Kapsayıcıları**. Kapsayıcılar uygulama ile uygulamanın bağımlılıkları ekleme yeteneği verir. Kapsayıcıyla taşıma hazırlık ortamları test veya üretim ortamlarına dağıttığınızda karşılaşabileceğiniz sorunların sayısını önemli ölçüde azaltır. Sonuç olarak, kapsayıcı uygulama teslim çeviklik geliştirin.

-   **Esnek, ölçeklenebilir ve bulut**. Bulut yönetilen, esnek, ölçeklenebilir ve esnek bir platform sağlar. Bu özelliklere maliyet geliştirmeleri kazanmak ve yüksek oranda kullanılabilir ve güvenilir uygulamaları sürekli bir teslimi sevk etmek için gerekli olan araçlardır. Yönetilen Hizmetleri ister yönetilen veritabanları, yönetilen önbellek hizmeti (CaaS) ve yönetilen depolama uygulamanızın bakım maliyetlerini ortadan kaldırılmasına içinde temel parçalar olarak.

-   **İzleme**. Güvenilir Uygulama algılamak ve özel durumları ve uygulama performans sorunlarını tanılamak için en iyi yolu gerek kalmadan sahip olamaz. Uygulama performansı yönetimi ve anlık analytics eyleme dönüştürülebilir Öngörüler almanız gerekir.

-   **DevOps kültür ve kesintisiz teslim**. Bulut DevOps hazır yöntemlerini kullanma takımlar artık bağımsız gruplar halinde çalıştığı bir kültür değişiklik gerektirir. CI/CD ardışık düzen yalnızca geliştirme ve kapsayıcılar ve CI/CD araçları tarafından desteklenen BT işletim ekipleri arasında daha yüksek bir işbirliği olduğunda kullanılabilir.

Şekil 4-2 ana isteğe bağlı dayanaklarından bulut DevOps hazır bir uygulama biri gösterir. Daha fazla ayaklar uygulayabilir, uygulamanızın müşterilerinizin beklentilerini karşılamak için başarılı olması için readier olacaktır.

> ![Bulut DevOps hazır bir uygulama, ana ayaklar](./media/image2.png)
>
> **Şekil 4-2.** Bulut DevOps hazır bir uygulama, ana ayaklar

Özetlemek için bir yaklaşım oluşturma ve uygulamaları yönetmek için modeli kapsayıcıları, yönetilen bir bulut altyapısı, esnek uygulama teknikler birleşimini kullanırken bulut yararlanan bulut DevOps hazır bir uygulama olan İzleme, kesintisiz teslim ve tüm yeniden düzenlenmesine ve mevcut uygulamalarınızı recode gerek kalmadan DevOps.

Kuruluşunuz bu teknolojiler ve yaklaşımlar kademeli olarak benimseyebilirsiniz. Bunların, tümünün aynı anda çekirdeğin gerekmez. Kurumsal öncelikleri ve kullanıcı gereksinimlerinize bağlı olarak artımlı olarak, benimseyebilirsiniz.

## <a name="benefits-of-a-cloud-devops-ready-application"></a>Bulut DevOps hazır bir uygulama yararları

(Bulut DevOps hazır bir uygulama varolan bir uygulamaya mimarisinin yeniden düzenlenmesinden veya kodlama olmadan) dönüştürerek aşağıdaki faydaları elde edebilirsiniz:

-   **Düşük maliyetler, bulut sağlayıcısı tarafından yönetilen altyapı işlendiğinden**. Bulut DevOps kullanılmaya hazır uygulamalar, bulutun Giden kutusu esneklik, otomatik ölçeklendirme ve yüksek kullanılabilirlik kullanarak bulutun avantajlarını elde edersiniz. Avantajları yalnızca işlem özellikleri (VM'ler ve kapsayıcılar) ilişkilidir, ancak aynı zamanda bulut kaynaklarında bağlıdır DBaaS, CaaS ve herhangi bir altyapı gibi bir uygulama gerekli.

-   **Esnek uygulama ve altyapı**. Buluta geçirirken, geçici hataları çekirdeğin gerekir; hataları bulutta meydana gelir. Ayrıca, bulut altyapısı donanım ise "değiştirilebilir," geçici kapalı kalma süresi için fırsatlar artırır. Aynı anda iç bulut özelliklerini ve dayanıklılık uygulamak ve kurtarma otomatikleştirmek belirli uygulama geliştirme teknikleri çok bulutta beklenmeyen hatalar kurtarılır kolaylaştırır.

-   **Uygulama performansı daha ayrıntılı Öngörüler**. Azure Application Insights sistem durumu yönetimi, günlüğe kaydetme ve bildirimler için görselleştirme sağlamak gibi izleme araçları bulut. Denetim uygulamaları kolay hata ayıklama ve denetim günlüklerini. Bu, güvenilir bulut uygulaması için temel önemdedir.

-   **Çevik dağıtımlar ile uygulama taşınabilirliği**. Kapsayıcılar (Docker altyapısını temel Linux veya Windows kapsayıcıları) önleme bulut kilitli bir uygulama için en iyi çözüm sunar. Kapsayıcılar, Docker ana bilgisayarları ve birden çok bulut orchestrators kullanarak kolayca bir ortamdan taşıma veya başka bir bulut. Kapsayıcıları herhangi bir ortamın (aşama/test/üretim) dağıtımları genellikle oluşuyor uyuşmazlık ortadan kaldırır.

Tüm avantajlar sonuçta uçtan uca uygulama yaşam döngünüz için önemli maliyet azaltması sağlayın.

Aşağıdaki bölümlerde bu faydaları daha ayrıntılı olarak açıklanmıştır ve belirli teknolojileri bağlanır.

>[!div class="step-by-step"]
[Önceki](index.md)
[sonraki](microsoft-technologies-in-cloud-devops-ready-applications.md)
