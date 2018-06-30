---
title: Docker uygulamalar için geliştirme ortamı
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3da7816127982c3657129561975eed6d1f5aad5a
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104513"
---
# <a name="development-environment-for-docker-apps"></a>Docker uygulamalar için geliştirme ortamı

## <a name="development-tools-choices-ide-or-editor"></a>Geliştirme araçları seçenekleri: IDE veya Düzenleyicisi

Tam ve güçlü bir IDE veya basit ve Çevik Düzenleyicisi tercih ederseniz bağımsız Microsoft, Docker uygulamaları geliştirme geldiği zaman kapsamdaki sahiptir.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code ve Docker CLI (Mac, Linux ve Windows için platformlar arası araçları)

Herhangi bir geliştirme dili destekleyen bir basit, platformlar arası Düzenleyicisi tercih ederseniz, Visual Studio Code ve Docker CLI kullanabilirsiniz. Bu ürünler Geliştirici iş akışı hızlandırma için kritik bir basit ancak güçlü deneyimi sağlar. "Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiriciler, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI kullanabilir. Ayrıca, Visual Studio Code uzantıları Docker Dockerfiles ve kısayol görevleri Düzenleyicisi'nden Docker komutları çalıştırmak için IntelliSense ile destekler.

> [!NOTE]
> Visual Studio Code indirmek için Git <https://code.visualstudio.com/download>.

Mac ve Windows için Docker indirmek için Git <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Docker araçları ile Visual Studio

Visual Studio 2015 kullanırken eklenti Araçları "Visual Studio Araçları Docker". yükleyebilirsiniz Visual Studio 2017 Docker Araçları zaten içinde yerleşik olarak sunulur. Her iki durumda da geliştirmek, çalıştırmak ve uygulamalarınızı seçilen Docker ortamında doğrudan doğrulayın. F5 uygulamanıza (tek kapsayıcısı veya birden çok kapsayıcı) doğrudan bir Docker hata ayıklama ile ana bilgisayar veya düzenleyin ve kapsayıcı yeniden oluşturmak zorunda kalmadan, uygulamanızın yenilemek için Ctrl + F5'e basın. Linux veya Windows için Docker kapsayıcıları oluşturma Windows geliştiriciler için basit ve daha güçlü seçenek budur.

> [!NOTE]
> Visual Studio için Docker Araçları'nı indirmek için Git <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Dil ve çerçeve seçenekleri

Docker uygulamaları ve çoğu modern dilleri Microsoft araçlarla geliştirme yapabilirsiniz. Başlangıç listesi aşağıda verilmiştir ancak ona sınırlı değildir:

-   .NET core ve ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dil kullanabilirsiniz.


>[!div class="step-by-step"]
[Önceki](orchestrate-high-scalability-availability.md)
[sonraki](docker-apps-inner-loop-workflow.md)
