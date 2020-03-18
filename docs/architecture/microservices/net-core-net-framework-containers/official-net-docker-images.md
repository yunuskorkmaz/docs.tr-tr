---
title: Resmi .NET Docker görüntüleri
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Resmi .NET Docker görüntüleri
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501872"
---
# <a name="official-net-docker-images"></a>Resmi .NET Docker görüntüleri

Official .NET Docker görüntüleri, Microsoft tarafından oluşturulan ve optimize edilen Docker görüntüleridir. Bunlar, [Docker Hub'daki](https://hub.docker.com/u/microsoft/)Microsoft depolarında herkese açıktır. Her depo ,.NET sürümlerine ve işletim sistemi ve sürümlerine (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, vb.) bağlı olarak birden çok görüntü içerebilir.

.NET Core 2.1'den bu yana, ASP.NET Core dahil olmak üzere tüm .NET Core görüntüleri Docker <https://hub.docker.com/_/microsoft-dotnet-core/>Hub'da .NET Core görüntü deposunda mevcuttur: .

Mayıs 2018'den bu yana Microsoft görüntüleri [Microsoft Konteyner Kayıt Defteri'nde sendikasyon](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/)alabilmemektedir. Resmi katalog hala yalnızca Docker Hub'da mevcuttur ve görüntüyü çekmek için güncelleştirilmiş adresi orada bulacaksınız.

Çoğu resim deposu, yalnızca belirli bir çerçeve sürümünü değil, aynı zamanda bir işletim sistemi (Linux dağıtımı veya Windows sürümü) seçmenize yardımcı olmak için kapsamlı etiketleme sağlar.

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET Core ve Docker görüntü optimizasyonları için geliştirme ve üretim

Geliştiriciler için Docker görüntüleri yaparken, Microsoft aşağıdaki ana senaryolara odaklanmıştır:

- .NET Core uygulamaları *geliştirmek* ve oluşturmak için kullanılan görüntüler.

- .NET Core uygulamalarını *çalıştırmak* için kullanılan görüntüler.

Neden birden fazla resim? Kapsayıcı uygulamaları geliştirirken, inşa ederken ve çalıştırırken genellikle farklı öncelikleriniz vardır. Microsoft, bu ayrı görevler için farklı görüntüler sağlayarak, uygulamaları geliştirme, oluşturma ve dağıtma işlemlerini optimize etmeye yardımcı olur.

### <a name="during-development-and-build"></a>Geliştirme ve inşa sırasında

Geliştirme sırasında önemli olan değişiklikleri ne kadar hızlı yinelediğiniz ve değişiklikleri ayıklama yeteneğidir. Görüntünün boyutu, kodunuzda değişiklik yapma ve değişiklikleri hızlı bir şekilde görme yeteneği kadar önemli değildir. Bazı araçlar ve "yapı aracıkapsayıcıları", geliştirme ve oluşturma işlemi sırasında .NET Core görüntüsünü *(mcr.microsoft.com/dotnet/core/sdk:3.1)* kullanır. Docker konteynerinin içine bina yaparken, önemli hususlar uygulamanızı derlemek için gereken öğelerdir. Bu derleyici ve diğer .NET bağımlılıkları içerir.

Bu tür yapı görüntüsü neden önemlidir? Bu görüntüyü üretime dağıtamazsınız. Bunun yerine, yerleştirdiğiniz içeriği bir üretim resmine oluşturmak için kullandığınız bir görüntü. Bu görüntü, Docker çok aşamalı yapılarını kullanırken sürekli tümleştirme (CI) ortamınızda veya yapı ortamınızda kullanılır.

### <a name="in-production"></a>Üretimde

Üretimde önemli olan, bir üretim .NET Core görüntüsüne dayalı olarak kaplarınızı ne kadar hızlı dağıtabileceğiniz ve başlatabileceğinizdir. Bu nedenle, *yalnızca mcr.microsoft.com/dotnet/core/aspnet:3.1* dayalı çalışma zamanı görüntüsü küçüktür, böylece Docker kayıt defterinizden Docker ev sahiplerine kadar ağ üzerinde hızlı bir şekilde seyahat edebilir. İçeriği çalışmaya hazır dır, bu da kapsayıcının başlatılmasından işleme sonuçlarına kadar en hızlı zamanı sağlar. Docker modelinde, yapı kapsayıcısını kullanırken\# dotnet build veya dotnet yayımlama çalıştırdığınızda olduğu gibi C kodundan derlemeye gerek yoktur.

Bu optimize edilmiş görüntüde, uygulamayı çalıştırmak için gereken yalnızca ikili leri ve diğer içeriği koyarsınız. Örneğin, yalnızca `dotnet publish` derlenen .NET ikilileri, resimler, .js ve .css dosyalarını içeren içerik. Zamanla, önceden jitted içeren görüntüler görürsünüz (çalışma zamanında oluşan IL'den yerele derleme).

.NET Core ve ASP.NET Core görüntülerinin birden çok sürümü olmasına rağmen, hepsi temel katman da dahil olmak üzere bir veya daha fazla katmanı paylaşır. Bu nedenle, bir görüntüyü depolamak için gereken disk alanı miktarı küçüktür; yalnızca özel görüntünüz ile temel görüntüsü arasındaki deltadan oluşur. Sonuç olarak, resmi kayıt defterinizden hızlı bir şekilde çekin.

Docker Hub'daki .NET resim depolarını keşfettiğiniz zaman, etiketlerle sınıflandırılmış veya işaretlenmiş birden çok resim sürümü bulacaksınız. Bu etiketler, aşağıdaki tablodakiler gibi gereksinim duyduğunuz sürüme bağlı olarak hangisini kullanacağınıza karar vermenize yardımcı olur:

| Görüntü | Yorumlar |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3.1** | ASP.NET Core, yalnızca çalışma süresi ve ASP.NET Core optimizasyonları ile Linux ve Windows'da (çoklu kemer) |
| mcr.microsoft.com/dotnet/core/sdk:**3.1** | .NET Core, SDK'lar dahil, Linux ve Windows 'ta (multi-arch) |

> [!div class="step-by-step"]
> [Önceki](net-container-os-targets.md)
> [Sonraki](../architect-microservice-container-applications/index.md)
