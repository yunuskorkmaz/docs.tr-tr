---
title: Bulutta Yerel uygulamalar nedir?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Bulut-Yerel uygulamalar ne olacak?
ms.date: 04/28/2018
ms.openlocfilehash: d2a7f89e347d75ddbdae84c8eb57e32447b83297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543553"
---
# <a name="what-about-cloud-native-applications"></a>Bulutta Yerel uygulamalar nedir?

[Bulut-Yerel](https://azure.microsoft.com/overview/cloudnative/) uygulamalar bu kılavuzun ana odak noktası olmasa da, bu modernizasyon olgunluk düzeyini anlamak ve bulut için optimize edilmiş uygulamalardan ayırt etmek yararlı dır.

Şekil 4-3 pozisyonları Uygulama modernizasyon olgunluk düzeylerinde Bulut-Yerel uygulamalar:

![Bulut ait uygulamaların nasıl konumlandırılabildiğini gösteren diyagram.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Şekil 4-3.** Bulut-Yerel uygulamaları konumlandırma

Bulut-Yerel modernizasyon olgunluk düzeyi genellikle yeni geliştirme yatırımları gerektirir. Bulut-Yerel düzeyine geçmek genellikle iş ihtiyaçları tarafından yönlendirilen büyük uygulamalarda büyük ölçekli büyük ölçüde geliştirmek için büyük uygulamalarda büyük ölçekli geliştirmek için dağıtılabilir ve bağımsız ölçeklenebilir özerk alt sistemler (mikro hizmetler) oluşturmak için uygulamanın diğer alanlarından uzun vadede maliyetleri düşürürken ve önemli rekabet avantajları sağlayan bu özerk uygulama parçalarının evrim çevikliğini artırır.

Cloud-Native uygulamalarının temel direkleri, şirket içi veya buluta dağıtılan yekpare bir mimaride elde edilmesi zor olan sınırlara çeviklik ve ölçekle gelişebilen mikro hizmet mimarisi yaklaşımlarına dayanmaktadır. Ortam.

Şekil 4-4, Bulut-Yerel modelinin ana özelliklerini gösterir.

![Ana bulut aadil özelliklerini listeleyen diyagram.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Şekil 4-4.** Bulut-Yerel özellikleri

Buna ek olarak, yapay zeka (AI), makine öğrenimi (ML) ve IoT gibi diğer hizmetleri ekleyerek temel modern web uygulamalarını ve bulut ayarı uygulamaları genişletebilirsiniz. Bu hizmetlerden herhangi birini, bulut için optimize edilmiş olası yaklaşımlardan herhangi birini genişletmek için kullanabilirsiniz.

Bulut-Yerel düzeyindeki uygulamalardaki temel fark, uygulama mimarisindedir. Bulut ait uygulamalar, tanım gereği, mikro hizmetlere dayalı uygulamalardır. Bulut tabanlı uygulamalar, yekpare bir web uygulaması veya geleneksel N-Tier uygulamasıyla karşılaştırıldığında özel mimariler, teknolojiler ve platformlar gerektirir.

## <a name="cloud-native-applications-details"></a>Bulut tabanlı uygulamalar ayrıntıları

Bulut-Yerel büyük ve görev açısından kritik uygulamalar için daha gelişmiş veya olgun bir durumdur. Bulut-Yerel uygulamalar genellikle varolan uygulamaları modernize etmek yerine sıfırdan oluşturulan mimari ve tasarım gerektirir. Bulut-Yerel uygulama ile daha basit bir Bulut Optimize edilmiş web uygulaması arasındaki temel fark, mikro hizmetler mimarilerini bulut ayarı açısından kullanma önerisidir. Bulut için optimize edilmiş uygulamalar, yekpare web uygulamaları veya N-Tier uygulamaları da olabilir.

[On iki faktörlü uygulama](https://12factor.net/) (mikro hizmet yaklaşımları ile yakından ilişkili desenler topluluğu) bulut yerel uygulama mimarileri için bir gereklilik olarak kabul edilir.

[Cloud Native Computing Foundation (CNCF),](https://www.cncf.io/) buluta özgü ilkelerin birincil organizatörüdür. Microsoft [CNCF üyesidir.](https://azure.microsoft.com/blog/announcing-cncf/)

Bulut taşımacılığı uygulamalarının tasarlatımı ve geliştirilen ler hakkında ayrıntılı rehberlik için, ücretsiz e- kitapları okuyun:

* [Azure için Bulut-Yerel .NET Uygulamalarını Temel Alma](../../cloud-native/introduction.md)
* [.NET Microservices: Konteynerleştirilmiş .NET uygulamaları için mimari.](../../microservices/index.md)

Bulut yerel modeline tam bir uygulama geçirtinizin göz önünde bulundurulması gereken en önemli faktör, mikro hizmetler tabanlı bir mimariye yeniden mimarlık yapmak zorunda olduğunuzdur. Bu açıkça ilgili büyük refactoring süreci nedeniyle kalkınma önemli bir yatırım gerektirir. Bu seçenek genellikle ölçeklenebilirlik ve uzun vadeli çeviklik yeni düzeylerde gerektiren görev kritik uygulamalar için seçilir. Ancak, sadece birkaç yeni senaryo için mikro hizmetler ekleyerek bulut yerel doğru hareket başlayabilir ve sonunda tamamen mikro hizmetler olarak uygulama refactor. Bu, bazı senaryolar için en iyi seçenek olan artımlı bir yaklaşımdır.

## <a name="what-about-microservices"></a>Peki ya mikro hizmetler?

Kuruluşunuz için bulut tabanlı uygulamaları düşünürken mikro hizmetleri ve bunların nasıl çalıştığını anlamak önemlidir.

Microservices mimarisi, sıfırdan oluşturulan uygulamalar için veya varolan uygulamaları bulut tabanlı uygulamalara doğru geliştirdiğinizde kullanabileceğiniz gelişmiş bir yaklaşımdır. Yeni mikrohizmetler paradigmaları hakkında bilgi edinmek için mevcut uygulamalara birkaç mikro hizmet ekleyerek başlayabilirsiniz. Ama açıkça, mimari yaklaşım bu tür özellikle, mimar ve kod gerekir.

Ancak, mikro hizmetler herhangi bir yeni veya modern uygulama için zorunlu değildir. Microservices bir "sihirli mermi" değildir ve her uygulamayı oluşturmak için tek, en iyi yol değildir. Mikro hizmetleri nasıl ve ne zaman kullanacağınız, oluşturmanız gereken uygulama türüne bağlıdır.

Mikro hizmetler mimarisi, özerk hizmetler biçiminde birden fazla bağımsız alt sistemi temel alan dağıtılmış ve büyük veya karmaşık görev açısından kritik uygulamalar için tercih edilen bir yaklaşım haline gelmektedir. Mikro hizmetler tabanlı bir mimaride, bir uygulama bağımsız olarak geliştirilebilen, test edilebilen, sürümlendirilebilen, dağıtılabilen ve ölçeklendirilebilen hizmetler topluluğu olarak oluşturulur. Bu, mikro hizmet başına ilgili, özerk veritabanını içerebilir.

.NET Core'u kullanarak uygulayabileceğiniz bir mikrohizmet mimarisine ayrıntılı bir bakış için indirilebilir PDF e-kitap [.NET microservices: Containerized .NET uygulamaları için mimariye](https://aka.ms/microservicesebook)bakın. Kılavuz da [online](../../microservices/index.md)olarak mevcuttur.

Ancak mikro hizmetlerin güçlü yeteneklerden bağımsız dağıtım, güçlü alt sistem sınırları ve teknoloji çeşitliliği sunduğu senaryolarda bile birçok yeni zorluk da gündeme getirmektedir. Zorluklar, parçalanmış ve bağımsız veri modelleri gibi dağıtılmış uygulama geliştirme ile ilgilidir; mikro hizmetler arasında esnek iletişimin sağlanması; nihai tutarlılık için ihtiyaç; ve operasyonel karmaşıklık. Microservices geleneksel monolitik uygulamalara göre daha yüksek bir karmaşıklık düzeyi sunar.

Bir microservices mimarisinin karmaşıklığı nedeniyle, yalnızca belirli senaryolar ve belirli uygulama türleri mikrohizmet tabanlı uygulamalar için uygundur. Bunlar, birden çok, değişen alt sistemlere sahip büyük ve karmaşık uygulamaları içerir. Bu gibi durumlarda, daha uzun vadeli çeviklik ve daha verimli uygulama bakımı için daha karmaşık bir yazılım mimarisine yatırım yapmaya değer. Ancak daha az karmaşık senaryolar için, yekpare bir uygulama yaklaşımı veya daha basit N-Tier yaklaşımları ile devam etmek daha iyi olabilir.

Son bir not olarak, bu kavram hakkında tekrarlayan olma riski bile, uygulamalarınızda mikro hizmetleri kullanarak bakmamalısınız "all-in ya da hiçbir şey." Mikro hizmetlere dayalı yeni, küçük senaryolar ekleyerek varolan yekpare uygulamaları genişletebilir ve geliştirebilirsiniz. Mikro hizmetler mimarisi yaklaşımıyla çalışmaya başlamak için sıfırdan başlamanız gerekmez. Aslında, yeni senaryolar ekleyerek varolan yekpare veya N-Tier uygulamasını kullanarak gelişmenizi öneririz. Sonunda, uygulamayı özerk bileşenlere veya mikro hizmetlere ayırabilirsiniz. Yekpare uygulamalarınızı adım adım mikrohizmetler yönünde gelişmeye başlayabilirsiniz.

Her durumda, bu kılavuzun geri kalanı en çok "mikro hizmet tabanlı uygulamalara" odaklanır, çünkü bu kılavuz esas olarak genellikle yekpare veya N Katmanlı mimarilere sahip mevcut uygulamaların modernizasyonunu hedeflemektedir.

> [!div class="step-by-step"]
> [Önceki](microsoft-technologies-in-cloud-optimized-applications.md)
> [Sonraki](deploy-existing-net-apps-as-windows-containers.md)
