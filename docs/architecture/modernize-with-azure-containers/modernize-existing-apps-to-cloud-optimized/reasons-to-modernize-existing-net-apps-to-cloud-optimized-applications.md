---
title: Mevcut .NET uygulamalarını Cloud-Optimized uygulamalar için modernleştirin nedenleri
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Mevcut .NET uygulamalarını Cloud-Optimized uygulamalar için modernleştirin nedenleri
ms.date: 12/21/2020
ms.openlocfilehash: e9b3ad151cf0591783ada8a1ab87cb0f14423a7e
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025218"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Mevcut .NET uygulamalarını Cloud-Optimized uygulamalar için modernleştirin nedenleri

Cloud-Optimized bir uygulamayla, müşterilerinize hızlı ve sürekli olarak güvenilir uygulamalar gönderebilirsiniz. Uygulamanızın işlemsel karmaşıklığını çok fazla erteleyerek önemli çeviklik ve güvenilirlik elde edersiniz.

Uygulamalarınızın hızla pazara sunabilmenize izin alamazsanız, uygulamanızı sevk etmeniz sırasında hedeflediğiniz Pazar gelişmiş olacaktır. Uygulamanın ne kadar iyi bir şekilde tasarlanmış veya uygulanan ne kadar iyi olduğuna bakılmaksızın, çok geç olabilirsiniz. Market ihtiyaçlarına göre uygulama dağıtımını eşitleyemediği için, başarısız olabilir veya tam potansiyeline ulaşamıyoruz.

Sürekli iş yeniliği gereksinimi, geliştirme ve operasyon ekiplerini limite gönderir. Sürekli iş yeniliği için ihtiyaç duyduğunuz çevikliği elde etmenin tek yolu, uygulamalarınızı kapsayıcılar ve belirli Cloud-Optimized uygulama ilkeleri gibi teknolojilerle modernleştirmeye göre yapılır.

En alttaki satır, bir kuruluşun bulut için optimize edilmiş uygulamaları oluşturup yönettiğine göre, çözümleri daha önce müşterilere yerleştirebilir ve ilgili olduklarında pazara yeni fikirler getirebilir.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Cloud-Optimized uygulama ilkeleri ve tenetler

Buluttaki geliştirmeler genellikle iki hedefi karşılamaya odaklanılmıştır: çevikliği artırarak maliyetleri azaltın ve iş artışını geliştirebilirsiniz. Bu hedefler, uygulamaları serbest bırakma ve sevk ettiğiniz sırada süreçler basitleştirilerek ve uçuşmadan elde edilir.

Uygulamanız Cloud-Optimized, diğer şirket içi uygulamalardan uygulama olarak çalışabilen geliştirin ve ardından bulutta uygulamanızı serbest bırakma, dağıtma, otomatik ölçeklendirme, izleme ve sorun giderme.

Anahtar *çeviklik*. En az bir dağıtım-üretim sorunları ve geliştirme/test ortamı sorunlarını azaltmadığınız müddetçe çevikiyle birlikte gönderim yapamazsınız. Kapsayıcılar (özellikle de bir de standart olarak Docker) ve yönetilen hizmetler bu amaçla özel olarak tasarlanmıştır.

Çeviklik sağlamak için, buluttaki ölçeklenebilir platformları oluşturan CI/CD işlem hatlarını temel alan otomatik DevOps işlemlerine de ihtiyacınız vardır. Ölçeklenebilir ve dayanıklı bir bulut platformuna (Azure App Service ya da Azure Kubernetes hizmeti gibi) dağıtan CI/CD platformları (Azure DevOps Services veya Jenkins gibi), bulutta çeviklik sağlamak için önemli teknolojilerdir.

Aşağıdaki listede, Cloud-Optimized uygulamalara yönelik ana örnekler veya uygulamalar açıklanmaktadır. Bu ilkelerin tümünü veya yalnızca bazılarını aşamalı veya artımlı bir yaklaşımda benimseyebileceğinizi unutmayın:

- **Kapsayıcılar**. Kapsayıcılar, uygulama bağımlılıklarını uygulamanın kendisiyle birlikte dahil etme olanağı sunar. Kapsayıcılama, üretim ortamlarına dağıtırken veya hazırlama ortamlarında test ettiğinizde karşılaşabileceğiniz sorun sayısını önemli ölçüde azaltır. Son olarak, kapsayıcılar uygulama tesliminin çevikliğini geliştirir.

- Dayanıklı **ve ölçeklenebilir bulut**. Bulut, yönetilen, elastik, ölçeklenebilir ve esnek bir platform sağlar. Bu özellikler, maliyet iyileştirmeleri kazanmak ve sürekli olarak kullanılabilir ve güvenilir uygulamalar elde etmek için temel düzeyde kullanıma sunulmuştur. Yönetilen veritabanları gibi yönetilen hizmetler, bir hizmet olarak yönetilen önbellek (CaaS) ve yönetilen depolama, uygulamanızın bakım maliyetlerini hafifletmesini içinde temel parçalardır.

- **İzleme**. Özel durumları ve uygulama performansı sorunlarını tespit etmek ve tanılamak için iyi bir yöntem olmadan güvenilir bir uygulamanız olamaz. Uygulama performansı yönetimi ve anında analiz aracılığıyla eyleme dönüştürülebilir Öngörüler almanız gerekir.

- **DevOps kültürü ve sürekli teslim**. DevOps uygulamalarını benimseme, takımlarının bağımsız silolarda artık çalışmadıkları kültürel değişikliği gerektirir. CI/CD işlem hatları yalnızca geliştirme ve BT operasyon takımları arasında, kapsayıcılar ve CI/CD araçları tarafından desteklenen bir işbirliği olduğunda mümkündür.

Şekil 4-2 Cloud-Optimized bir uygulamanın ana isteğe bağlı ananlarına gösterir. Uyguladığınız daha fazla sayıda işlem, müşterilerinizin beklentilerini karşıladığı için uygulamanızın başarılı olması için readier.

![Bir Cloud-Optimized uygulamasının ana paragraf adlarını adlandırma diyagramı.](./media/main-pillars-cloud-optimized-application.png)

**Şekil 4-2.** Cloud-Optimized uygulamasının ana paragraf oluşturma

Özetlemek gerekirse, Cloud-Optimized bir uygulama, mevcut uygulamalarınızı yeniden mimarmaya ve yeniden kodlamadan bir kapsayıcı, yönetilen bulut altyapısı, dayanıklı uygulama teknikleri, izleme, sürekli teslim ve DevOps birleşimini kullanarak, bulut bilgi işlem modelinden faydalanan uygulamaları oluşturma ve yönetmeye yönelik bir yaklaşımdır.

Kuruluşunuz bu teknolojileri benimseyebileceği gibi, yavaş bir yaklaşımlar alabilir. Hepsi bir kez olmak üzere tümünü tek tek ayraç içine almanız gerekmez. Kurumsal önceliklere ve kullanıcı gereksinimlerine bağlı olarak bunları artımlı olarak benimseyebilirsiniz.

## <a name="benefits-of-a-cloud-optimized-application"></a>Cloud-Optimized uygulamasının avantajları

Mevcut bir uygulamayı bir Cloud-Optimized uygulamasına dönüştürerek aşağıdaki avantajları elde edebilirsiniz (yeniden mimari veya kodlama yapmadan):

- **Daha düşük maliyetler, yönetilen altyapı bulut sağlayıcısı tarafından işlenir**. Cloud-Optimized uygulamalar, bulutun kullanıma hazır esneklik, otomatik ölçeklendirme ve yüksek kullanılabilirliği kullanarak bulutun avantajlarını elde edin. Avantajlar yalnızca işlem özelliklerine (VM 'Ler ve kapsayıcılar) değil, aynı zamanda buluttaki kaynaklara da (örneğin, DBaaS, CaaS) ve bir uygulamanın gereksinim duyabileceği herhangi bir altyapıya bağlıdır.

- Dayanıklı **uygulama ve altyapı**. Buluta geçiş yaptığınızda, geçici hatalardan yararlanın; bulutta sorunlar meydana gelir. Ayrıca, bulut altyapısı ve donanımı, geçici kapalı kalma süresi için fırsatları artıran "değiştirilebilir". Aynı zamanda, iç bulut özellikleri ve dayanıklılık ve otomatik kurtarma uygulayan bazı uygulama geliştirme teknikleri, buluttaki beklenmedik hatalardan kurtulmayı çok daha kolay hale getirir.

- **Uygulama performansına daha derin Öngörüler**. Azure Application Insights gibi bulut izleme araçları, sistem durumu yönetimi, günlüğe kaydetme ve bildirimler için görselleştirme sağlar. Denetim günlükleri, uygulamaların hata ayıklamayı ve denetlenmesini, güvenilir bir bulut uygulaması için temel hale getirme işlemlerini kolaylaştırır.

- **Çevik dağıtımlar Ile uygulama taşınabilirliği**. Kapsayıcılar (Docker altyapısını temel alan Linux veya Windows kapsayıcıları), bulut kilitli bir uygulamanın önünden kaçınmak için en iyi çözümü sunmaktadır. Kapsayıcıları, Docker konaklarını ve çok bulut düzenleyicilerinden birini kullanarak bir ortamdan veya buluttan diğerine kolayca geçebilirsiniz. Kapsayıcılar, genellikle her türlü ortama yönelik dağıtımlarda gerçekleşen, bu işlemi ortadan kaldırır (aşama/test/üretim).

Bu avantajların hepsi son olarak uçtan uca uygulama yaşam döngüleriniz için önemli maliyet indirimleri sağlar.

Aşağıdaki bölümlerde, bu avantajlar daha ayrıntılı olarak açıklanmıştır ve belirli teknolojilere bağlanır.

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](microsoft-technologies-in-cloud-optimized-applications.md)
