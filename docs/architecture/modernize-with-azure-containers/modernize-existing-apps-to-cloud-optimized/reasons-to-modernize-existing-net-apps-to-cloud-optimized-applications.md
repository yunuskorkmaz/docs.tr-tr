---
title: Mevcut .NET uygulamalarını buluta Iyileştirilmiş uygulamalarla modernleştirin nedenleri
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Mevcut .NET uygulamalarını buluta Iyileştirilmiş uygulamalarla modernleştirin nedenleri
ms.date: 04/28/2018
ms.openlocfilehash: 3154f9a9e11b42330fcc753ffd961316e4ada335
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522921"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Mevcut .NET uygulamalarını buluta Iyileştirilmiş uygulamalarla modernleştirin nedenleri

Buluta Iyileştirilmiş bir uygulamayla, müşterilerinize hızlı ve sürekli olarak güvenilir uygulamalar gönderebilirsiniz. Uygulamanızın işlemsel karmaşıklığını çok fazla erteleyerek önemli çeviklik ve güvenilirlik elde edersiniz.

Uygulamalarınızın hızla pazara sunabilmenize izin alamazsanız, uygulamanızı sevk etmeniz sırasında hedeflediğiniz Pazar gelişmiş olacaktır. Uygulamanın ne kadar iyi bir şekilde tasarlanmış veya uygulanan ne kadar iyi olduğuna bakılmaksızın, çok geç olabilirsiniz. Market ihtiyaçlarına göre uygulama dağıtımını eşitleyemediği için, başarısız olabilir veya tam potansiyeline ulaşamıyoruz.

Sürekli iş yeniliği gereksinimi, geliştirme ve operasyon ekiplerini limite gönderir. Sürekli iş yeniliği için ihtiyaç duyduğunuz çevikliği elde etmenin tek yolu, uygulamalarınızı kapsayıcılar gibi teknolojiler ve bulut için Iyileştirilmiş belirli uygulama ilkeleri ile modernleştirmelidir.

En alttaki satır, bir kuruluşun bulut için optimize edilmiş uygulamaları oluşturup yönettiğine göre, çözümleri daha önce müşterilere yerleştirebilir ve ilgili olduklarında pazara yeni fikirler getirebilir.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Buluta Iyileştirilmiş uygulama ilkeleri ve tenetler 

Buluttaki geliştirmeler genellikle iki hedefi karşılamaya odaklanılmıştır: çevikliği artırarak maliyetleri azaltın ve iş artışını geliştirebilirsiniz. Bu hedefler, uygulamaları serbest bırakma ve sevk ettiğiniz sırada süreçler basitleştirilerek ve uçuşmadan elde edilir.

Uygulamanızı bulutta En Iyi duruma getirilmiş bir şekilde, diğer şirket içi uygulamalardan uygulamanızı olarak çalışabilen geliştirin ve ardından bulutta uygulamanızı serbest bırakma, dağıtma, otomatik ölçeklendirme, izleme ve sorun giderme işlemleri yapabilirsiniz.

Anahtar *çeviklik*. En az bir dağıtım-üretim sorunları ve geliştirme/test ortamı sorunlarını azaltmadığınız müddetçe çevikiyle birlikte gönderim yapamazsınız. Kapsayıcılar (özellikle de bir de standart olarak Docker) ve yönetilen hizmetler bu amaçla özel olarak tasarlanmıştır.

Çeviklik sağlamak için, buluttaki ölçeklenebilir platformları oluşturan CI/CD işlem hatlarını temel alan otomatik DevOps işlemlerine de ihtiyacınız vardır. Ölçeklenebilir ve dayanıklı bir bulut platformuna (Azure App Service ya da Azure Kubernetes hizmeti gibi) dağıtan CI/CD platformları (Azure DevOps Services veya Jenkins gibi), bulutta çeviklik sağlamak için önemli teknolojilerdir.

Aşağıdaki listede, bulutta Iyileştirilmiş uygulamalar için ana taraf veya uygulamalar açıklanmaktadır. Bu ilkelerin tümünü veya yalnızca bazılarını aşamalı veya artımlı bir yaklaşımda benimseyebileceğinizi unutmayın:

- **Kapsayıcılar**. Kapsayıcılar, uygulama bağımlılıklarını uygulamanın kendisiyle birlikte dahil etme olanağı sunar. Kapsayıcılama, üretim ortamlarına dağıtırken veya hazırlama ortamlarında test ettiğinizde karşılaşabileceğiniz sorun sayısını önemli ölçüde azaltır. Son olarak, kapsayıcılar uygulama tesliminin çevikliğini geliştirir.

- Dayanıklı **ve ölçeklenebilir bulut**. Bulut, yönetilen, elastik, ölçeklenebilir ve esnek bir platform sağlar. Bu özellikler, maliyet iyileştirmeleri kazanmak ve sürekli olarak kullanılabilir ve güvenilir uygulamalar elde etmek için temel düzeyde kullanıma sunulmuştur. Yönetilen veritabanları gibi yönetilen hizmetler, bir hizmet olarak yönetilen önbellek (CaaS) ve yönetilen depolama, uygulamanızın bakım maliyetlerini hafifletmesini içinde temel parçalardır.

- **İzleme**. Özel durumları ve uygulama performansı sorunlarını tespit etmek ve tanılamak için iyi bir yöntem olmadan güvenilir bir uygulamanız olamaz. Uygulama performansı yönetimi ve anında analiz aracılığıyla eyleme dönüştürülebilir Öngörüler almanız gerekir.

- **DevOps kültürü ve sürekli teslim**. DevOps uygulamalarını benimseme, takımlarının bağımsız silolarda artık çalışmadıkları kültürel değişikliği gerektirir. CI/CD işlem hatları yalnızca geliştirme ve BT operasyon takımları arasında, kapsayıcılar ve CI/CD araçları tarafından desteklenen bir işbirliği olduğunda mümkündür.

Şekil 4-2, buluta Iyileştirilmiş bir uygulamanın ana isteğe bağlı ananlarına gösterir. Uyguladığınız daha fazla sayıda işlem, müşterilerinizin beklentilerini karşıladığı için uygulamanızın başarılı olması için readier.

![Bir buluta Iyileştirilmiş uygulamanın ana pillerinden oluşan şema.](./media/main-pillars-cloud-optimized-application.png)

**Şekil 4-2.** Bulut için Iyileştirilmiş uygulamanın ana paragraf oluşturma

Özetlemek gerekirse, bulut ile Iyileştirilmiş bir uygulama, bulut bilgi işlem modelinden faydalanan uygulamalar oluşturma ve yönetmeye yönelik bir yaklaşım, bir kapsayıcı birleşimi, yönetilen bulut altyapısı, dayanıklı uygulama teknikleri, izleme, sürekli teslim ve DevOps, mevcut uygulamalarınızın yeniden mimari ve yeniden kodlenmesi gerekmeden.

Kuruluşunuz bu teknolojileri benimseyebileceği gibi, yavaş bir yaklaşımlar alabilir. Hepsi bir kez olmak üzere tümünü tek tek ayraç içine almanız gerekmez. Kurumsal önceliklere ve kullanıcı gereksinimlerine bağlı olarak bunları artımlı olarak benimseyebilirsiniz.

## <a name="benefits-of-a-cloud-optimized-application"></a>Bulut için Iyileştirilmiş uygulamanın avantajları

Mevcut bir uygulamayı buluta Iyileştirilmiş bir uygulamaya dönüştürerek (yeniden mimari veya kodlama yapmadan) aşağıdaki avantajları elde edebilirsiniz:

- **Daha düşük maliyetler, yönetilen altyapı bulut sağlayıcısı tarafından işlenir**. Bulutun En Iyi duruma getirilmiş uygulamalar, bulutun kullanıma hazır esneklik, otomatik ölçeklendirme ve yüksek kullanılabilirlik özelliğini kullanarak bulutun avantajlarını elde edin. Avantajlar yalnızca işlem özelliklerine (VM 'Ler ve kapsayıcılar) değil, aynı zamanda buluttaki kaynaklara da (örneğin, DBaaS, CaaS) ve bir uygulamanın gereksinim duyabileceği herhangi bir altyapıya bağlıdır.

- Dayanıklı **uygulama ve altyapı**. Buluta geçiş yaptığınızda, geçici hatalardan yararlanın; bulutta sorunlar meydana gelir. Ayrıca, bulut altyapısı ve donanımı, geçici kapalı kalma süresi için fırsatları artıran "değiştirilebilir". Aynı zamanda, iç bulut özellikleri ve dayanıklılık ve otomatik kurtarma uygulayan bazı uygulama geliştirme teknikleri, buluttaki beklenmedik hatalardan kurtulmayı çok daha kolay hale getirir.

- **Uygulama performansına daha derin Öngörüler**. Azure Application Insights gibi bulut izleme araçları, sistem durumu yönetimi, günlüğe kaydetme ve bildirimler için görselleştirme sağlar. Denetim günlükleri, uygulamaların hata ayıklamayı ve denetlenmesini, güvenilir bir bulut uygulaması için temel hale getirme işlemlerini kolaylaştırır.

- **Çevik dağıtımlar Ile uygulama taşınabilirliği**. Kapsayıcılar (Docker altyapısını temel alan Linux veya Windows kapsayıcıları), bulut kilitli bir uygulamanın önünden kaçınmak için en iyi çözümü sunmaktadır. Kapsayıcıları, Docker konaklarını ve çok bulut düzenleyicilerinden birini kullanarak bir ortamdan veya buluttan diğerine kolayca geçebilirsiniz. Kapsayıcılar, genellikle her türlü ortama yönelik dağıtımlarda gerçekleşen, bu işlemi ortadan kaldırır (aşama/test/üretim).

Bu avantajların hepsi son olarak uçtan uca uygulama yaşam döngüleriniz için önemli maliyet indirimleri sağlar.

Aşağıdaki bölümlerde, bu avantajlar daha ayrıntılı olarak açıklanmıştır ve belirli teknolojilere bağlanır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](microsoft-technologies-in-cloud-optimized-applications.md)
