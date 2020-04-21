---
title: Varolan .NET uygulamalarını Windows kapsayıcıları olarak dağıtma
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Varolan .NET uygulamalarını Windows kapsayıcıları olarak dağıtma
ms.date: 04/29/2018
ms.openlocfilehash: 15e99e2ec0edd072a3d47d5c212ebbbf6705ecef
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738425"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Varolan .NET uygulamalarını Windows kapsayıcıları olarak dağıtma

Windows Kapsayıcılarını temel alan dağıtımlar, Bulut için optimize edilmiş uygulamalar ve Bulut Tabanlı uygulamalar için geçerlidir.

Ancak, bu kılavuzda ve özellikle aşağıdaki bölümlerde, çoğunlukla uygulamanızı yeniden architectneed gerekmez *Bulut-Optimize* uygulamaları için Windows Kapsayıcılar kullanarak odaklanır.

## <a name="what-are-containers-linux-or-windows"></a>Kapsayıcılar nedir? (Linux veya Windows)

Kapsayıcılar, bir uygulamayı kendi yalıtılmış paketine sığdırmak için bir yoldur. Kapsayıcısında, uygulama kapsayıcının dışında bulunan uygulamalar dan veya işlemlerden etkilenmez. Bir işlem kapsayıcının içinde olduğu için uygulamanın başarılı bir şekilde çalışmasına bağlı olan her şey. Kapsayıcı nereye taşınırsa taşınsın, doğrudan bağımlılıklar açısından uygulamanın gereksinimleri her zaman karşılanır, çünkü çalışması gereken her şeyle birlikte dir (kitaplık bağımlılıkları, çalışma süreleri vb.).

Bir kapsayıcının temel özelliği, kapsayıcının kendisi ihtiyacı olan tüm bağımlılıklarla birlikte geldiğinden, ortamı farklı dağıtımlar arasında aynı hale getirir. Uygulamanın hatasını makinenizde ayıklayabilir ve ardından aynı ortam garanti edilmiş başka bir makineye dağıtabilirsiniz.

Kapsayıcı, kapsayıcı görüntüsünün bir örneğidir. Kapsayıcı görüntüsü, bir uygulamayı veya hizmeti paketlemenin (anlık görüntü gibi) ve ardından güvenilir ve tekrarlanabilir bir şekilde dağıtmanın bir yoludur. Docker'ın sadece bir teknoloji olmadığını, aynı zamanda bir felsefe ve bir süreç olduğunu söyleyebilirsiniz.

Kapsayıcılar her gün daha yaygın hale geldikçe, endüstri çapında bir "dağıtım birimi" haline gelmektedir.

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Konteynerlerin faydaları (Docker Engine on Linux veya Windows)

Hafif yapı taşları olarak da tanımlanabilecek konteynerler kullanarak uygulama oluşturma, herhangi bir altyapı üzerinde herhangi bir uygulama nın oluşturulması, nakliyesi ve çalıştırılması için çeviklikte önemli bir artış sağlar.

Kapsayıcılarla, Microsoft geliştirici araçları, işletim sistemleri ve bulut genelinde Docker tümleştirmesi sayesinde, çok az veya hiç kod değişikliği olmadan geliştirmeden üretime kadar her uygulamayı alabilirsiniz.

Düz VM'lere dağıtırken, büyük olasılıkla ASP.NET uygulamaları VM'lerinize dağıtmak için zaten bir yönteminiz vardır. Ancak, yönteminizin Puppet gibi bir dağıtım aracı veya benzer bir araç kullanarak birden çok el ile adım veya karmaşık otomatik işlemler içerme olasılığı yüksektir. Yapılandırma öğelerini değiştirme, sunucular arasında uygulama içeriğini kopyalama ve .msi kurulumlarını temel alan etkileşimli kurulum programlarını çalıştırma ve ardından sınama gibi görevleri gerçekleştirmeniz gerekebilir. Dağıtımdaki tüm bu adımlar, dağıtımlara zaman ve risk katar. Hedef ortamda bir bağımlılık olmadığında hata alırsınız.

Windows Kapsayıcılarında, paketleme uygulamaları işlemi tam otomatiktir. Windows Kapsayıcıları, kapsayıcı dağıtımları için otomatik güncelleştirmeler ve geri almalar sunan Docker platformuna dayanır. Docker motorunu kullanarak elde ettiğiniz temel gelişme, uygulamanızın anlık görüntüleri gibi tüm bağımlılıkları ile görüntüler oluşturmanızdır. Görüntüler Docker görüntüleridir (bu durumda bir Windows kapsayıcı görüntüsü). Görüntüler, kaynak koduna geri dönmeden ASP.NET uygulamaları kapsayıcılarda çalıştırın. Kapsayıcı anlık görüntüsü dağıtım birimi olur.

Birçok kuruluş aşağıdaki nedenlerle varolan monolitik uygulamaları kapsayıcılaştırıyor:

- **Geliştirilmiş dağıtım yoluyla çeviklik bırakın.** Kapsayıcılar geliştirme ve işlemler arasında tutarlı bir dağıtım sözleşmesi sunar. Konteynerleri kullandığınızda, geliştiricilerin "Makinemde çalışıyor, neden üretimde değil?" dediğini duymayacaksınız. "Konteyner olarak çalışıyor, bu yüzden üretimde çalışacak" diyebilirler. Paketlenmiş uygulama, tüm bağımlılıkları ile, desteklenen kapsayıcı tabanlı ortamda yürütülebilir. Tüm dağıtım hedeflerinde (dev, QA, evreleme, üretim) çalışması amaçlandığı şekilde çalışacaktır. Kapsayıcılar, bir aşamadan diğerine geçerken çoğu sürtünmeyi ortadan kaldırır, bu da dağıtımı büyük ölçüde artırır ve daha hızlı gönderim yapabilirsiniz.

- **Maliyet indirimleri.** Kapsayıcılar, mevcut donanımın konsolidasyonu ve kaldırılması veya donanım birimi başına daha yüksek yoğunlukta uygulamaların çalıştırılmasını sağlayarak daha düşük maliyetlere yol açar.

- **Taşınabilirlik**. Konteynerler modüler ve taşınabilirdir. Docker kapsayıcıları herhangi bir sunucu işletim sisteminde (Linux ve Windows), herhangi bir genel bulutta (Microsoft Azure, Amazon AWS, Google, IBM) ve şirket içi ve özel veya karma bulut ortamlarında desteklenir.

- **Kontrol**. Konteynerler, konteyner seviyesinde kontrol edilen esnek ve güvenli bir ortam sunar. Kapsayıcı, kapsayıcıüzerinde yürütme kısıtlaması ilkeleri ayarlayarak güvenli, yalıtılmış ve hatta sınırlandırılabilir. Windows Kapsayıcıları, Windows Server 2016 ve Hyper-V kapsayıcıları hakkında bölümde ayrıntılı olarak belirtildiği gibi ek kurumsal destek seçenekleri sunar.

Uygulamaları geliştirmek ve sürdürmek için kapsayıcıları kullandığınızda çeviklik, taşınabilirlik ve denetimde önemli iyileştirmeler sonuçta önemli maliyet düşüşlerine yol açar.

## <a name="what-is-docker"></a>Docker nedir?

[Docker,](https://www.docker.com/) uygulamaların bulutta veya şirket içinde çalıştırılabilen taşınabilir, kendi kendine yetebilen kapsayıcılar olarak dağıtımını otomatikleştiren açık kaynaklı bir [projedir.](https://github.com/docker/docker) Docker aynı zamanda bu teknolojiyi geliştiren ve geliştiren bir [şirkettir.](https://www.docker.com/) Şirket, Microsoft da dahil olmak üzere bulut, Linux ve Windows satıcılarıyla işbirliği içinde çalışır.

![Docker'ın kapital bulutta kapsayıcıları nasıl dağıttığını gösteren diyagram.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Şekil 4-6.** Docker, hibrit bulutun tüm katmanlarına konteyner dağıtıyor

Sanal makinelere aşina olan biri için, kapsayıcılar oldukça benzer görünebilir. Kapsayıcı bir işletim sistemi çalıştırıyor, bir dosya sistemi vardır ve fiziksel veya sanal bilgisayar sistemi gibi bir ağ üzerinden erişilebilir. Ancak, konteynerlerin arkasındaki teknoloji ve kavramlar sanal makinelerden çok farklıdır. Geliştirici açısından bakıldığında, bir kapsayıcı daha çok tek bir işlem gibi ele alınmalıdır. Aslında, bir kapsayıcı nın tek bir işlem için tek bir giriş noktası vardır.

Docker kapsayıcıları (basitlik, *kapsayıcılar*için) Linux ve Windows'da yerel olarak çalıştırılabilir. Normal kapsayıcılar çalıştırırken, Windows kapsayıcıları yalnızca Windows ana bilgisayarlarında (ana bilgisayar sunucusu veya VM) ve Linux kapsayıcıları yalnızca Linux ana bilgisayarlarında çalıştırılabilir. Ancak, Windows Server ve Hyper-V kapsayıcılarının son sürümlerinde, bir Linux kapsayıcısı şu anda yalnızca Windows Server Kapsayıcılarında kullanılabilen Hyper-V yalıtım teknolojisini kullanarak Windows Server'da yerel olarak da çalıştırılabilir.

Yakın gelecekte, hem Linux hem de Windows kapsayıcılarına sahip karma ortamlar mümkün ve hatta yaygın olacaktır.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Mevcut .NET uygulamalarınız için Windows Kapsayıcılarının Avantajları

Windows Kapsayıcıları kullanmanın yararları temelde genel olarak kapsayıcılardan elde ettiğiniz faydalarla aynıdır. Windows Kapsayıcıları'nı kullanmak çevikliği, taşınabilirliği ve denetimi büyük ölçüde geliştirmektir.

Varolan .NET uygulamaları ,.NET Framework kullanılarak oluşturulan bu uygulamalara başvurur. Örneğin, web uygulamaları ASP.NET geleneksel olabilirler-daha yeni olan ve Linux, Windows ve MacOS'ta çapraz platform çalıştıran .NET Core'u kullanmıyorlar.

.NET Framework'deki temel bağımlılık Windows'dur. Ayrıca, IIS ve System.Web gibi ikincil bağımlılıkları vardır ASP.NET.

Bir .NET Framework uygulaması Windows üzerinde çalışmalıdır, nokta. Varolan .NET Framework uygulamalarını kapsayıcı hale getirmek istiyorsanız ve .NET Core'a geçişe yatırım yapamaz veya yatırım yapmak istemiyorsanız ("Düzgün çalışıyorsa, onu geçirtmeyin"), kapsayıcılar için tek seçeneğiniz Windows Kapsayıcıları kullanmaktır.

Bu nedenle, Windows Kapsayıcıları'nın en önemli avantajlarından biri, windows aracılığıyla kapsayıcılaştırma üzerinde çalışan varolan .NET Framework uygulamalarınızı modernize etmenin bir yolunu sunmalarıdır. Sonuç olarak, Windows Kapsayıcıları kapsayıcılar çeviklik, taşınabilirlik ve daha iyi kontrol kullanarak aradığınız avantajları sağlar.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>'ile hedeflemek için bir işletim sistemi seçin. NET tabanlı kaplar

Docker tarafından desteklenen işletim sistemlerinin çeşitliliğinin yanı sıra .NET Framework ve .NET Core arasındaki farklar göz önüne alındığında, kullandığınız çerçeveye göre belirli bir işletim sistemi ve belirli sürümleri hedeflemeniz gerekir.

Windows için Windows Server Core veya Windows Nano Server'ı kullanabilirsiniz. Bu Windows sürümleri ,NET Framework veya .NET Core uygulamaları tarafından ihtiyaç duyulabilecek farklı özellikler sağlar (IIS karşı Kestrel gibi kendi kendine barındırılan bir web sunucusu).

Linux için, birden fazla dağıtım mevcuttur ve resmi .NET Docker görüntüleri (Debian gibi) desteklenir.

Şekil 4-7, .NET Framework'ün uygulama sürümüne bağlı olarak hedeflenebildiğiniz işletim sistemi sürümlerini gösterir.

![.NET Framework sürümüne göre hangi işletim sistemi hedeflenebilmek için diyagram.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Şekil 4-7.** .NET Framework sürümüne göre hedef olacak işletim sistemleri

.NET Framework uygulamalarını temel alan varolan veya eski uygulamalar için geçiş senaryolarında, temel bağımlılıklar Windows ve IIS'dir. Tek seçeneğiniz, Windows Server Core ve .NET Framework'e dayalı Docker görüntülerini kullanmaktır.

Dockerfile dosyanıza görüntü adını eklediğinizde, .NET Framework tabanlı Windows kapsayıcı görüntülerine yönelik aşağıdaki örneklerde olduğu gibi bir etiket kullanarak işletim sistemini ve sürümü seçebilirsiniz:

> | **Tag** | **Sistem ve sürüm** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET Framework 4.x Windows Server Core üzerinde |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET Framework 4.x ek ASP.NET özelleştirme, Windows Server Core üzerinde |

.NET Core (Linux ve Windows için çapraz platform) için etiketler aşağıdaki gibi görünür:

> | **Tag** | **Sistem ve sürüm**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET Core 2.0 yalnızca Linux'ta çalışma zamanı |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET Core 2.0 yalnızca Windows Nano Server'da çalışma zamanı |

### <a name="multi-arch-images"></a>Çok kemerli görüntüler

2017'nin ortalarından itibaren Docker'da [çoklu kemerli](https://github.com/moby/moby/issues/15866) görüntüler adı verilen yeni bir özellik de kullanabilirsiniz. .NET Core Docker görüntüleri çok kemerli etiketleri kullanabilir. Dockerfile dosyalarınızın artık hedeflediğiniz işletim sistemini tanımlamasına gerek yoktur. Çok kemerli özellik, birden çok makine yapılandırması arasında tek bir etiketin kullanılmasını sağlar. Örneğin, çoklu kemerile tek bir ortak etiket kullanabilirsiniz: **microsoft/dotnet:2.0.0-runtime**. Bu etiketi Bir Linux kapsayıcı ortamından çekerseniz, Debian tabanlı görüntüyü elde elabilirsiniz. Bu etiketi Windows kapsayıcı ortamından çekerseniz, Nano Server tabanlı görüntüyü elde edersiniz.

.NET Framework görüntüleri için, geleneksel .NET Framework yalnızca Windows'u desteklediğinden, çoklu kemer özelliğini kullanamazsınız.

## <a name="windows-container-types"></a>Windows kapsayıcı türleri

Linux kapsayıcıları gibi, Windows Server kapsayıcıları da Docker Engine kullanılarak yönetilir. Linux kapsayıcılarından farklı olarak, Windows kapsayıcıları iki farklı kapsayıcı türü içerir veya windows server kapsayıcıları ve Hyper-V yalıtımı kez çalıştırır.

**Windows Server kapsayıcıları**: Proses ve ad alanı yalıtım teknolojisi ile uygulama yalıtımı sağlar. Windows Server kapsayıcısı, kapsayıcı ana bilgisayar ve ana bilgisayarda çalışan tüm kapsayıcılarla bir çekirdek paylaşır. Bu kapsayıcılar düşmanca bir güvenlik sınırı sağlamaz ve güvenilmeyen kodu yalıtmak için kullanılmamalıdır. Paylaşılan çekirdek alanı nedeniyle, bu kapsayıcılar aynı çekirdek sürümü ve yapılandırma gerektirir.

**Hyper-V yalıtımı**: Windows Server Containers tarafından sağlanan yalıtımı, her bir kapsayıcıyı son derece optimize edilmiş bir VM üzerinde çalıştırarak genişletir. Bu yapılandırmada, kapsayıcı ana bilgisayarın çekirdeği aynı ana bilgisayardaki diğer kapsayıcılarla paylaşılmaz. Bu konteynerler, bir VM'nin aynı güvenlik güvencesiyle, düşmanca çok kiracılı barındırma için tasarlanmıştır. Bu kapsayıcılar çekirdeği ana bilgisayarla veya ana bilgisayardaki diğer kapsayıcılarla paylaşmadığından, çekirdekleri farklı sürümlere ve yapılandırmalara (desteklenen sürümlerle) çalıştırabilirler. Örneğin, Windows 10'daki tüm Windows kapsayıcıları, Windows Server çekirdek sürümünü ve yapılandırmasını kullanmak için Hyper-V yalıtımını kullanır.

Windows'da Hyper-V yalıtımı olan veya olmayan bir kapsayıcıyı çalıştırmak çalışma zamanı bir karardır. Başlangıçta Hyper-V yalıtımlı kapsayıcıyı oluşturmayı seçebilirsiniz ve çalışma zamanında bunun yerine windows server kapsayıcısı olarak çalıştırmayı seçebilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Windows Kapsayıcıları belgeleri**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Windows Kapsayıcıları temelleri**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Bilgi grafiği: Microsoft ve kapsayıcılar**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Azure'daki konteyner ekosistemi

Önceki bölümlerde, Docker kapsayıcılarının yararlarının yanı sıra .NET uygulamaları için belirli kapsayıcı görüntüleriyle ilgili ayrıntılar açıklanmıştır. Tüm bu genel bilgiler, bir uygulamayı geliştirmek veya kapsayıcı hale getirmek için temeldir.
Ancak, üretim dağıtım ortamı ve hatta QA ve Dev/Test ortamları hakkında düşünürken, Microsoft Azure açık ve geniş bir seçenek yelpazesi, bulutta tam bir kapsayıcı ekosistemi (aşağıdaki diyagramda gösterilmiştir) sağlar. Özel uygulamanızın gereksinimlerine bağlı olarak, bir veya başka bir Azure ürünü seçmeniz gerekir.

![Azure'daki konteyner ekosisteminin diyagramı.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Şekil 4-7.5.** Azure'daki konteyner ekosistemi

Azure'daki konteyner ekosisteminden, altyapı olarak kabul edilen kapsayıcıları destekleyen aşağıdaki ürünler:

- **Azure Container Instances (ACI)**
- **Azure Sanal Makineler** (Konteyner desteği ile)
- **Azure Sanal Makine Ölçek Setleri** (Konteyner desteği ile)

Bu üç itibaren, ACI temel işletim sistemi korumak gerekmez, yükseltme / yama, vb ama ACI hala altyapı düzeyinde konumlandırılmış olduğu gerçeği, daha iyi bu kitabın gelecek bölümlerinde açıklandığı gibi büyük bir fayda sağlar.

Aynı zamanda PaaS (Hizmet Olarak Platform) düzeyinde daha fazla konumlandırılmış olan Azure destek kapsayıcılarında bulunan ürünler şunlardır:

- **Azure App Service**
- **Azure Kubernetes Servisi (AKS ve ACS)**
- **Azure Batch**

Ardından, Azure Kapsayıcı Kayıt Defteri, Azure'da barındırılan ve özel kapsayıcı resimlerinizi kaydederken ve dağıtırken önceki tüm ürünlerden kullanabileceğiniz yüksek ölçeklenebilir bir kapsayıcı kayıt defteridir.

Ayrıca, kapsayıcılarınızdan Azure SQL Veritabanı, Azure Redis önbelleği, Azure Cosmos DB gibi diğer yönetilen hizmetleri de tüketebilirsiniz. ayrıca Azure Marketi'nde Bulut Dökümhanesi ve OpenShift gibi azure'daki kapsayıcıları da kullanabileceğiniz üçüncü taraf çözümleri/platformları vardır.

Sonraki bölümlerde, Microsoft'un bu Azure ürünlerinin ve çözümlerinin her birini ne zaman kullanacağınız konusundaki önerilerini özellikle Windows Kapsayıcıları'nı hedeflerken keşfedebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](what-about-cloud-native-applications.md)
>[Sonraki](when-not-to-deploy-to-windows-containers.md)
