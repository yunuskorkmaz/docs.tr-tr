---
title: Cloud Native için aday uygulamalar
description: Bulut Yerel yaklaşımdan hangi tür uygulamaların avantajına yarar olduğunu öğrenin
author: robvet
ms.date: 05/14/2020
ms.openlocfilehash: 8f00633a575dad12b0bc1d5adb83acac03db0659
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160950"
---
# <a name="candidate-apps-for-cloud-native"></a>Cloud Native için aday uygulamalar

Portföyünüzdeki uygulamalara bakın. Bunlardan kaç tane bulut yerel mimari için uygun? Bunların tümü? Belki de misiniz?

Maliyet/avantaj Analizi uygulama, büyük olasılıkla bulut Yerel olması için gereken Hefty fiyat etiketini desteklememe olasılığı vardır. Cloud Native 'in maliyeti, uygulamanın iş değerini aşacak.

Bulut Native için hangi tür bir uygulama aday olabilir?

- İş yeteneklerini/özelliklerini sürekli olarak gelişmesi gereken Stratejik Kurumsal Sistem

- Yüksek bir sürüm hızı gerektiren ve yüksek güvenle bir uygulama

- Tüm sistemin tam yeniden dağıtımı *olmadan* tek tek özelliklerin yayımlanması gereken bir sistem

- Farklı teknoloji yığınlarında uzmanlığa sahip takımlar tarafından geliştirilen bir uygulama

- Bağımsız olarak ölçeklendirilmesi gereken bileşenlere sahip bir uygulama

Ardından eski sistemler vardır. Yeni uygulamalar oluşturmak istiyoruz, ancak iş için kritik olan eski iş yüklerini modernleştirmekten genellikle sorumlu veriyoruz. Zaman içinde, eski bir uygulama mikro hizmetlere, Kapsayıcılı ve sonunda "replatbiçimlendirilmiş" bir bulutta yerel mimariye ayrılabilir.

### <a name="modernizing-legacy-apps"></a>Eski uygulamaları modernleştiriliyor

[Azure bulut ve Windows kapsayıcıları ile](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) ücretsiz Microsoft e-book modernleştirin mevcut .NET uygulamaları, şirket içi iş yüklerini buluta geçirmeye yönelik yönergeler sağlar. Şekil 1-10, eski uygulamaların modernleştirilmesi için tek, tek boyutlu uygun bir strateji olmadığını gösterir.

![Eski iş yüklerini geçirme stratejileri](./media/strategies-for-migrating-legacy-workloads.png)

**Şekil 1-10**. Eski iş yüklerini geçirme stratejileri

Kritik olmayan tek parçalı uygulamalar hızlı bir kaldırma ve kaydırma ([bulut altyapıya](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)yönelik) geçiş işleminden büyük ölçüde avantaj sağlıyor. Burada, şirket içi iş yükü, hiçbir değişiklik yapılmadan bulut tabanlı bir VM 'de yeniden barındırılır. Bu yaklaşım [IaaS (hizmet olarak altyapı) modeli](https://azure.microsoft.com/overview/what-is-iaas/)kullanır. Azure, böyle bir taşımanın daha kolay olması için [Azure geçişi](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)ve [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/) gibi çeşitli araçlar içerir. Bu strateji bazı maliyet tasarrufu sağlayabilir, ancak bu gibi uygulamalar genellikle kilit açma ve bulut bilgi işlemin avantajlarından faydalanmayı sanallaştırmıştır.

İş açısından kritik öneme sahip tek parçalı uygulamalar, gelişmiş bir kaldırma ve kaydırma (*buluta iyileştirilmiş*) geçişinden faydalanır. Bu yaklaşım, uygulamanın çekirdek mimarisini değiştirmeden anahtar bulut hizmetlerini etkinleştiren dağıtım iyileştirmelerini içerir. Örneğin [, uygulamayı](/virtualization/windowscontainers/about/) kapsayıcınıza ve bu kitabın ilerleyen kısımlarında açıklanan [Azure Kubernetes Hizmetleri](https://azure.microsoft.com/services/kubernetes-service/)gibi bir kapsayıcı Orchestrator 'a dağıtırsınız. Bulutta, uygulama veritabanları, ileti kuyrukları, izleme ve dağıtılmış önbelleğe alma gibi diğer bulut hizmetlerini tüketebilir.

Son olarak, Stratejik Kurumsal işlevleri gerçekleştiren tek parçalı uygulamalar, bu kitabın konusu olan bir *bulutta yerel* yaklaşımdan en iyi şekilde faydalanabilir. Bu yaklaşım, çeviklik ve hız sağlar. Ancak, kod yeniden oluşturma, yeniden mimari işleme ve kodu yeniden yazma maliyetlerine gelir.

Siz ve takımınız, buluta özgü bir yaklaşıma uygun olduğunu düşünüyorsanız, bu kararı kuruluşunuzla kararlaşmanızı behooves. Bulutta yerel yaklaşımın hangi iş sorununa göre çözülecektir? İş ihtiyaçları nasıl hizalanır?

- Artırılmış güvenle özelliklerin hızlı sürümleri mı?

- Hassas ölçeklenebilirlik-kaynakların daha verimli kullanımı

- Geliştirilmiş sistem dayanıklılığı?

- Sistem performansı iyileştirildi mi?

- İşlemlere daha fazla görünürlük mı?

- İş için en iyi araca ulaşmak üzere geliştirme platformları ve veri depoları Blend?

- Gelecekteki uygulama yatırımı

Doğru geçiş stratejisi, kuruluşunuzun önceliklerine ve hedeflediğiniz sistemlere bağlıdır. Çoğu için, tek parçalı bir uygulamayı en iyi duruma getirmeyi veya N katmanlı bir uygulamaya kaba hizmetler eklemeyi daha fazla maliyetli olabilir. Bu gibi durumlarda, Azure App Service tarafından sunulan bulut PaaS yeteneklerini de tamamen kullanabilirsiniz.

## <a name="summary"></a>Özet

Bu bölümde, bulutta yerel bilgi işlem tanıtıldık. Bulut Yerel uygulamasını hedefleyen anahtar özellikleri ile birlikte bir tanım sağladık. Bu yatırım ve çabayı göz ardı edebilir uygulama türlerine baktık.

Bu konuda daha ayrıntılı bilgi edinmek için artık Cloud Native 'e çok daha ayrıntılı bir bakış sunuyoruz.

### <a name="references"></a>Başvurular

- [Bulut Yerel Bilgi Işlem altyapısı](https://www.cncf.io/)

- [.NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Bir Davis 'e göre bulutta yerel desenler](https://www.manning.com/books/cloud-native-patterns)

- [On Iki öğeli uygulamanın ötesinde](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Kod olarak altyapı nedir?](/azure/devops/learn/what-is-infrastructure-as-code)

- [Uıber mühendisin mikro dağıtımı: her gün güvenle dağıtım](https://eng.uber.com/micro-deploy/)

- [Netflix kodu dağıtır](https://www.infoq.com/news/2013/06/netflix/)

- [WeChat mikro hizmetlerini ölçeklendirmeye yönelik aşırı yükleme denetimi](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Önceki](definition.md) 
> [Sonraki](introduce-eshoponcontainers-reference-app.md)
