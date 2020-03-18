---
title: Docker tabanlı uygulamalar için geliştirme süreci
description: Docker tabanlı uygulamalar geliştirme seçeneklerine üst düzey bir genel bakış elde edin. Çok platformlu destek için Windows için Visual Studio, Mac için Visual Studio veya Visual Studio Code (Windows, macOS ve Linux) seçiminizi kullanma.
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77502714"
---
# <a name="development-process-for-docker-based-applications"></a>Docker tabanlı uygulamalar için geliştirme süreci

*Docker için Visual Studio ve Visual Studio araçlarıyla odaklanmış Entegre Geliştirme Ortamı (IDE) veya Docker CLI ve Visual Studio Code ile odaklanmış CLI/Editor ile kaplanmış .NET uygulamalarını istediğiniz gibi geliştirin.*

## <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

### <a name="development-tool-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya düzenleyici

İster tam ve güçlü bir IDE'yi ister hafif ve çevik bir düzenleyiciyi tercih edin, Microsoft Docker uygulamalarını geliştirmek için kullanabileceğiniz araçlara sahiptir.

**Visual Studio (Windows için).** Visual Studio ile Docker tabanlı .NET Core 3.1 uygulama geliştirme Visual Studio gerektirir 2019 sürüm 16.4 veya daha sonra. Visual Studio 2019, Docker için halihazırda yerleşik araçlarla birlikte geliyor. Docker için araçlar, uygulamalarınızı doğrudan hedef Docker ortamında geliştirmenize, çalıştırmanıza ve doğrulamanıza izin verebiliyor. Uygulamanızı çalıştırmak ve hata ayıklamak için F5 tuşuna basarak (tek kapsayıcı veya birden fazla kapsayıcı) doğrudan bir Docker ana bilgisayara veya kapsayıcıyı yeniden oluşturmanıza gerek kalmadan uygulamanızı düzenleyip yenilemek için CTRL+F5 tuşuna basabilirsiniz. Bu, Docker tabanlı uygulamalar için en güçlü geliştirme seçimidir.

**Mac için Visual Studio.** Bu bir IDE, Xamarin Studio evrimi, macOS çalışan. .NET Core 3.1 geliştirmeiçin sürüm 8.4 veya daha sonra gerektirir. Bu, güçlü bir IDE kullanmak isteyen macOS makinelerinde çalışan geliştiriciler için tercih edilen seçenek olmalıdır.

**Görsel Stüdyo Kodu ve Docker CLI**. Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyici tercih ederseniz, Visual Studio Code ve Docker CLI'yi kullanabilirsiniz. Bu macOS, Linux ve Windows için bir çapraz platform geliştirme yaklaşımıdır. Ayrıca Visual Studio Code, Docker komutlarını editörden çalıştırmak için IntelliSense for Dockerfiles ve kısayol görevleri gibi Docker uzantılarını destekler.

Docker [Desktop Community Edition'ı (CE)](https://hub.docker.com/search/?type=edition&offering=community)yükleyerek, hem Windows hem de Linux için uygulamalar oluşturmak için tek bir Docker CLI kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Görsel Stüdyo**. Resmi site. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Görsel Stüdyo Kodu**. Resmi site. \
  <https://code.visualstudio.com/download>

- **Windows Community Edition için Docker Masaüstü (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Mac Community Edition için Docker Masaüstü (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET dilleri ve Docker konteynerleri için çerçeveler

Bu kılavuzun önceki bölümlerinde belirtildiği gibi, Docker containerized .NET uygulamalarını geliştirirken .NET Framework, .NET Core veya açık kaynak Mono projesini kullanabilirsiniz. .NET çerçevesinin\#kullanıldığına bağlı olarak Linux veya Windows Kapsayıcılarını hedefalırken C, F\#veya Visual Basic olarak geliştirebilirsiniz. Dilleri about.NET daha fazla bilgi için [.NET Dil Stratejisi](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/)adlı blog yazısına bakın.

>[!div class="step-by-step"]
>[Önceki](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[Sonraki](docker-app-development-workflow.md)
