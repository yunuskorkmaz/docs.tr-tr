---
title: Resmi .NET Docker görüntüleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Resmi .NET Docker görüntüleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: bb2190a4fae6f8a26b220fd12ecb9f65ea6f4b96
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251122"
---
# <a name="official-net-docker-images"></a>Resmi .NET Docker görüntüleri

Resmi .NET Docker görüntüleri oluşturulur ve Microsoft tarafından en iyi duruma getirilmiş Docker görüntüleri bağımsızdır. Microsoft depoları üzerinde genel kullanıma açık bulundukları [Docker hub'a](https://hub.docker.com/u/microsoft/). Her depo .NET sürümleri bağlı olarak ve işletim sistemi ve sürümleri (Linux Debian, Alpine Linux, Windows Nano Server, Windows Server Core, vb.) bağlı olarak birden fazla görüntü içerebilir.

.NET Core 2.1 itibaren Docker Hub'ına adresindeki ASP.NET Core için de dahil olmak üzere tüm .NET Core görüntüleri kullanılabilir [.NET Core görüntü deposuna](https://hub.docker.com/r/microsoft/dotnet/).

Çoğu görüntü depoları, yalnızca belirli framework sürümünü seçmenize yardımcı olmak için aynı zamanda bir işletim sistemine (Linux distro veya Windows sürümü) seçmek için kapsamlı etiketleme sağlar.


## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core ve Docker görüntü iyileştirmeler geliştirme üretim karşılaştırması

Geliştiriciler için Docker görüntülerinizi oluşturmak, Microsoft aşağıdaki ana senaryoları odaklanır:

-   Kullanılacak görüntüleri *geliştirmek* ve .NET Core uygulamaları oluşturun.

-   Kullanılacak görüntüleri *çalıştırmak* .NET Core uygulamaları.

Neden birden fazla görüntü? Geliştirme, derleme ve kapsayıcılı uygulamaları çalıştıran genellikle farklı önceliklere sahip. Microsoft, bu farklı görevler için farklı görüntüleri sağlayarak, geliştirme, derleme ve uygulamaları dağıtma ayrı işlemleri en iyi duruma getirme yardımcı olur.

### <a name="during-development-and-build"></a>Geliştirme ve derleme sırasında

Geliştirme sırasında ne kadar hızlı değişiklikler ve değişiklikleri hata ayıklama özelliği yineleyebilirsiniz önemli olan ' dir. Görüntü boyutunu kodunuzda değişiklikler yapmak ve değişiklikleri hızlıca görmek yeteneği gibi önemli değildir. Bazı araçlar ve "yapı aracısı kapsayıcıları" ASP.NET Core görüntü geliştirme kullanır (**microsoft / dotnet:2.1-sdk**) geliştirme ve oluşturma işlemi sırasında. Docker kapsayıcısı içindeki oluştururken, önemli yönlerinden uygulamanızı derlemek için gereken öğelerdir. Bu, derleyici ve herhangi diğer .NET bağımlılıkları yanı sıra web geliştirme bağımlılıkları içerir.

Bu tür yapı görüntü neden önemlidir? Bu görüntü üretime dağıtmayın. Bunun yerine, bir üretim görüntüsüne yerleştirdiğiniz içeriği oluşturmak için kullandığınız bir görüntüdür. Bu görüntü, sürekli tümleştirme (CI) ortamınızda kullanılacak veya Docker çok aşama kullanırken yapı ortamı oluşturur.

### <a name="in-production"></a>Üretimde

Üretimde önemlidir ne kadar hızlı dağıtma ve üretim .NET Core görüntüyü temel alarak kapsayıcılarınızı başlatma ' dir. Bu nedenle, yalnızca çalışma zamanında resmin dayalı olarak **microsoft / dotnet:2.1-aspnetcore-çalışma zamanı** küçük, böylelikle onu hızlı bir şekilde ağ üzerinden Docker kayıt defterinden Docker konaklarınızın izler. Sonuçlar işlenirken kapsayıcıya başlatılmasını süreye etkinleştirme içeriği çalıştırmak hazır olursunuz. Docker modelinde c derleme için gerek yoktur\# kod, orada ne zaman dotnet yapı çalıştırmak veya dotnet yayımlama yapı kapsayıcı kullanıyor.

Bu en iyi duruma getirilmiş yansımasına yalnızca ikili dosyaları ve uygulamayı çalıştırmak için gereken diğer içeriği yerleştirin. Örneğin, dotnet tarafından oluşturulmuş içerik yayımlama yalnızca derlenmiş .NET ikili dosyaları, görüntüler, .js ve .css dosyaları içerir. Zaman içinde öncesi jitted paketleri içeren resimler görürsünüz.

.NET Core ve ASP.NET Core görüntüleri birden fazla sürümünü olsa da, tüm temel katmanın dahil olmak üzere, bir veya daha fazla katmanları paylaşın. Bu nedenle, görüntüyü depolamak için gereken disk alanı miktarını küçüktür; yalnızca özel görüntünüzü ve temel görüntü arasındaki delta oluşur. Kayıt defterinden görüntü çekmesini hızlı sonucudur.

Docker hub'a adresindeki .NET görüntü depoları geçirirken, sınıflandırılmış veya etiketleriyle işaretlenmiş birden fazla görüntü sürümleri bulacaksınız. Bu etiketler hangisinin, aşağıdaki tabloda bulunanlar gibi ihtiyaç sürümüne bağlı olarak kullanmaya karar vermenize yardımcı olur:

-   Microsoft/dotnet:**2.1 aspnetcore çalışma**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**dotnet:2.1-sdk**

        .NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Önceki] (net-kapsayıcı-os-targets.md) [sonraki] (.. /Architect-microservice-Container-Applications/index.MD)
