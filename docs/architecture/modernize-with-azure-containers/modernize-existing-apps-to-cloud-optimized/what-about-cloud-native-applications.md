---
title: Bulutta Yerel uygulamalar nedir?
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Bulutta yerel uygulamalar hakkında ne olacak?
ms.date: 04/28/2018
ms.openlocfilehash: cf4c3b24a4eeb62ed84a5fccb294b675d38fcc36
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318431"
---
# <a name="what-about-cloud-native-applications"></a>Bulutta Yerel uygulamalar nedir?

[Bulutta yerel](https://azure.microsoft.com/overview/cloudnative/) uygulamalar bu kılavuzun ana odağa sahip olmasa da, bu modernleştirme vade düzeyinin anlaşılmasında ve buluta iyileştirilmiş uygulamalardan ayırt edilebilmesi yararlı olur.

Şekil 4-3, uygulama içindeki bulutta yerel uygulamaların yer aldığı konumları konumlandırır.

![Bulutta yerel uygulamaların nasıl konumlandıralınacağını gösteren diyagram.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Şekil 4-3.** Bulutta yerel uygulamaları konumlandırma

Bulut Yerel modernleştirme vade düzeyi genellikle yeni geliştirme yatırımları gerektirir. Bulutta yerel düzeye geçiş, genellikle, bağımsız olarak dağıtılabilecek ve ölçeklendirilebilen otonom alt sistemler (mikro hizmetler) oluşturarak büyük uygulamalardaki ölçeği büyük ölçüde artırmak için iş gereği tarafından dağıtılır uygulamanın diğer alanlarından, uzun vadede maliyetleri düşürürken ve bu otonom uygulamanın önemli rekabet avantajları sağlayan parçalarının artmasını artırma.

Bulutta yerel uygulamaların başlıca temel değerleri, çeviklik ile gelişebilir ve şirket içi ya da buluta dağıtılan tek parçalı bir mimariye ulaşmak zor olan sınırlara göre ölçeklenebilen mikro hizmetler mimari yaklaşımlarına dayalıdır ortamınızın.

Şekil 4-4, bulut Yerel modelinin ana özelliklerini gösterir.

![Ana bulut Yerel özelliklerinin listelendiği diyagram.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Şekil 4-4.** Bulutta yerel özellikler

Ayrıca, yapay zeka (AI), Machine Learning (ML) ve IoT gibi diğer hizmetleri ekleyerek temel Modern Web uygulamalarını ve bulutta yerel uygulamaları genişletebilirsiniz. Bulut için Iyileştirilmiş olası yaklaşımlardan herhangi birini genişletmek için bu hizmetlerden herhangi birini kullanabilirsiniz.

Bulutta yerel düzeydeki uygulamalardaki temel fark, uygulama mimarisidir. Bulutta yerel uygulamalar, mikro hizmetlere dayalı uygulamalar tanımına göre yapılır. Bulutta yerel uygulamalar, tek parçalı bir Web uygulamasıyla veya geleneksel N katmanlı bir uygulamayla karşılaştırıldığında özel mimariler, teknolojiler ve platformlar gerektirir.

## <a name="cloud-native-applications-details"></a>Bulutta yerel uygulamalar ayrıntıları

Cloud-Native, büyük ve görev açısından kritik uygulamalar için daha gelişmiş veya yetişkin bir durumdur. Bulutta yerel uygulamalar genellikle mevcut uygulamaları modernleştirerek değil, sıfırdan oluşturulan mimari ve tasarım gerektirir. Bulutta yerel bir uygulama ile daha basit bir buluta Iyileştirilmiş Web uygulaması arasındaki önemli fark, mikro hizmet mimarilerini bulutta yerel bir yaklaşımda kullanmanın önerisine sahiptir. Bulut için Iyileştirilmiş uygulamalar, tek parçalı Web uygulamaları veya N katmanlı uygulamalar da olabilir.

[On Iki öğeli](https://12factor.net/) uygulama (mikro hizmetler yaklaşımının yakından ilişkili desenlerinin bir koleksiyonu), bulut Yerel uygulama mimarileri için de gereksinim olarak kabul edilir.

[Bulut Yerel Bilgi Işlem altyapısı (CNCF)](https://www.cncf.io/) , bulutta yerel ilkelerin birincil promokdır. Microsoft, [CNCF 'nin bir üyesidir](https://azure.microsoft.com/blog/announcing-cncf/).

Örnek bir tanım ve bulut Yerel uygulamalarının özellikleri hakkında daha fazla bilgi için bkz. Gartner, [bulutta yerel uygulamaları mimari ve tasarlama](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Microsoft 'un bulut Yerel uygulamasının nasıl uygulanacağı hakkında belirli yönergeler için bkz. [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://aka.ms/microservicesebook).

Tam bir uygulamayı bulutta yerel modele geçirdiğinizde göz önünde bulundurmanız gereken en önemli faktör, mikro hizmet tabanlı bir mimariye yeniden mimarinizin olması gerekir. Bu, ilgili büyük yeniden düzenleme süreci nedeniyle geliştirmede önemli bir yatırım gerektirir. Bu seçenek genellikle yeni ölçeklenebilirlik düzeyi ve uzun süreli çeviklik gerektiren görev açısından kritik uygulamalar için seçilir. Ancak, yalnızca birkaç yeni senaryo için mikro hizmetler ekleyerek buluta yerel olarak taşımaya başlayabilir ve sonunda uygulamayı mikro hizmet olarak tamamen yeniden düzenleyin. Bu, bazı senaryolar için en iyi seçenek olan artımlı bir yaklaşımdır.

## <a name="what-about-microservices"></a>Mikro hizmetler hakkında ne var?

Mikro hizmetleri ve bunların nasıl çalıştığını anlamak, kuruluşunuz için bulutta yerel uygulamalar düşünürken önem taşımaktadır.

Mikro hizmet mimarisi, sıfırdan oluşturulan veya bulut Yerel uygulamalarına yönelik mevcut uygulamaları geliştirmiş olduğunuz uygulamalar için kullanabileceğiniz gelişmiş bir yaklaşımdır. Yeni mikro hizmetler paradigmalarına hakkında bilgi edinmek için mevcut uygulamalara birkaç mikro hizmet ekleyerek başlayabilirsiniz. Ancak, özellikle de bu tür mimari yaklaşım için mimariyi ve kodlabilmeniz gerekir.

Ancak, mikro hizmetler yeni veya modern uygulamalar için zorunlu değildir. Mikro hizmetler bir "sihirli madde işareti" değil, her uygulamayı oluşturmanın tek ve en iyi yolu değildir. Mikro hizmetleri nasıl ve ne zaman kullanacağınızı oluşturmanız gereken uygulama türüne bağlıdır.

Mikro hizmetler mimarisi, özerk hizmetler biçiminde birden çok bağımsız alt sistemi temel alan dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen yaklaşım haline geliyor. Mikro hizmet tabanlı bir mimaride, bir uygulama bağımsız olarak geliştirilen, test edilmiş, sürümlü, dağıtılan ve ölçeklendirilen bir hizmetler koleksiyonu olarak oluşturulur. Bu, mikro hizmet başına herhangi bir ilgili, özerk veritabanı içerebilir.

.NET Core kullanarak uygulayabileceğiniz mikro hizmetler mimarisine ayrıntılı bir bakış için bkz. indirilebilir PDF e-book [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://aka.ms/microservicesebook). Kılavuz ayrıca [çevrimiçi](../../microservices/index.md)olarak da kullanılabilir.

Ayrıca, mikro hizmetlerin güçlü yetenekler bağımsız dağıtım, güçlü alt sistem sınırları ve teknoloji çeşitlemesi sunabileceği senaryolarda bile, birçok yeni zorluk da daha da çalışırlar. Sorunlar, parçalanmış ve bağımsız veri modelleri gibi dağıtılmış uygulama geliştirmeyle ilgilidir; Mikro hizmetler arasında esnek iletişim sağlama; nihai tutarlılık gereksinimi; ve işlemsel karmaşıklık. Mikro hizmetler geleneksel tek parçalı uygulamalar ile karşılaştırıldığında daha yüksek düzeyde karmaşıklığa sahiptir.

Mikro hizmetler mimarisinin karmaşıklığı nedeniyle, mikro hizmet tabanlı uygulamalar için yalnızca belirli senaryolar ve belirli uygulama türleri uygundur. Bunlar, birden çok, gelişen alt sistemi olan büyük ve karmaşık uygulamaları içerir. Bu gibi durumlarda, uzun süreli çevikliği ve daha verimli uygulama bakımı için daha karmaşık bir yazılım mimarisine yatırım harcamıştır. Ancak, daha az karmaşık senaryolar için tek parçalı bir uygulama yaklaşımına veya daha basit N katmanlı yaklaşımla devam etmek daha iyi olabilir.

Son bir notta, bu kavram hakkında tekrarlanabilecek risklere bile, uygulamalarınızda "hepsi veya hiçbir şey yok" gibi mikro hizmetleri kullanma konusuna bakmamanız gerekir. Mikro hizmetlere dayalı yeni, küçük senaryolar ekleyerek mevcut tek parçalı uygulamaları genişletebilir ve geliştirebilirsiniz. Mikro hizmet mimarisi yaklaşımıyla çalışmaya başlamak için sıfırdan başlamanız gerekmez. Aslında, yeni senaryolar ekleyerek mevcut bir monoparçalı veya N katmanlı uygulamayı kullanmayı öneririz. Sonuç olarak, uygulamayı otonom bileşenlere veya mikro hizmetlere kesebilirsiniz. Tek parçalı uygulamalarınızı, bir mikro hizmet yönünde, adım adım ' da gelişen şekilde başlatabilirsiniz.

Herhangi bir durumda, bu kılavuz genellikle tek parçalı veya N katmanlı mimarilere sahip olan mevcut uygulamaların modernisini hedeflediğinden, bu mevcut yönergelerin geri kalanı tüm "mikro hizmet tabanlı uygulamalar yok" kısmında odaklanır.

> [!div class="step-by-step"]
> [Önceki](microsoft-technologies-in-cloud-optimized-applications.md)
> [İleri](deploy-existing-net-apps-as-windows-containers.md)
