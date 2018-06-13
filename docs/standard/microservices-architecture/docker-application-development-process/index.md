---
title: Geliştirme işlemi için Docker tabanlı uygulamaları
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Geliştirme işlemi için Docker tabanlı uygulamaları
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 881817f4f1007edad85eefb9002d56764cbf2a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574790"
---
# <a name="development-process-for-docker-based-applications"></a>Docker tabanlı uygulamalar için geliştirme işlemi

*Kapsayıcılı .NET uygulamaları, istediğiniz şekilde Visual Studio ve Visual Studio Araçları ile için Docker odaklanmış IDE veya CLI/Düzenleyicisi Docker CLI ve Visual Studio Code ile odaklanmış geliştirin.*

## <a name="development-environment-for-docker-apps"></a>Docker uygulamalar için geliştirme ortamı

### <a name="development-tool-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya Düzenleyicisi

Microsoft, tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi tercih olsun, Docker uygulamaları geliştirmek için kullanabileceğiniz araçlar sahiptir.

**Visual Studio (Windows için)**. Docker tabanlı uygulamalar geliştirmek için Visual Studio 2017 veya Docker zaten yerleşik araçlarıyla birlikte gelir sonraki sürümlerinde kullanın. Docker için araçları geliştirmek, çalıştırmak ve uygulamalarınızda doğrudan hedef Docker ortam doğrulamanıza olanak tanır. Çalıştırın ve uygulamanızda (tek kapsayıcısı veya birden çok kapsayıcı) doğrudan bir Docker ana hata ayıklama için F5 tuşuna basın veya düzenleyin ve kapsayıcı yeniden oluşturmak zorunda kalmadan, uygulamanızın yenilemek için CTRL + F5'e basın. Bu Docker tabanlı uygulamalar için en güçlü geliştirme seçimdir.

**Mac için Visual Studio**. Bu, bir IDE macOS üzerinde çalışır ve Docker tabanlı uygulama geliştirme destekleyen Xamarin Studio evrimi olur. Bu Mac makinelerinizde çalışma de güçlü bir IDE kullanmak isteyen geliştiriciler için tercih edilen seçenek olmalıdır.

**Visual Studio Code ve Docker CLI**. Herhangi bir geliştirme dili destekleyen bir basit ve platformlar arası Düzenleyicisi tercih ederseniz, Microsoft Visual Studio Code (VS Code) ve Docker CLI kullanabilirsiniz. Bu, Mac, Linux ve Windows için platformlar arası geliştirme yaklaşımdır.

Yükleyerek [Docker Community Edition (CE)](https://www.docker.com/community-edition) araçları, Windows ve Linux için uygulamalar oluşturmak için tek bir Docker CLI kullanabilirsiniz. Ayrıca, Visual Studio Code Docker Düzenleyicisi'nden Docker komutları çalıştırmak için Dockerfiles ve kısayol görevleri için IntelliSense gibi uzantıları destekler.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Docker için Visual Studio Araçları**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)

-   **Visual Studio Code**. Resmi sitesi.
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Mac ve Windows için docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET dilleri ve çerçeveleri Docker kapsayıcıları için

Geliştirme Docker .NET uygulamaları kapsayıcılı olduğunda bu kılavuzun önceki bölümlerinde belirtildiği gibi .NET Framework, .NET Core ve açık kaynaklı Mono proje kullanabilirsiniz. C'de geliştirebilirsiniz\#, F\#, ya da Linux veya Windows kapsayıcıları, bağlı olarak hangi .NET framework kullanılıyor hedeflerken Visual Basic. Daha fazla ayrıntı about.NET diller için blog gönderisine bakın [.NET dil stratejisi](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).


>[!div class="step-by-step"]
[Önceki] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [sonraki] (docker-app-development-workflow.md)
