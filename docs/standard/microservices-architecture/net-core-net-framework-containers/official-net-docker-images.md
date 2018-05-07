---
title: Resmi .NET Docker görüntüleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Resmi .NET Docker görüntüleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: d2105603fe1fcbacd995710c9b365ec406bad255
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="official-net-docker-images"></a>Resmi .NET Docker görüntüleri

Resmi .NET Docker görüntüleri oluşturulur ve Microsoft tarafından en iyi duruma getirilmiş Docker görüntüleri bağımsızdır. Microsoft depoları üzerinde genel kullanıma açık bulundukları [Docker hub'a](https://hub.docker.com/u/microsoft/). Her depo .NET sürümleri bağlı olarak ve işletim sistemi ve sürümleri (Linux Debian, Alpine Linux, Windows Nano Server, Windows Server Core, vb.) bağlı olarak birden fazla görüntü içerebilir.

Microsoft'un vizyonu .NET depoları için ayrıntılı ve odaklanmış depoları, bir depo belirli bir senaryoyu veya iş yükünü temsil ettiği olmalıdır. Örneğin, [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) ne zaman bu ASP.NET Core görüntüleri bunu kapsayıcıları ek iyileştirmeler sağladığından, Docker üzerinde ASP.NET Core kullanarak daha hızlı başlayabileceğini görüntüleri'nin kullanılması gerekir.

Diğer taraftan, .NET Core görüntüleri (microsoft/dotnet) .NET Core üzerinde tabanlı konsol uygulamaları için tasarlanmıştır. Örneğin, toplu işlemler, Azure Web işleri ve diğer konsol senaryoları .NET Core kullanmanız gerekir. Bu görüntüleri daha küçük bir kapsayıcı görüntüde kaynaklanan ASP.NET Core yığını dahil etmeyin.

Çoğu görüntü depoları, yalnızca belirli framework sürümünü seçmenize yardımcı olmak için aynı zamanda bir işletim sistemine (Linux distro veya Windows sürümü) seçmek için kapsamlı etiketleme sağlar.

Microsoft tarafından sağlanan resmi .NET Docker görüntüleri hakkında daha fazla bilgi için bkz: [.NET Docker görüntüleri Özet](https://aka.ms/dotnetdockerimages).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core ve Docker görüntü iyileştirmeler geliştirme üretim karşılaştırması

Geliştiriciler için Docker görüntülerinizi oluşturmak, Microsoft aşağıdaki ana senaryoları odaklanır:

-   Kullanılacak görüntüleri *geliştirmek* ve .NET Core uygulamaları oluşturun.

-   Kullanılacak görüntüleri *çalıştırmak* .NET Core uygulamaları.

Neden birden fazla görüntü? Geliştirme, derleme ve kapsayıcılı uygulamaları çalıştıran genellikle farklı önceliklere sahip. Microsoft, bu farklı görevler için farklı görüntüleri sağlayarak, geliştirme, derleme ve uygulamaları dağıtma ayrı işlemleri en iyi duruma getirme yardımcı olur.

### <a name="during-development-and-build"></a>Geliştirme ve derleme sırasında

Geliştirme sırasında ne kadar hızlı değişiklikler ve değişiklikleri hata ayıklama özelliği yineleyebilirsiniz önemli olan ' dir. Görüntü boyutunu kodunuzda değişiklikler yapmak ve değişiklikleri hızlıca görmek yeteneği gibi önemli değildir. Bazı araçlar ve "yapı aracısı kapsayıcıları" geliştirme sırasında ASP.NET Core görüntü (aspnetcore/microsoft-derleme) geliştirme kullanabilir ve derleme işlemi. Docker kapsayıcısı içindeki oluştururken, önemli yönlerinden uygulamanızı derlemek için gereken öğelerdir. Bu derleyici ve içerir herhangi diğer .NET bağımlılıkları yanı sıra web geliştirme bağımlılıkları gibi npm, Gulp, Bower.

Bu tür yapı görüntü neden önemlidir? Bu görüntü üretime dağıtmayın. Bunun yerine, bir üretim görüntüsüne yerleştirdiğiniz içeriği oluşturmak için kullandığınız bir görüntüdür. Bu görüntü, sürekli tümleştirme (CI) ortamında veya yapı ortamında kullanılır. Örneğin, (örneğin, bir VM) tüm uygulama bağımlılıklarını doğrudan bir yapı aracısında el ile yükleme yerine ana bilgisayar, derleme aracısı .NET Core yapı görüntü uygulama oluşturmak için gerekli tüm bağımlılıkları olan örneği. Derleme aracınızı, yalnızca bu Docker görüntü çalıştırma bilmesi gerekir. Bu, CI ortamınızı basitleştirir ve çok daha tahmin edilebilir hale getirir.

### <a name="in-production"></a>Üretimde

Üretimde önemlidir ne kadar hızlı dağıtma ve üretim .NET Core görüntüyü temel alarak kapsayıcılarınızı başlatma ' dir. Bu nedenle, yalnızca çalışma zamanında resmin dayalı olarak [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) küçük, böylelikle onu hızlı bir şekilde ağ üzerinden Docker kayıt defterinden Docker konaklarınızın izler. Sonuçlar işlenirken kapsayıcıya başlatılmasını süreye etkinleştirme içeriği çalıştırmak hazır olursunuz. Docker modelinde c derleme için gerek yoktur\# kod, orada ne zaman dotnet yapı çalıştırmak veya dotnet yayımlama yapı kapsayıcı kullanıyor.

Bu en iyi duruma getirilmiş yansımasına yalnızca ikili dosyaları ve uygulamayı çalıştırmak için gereken diğer içeriği yerleştirin. Örneğin, dotnet tarafından oluşturulmuş içerik yayımlama yalnızca derlenmiş .NET ikili dosyaları, görüntüler, .js ve .css dosyaları içerir. Zaman içinde öncesi jitted paketleri içeren resimler görürsünüz.

.NET Core ve ASP.NET Core görüntüleri birden fazla sürümünü olsa da, tüm temel katmanın dahil olmak üzere, bir veya daha fazla katmanları paylaşın. Bu nedenle, görüntüyü depolamak için gereken disk alanı miktarını küçüktür; yalnızca özel görüntünüzü ve temel görüntü arasındaki delta oluşur. Kayıt defterinden görüntü çekmesini hızlı sonucudur.

Docker hub'a adresindeki .NET görüntü depoları geçirirken, sınıflandırılmış veya etiketleriyle işaretlenmiş birden fazla görüntü sürümleri bulacaksınız. Bu etiketler hangisinin, aşağıdaki tabloda bulunanlar gibi ihtiyaç sürümüne bağlı olarak kullanmaya karar vermenize yardımcı olur:

-   Microsoft /**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**aspnetcore-yapı: 2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Önceki] (net-kapsayıcı-os-targets.md) [sonraki] (.. /Architect-microservice-Container-Applications/index.MD)
