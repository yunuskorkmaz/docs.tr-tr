---
title: Bulut yerel için aday uygulamalar
description: Bulut ayarı olan bir yaklaşımdan hangi tür uygulamaların yararlandığını öğrenin
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805616"
---
# <a name="candidate-apps-for-cloud-native"></a>Bulut yerel için aday uygulamalar

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Portföyünüzdeki uygulamalara bakın. Kaç tanesi bulut-yerel mimari için uygun? Bunların tümü? Belki biraz?

Maliyet/fayda çözümlemesi uygulayarak, çoğu bulut yerel olması için gerekli ağır fiyat etiketini desteklemez iyi bir şans var. Bulut yerel olmanın maliyeti, uygulamanın iş değerini çok aşar.

Bulut yerel için ne tür bir uygulama adayı olabilir?

- Sürekli iş yetenekleri / özellikleri geliştirmek için gereken büyük, stratejik kurumsal sistem

- Yüksek serbest bırakma hızı gerektiren bir uygulama - yüksek güven ile

- Tüm sistemin tam olarak yeniden dağıtılması *olmadan* tek tek özelliklerin serbest bırakılması gereken bir sistem

- Farklı teknoloji yığınlarında uzman ekipler tarafından geliştirilen bir uygulama

- Bağımsız ölçeklendirmesi gereken bileşenlere sahip bir uygulama

Bir de eski sistemler var. Hepimiz yeni uygulamalar oluşturmak isterken, genellikle işletme için kritik öneme sahip eski iş yüklerini modernize etmekle yükümlüyuz. Zaman içinde, eski bir uygulama mikro hizmetlere ayrıştırılabilir, konteynerlenebilir ve sonuçta bulut-yerel mimariye "yeniden platformlaştırılabilir".

### <a name="modernizing-legacy-apps"></a>Eski uygulamaları modernize etme

Ücretsiz Microsoft e-kitap [Azure bulutu ve Windows Kapsayıcıları ile mevcut .NET uygulamalarını](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) modernleştirin, şirket içi iş yüklerini buluta geçirmek için kılavuz sağlar. Şekil 1-10, eski uygulamaları modernize etmek için tek, tek boyutlu bir strateji olmadığını gösterir.

![Eski iş yüklerini geçirme stratejileri](./media/strategies-for-migrating-legacy-workloads.png)

**Şekil 1-10**. Eski iş yüklerini geçirme stratejileri

Kritik olmayan monolitik uygulamalar büyük ölçüde hızlı kaldırma ve kaydırma[(Bulut Altyapısına Hazır)](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)geçişinden yararlanır. Burada, şirket içi iş yükü, herhangi bir değişiklik olmaksızın bulut tabanlı bir VM'ye yeniden barındırılır. Bu yaklaşım, [IaaS (Hizmet Olarak Altyapı) modelini](https://azure.microsoft.com/overview/what-is-iaas/)kullanır. Azure, böyle bir hareketi kolaylaştırmak için [Azure Geçiş,](https://azure.microsoft.com/services/azure-migrate/) [Azure Site Kurtarma](https://azure.microsoft.com/services/site-recovery/)ve Azure Veritabanı Geçiş [Hizmeti](https://azure.microsoft.com/campaigns/database-migration/) gibi çeşitli araçları içerir. Bu strateji bazı maliyet tasarrufları sağlayabilir ken, bu tür uygulamalar genellikle bulut bilgi işlemin avantajlarının kilidini açmak ve bunlardan yararlanmak için tasarlanmadı.

İşletme için kritik öneme sahip monolitik uygulamalar, gelişmiş kaldırma ve kaydırma *(Bulut Optimize Edilmiş)* geçişinden çoğu zaman yararlanır. Bu yaklaşım, uygulamanın temel mimarisini değiştirmeden anahtar bulut hizmetlerini etkinleştiren dağıtım optimizasyonlarını içerir. Örneğin, uygulamayı [kapsayıcı hale](https://docs.microsoft.com/virtualization/windowscontainers/about/) getirebilir ve bu kitapta daha sonra tartışılan [Azure Kubernetes Hizmetleri](https://azure.microsoft.com/services/kubernetes-service/)gibi bir kapsayıcı orkestratöre dağıtabilirsiniz. Buluta girdikten sonra, uygulama veritabanları, ileti kuyrukları, izleme ve dağıtılmış önbelleğe alma gibi diğer bulut hizmetlerini tüketebilir.

Son olarak, stratejik kurumsal işlevleri gerçekleştiren yekpare uygulamalar, bu kitabın konusu olan *Bulut-Yerel* yaklaşımından en iyi şekilde yararlanabilir. Bu yaklaşım çeviklik ve hız sağlar. Ancak, yeniden platformlama, yeniden architectyon ve kod yeniden yazma bir maliyetle gelir.

Siz ve ekibiniz bulut ait bir yaklaşımın uygun olduğuna inanıyorsanız, kararı kuruluşunuzla birlikte mantıklı hale getirmek size yakıştırılır. Bulut-yerel bir yaklaşımın çözeceği iş sorunu tam olarak nedir? İş ihtiyaçlarıyla nasıl uyumlu olacak?

- Artan güven ile özellikleri hızlı bültenleri?

- İnce taneli ölçeklenebilirlik - kaynakların daha verimli kullanımı?

- Geliştirilmiş sistem esnekliği?

- Geliştirilmiş sistem performansı?

- Operasyonlarda daha fazla görünürlük mü?

- İş için en iyi araca ulaşmak için geliştirme platformlarını ve veri depolarını harmanlamak mı?

- Geleceğe dönük uygulama yatırımı mı?

Doğru geçiş stratejisi, kuruluş önceliklerine ve hedeflediğiniz sistemlere bağlıdır. Birçokları için, yekpare bir uygulamayı buluta optimize etmek veya bir N-Tier uygulamasına kaba taneli hizmetler eklemek daha uygun maliyetli olabilir. Bu gibi durumlarda, Azure Uygulama Hizmeti tarafından sunulanlar gibi bulut PaaS özelliklerinden tam olarak yararlanabilirsiniz.

## <a name="summary"></a>Özet

Bu bölümde, bulut-yerli bilgi işlem tanıttı. Bulut ayarı yapan bir uygulamayı yönlendiren temel özelliklerle birlikte bir tanım sağladık. Bu yatırımı ve çabayı haklı çıkaracak uygulama türlerine baktık.

Arkadaki girişle birlikte, şimdi bulut anına çok daha ayrıntılı bir bakış atıyoruz.

### <a name="references"></a>Başvurular

- [Cloud Native Computing Foundation](https://www.cncf.io/)

- [.NET Microservices: Containerized .NET uygulamaları için mimari](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Azure bulutu ve Windows Kapsayıcıları ile mevcut .NET uygulamalarını modernize edin](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Cornelia Davis tarafından Cloud Yerli Desenler](https://www.manning.com/books/cloud-native-patterns)

- [On iki Faktörlü Uygulamanın Ötesinde](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [Kod Olarak Altyapı Nedir](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Uber Engineering's Micro Deploy: Günlük Güvenle Dağıtım](https://eng.uber.com/micro-deploy/)

- [Netflix Kodu Nasıl Dağır](https://www.infoq.com/news/2013/06/netflix/)

- [WeChat Microservices Ölçekleme için Aşırı Yük Kontrolü](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Önceki](definition.md)
>[Sonraki](introduce-eshoponcontainers-reference-app.md)
