---
title: Bulut için iyileştirilmiş uygulamalar için var olan .NET uygulamalarını modernleştirme nedenleri
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Bulut için iyileştirilmiş uygulamalar için var olan .NET uygulamalarını modernleştirme nedenleri
ms.date: 04/28/2018
ms.openlocfilehash: e09d8066e883aaef55408336e3817158e2c14be6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639055"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Bulut için iyileştirilmiş uygulamalar için var olan .NET uygulamalarını modernleştirme nedenleri

Bulut için iyileştirilmiş bir uygulama ile müşterilerinize güvenilir uygulamaları hızla ve sürekli olarak sunabilirsiniz. Temel çevikliği ve güvenilirlik platforma uygulamanızın işletimsel karmaşıklığın çoğunu erteleyerek elde edin.

Uygulamanızı gönderin zamanında hızla pazara uygulamalarınızı erişemiyorsanız hedefleyen Pazar göstermiştir. Ne kadar iyi uygulamayı desteklemesi için tasarlanmış veya ne olursa olsun çok geç olabilir. Başarısız veya uygulama teslimini Pazar ihtiyaçlarını eşitleme yapılamıyor çünkü tam potansiyelinize ulaşmak değil.

Gereken iş sürekli yenilik için geliştirme ve işlem ekipleri için sınır iter. Sürekli işinizde yeniliği gereksinim duyduğunuz çeviklik elde etmek için yalnızca kapsayıcılar ve bulut için iyileştirilmiş belirli bir uygulama ilkeleri gibi teknolojiler ile uygulamalarınız bir hale getirerek yoludur.

İşin özü oluştururken bir kuruluş bulut için iyileştirilmiş olan uygulamaları yönetir ve bu çözümleri müşterilerin daha çabuk ulaştırın ve yeni fikirler, ilgili oldukları zaman pazara Getir olmasıdır.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Bulut için iyileştirilmiş uygulama ilkeleri ve İlkesi 

Bulutta geliştirmeleri çoğunlukla iki hedeflerimize üzerinde odaklanır: Maliyetleri azaltmak ve çeviklik geliştirerek büyütmeye geliştirin. Bu hedefleri süreçlerini basitleştirir ve serbest bırakın ve uygulamalar gönderin, uyuşmazlığı azaltarak elde edilir.

Bulut iyileştirilmiş can, Çevik bir şekilde-diğer şirket içi uygulamalardan otonom olarak uygulamanızı geliştirin ve ardından serbest bırakın, otomatik ölçeklendirme, dağıtırsanız, uygulama izleme ve bulutta uygulama sorunlarını giderme.

Anahtar *çevikliği*. Tüm dağıtım geliştirmeden üretime kadar bir mutlak en aza indirmek sürece çeviklikle yollanamaz ve geliştirme/test ortamı sorunlarını. Kapsayıcılar (özellikle, Docker, pratikte bir standart olarak) ve yönetilen hizmetler, özellikle bu amaç için tasarlanmıştır.

Çeviklik elde etmek için de bulutta ölçeklenebilir platformları için yayın CI/CD işlem hatları temel alan otomatik DevOps süreçlerini gerekir. Ölçeklenebilir ve esnek bulut Platformu (örneğin, Azure App Service, Azure Service Fabric veya Azure Kubernetes hizmeti) dağıtmak CI/CD platformları (örneğin, Azure DevOps Services veya Jenkins'i) bulut çevikliği elde etmek için anahtar teknolojilerdir.

Aşağıdaki listede, ana sacayakları veya Bulut için iyileştirilmiş uygulamalarına yönelik yöntemler açıklanmaktadır. Tümünün veya yalnızca bu kurallara aşamalı ya da artımlı bir yaklaşım benimseyebilirsiniz dikkat edin:

- **Kapsayıcıları**. Kapsayıcılar uygulama ile uygulamanın bağımlılıkları içerecek şekilde yüklemenizi sağlar. Kapsayıcı, üretim ortamlarına dağıtmak ya da hazırlık ortamı test karşılaşabileceğiniz sorunların sayısını önemli ölçüde azaltır. Sonuç olarak, kapsayıcılar, uygulama tesliminin çevikliği geliştiriyor.

- **Dayanıklı ve ölçeklenebilir bulut**. Bulut, yönetilen, esnek, ölçeklenebilir ve dayanıklı bir platform sunar. Bu özellikleri, maliyeti geliştirmeleri kazanmak ve yüksek oranda kullanılabilir ve güvenilir uygulamaları bir sürekli teslim, teslim etmek zorunludur. Yönetilen, yönetilen bir veritabanı gibi yönetilen Hizmetleri önbellek hizmeti (CaaS) ve yönetilen depolama, uygulamanızın bakım maliyetlerini ortadan kaldırılmasına, temel parçaları olarak.

- **İzleme**. Özel durumları ve uygulama performası sorunlarını algılamak ve tanılamak için iyi bir yol olmadan güvenilir bir uygulama sahip olamaz. Uygulama performansı yönetimi ve anında analiz eyleme dönüştürülebilir Öngörüler elde edin gerekir.

- **DevOps kültürü ve sürekli teslim**. DevOps uygulamaları benimsemek takımlar artık bağımsız siloları içinde çalıştığı kültürel bir değişiklik gerektirir. CI/CD işlem hatları, yalnızca geliştirme ve BT işlem ekipleri, kapsayıcılar ve CI/CD araçları tarafından desteklenen arasında artan bir işbirliği olduğunda mümkündür.

Şekil 4-2, bulut için iyileştirilmiş bir uygulama, ana isteğe bağlı yapı taşına gösterir. Daha fazla yapı taşları uygulamanız, uygulamanızın, müşterilerinizin beklentilerini karşılamak başarılı olması için readier olur.

> ![Bir bulut için iyileştirilmiş uygulamasının temel yapı taşları](./media/image2.png)
>
> **Şekil 4-2.** Bir bulut için iyileştirilmiş uygulamasının temel yapı taşları

Özetlemek gerekirse, bulut için iyileştirilmiş bir uygulama modeli, kapsayıcılar, yönetilen bir bulut altyapısı, dayanıklı uygulama teknikler birleşimini kullanırken bulut faydalanan oluşturmak ve uygulamaları yönetmek için bir yaklaşımdır, İzleme, sürekli teslim ve Devops'a, tüm yeniden oluşturma ve mevcut uygulamalarınızı recode gerek kalmadan.

Kuruluşunuz kademeli olarak bu teknolojiler ve yaklaşım benimseyebilirsiniz. Tümünün, aynı anda benimsemek zorunda değilsiniz. Kurumsal öncelikleri ve kullanıcı gereksinimlerine bağlı olarak kademeli olarak benimseyebilirsiniz.

## <a name="benefits-of-a-cloud-optimized-application"></a>Bulut için iyileştirilmiş bir uygulama avantajları

Bulut için iyileştirilmiş bir uygulama mevcut bir uygulamaya (bütçeden veya kodlama olmadan) dönüştürme aşağıdaki faydaları elde edebilirsiniz:

- **Düşük maliyet, bulut sağlayıcısı tarafından yönetilen altyapı işlendiğinden**. Uygulamaları bulut için iyileştirilmiş, bulutun kullanıma hazır esneklik, otomatik ölçeklendirme ve yüksek kullanılabilirlik kullanarak bulut avantajlarından yararlanın. Avantajları, yalnızca işlem özelliklerine (VM'ler ve kapsayıcılar) ilişkilidir, ancak bulut kaynaklarında de bağlı DBaaS, CaaS ve herhangi bir altyapının gibi bir uygulama gerekli.

- **Dayanıklı uygulama ve altyapı**. Buluta geçirirken, geçici hataları Kucak gerekir; bulutta hataları meydana gelir. Ayrıca, bulut altyapısından ve donanım "değiştirilebilir," geçici kapalı kalma süresi için fırsatlar artıran kullanılabilir. Aynı zamanda, iç bulut özellikleri ve uygulama dayanıklılığı ve kurtarmayı belirli uygulama geliştirme teknikleri bulutta beklenmeyen hatalardan kurtarmak çok kolay hale getirmek.

- **Uygulama performansını daha ayrıntılı Öngörüler**. Azure Application Insights görselleştirme için sistem durumu yönetimi, günlüğe kaydetme ve bildirimleri sağlamak gibi izleme araçları bulut. Denetim günlükleri uygulamaları hata ayıklama ve denetim, güvenilir bulut uygulaması için temel kolaylaştırır.

- **Çevik dağıtımları olan uygulama taşınabilirliğini**. Kapsayıcılar (Docker altyapısını temel alan Linux veya Windows kapsayıcıları) bulut kilitli bir uygulama önlemenin en iyi çözümü sunar. Kapsayıcılar, Docker ana bilgisayarları ve çoklu bulut düzenleyicileri kullanarak kolayca bir ortamdan taşıma veya başka bir bulut. Kapsayıcılar genellikle herhangi bir ortam (aşama/test/üretim) dağıtımları oluşan ayırmamıza ortadan kaldırır.

Tüm avantajlar, uçtan uca uygulama yaşam döngünüz için önemli maliyet indirimleri sonuçta sağlayın.

Aşağıdaki bölümlerde, bu avantajlar daha ayrıntılı olarak açıklanmıştır ve belirli teknolojileri için bağlı olmaz.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](microsoft-technologies-in-cloud-optimized-applications.md)
