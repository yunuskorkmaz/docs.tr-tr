---
title: Resmi .NET Docker görüntüleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Resmi .NET Docker görüntüleri
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501872"
---
# <a name="official-net-docker-images"></a>Resmi .NET Docker görüntüleri

Resmi .NET Docker görüntüleri, Microsoft tarafından oluşturulan ve iyileştirilen Docker görüntüleridir. Bunlar, [Docker Hub](https://hub.docker.com/u/microsoft/)'daki Microsoft depolarında herkese açık bir şekilde sunulmaktadır. Her bir depo, .NET sürümlerine bağlı olarak birden çok görüntü içerebilir ve işletim sistemi ve sürümlere (Linux de, Linux alçam, Windows nano Server, Windows Server Core vb.) bağlıdır.

.NET Core 2,1 sürümünden itibaren, ASP.NET Core dahil olmak üzere tüm .NET Core görüntüleri .NET Core görüntü deposundaki Docker Hub 'ında bulunabilir: <https://hub.docker.com/_/microsoft-dotnet-core/>.

2018 Mayıs 'tan itibaren Microsoft görüntüleri [microsoft Container Registry dağıtılır](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/). Resmi katalog, hala Docker Hub 'ında mevcuttur ve görüntüyü çekmek için güncelleştirilmiş adresi bulacaksınız.

Çoğu görüntü deposu yalnızca belirli bir Framework sürümü değil, aynı zamanda bir işletim sistemi (Linux dağıtımı veya Windows sürümü) seçmenize yardımcı olmak için kapsamlı etiketleme sağlar.

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Geliştirme ve üretime karşı .NET Core ve Docker görüntü iyileştirmeleri

Geliştiriciler için Docker görüntüleri oluştururken, Microsoft aşağıdaki ana senaryolara odaklanılmıştır:

- .NET Core Uygulamaları *geliştirmek* ve derlemek için kullanılan görüntüler.

- .NET Core uygulamalarını *çalıştırmak* için kullanılan görüntüler.

Neden birden çok görüntü var? Kapsayıcılı uygulamalar geliştirirken, oluştururken ve çalıştırırken genellikle farklı önceliklere sahip olursunuz. Bu ayrı görevler için farklı görüntüler sağlayarak Microsoft, uygulamaları geliştirme, oluşturma ve dağıtmaya yönelik ayrı işlemleri iyileştirmenize yardımcı olur.

### <a name="during-development-and-build"></a>Geliştirme ve derleme sırasında

Geliştirme sırasında, ne kadar hızlı değişiklikler yineleyebileceğinizi ve değişikliklerin hatalarını ayıklamanın ne kadar hızlı olduğunu önemli bir öneme sahiptir. Görüntü boyutu, kodunuzda değişiklik yapma ve değişiklikleri hızlıca görme yeteneği kadar önemli değildir. Bazı araçlar ve "derleme Aracısı kapsayıcıları", geliştirme ve oluşturma işlemi sırasında geliştirme .NET Core görüntüsünü (*MCR.Microsoft.com/DotNet/Core/SDK:3.1*) kullanır. Bir Docker kapsayıcısı içinde oluştururken, önemli yönleri uygulamanızı derlemek için gereken öğelerdir. Bu, derleyicisini ve diğer .NET bağımlılıklarını içerir.

Bu tür derleme görüntüsü neden önemlidir? Bu görüntüyü üretime dağıtmazsınız. Bunun yerine, bir üretim görüntüsüne yerleştirdiğiniz içeriği oluşturmak için kullandığınız bir görüntüdür. Bu görüntü, Docker Multi-Stage derlemeleri kullanılırken sürekli tümleştirme (CI) ortamınızda veya yapı ortamınızda kullanılacaktır.

### <a name="in-production"></a>Üretimde

Üretimde önemli olan özellikler, bir üretim .NET Core görüntüsüne göre kapsayıcıları dağıtmanıza ve başlatabilir. Bu nedenle, Docker Kayıt defterinizden Docker konaklarınıza ağ üzerinden hızla geçebilmesi için *MCR.Microsoft.com/DotNet/Core/ASPNET:3.1* tabanlı çalışma zamanı görüntüsü küçüktür. İçerik çalıştırılmaya hazırsa da, kapsayıcının sonuçları işlemeye başlaması için en hızlı süreyi etkinleştirir. Docker modelinde, derleme kapsayıcısını kullanırken DotNet derlemesini veya dotnet publish çalıştırdığınızda olduğu gibi, C\# kodundan derleme için ihtiyacınız yoktur.

Bu iyileştirilmiş görüntüde yalnızca, uygulamayı çalıştırmak için gereken ikili dosyaları ve diğer içerikleri yerleştirebilirsiniz. Örneğin, `dotnet publish` tarafından oluşturulan içerik yalnızca derlenmiş .NET ikilileri, görüntüleri,. js ve. CSS dosyalarını içerir. Zaman içinde, önceden içe geçmiş (çalışma zamanında gerçekleşen Il 'den yerel 'e derleme) paketleri içeren görüntüleri görürsünüz.

.NET Core ve ASP.NET Core görüntülerinin birden çok sürümü olsa da, hepsi temel katman dahil olmak üzere bir veya daha fazla katmanı paylaşır. Bu nedenle, bir görüntüyü depolamak için gereken disk alanı miktarı küçüktür; yalnızca özel görüntünüz ve onun temel görüntüsü arasındaki Delta bilgisinden oluşur. Sonuç olarak, görüntüyü Kayıt defterinizden çekmeniz hızlı bir hale gelir.

Docker Hub 'ında .NET görüntü depoları araştırdığınızda, etiketlerle sınıflandırılan veya işaretli birden çok görüntü sürümü bulacaksınız. Bu Etiketler, ihtiyacınız olan sürüme bağlı olarak, aşağıdaki tabloda olduğu gibi, hangisinin kullanılacağına karar vermenize yardımcı olur:

| Görüntü | Yorumlar |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3,1** | ASP.NET Core, yalnızca çalışma zamanı ve ASP.NET Core iyileştirmeleri, Linux ve Windows 'da (çoklu mimari) |
| mcr.microsoft.com/dotnet/core/sdk:**3,1** | .NET Core, SDK 'lar dahil, Linux ve Windows üzerinde (çoklu mimari) |

> [!div class="step-by-step"]
> [Önceki](net-container-os-targets.md)
> [İleri](../architect-microservice-container-applications/index.md)
