---
title: Mevcut .NET uygulamalarını Windows kapsayıcıları olarak dağıtma
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Mevcut .NET uygulamalarını Windows kapsayıcıları olarak dağıtma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 646acc6fd14c1ff85593dbf6074f0d03d86f04bd
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143766"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Mevcut .NET uygulamalarını Windows kapsayıcıları olarak dağıtma

Windows kapsayıcılarında tabanlı dağıtımlar, uygulamaları bulut için iyileştirilmiş ve bulutta yerel uygulamalar için geçerlidir.

Ancak, bu kılavuzdaki ve özellikle aşağıdaki bölümlerde, çoğunlukla Windows kapsayıcıları için kullanmaya odaklanmıştır *bulut için iyileştirilmiş* uygulamaları burada gerekmeyen uygulamanızı yeniden oluşturma.

## <a name="what-are-containers-linux-or-windows"></a>Kapsayıcıları nelerdir? (Linux veya Windows)

Kapsayıcıları kendi yalıtılmış paket uygulamaya kaydırılmasına bir yoludur. Kapsayıcısı, uygulamalar veya işlemler kapsayıcı dışından mevcut uygulama etkilenmez. Bir işlem kapsayıcısı içinde olduğu gibi her şeyi uygulama çalıştırma açın başarıyla bağlıdır. Her yerde kapsayıcıyı taşınmasını gerektirecek (kitaplık bağımlılıkları, çalışma zamanları vb.) çalıştırmak için gereken her şeyi sunulur çünkü uygulama gereksinimlerini her zaman, doğrudan bağımlılıklar bakımından karşılanır.

Bir kapsayıcının ana özelliği kapsayıcı ihtiyaç duyduğu tüm bağımlılıklarla birlikte geldiğinden, ortamı aynı farklı dağıtımlar arasında yapmasıdır. Uygulamayı makinenizde hata ayıklayın ve ardından başka bir makineye garanti ortamıyla dağıtın.

Bir kapsayıcı, bir kapsayıcı görüntüsü örneğidir. Bir kapsayıcı görüntüsü, bir uygulama veya hizmet (örneğin, bir anlık görüntü) paketini ve ardından güvenilir ve tekrarlanabilir bir şekilde dağıtmak için bir yoldur. Docker yalnızca bir teknoloji-BT bir felsefesi ve işlem kılavuzuna olmadığını diyebilirsiniz.

Kapsayıcıları her gün daha yaygın hale geldikçe bir endüstri genelinde "dağıtım birimidir." gelmektedir

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Kapsayıcılar (Linux veya Windows üzerindeki Docker altyapısı) avantajları

Ve kapsayıcılar kullanılarak uygulamaları oluşturmaya da olabilir çevikliği herhangi bir uygulama çalıştıran herhangi bir altyapıda oluşturma ve aktarma için önemli bir artış tanımlanan basit yapı taşlarını sunar.

Kapsayıcılar ile herhangi bir uygulama geliştirmeden üretime çok az kayıpla veya hiç kod değişikliği, Microsoft Geliştirici Araçları, işletim sistemleri ve bulut arasında Docker tümleştirmesi sayesinde alabilir.

Düz Vm'lere dağıttığınızda, büyük olasılıkla bir yöntem Vm'lerinizi ASP.NET uygulamaları dağıtmak için bir yerde zaten. Ancak, yönteminiz birden çok el ile yapılacak adımlar veya karmaşık otomatik işlemler Puppet gibi bir dağıtım aracı veya benzer bir araç kullanarak içerdiğini, olasıdır. Yapılandırma öğelerini değiştirme, uygulama içeriği sunucular arasında kopyalama ve test ederek ve ardından, .msi kurulumları dayalı etkileşimli kurulum programları çalıştırma gibi görevleri gerçekleştirmek gerekebilir. Bu Dağıtımdaki tüm adımları dağıtımları için zaman ve riske ekleyin. Bir bağımlılık, hedef ortamda mevcut değil. her hatalarıyla karşılaşırsınız.

Windows kapsayıcıları içinde tam olarak uygulama paketleme işlemi otomatik değildir. Windows kapsayıcıları Docker platformu, Otomatik Güncelleştirmeler ve kapsayıcı dağıtımı için geri alma işlemleri sunar temel alır. Docker altyapısı kullanarak alma ana geliştirme ile tüm bağımlılıkları gibi uygulamanızın anlık görüntüleri olan görüntüleri, oluşturduğunuz ' dir. Docker görüntülerini (Windows kapsayıcı görüntüsü, bu durumda) görüntüleridir. Görüntüleri, ASP.NET uygulamaları için kaynak kodu olmadan kapsayıcılarda çalıştırın. Kapsayıcı anlık görüntü dağıtım birimi olur.

Çoğu kuruluş aşağıdaki nedenlerden dolayı mevcut tek yapılı uygulamaları kapsayıcıya alma:

-   **Yayın geliştirilmiş dağıtım yoluyla çeviklik**. Kapsayıcılar, geliştirme ve operasyon arasında tutarlı dağıtım sözleşme sunar. Kapsayıcıları kullandığınızda, geliştiricilerin söyleyin duymazsınız, "Benim makinemde neden üretimde çalışır?" Diyor "üretimde çalışır, bir kapsayıcı olarak çalışır, böylece." İle tüm bağımlılıkları, paketlenmiş bir uygulama, desteklenen tüm kapsayıcı tabanlı ortamda çalıştırılabilir. Tüm dağıtım hedefleri (geliştirme, QA, hazırlama, üretim) çalıştırmak için tasarlanmıştı şekilde çalışacaktır. Dağıtım önemli ölçüde artıran, sonraki bir aşamadan diğerine taşıdığınızda, çoğu frictions kapsayıcıları ortadan kaldırarak kodlama işini daha hızlı gönderin.

-   **İndirimleri maliyet**. Kapsayıcılar, birleştirme ve temizleme donanımdan veya uygulamaları donanım birimi başına daha yüksek yoğunlukta çalışan tarafından ya da maliyetlerini düşürmek için sağlama.

-   **Taşınabilirlik**. Kapsayıcılar, modüler ve taşınabilir. Docker kapsayıcıları, herhangi bir sunucu işletim sistemi (Linux ve Windows), tüm büyük genel bulut (Microsoft Azure, Amazon AWS, Google, IBM) ve şirket içi ve özel veya hibrit bulut ortamlarında desteklenir.

-   **Denetim**. Kapsayıcılar kapsayıcı düzeyinde denetlenir esnek ve güvenli bir ortam sunar. Bir kapsayıcı güvenli, yalıtılmış ve yürütme kısıtlama ilkeleri kapsayıcıdaki ayarlayarak bile sınırlıdır. Windows kapsayıcıları hakkında bölümünde olarak ayrıntılı, Windows Server 2016 ve Hyper-V kapsayıcıları ek kurumsal destek seçenekleri sunar.

Geliştirme ve bakımını yapmanız için kapsayıcılar kullandığınızda önemli geliştirmeler çeviklik, taşınabilirlik ve denetim için önemli maliyet indirimleri sonuçta sağlama.

## <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) olduğu bir [açık kaynaklı proje](https://github.com/docker/docker) bulutta veya şirket içinde çalışan taşınabilir, kendi kendine yeterli kapsayıcı uygulamalarının dağıtımını otomatikleştirir. Docker, ayrıca bir [şirket](https://www.docker.com/) yükseltir ve bu teknoloji geliştikçe. Şirket, bulut, Linux ve Windows sağlayıcılar dahil olmak üzere Microsoft ile işbirliği içinde çalışır.

![](./media/image6.png)

> **Şekil 4-6.** Docker kapsayıcıları tüm katmanlarda karma bulutun dağıtır.

Birine aşina sanal makineler, kapsayıcılar son derece benzer görünebilir. Bir kapsayıcı bir işletim sistemi çalıştıran bir dosya sistemine sahip ve bir fiziksel veya sanal bilgisayar sistemi gibi bir ağ üzerinden erişilebilir. Ancak, teknoloji ve kapsayıcıları kavramları sanal makinelerden büyük ölçüde farklılık gösterir. Bir geliştirici açısından bakıldığında, kapsayıcı daha tek bir işlem gibi Muamele görmelidir. Aslında, tek giriş noktası bir işlem için bir kapsayıcı vardır.

Docker kapsayıcıları (kolaylık *kapsayıcıları*) Linux ve Windows üzerinde yerel olarak çalıştırabilirsiniz. Normal kapsayıcıları çalıştırırken, yalnızca Windows konaklarda (bir konak sunucusu veya bir sanal makine) Windows kapsayıcıları çalıştırabilirsiniz ve Linux kapsayıcıları yalnızca Linux konaklarda çalışabilir. Ancak, Windows Server ve Hyper-V kapsayıcıları son sürümlerinde, bir Linux kapsayıcı da yerel olarak Windows Server üzerinde şu anda yalnızca Windows Server kapsayıcıları kullanılabilir Hyper-V yalıtım teknolojisini kullanarak çalıştırabilirsiniz.

Yakın gelecekte, hem Linux hem de Windows kapsayıcıları olan karma ortamlar, olası ve hatta ortak olacaktır.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Mevcut .NET uygulamalarınız için Windows kapsayıcılarının avantajları

Windows kapsayıcıları kullanmanın avantajları, temelde genel olarak kapsayıcılardan alma aynı yararlar şunlardır. Windows kapsayıcıları çeviklik, taşınabilirlik ve denetimi artırma hakkında önemli ölçüde kullanmaktır.

.NET Framework kullanılarak oluşturulan bu uygulamaları mevcut .NET uygulamalarını bakın. Örneğin, geleneksel ASP.NET web uygulamaları olabilir-bunlar daha yeni olan ve platformlar arası çalışan .NET Core kullanma Linux, Windows ve MacOS üzerinde.

Ana .NET Framework Windows bağımlılığıdır. Ayrıca ikincil bağımlılıkları, IIS ve System.Web gibi geleneksel ASP.NET sahiptir.

Windows üzerinde .NET Framework uygulamasına dönem çalıştırmanız gerekir. Mevcut .NET Framework uygulamalarınızı kapsayıcılı hale getirme istediğiniz ve .NET Core geçişi yatırım istemiyorsanız veya varsa ("düzgün çalışıyorsa, yoksa geçişini,"), kapsayıcılar için sahip tek seçim Windows kapsayıcıları kullanmaktır.

Windows kapsayıcıları, ana avantajlarından biri, bunlar, Windows aracılığıyla, kapsayıcı çalışan mevcut .NET Framework uygulamalarınızı modernize etme bir yol sunar bu nedenle. Sonuç olarak, Windows kapsayıcıları kapsayıcıları çeviklik, taşınabilirlik ve daha iyi denetim kullanarak aradığınız avantajları alır.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Bir işletim sistemi ile hedef seçin. AĞ tabanlı kapsayıcılar

.NET Framework ve .NET Core arasındaki farklar yanı sıra Docker tarafından desteklenen işletim sistemleri yelpazesi göz önünde bulundurulduğunda, belirli bir işletim sistemi ve kullanmakta olduğunuz altyapısını temel alan belirli sürümlerini hedefleyen.

Windows için Windows Server Core veya Windows Nano sunucu kullanabilirsiniz. Bu Windows sürümleri .NET Framework veya .NET Core uygulamalar için gerekli (Kestrel gibi bir şirket içinde barındırılan web sunucusu yerine IIS gibi) farklı özellikleri sağlar.

Linux için birden çok dağıtım paketlerini kullanılabilir ve (Debian gibi) resmi .NET Docker görüntüleri desteklenir.

Şekil 4-7, uygulamanın .NET Framework sürümüne bağlı olarak hedefleyebilen işletim sistemi sürümleri gösterilir.

![](./media/image7.png)

> **Şekil 4-7.** Hedef .NET Framework sürümüne dayanan işletim sistemi

.NET Framework uygulamalarını temel mevcut veya eski uygulamalar için geçiş senaryolarında, Windows ve IIS ana bağımlılıkları gerekir. Tek seçeneğiniz, Windows Server Core ve .NET Framework üzerinde temelinde Docker görüntülerini kullanmaktır.

Görüntü adı, Dockerfile dosyasına eklediğinizde, .NET Framework tabanlı Windows kapsayıcı görüntüleri için aşağıdaki örneklerde gösterildiği gibi bir etiket kullanarak işletim sistemi ve sürümü seçebilirsiniz:

> | **Etiket** | **Sistemi ve sürümü** |
> |---|---|
> | **Microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x Windows Server core'da |
> | **aspnet:4.x/Microsoft-windowsservercore** | .NET framework 4.x Windows Server core'da ek ASP.NET özelleştirme |

.NET Core (platformlar arası Linux ve Windows için), etiketler, aşağıdaki gibi görünür:

> | **Etiket** | **Sistemi ve sürümü**
> |---|---|
> | **Microsoft/dotnet:2.0.0-Runtime** | .NET core 2.0, Linux üzerinde salt çalışma zamanı |
> | **Microsoft/dotnet:2.0.0-Runtime-nanoserver** | .NET core 2.0 Windows Nano Sunucu'da salt çalışma zamanı |

### <a name="multi-arch-images"></a>Çok yay görüntüleri

Mid-2017'de başlayarak, yeni bir özellik adında Docker kullanabilirsiniz [çok arch](https://github.com/moby/moby/issues/15866) görüntüler. .NET core Docker görüntülerini çok yay etiketleri kullanabilirsiniz. Dockerfile, hedeflediğiniz işletim sistemini tanımlamak için gerek artık dosyaları. Birden çok makine yapılandırmaları arasında kullanılacak tek bir etiket yay çok özellik sağlar. Örneğin, çok arch ile tek bir ortak etiket kullanabilirsiniz: **microsoft/dotnet:2.0.0-runtime**. Bir Linux kapsayıcı ortamında bu etiketi çekme, Debian tabanlı görüntü alırsınız. Bir Windows kapsayıcı ortamında bu etiketi çekme, Nano sunucu tabanlı bir görüntü alırsınız.

Geleneksel .NET Framework yalnızca Windows desteklediğinden, .NET Framework görüntüler için çok yay özelliği kullanamaz.

## <a name="windows-container-types"></a>Windows kapsayıcı türleri

Linux kapsayıcıları gibi Windows Server kapsayıcıları, Docker altyapısı kullanılarak yönetilir. Linux kapsayıcıları aksine Windows kapsayıcıları iki farklı kapsayıcı türler veya kez Windows Server kapsayıcıları ve Hyper-V yalıtımı'nı çalıştırın.

**Windows Server kapsayıcıları**: İşlem ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Bir Windows Server kapsayıcı bir çekirdek kapsayıcı konağı ve ana bilgisayarda çalışan tüm kapsayıcılar ile paylaşıyor. Bu kapsayıcıların tehlikeli güvenlik sınırı sağlamaz ve güvenilmeyen kod yalıtmak için kullanılmamalıdır. Paylaşılan çekirdek alanı nedeniyle bu kapsayıcıların aynı çekirdeği sürümüne ve yapılandırma gerektirir.

**Hyper-V yalıtım**: Her kapsayıcı yüksek oranda iyileştirilmiş bir VM'de çalıştırarak Windows Server kapsayıcıları tarafından sağlanan yalıtımı kapsayacak şekilde genişletiyor. Bu yapılandırmada, aynı ana bilgisayardaki diğer kapsayıcılar ile kapsayıcı konağı çekirdeğini paylaşılmıyor. Bu kapsayıcıların tehlikeli çok kiracılı, bir VM ile aynı güvenlik Güvenceleri barındırmak için tasarlanmıştır. Konak veya konak makinedeki diğer kapsayıcılardan bu kapsayıcıların çekirdek paylaşmayın olduğundan farklı sürümleri ve yapılandırmaları (ile desteklenen sürümler) ile tekrar çalıştırabilirsiniz. Örneğin, Windows 10 tüm Windows kapsayıcıları, yapılandırma ve Windows Server çekirdek sürümünü kullanmak için Hyper-V yalıtım kullanın.

Bir kapsayıcı olan veya olmayan Hyper-V yalıtım Windows üzerinde çalışan bir çalışma zamanı kararıdır. İlk olarak Hyper-V yalıtımı ile kapsayıcı oluşturmak seçin ve çalışma zamanında çalıştırmak için Windows Server kapsayıcı olarak bunun yerine tercih.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Windows kapsayıcıları belgeleri**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Windows kapsayıcıları ile ilgili temel bilgiler**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **Bilgi grafiği: Microsoft ve kapsayıcılar**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)


## <a name="the-container-ecosystem-in-azure"></a>Azure'da kapsayıcı ekosistemi

Önceki bölümlerde, .NET uygulamaları için özgü kapsayıcı görüntüleri ile ilgili ayrıntılar yanı sıra Docker kapsayıcılarının avantajları nelerdir açıklandığı. Tüm genel bilgiler, geliştirme veya bir uygulamayı kapsayıcılı hale getirme için temeldir.
Ancak, bile QA ve geliştirme/Test ortamları ve üretim dağıtım ortamı hakkında düşünürken, Microsoft Azure bir açık ve çok çeşitli seçenekler, bulutta (Aşağıdaki diyagramda gösterilen) bir tam kapsayıcı ekosistem sağlar. Özel uygulamanızın ihtiyaçlarına bağlı olarak bir ya da başka bir Azure ürün seçmeniz gerekir.

![](./media/image7.5.png)

> **Şekil 4-7.5.** Azure'da kapsayıcı ekosistemi

Kapsayıcı ekosisteminden azure'da altyapı değerlendirilir kapsayıcıları destekleyen aşağıdaki ürünler:
-   **Azure Container Instances (ACI)**
-   **Azure sanal makineleri** (kapsayıcının destekle)
-   **Azure sanal makine ölçek kümeleri** (kapsayıcının destekle)

Bu üç ACI gerek, yükseltmek/yama uygulamak, vb. için temel işletim sistemi sürdürmeniz gerekmez, ancak ACI yine de daha iyi kitabın yaklaşan bölümlerinde anlatıldığı gibi altyapı düzeyinde konumlandırılmış gerçeğidir harika bir avantaj sağlar.

Aynı anda daha PaaS (hizmet olarak Platform) yerleştirdiğiniz düzeyi destekleyici Azure kapsayıcıları ürünleri şunlardır:

-   **Azure uygulama hizmeti**
-   **Azure Kubernetes Service (AKS ve ACS)**
-   **Azure Service Fabric** 
-   **Azure Batch** 

Daha sonra Azure Container Registry, kaydetme ve özel kapsayıcı görüntülerinizi dağıtırken tüm önceki ürünlerden kullanabileceğiniz Azure'de barındırılan bir yüksek ölçeklenebilir kapsayıcı kayıt defteridir.

Ayrıca, kapsayıcılardan, diğer yönetilen Hizmetleri tüketebileceği Azure Cosmos DB, Azure SQL veritabanı, Azure Redis önbelleği gibi Azure vb. Ayrıca, kullanılabilir üçüncü taraf çözümleri/platformları Azure Marketi'nde Cloud Foundry ve OpenShift Azure kapsayıcılara burada da kullanabilirsiniz. 

Sonraki bölümlerde, her biri söz konusu Azure ürünleri ve çözümleri özellikle Windows kapsayıcıları emit hedeflerken kullanılacak ne zaman Microsoft'un öneriler keşfedebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](what-about-cloud-native-applications.md)
>[İleri](when-not-to-deploy-to-windows-containers.md)