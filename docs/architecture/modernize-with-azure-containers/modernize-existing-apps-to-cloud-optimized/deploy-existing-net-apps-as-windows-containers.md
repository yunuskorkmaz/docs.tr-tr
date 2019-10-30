---
title: Varolan .NET uygulamalarını Windows kapsayıcıları olarak dağıtma
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Mevcut .NET uygulamalarını Windows kapsayıcıları olarak dağıtma
ms.date: 04/29/2018
ms.openlocfilehash: 28568ca363bfc8100f78b100f8a7f0242c4f04c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089553"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Varolan .NET uygulamalarını Windows kapsayıcıları olarak dağıtma

Windows kapsayıcıları tabanlı dağıtımlar, buluta Iyileştirilmiş uygulamalar ve bulutta yerel uygulamalar için geçerlidir.

Bununla birlikte, bu kılavuzda ve özellikle de aşağıdaki bölümlerde, uygulamanızı yeniden mimarın, *buluta En Iyi duruma getirilmiş* uygulamalar Için Windows kapsayıcıları kullanımına odaklanılır.

## <a name="what-are-containers-linux-or-windows"></a>Kapsayıcılar nelerdir? (Linux veya Windows)

Kapsayıcılar, bir uygulamayı kendi yalıtılmış paketine kaydırmak için bir yoldur. Kapsayıcıda, uygulama kapsayıcının dışında mevcut olan uygulamalardan veya işlemlerden etkilenmez. Bir işlem kapsayıcının içinde olduğundan, uygulamanın başarıyla çalışmasına bağlı olduğu her şey. Kapsayıcının taşınabileceği her yerde, uygulamanın gereksinimleri, çalışması gereken her şey (kitaplık bağımlılıkları, çalışma zamanları vb.) ile paketlenmiş olduğundan, doğrudan bağımlılıklar açısından her zaman karşılanır.

Kapsayıcının asıl özelliği, kapsayıcının kendisi gereken tüm bağımlılıklarla birlikte geldiğinden, ortamın farklı dağıtımlarda aynı olmasını sağlar. Makinenizde uygulamada hata ayıklayın ve ardından aynı ortam garantisini vererek başka bir makineye dağıtabilirsiniz.

Kapsayıcı, kapsayıcı görüntüsünün bir örneğidir. Kapsayıcı görüntüsü, bir uygulamayı veya hizmeti paketlemeyi (bir anlık görüntü gibi) ve ardından güvenilir ve tekrarlanabilir bir şekilde dağıtmayı bir yoludur. Docker 'ın yalnızca bir teknoloji değil, ayrıca bir FIN ve bir işlem olduğunu varsayalım.

Kapsayıcılar günlük olarak daha yaygın hale geldiklerinden, sektör genelinde "dağıtım birimi" haline gelir.

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Kapsayıcıların avantajları (Linux veya Windows üzerinde Docker motoru)

Kapsayıcıları kullanarak uygulamalar oluşturma-basit yapı taşları olarak da tanımlanabilir; tüm altyapılarda herhangi bir uygulamayı oluşturmak, teslim etmek ve çalıştırmak için çeviklik açısından önemli bir artış sunar.

Kapsayıcılarla, Microsoft Geliştirici araçları, işletim sistemleri ve bulutunda Docker tümleştirmesi sayesinde, geliştirme ve kod değişikliği yapmadan her türlü uygulamayı üretime alabilirsiniz.

Düz VM 'lere dağıtırken, büyük olasılıkla ASP.NET uygulamalarını sanal makinelerinize dağıtmak için bir yönteminiz zaten vardır. Büyük olasılıkla, yönteminiz Pupevcil hayvan veya benzer bir araç gibi bir dağıtım aracını kullanarak birden çok el ile adım veya karmaşık otomatik işlem içeriyor olabilir. Yapılandırma öğelerini değiştirme, sunucular arasında uygulama içeriğini kopyalama ve test eden. msi kurulumları temelinde etkileşimli kurulum programları çalıştırma gibi görevleri gerçekleştirmeniz gerekebilir. Dağıtımdaki tüm bu adımlar, dağıtıma zaman ve risk ekler. Hedef ortamda bir bağımlılık bulunmadığı zaman, hatalara sahip olursunuz.

Windows kapsayıcılarında, uygulama paketleme işlemi tamamen otomatikleştirilmiştir. Windows kapsayıcıları, kapsayıcı dağıtımları için otomatik güncelleştirmeler ve geri göndermeler sunan Docker platformunu temel alır. Docker altyapısını kullanarak alacağınız ana geliştirme, uygulamanızın anlık görüntüleri gibi tüm bağımlılıklarıyla birlikte görüntü oluşturmalarıdır. Görüntüler Docker görüntüleridir (Bu durumda bir Windows kapsayıcı görüntüsü). Görüntüler, kaynak koduna geri dönerek kapsayıcılarda ASP.NET uygulamaları çalıştırır. Kapsayıcı anlık görüntüsü dağıtım birimi olur.

Birçok kuruluş, aşağıdaki nedenlerden dolayı mevcut tek parçalı uygulamalar arasında Kapsayıcılı hale getirir:

- **İyileştirilmiş dağıtım aracılığıyla çevikliği yayınlayın**. Kapsayıcılar, geliştirme ve işlemler arasında tutarlı bir dağıtım sözleşmesi sunar. Kapsayıcılar kullandığınızda, "BT makinelerimde çalışıyor, neden üretimde çalışmıyor?" "Bir kapsayıcı olarak çalışır, bu nedenle üretimde çalıştırılır." şeklinde görünür. Paketlenmiş uygulama, tüm bağımlılıklarıyla birlikte desteklenen herhangi bir kapsayıcı tabanlı ortamda yürütülebilir. Tüm dağıtım hedeflerinde (dev, QA, hazırlama, üretim) çalıştırılması amaçlanan şekilde çalışır. Kapsayıcılar, bir aşamanın yanına geçtiğinde büyük ölçüde dağıtımı ortadan kaldırır, bu da dağıtımı büyük ölçüde geliştirir ve daha hızlı gönderebilirsiniz.

- **Maliyet indirimleri**. Kapsayıcılar, mevcut donanımın birleştirilmesi ve kaldırılmasına göre veya donanım birimi başına daha yüksek bir yoğunlukta çalışan uygulamalardan daha düşük maliyetlere yol açabilir.

- **Taşınabilirlik**. Kapsayıcılar modüler ve taşınabilir. Docker kapsayıcıları, herhangi bir büyük genel bulutta (Microsoft Azure, Amazon AWS, Google, IBM) ve şirket içi ve özel ya da karma bulut ortamlarında herhangi bir sunucu işletim sisteminde (Linux ve Windows) desteklenir.

- **Denetim**. Kapsayıcılar, kapsayıcı düzeyinde denetlenen esnek ve güvenli bir ortam sunar. Kapsayıcıda yürütme kısıtlama ilkeleri ayarlanarak bir kapsayıcı güvenli, yalıtılmış ve hatta sınırlı olabilir. Windows kapsayıcıları hakkında bölümünde açıklandığı gibi, Windows Server 2016 ve Hyper-V kapsayıcıları ek kurumsal destek seçenekleri sunar.

Çeviklik, taşınabilirlik ve denetim açısından önemli iyileştirmeler, uygulama geliştirmek ve sürdürmek için kapsayıcılar kullandığınızda önemli maliyet indirimlerine yol açabilir.

## <a name="what-is-docker"></a>Docker nedir?

[Docker](https://www.docker.com/) , uygulamaların bulutta veya şirket içinde çalışabilen taşınabilir, kendi kendine yeterli kapsayıcılar olarak dağıtımını otomatik hale getiren [Açık kaynaklı bir projem](https://github.com/docker/docker) . Docker Ayrıca bu teknolojiyi tanıtan ve geliştikçe bir [şirkettir](https://www.docker.com/) . Şirket, Microsoft dahil olmak üzere Cloud, Linux ve Windows satıcılarıyla işbirliği içinde çalışmaktadır.

![Docker 'ın karma buluttaki kapsayıcıları nasıl dağıttığı gösteren diyagram.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Şekil 4-6.** Docker, kapsayıcıyı karma bulutun tüm katmanlarında dağıtır

Sanal makineleri bildiğiniz bir kişiye, kapsayıcılar benzer şekilde benzerdir. Bir kapsayıcı, bir işletim sistemini çalıştırır, bir dosya sistemine sahiptir ve fiziksel veya sanal bilgisayar sistemi gibi bir ağ üzerinden erişilebilir. Ancak, kapsayıcıların arkasındaki teknoloji ve kavramlar, sanal makinelerden büyük ölçüde farklıdır. Bir geliştirici görünümünden bir kapsayıcı tek bir işlem gibi ele alınmalıdır. Aslında, bir kapsayıcı bir işlem için tek bir giriş noktasına sahiptir.

Docker Kapsayıcıları (basitlik, *kapsayıcılar*Için) Linux ve Windows üzerinde yerel olarak çalışabilir. Normal kapsayıcıları çalıştırırken Windows kapsayıcıları yalnızca Windows Konakları (bir konak sunucusu veya VM) üzerinde çalışabilir ve Linux kapsayıcıları yalnızca Linux konakları üzerinde çalışabilir. Ancak, Windows Server ve Hyper-V kapsayıcılarının son sürümlerinde bir Linux kapsayıcısı, şu anda yalnızca Windows Server kapsayıcılarında bulunan Hyper-V yalıtım teknolojisini kullanarak Windows Server 'da yerel olarak da çalıştırılabilir.

Yakın gelecekte hem Linux hem de Windows kapsayıcılarına sahip karışık ortamlar mümkün ve hatta yaygın olacak.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Mevcut .NET uygulamalarınız için Windows kapsayıcılarının avantajları

Windows kapsayıcıları kullanmanın avantajları, genel olarak kapsayıcılardan elde edeceğiniz avantajlara göre temelde aynıdır. Windows kapsayıcıları kullanmak, çevikliği, taşınabilirliği ve denetimi önemli ölçüde geliştirmektir.

Mevcut .NET uygulamaları, .NET Framework kullanılarak oluşturulan uygulamalara başvurur. Örneğin, bunlar geleneksel ASP.NET Web uygulamaları olabilir. bu uygulamalar, daha yeni olan ve Linux, Windows ve MacOS üzerinde platformlar arası çalışan .NET Core 'u kullanmaz.

.NET Framework ana bağımlılık Windows ' tır. Ayrıca geleneksel ASP.NET içinde IIS ve System. Web gibi ikincil bağımlılıklara sahiptir.

.NET Framework bir uygulama Windows, nokta üzerinde çalışmalıdır. Var olan .NET Framework uygulamalarını kapsayılanmaya veya .NET Core 'a geçiş yapmak istemiyorsanız ("düzgün çalışıyorsa, geçirmezseniz"), kapsayıcılar için sahip olduğunuz tek seçenek Windows kapsayıcıları kullanmaktır.

Bu nedenle, Windows kapsayıcılarının başlıca avantajlarından biri, Windows ile kapsayıcılama üzerinde çalışan mevcut .NET Framework uygulamalarınızı modernleştirin için bir yol sunmalarıdır. Son olarak, Windows kapsayıcıları, kapsayıcıları, taşınabilirliği ve daha iyi denetimi kullanarak aradığınız avantajlardan yararlanır.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Hedeflenecek bir işletim sistemi seçin. NET tabanlı kapsayıcılar

Docker tarafından desteklenen işletim sistemlerinin ve .NET Framework ile .NET Core arasındaki farklılıkların farklılığı verildiğinde, kullanmakta olduğunuz çerçeveye bağlı olarak belirli bir işletim sistemini ve belirli sürümleri hedeflemelidir.

Windows için Windows Server Core veya Windows nano Server kullanabilirsiniz. Bu Windows sürümleri, .NET Framework veya .NET Core uygulamaları için gerekebilecek farklı Özellikler (IIS gibi, Kestrel gibi şirket içinde barındırılan bir Web sunucusuna karşılık gelen) sağlar.

Linux için, resmi .NET Docker görüntülerinde (Deklik gibi) Çoklu destekler mevcuttur ve desteklenir.

Şekil 4-7, uygulamanın .NET Framework sürümüne bağlı olarak hedefleyebilir işletim sistemi sürümlerini gösterir.

![.NET Framework sürümüne göre hangi işletim sisteminin hedeflenecek olduğunu gösteren diyagram.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Şekil 4-7.** .NET Framework sürümüne göre hedeflenecek işletim sistemleri

.NET Framework uygulamalarına dayalı mevcut veya eski uygulamalar için geçiş senaryolarında, ana bağımlılıklar Windows ve IIS ' de bulunur. Tek seçeneğiniz, Windows Server Core ve .NET Framework temel alınarak Docker görüntülerini kullanmaktır.

Resim adını Dockerfile dosyanıza eklediğinizde, .NET Framework tabanlı Windows kapsayıcı görüntüleri için aşağıdaki örneklerde olduğu gibi, işletim sistemini ve sürümü bir etiketi kullanarak seçebilirsiniz:

> | **Etiket** | **Sistem ve sürüm** |
> |---|---|
> | **Microsoft/DotNet-Framework: 4. x-windowsservercore** | Windows Server Core 'da 4. x .NET Framework |
> | **Microsoft/ASPNET: 4. x-windowsservercore** | .NET Framework 4. x, Windows Server Core 'da ek ASP.NET özelleştirmesi ile |

.NET Core için (Linux ve Windows için platformlar arası), Etiketler aşağıdaki gibi görünür:

> | **Etiket** | **Sistem ve sürüm**
> |---|---|
> | **Microsoft/DotNet: 2.0.0-Runtime** | .NET Core 2,0 çalışma zamanı-yalnızca Linux üzerinde |
> | **Microsoft/DotNet: 2.0.0-Runtime-nanoserver** | .NET Core 2,0 çalışma zamanı-yalnızca Windows nano Server üzerinde |

### <a name="multi-arch-images"></a>Çoklu mimari görüntüler

Orta 2017 ' den başlayarak, Docker 'da [çok katmanlı](https://github.com/moby/moby/issues/15866) görüntüler adlı yeni bir özellik de kullanabilirsiniz. .NET Core Docker görüntüleri, çoklu mimari etiketlerini kullanabilir. Dockerfile dosyalarınıza artık hedeflediğiniz işletim sistemini tanımlama gereksinimi yoktur. Çoklu mimari özelliği, birden çok makine yapılandırmasında tek bir etiketin kullanılmasına izin verir. Örneğin, çok katmanlı bir ortak etiket kullanabilirsiniz: **Microsoft/DotNet: 2.0.0-Runtime**. Bu etiketi bir Linux kapsayıcı ortamından çekmeniz halinde, detem tabanlı görüntüyü alırsınız. Bu etiketi bir Windows kapsayıcı ortamından çektiğinizde, nano sunucu tabanlı görüntüyü alırsınız.

.NET Framework görüntüleri için geleneksel .NET Framework yalnızca Windows 'u desteklediğinden, çoklu mimari özelliğini kullanamazsınız.

## <a name="windows-container-types"></a>Windows kapsayıcı türleri

Linux kapsayıcıları gibi Windows Server kapsayıcıları, Docker altyapısı kullanılarak yönetilir. Linux kapsayıcılarından farklı olarak, Windows kapsayıcıları iki farklı kapsayıcı türü veya çalışma zamanı-Windows Server kapsayıcıları ve Hyper-V yalıtımı içerir.

**Windows Server kapsayıcıları**: işlem ve ad alanı yalıtım teknolojisi aracılığıyla uygulama yalıtımı sağlar. Windows Server kapsayıcısı, kapsayıcı Konağı ve konakta çalışan tüm kapsayıcılar ile bir çekirdeği paylaşır. Bu kapsayıcılar, bir güvenlik sınırı sağlamaz ve güvenilmeyen kodu yalıtmak için kullanılmamalıdır. Paylaşılan çekirdek alanı nedeniyle, Bu kapsayıcılar aynı çekirdek sürümünü ve yapılandırmasını gerektirir.

**Hyper-V yalıtımı**: her kapsayıcıyı yüksek oranda IYILEŞTIRILMIŞ bir VM üzerinde çalıştırarak Windows Server kapsayıcıları tarafından sunulan yalıtımın üzerinde genişler. Bu yapılandırmada, kapsayıcı konağın çekirdeği aynı konaktaki diğer kapsayıcılarla paylaşılmaz. Bu kapsayıcılar, sanal makine ile aynı güvenlik açısından çok kiracılı barındırma için tasarlanmıştır. Bu kapsayıcılar, Konağı konaktaki konak veya diğer kapsayıcılarla paylaşmadığından, farklı sürüm ve yapılandırmalara sahip çekirdekler 'leri (desteklenen sürümlerle birlikte) çalıştırabilirler. Örneğin, Windows 10 ' da tüm Windows kapsayıcıları, Windows Server çekirdeği sürümünü ve yapılandırmasını kullanmak için Hyper-V yalıtımını kullanır.

Windows üzerinde veya Hyper-V yalıtımı olmadan bir kapsayıcı çalıştırmak, çalışma zamanı kararsıdır. Başlangıçta Hyper-V yalıtımı ile kapsayıcıyı oluşturmayı seçebilir ve çalışma zamanında onu bir Windows Server kapsayıcısı olarak çalıştırmayı tercih edebilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Windows kapsayıcıları belgeleri**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Windows kapsayıcıları temelleri**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infographic: Microsoft ve kapsayıcılar**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Azure 'da kapsayıcı ekosistemi

Önceki bölümlerde, Docker kapsayıcılarının avantajları ve .NET uygulamalarına özgü kapsayıcı görüntüleri hakkında ayrıntılı bilgiler de açıklanmıştı. Uygulamanın geliştirilmesi veya Kapsayıcılı olması için tüm bu genel bilgiler temel bir uygulamadır.
Bununla birlikte, üretim dağıtım ortamı veya soru-cevap geliştirme/test Microsoft Azure ortamları hakkında düşünürken, bulutta tam bir kapsayıcı ekosistemi olan açık ve çok çeşitli seçenekler sağlar (Aşağıdaki diyagramda gösterilmektedir). Belirli uygulamanızın ihtiyaçlarına bağlı olarak, bir veya başka bir Azure ürünü seçmeniz gerekir.

![Azure 'da kapsayıcı ekosisteminin diyagramı.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Şekil 4-7,5.** Azure 'da kapsayıcı ekosistemi

Azure 'da kapsayıcı ekosisteminden, altyapı olarak kabul edilen kapsayıcıları destekleyen aşağıdaki ürünler:

- **Azure Container Instances (ACI)**
- **Azure sanal makineleri** (kapsayıcının desteğiyle)
- **Azure sanal makine ölçek kümeleri** (kapsayıcının desteğiyle)

Bu üçünden, ACI, temel alınan işletim sistemini sürdürmenize gerek kalmaz, yükseltme/düzeltme eki uygulamanız gerekmez, ancak yine de altyapı düzeyinde konumlanır, bu da kitabın yaklaşan bölümlerinde daha da açıklanacaktır.

Azure 'daki ve aynı anda PaaS (hizmet olarak platform) düzeyinde konumlandırılmış kapsayıcıları destekleyen ürünler şunlardır:

- **Azure App Service**
- **Azure Kubernetes hizmeti (AKS ve ACS)**
- **Azure Batch**

Daha sonra Azure Container Registry, Azure 'da barındırılan ve özel kapsayıcı görüntülerinizi kaydederken ve dağıttığınızda önceki tüm ürünlerden kullanabileceğiniz yüksek düzeyde ölçeklenebilir bir kapsayıcı kayıt defteridir.

Bunlara ek olarak, kapsayıcılarınızdaki Azure SQL veritabanı, Azure Redsıs Cache, Azure Cosmos DB vb. gibi diğer yönetilen Hizmetleri de kullanabilirsiniz. Ayrıca, Azure Marketi 'nde Azure Market 'te de kullanabileceğiniz Cloud Foundry ve OpenShift gibi üçüncü taraf çözümler/platformlar mevcuttur.

Sonraki bölümlerde, Microsoft 'un bu Azure ürünlerinin ve çözümlerinin her birinin ne zaman kullanılacağı konusunda, özellikle Windows kapsayıcıları hedeflenirken bu önerileri inceleyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](what-about-cloud-native-applications.md)
>[İleri](when-not-to-deploy-to-windows-containers.md)
