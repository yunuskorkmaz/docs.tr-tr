---
title: Geliştirme işlemi için Docker tabanlı uygulamalar
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Geliştirme işlemi için Docker tabanlı uygulamalar
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 7736c1fe4cb1a2a4553ba36cecceab37e2fe90c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144474"
---
# <a name="development-process-for-docker-based-applications"></a>Docker tabanlı uygulamalar için geliştirme işlemi

*Kapsayıcılı .NET uygulamaları, istediğiniz şekilde Docker için Visual Studio ve Visual Studio Araçları ile odaklanmış IDE veya CLI/düzenleyici ile Docker CLI ve Visual Studio Code odaklı geliştirin.*

## <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

### <a name="development-tool-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da basit ve Çevik bir düzenleyici tercih olsun, Microsoft Docker uygulamaları geliştirmek için kullanabileceğiniz araçları vardır.

**Visual Studio (Windows)**. Docker tabanlı uygulamalar geliştirmek için Visual Studio 2017 veya zaten yerleşik için Docker araçları ile birlikte gelen sonraki sürümleri kullanın. Geliştirin, çalıştırın ve uygulamalarınızı doğrudan hedef Docker ortamında doğrulamak için Docker araçları sağlar. F5 tuşuna basarak çalıştırın ve doğrudan bir Docker Konağı (tek kapsayıcı ya da birden çok kapsayıcı), uygulamanızın hata ayıklama veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için CTRL + F5 tuşlarına basın. Docker tabanlı uygulamalar için en güçlü geliştirme seçenek budur.

**Mac için Visual Studio**. Bu, bir IDE macOS üzerinde çalışır ve Docker tabanlı uygulama geliştirmeyi destekleyen Xamarin Studio evrimi olur. Bu da güçlü bir IDE kullanmak isteyen Mac makinelerinizde çalışan geliştiriciler için tercih edilen seçenek olmalıdır.

**Visual Studio Code ve Docker CLI**. Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyici tercih ederseniz, Microsoft Visual Studio Code (VS Code) ve Docker CLI'yı kullanabilirsiniz. Bu, Mac, Linux ve Windows için platformlar arası geliştirme yaklaşımdır.

Yükleyerek [Docker Community Edition'ı (CE)](https://www.docker.com/community-edition) araçları, Windows ve Linux için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz. Ayrıca, Visual Studio Code için Docker düzenleyiciden Docker komutlarını çalıştırmak için dockerfile'ları ve kısayol görevler için IntelliSense gibi uzantıları destekler.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Docker için Visual Studio Araçları**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)

-   **Visual Studio Code**. Resmi sitesi.
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Mac ve Windows için docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET dil ve çerçeveyi kullanabilmek için Docker kapsayıcıları

Geliştirme Docker kapsayıcılı .NET uygulamaları, bu kılavuzun önceki bölümlerde belirtildiği gibi .NET Framework, .NET Core ve açık kaynaklı Mono projesi kullanabilirsiniz. C'de geliştirebilirsiniz\#, F\#, ya da Linux veya Windows kapsayıcıları, bağlı olarak hangi .NET framework, kullanımda olan hedeflenirken VisualBasic. Daha fazla ayrıntı about.NET diller için blog gönderisine bakın [.NET dil stratejisi](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Önceki](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[İleri](docker-app-development-workflow.md)