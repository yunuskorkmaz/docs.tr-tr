---
title: Resmi .NET Docker görüntüleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Resmi .NET Docker görüntüleri
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: c4fce49b079473ddcc2b840527b8aeb951fec780
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674659"
---
# <a name="official-net-docker-images"></a>Resmi .NET Docker görüntüleri

Resmi .NET Docker görüntüleri oluşturulan ve Microsoft tarafından en iyi duruma getirilmiş Docker görüntüleridir. Microsoft depolara göre genel kullanıma açık olduğu [Docker Hub](https://hub.docker.com/u/microsoft/). Her depo bağlı .NET sürümleri ve işletim sistemi ve sürümleri (Linux, Debian, Alpine Linux, Windows Nano sunucu, Windows Server Core, vb.) bağlı olarak birden çok görüntüsü içerebilir.

.NET Core 2.1 beri ASP.NET Core için de dahil olmak üzere tüm .NET Core görüntüleri adresinde deponun .NET Core görüntü Docker Hub kullanılabilir: https://hub.docker.com/r/microsoft/dotnet/

Çoğu resmi depoları, yalnızca belirli framework sürümü seçmenize yardımcı olmak için aynı zamanda (Linux distro veya Windows sürümü) bir işletim sistemi seçin kapsamlı etiketleme sağlar.

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Üretim ve geliştirme için .NET core ve Docker görüntü iyileştirmeleri

Geliştiriciler için Docker görüntülerini oluştururken, Microsoft aşağıdaki temel senaryolara odaklanır:

- Kullanılacak görüntüleri *geliştirme* ve .NET Core uygulamaları oluşturun.

- Kullanılacak görüntüleri *çalıştırma* .NET Core uygulamaları.

Neden birden çok görüntü? Geliştirme, derleme ve kapsayıcılı uygulamalar çalıştırmak, genellikle farklı önceliklere sahip. Microsoft, ayrı aşağıdaki görevler için farklı görüntüleri sağlayarak geliştirme, derleme ve uygulamaları dağıtma ayrı işlemleri iyileştirilmesine yardımcı olur.

### <a name="during-development-and-build"></a>Geliştirme ve derleme sırasında

Geliştirme sırasında ne kadar hızlı değişiklikler ve değişiklikleri hata ayıklama özelliği yineleyebilirsiniz önemli ' dir. Resmin boyutu kodunuzda değişiklikler yapmak ve değişiklikleri hızlıca görmek için özelliği gibi önemli değildir. Bazı araçlar ve "derleme aracısı kapsayıcılar" geliştirme .NET Core görüntüsü kullanma (*microsoft / dotnet:2.2-sdk*) geliştirme ve derleme işlemi sırasında. Bir Docker kapsayıcısı içinde oluştururken, önemli yönleri, uygulamanızı derlemek için gereken öğelerdir. Bu, derleyici ve diğer .NET bağımlılıklar içerir.

Bu tür bir yapı görüntüyü neden önemlidir? Bu görüntü için üretim dağıtmayın. Bunun yerine, bir üretim görüntüsüne yerleştirdiğiniz içerik oluşturmak için kullandığınız bir görüntüsüdür. Bu görüntü, sürekli tümleştirme (CI) ortamınızda kullanılan veya Docker çok aşamalı kullanırken yapı ortamı oluşturur.

### <a name="in-production"></a>Üretimde

Üretim ortamında önemli ne kadar hızlı dağıtabilir ve bir üretim .NET Core görüntüyle kapsayıcılarınızı Başlat ' dir. Bu nedenle, yalnızca çalışma zamanı görüntüyü temel alarak *microsoft / dotnet:2.2-aspnetcore-çalışma zamanı* , küçük, böylelikle onu hızlı ağ üzerinden Docker kayıt defterinizden Docker konaklarınıza izler. Sonuçları işleme için kapsayıcı başlatılmasını süreye etkinleştirme içeriğini çalıştırmak hazır olursunuz. Docker modelinde c derleme için gerek yoktur\# kod, derleme kapsayıcısı burada ne zaman dotnet yapıyı çalıştırmak veya dotnet yayımlama kullanıyor.

Bu en iyi duruma getirilmiş görüntüde yalnızca ikili dosyalar ve uygulamayı çalıştırmak için gereken diğer içerik yerleştirin. Örneğin, dotnet tarafından oluşturulan içerik yayımlama yalnızca derlenmiş .NET ikili dosyaları, görüntüler, .js ve .css dosyaları içerir. Zaman içinde pre-jıtted (IL derlemeden çalışma zamanında gerçekleşen yerel için) içeren resimler görürsünüz paketleri.

Birden çok sürümü .NET Core ve ASP.NET Core görüntülerin olsa da, tüm temel katman dahil, bir veya daha fazla katman paylaşırlar. Bu nedenle, bir görüntü depolamak için gereken disk alanı miktarını küçüktür; yalnızca özel görüntü ve taban görüntüsünü arasındaki delta oluşur. Görüntüyü kayıt defterinizden çekme hızlı sonucudur.

Docker Hub .NET resmi depoları geçirirken, Sınıflandırılmamış veya etiketlerle işaretlenmiş birden çok görüntü sürümü bulabilirsiniz. Bu etiketler, hangisinin kullanılacağını gelenler aşağıdaki tabloda, gereken sürümüne bağlı olarak karar vermek için yardımcı olur:

| Görüntü                                       | Açıklamalar                                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Microsoft/dotnet:**aspnetcore-2.2-çalışma zamanı** | ASP.NET Core, yalnızca çalışma zamanı ve ASP.NET Core iyileştirmeler, Linux ve Windows (çok arch) |
| Microsoft/dotnet:**2.2-sdk**                | .NET core SDK'ları dahil, Linux ve Windows (çok arch)                                  |

> [!div class="step-by-step"]
> [Önceki](net-container-os-targets.md)
> [İleri](../architect-microservice-container-applications/index.md)
