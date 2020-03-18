---
title: Bulut Tarafından Optimize Edilmiş uygulamalara mevcut .NET uygulamalarını modernize etme nedenleri
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Bulut Tarafından Optimize Edilmiş uygulamalara mevcut .NET uygulamalarını modernize etme nedenleri
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093628"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Bulut Tarafından Optimize Edilmiş uygulamalara mevcut .NET uygulamalarını modernize etme nedenleri

Bulut tarafından optimize edilmiş bir uygulama ile müşterilerinize hızlı ve sürekli olarak güvenilir uygulamalar sunabilirsiniz. Uygulamanızın operasyonel karmaşıklığının çoğunu platforma erteleyerek temel çeviklik ve güvenilirlik kazanırsınız.

Uygulamalarınızı hızlı bir şekilde pazara sunamıyorsanız, uygulamanızı gönderene kadar hedeflediğiniz pazar gelişmiş olur. Uygulama ne kadar iyi tasarlanmış veya tasarlanmış olursa olsun, çok geç olabilirsiniz. Uygulama dağıtımını pazarın gereksinimleriyle senkronize edemediğiniz için başarısız olabilir veya tam potansiyelinize ulaşamaz.

Sürekli iş inovasyonuna duyulan ihtiyaç, geliştirme ve operasyon ekiplerini sınıra kadar zorlar. Sürekli iş inovasyonunda ihtiyacınız olan çevikliği elde etmenin tek yolu, uygulamalarınızı kapsayıcılar ve belirli Bulut Optimize edilmiş uygulama ilkeleri gibi teknolojilerle modernize etmektir.

Sonuç olarak, bir kuruluş Bulut Tarafından Optimize Edilmiş uygulamalar oluşturup yönettiğinde, çözümleri daha erken müşterilerin eline verebilir ve ilgili olduklarında yeni fikirleri pazara sunabilir.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Bulut tarafından optimize edilmiş uygulama ilkeleri ve ilkeleri

Buluttaki gelişmeler çoğunlukla iki hedefi karşılamaya odaklanmıştır: Çevikliği artırarak maliyetleri azaltın ve iş büyümesini geliştirin. Bu hedeflere, uygulamaları serbest bırakıp sevk ettiğinizde süreçleri basitleştirerek ve sürtünmeyi azaltarak ulaşılır.

Uygulamanızı çevik bir şekilde diğer şirket içi uygulamalardan bağımsız olarak geliştirebilirseniz ve ardından uygulamanızı bulutta serbest bırakabilir, dağıtabilir, otomatik ölçeklendirebilir, izleyebilir ve sorun giderebilirseniz, uygulamanız Bulut Için Optimize Edilmiştir.

Anahtar *çeviklik.* Dağıtımdan üretime dağıtım sorunlarını ve geliştirme/test ortamı sorunlarını mutlak minimuma düşürmediğiniz sürece çeviklikle gönderi yapamazsınız. Konteynerler (özellikle, Docker, fiili bir standart olarak) ve yönetilen hizmetler bu amaç için özel olarak tasarlanmıştır.

Çeviklik elde etmek için, bulutta ölçeklenebilir platformlara serbest bırakılabilen CI/CD ardışık hatlar hattını temel alan otomatik DevOps işlemlerine de ihtiyacınız vardır. Ölçeklenebilir ve esnek bir bulut platformuna (Azure Uygulama Hizmeti veya Azure Kubernetes Hizmeti gibi) dağıtılan CI/CD platformları (Azure DevOps Services veya Jenkins gibi) bulutta çeviklik elde etmek için önemli teknolojilerdir.

Aşağıdaki listede Bulut Için Optimize Edilmiş uygulamalar için ana ilkeler veya uygulamalar açıklanmaktadır. Aşamalı veya artımlı bir yaklaşımla bu ilkelerin tümlerini veya yalnızca bazılarını benimseyebileceğinizi unutmayın:

- **Konteynerler**. Kapsayıcılar, uygulama bağımlılıklarını uygulamanın kendisine ekleme olanağı sağlar. Kapsayıcılık, üretim ortamlarına dağıtTığınızda veya hazırlama ortamlarında test ettiğinizde karşılaşabileceğiniz sorunların sayısını önemli ölçüde azaltır. Sonuç olarak, kapsayıcılar uygulama teslim çevikliğini artırır.

- **Esnek ve ölçeklenebilir bulut**. Bulut yönetilen, elastik, ölçeklenebilir ve esnek bir platform sağlar. Bu özellikler maliyet iyileştirmeleri kazanmak ve sürekli teslimatta yüksek kullanılabilir ve güvenilir uygulamalar geliştirmek için temel dir. Yönetilen veritabanları, hizmet olarak yönetilen önbellek (CaaS) ve yönetilen depolama gibi yönetilen hizmetler, uygulamanızın bakım maliyetlerini hafifletmede temel parçalardır.

- **İzleme**. Özel durumları ve uygulama performansı sorunlarını algılamak ve tanılamak için iyi bir yol olmadan güvenilir bir uygulama olamaz. Uygulama performansı yönetimi ve anında analitik aracılığıyla eyleme geçirilebilir öngörüler elde edebilirsiniz.

- **DevOps kültür ve sürekli teslimat**. DevOps uygulamalarını benimsemek, ekiplerin artık bağımsız silolarda çalışmadığı kültürel bir değişim gerektirir. CI/CD boru hatları, yalnızca geliştirme ve BT operasyon ekipleri arasında kapsayıcılar ve CI/CD araçları tarafından desteklenen daha fazla işbirliği olduğunda mümkündür.

Şekil 4-2, Bulut Tarafından Optimize Edilmiş bir uygulamanın isteğe bağlı temel direklerini gösterir. Ne kadar çok direği uygularsanız, uygulamanız müşterilerinizin beklentilerini karşılamada o kadar kolay olacaktır.

![Bulut Tarafından Optimize Edilmiş bir uygulamanın ana sütunlarını adlandırma diyagramı.](./media/main-pillars-cloud-optimized-application.png)

**Şekil 4-2.** Bulut Tarafından Optimize Edilmiş bir uygulamanın temel direkleri

Özetlemek gerekirse, Bulut Tarafından Optimize Edilmiş bir uygulama, kapsayıcılar, yönetilen bulut altyapısı, esnek uygulama teknikleri, kapsayıcılar, yönetilen uygulama teknikleri bir arada kullanırken, bulut bilgi işlem modelinden yararlanan uygulamalar oluşturma ve yönetme yaklaşımıdır. izleme, sürekli teslimat ve DevOps, tüm yeniden mimarlık ve mevcut uygulamaları yeniden kodlamak gerek kalmadan.

Kuruluşunuz bu teknolojileri ve yaklaşımları kademeli olarak benimseyebilir. Hepsini aynı anda kucaklamak zorunda değilsin. Bunları, kurumsal önceliklere ve kullanıcı gereksinimlerine bağlı olarak kademeli olarak benimseyebilirsiniz.

## <a name="benefits-of-a-cloud-optimized-application"></a>Bulut Için Optimize Edilmiş bir uygulamanın avantajları

Varolan bir uygulamayı Bulut Için Optimize Edilmiş bir uygulamaya dönüştürerek (yeniden architectyon veya kodlama yapmadan) aşağıdaki avantajlardan yararlanabilirsiniz:

- **Yönetilen altyapı bulut sağlayıcısı tarafından işlenir, çünkü daha düşük maliyetler.** Bulut için optimize edilmiş uygulamalar, bulutun hazır elastikiyetini, otomatik ölçeklendirmesini ve yüksek kullanılabilirliğini kullanarak bulutun avantajlarından yararlanır. Avantajlar yalnızca bilgi işlem özellikleriyle (VM'ler ve kapsayıcılar) değil, aynı zamanda DBaaS, CaaS ve bir uygulamanın ihtiyaç duyulabileceği altyapı gibi buluttaki kaynaklara da bağlıdır.

- **Esnek uygulama ve altyapı.** Buluta geçiş yaptığınızda, geçici hataları benimsemeniz gerekir; hatalar bulutta meydana gelecektir. Ayrıca, bulut altyapısı ve donanımı "değiştirilebilir", bu da geçici kapalı kalma sürelerini artırır. Aynı zamanda, iç bulut yetenekleri ve esnekliği uygulayan ve kurtarmayı otomatikleştiren belirli uygulama geliştirme teknikleri, buluttaki beklenmeyen hatalardan kurtulmayı çok daha kolay hale getirir.

- **Uygulama performansına ilişkin daha derin bilgiler.** Azure Application Insights gibi bulut izleme araçları, sistem durumu yönetimi, günlüğe kaydetme ve bildirimler için görselleştirme sağlar. Denetim günlükleri, güvenilir bir bulut uygulaması için temel olan uygulamaları hata ayıklamayı ve denetimi kolaylaştırır.

- **Uygulama taşınabilirliği, çevik dağıtımlar ile**. Kapsayıcılar (Docker Engine tabanlı Linux veya Windows kapsayıcıları) bulut kilitli bir uygulamadan kaçınmak için en iyi çözümü sunar. Kapsayıcıları, Docker ana bilgisayarlarını ve çok bulutlu orkestratörleri kullanarak bir ortamdan veya buluttan diğerine kolayca geçebilirsiniz. Kapsayıcılar, genellikle herhangi bir ortama (aşama/test/üretim) dağıtımlarda oluşan sürtünmeyi ortadan kaldırır.

Tüm bu avantajlar sonuçta uçtan uca uygulama yaşam döngüsü için önemli maliyet indirimleri sağlar.

Aşağıdaki bölümlerde, bu avantajlar daha ayrıntılı olarak açıklanır ve belirli teknolojilere bağlanır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](microsoft-technologies-in-cloud-optimized-applications.md)
