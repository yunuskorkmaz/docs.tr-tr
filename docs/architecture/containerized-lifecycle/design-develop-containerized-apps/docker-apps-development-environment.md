---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsünü destekleyen en önemli geliştirme aracı seçeneklerini tanıyın.
ms.date: 02/15/2019
ms.openlocfilehash: 35236e75f47e830d0970ca9cfd074d9a69e6f85c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71214297"
---
# <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

## <a name="development-tools-choices-ide-or-editor"></a>Geliştirme araçları seçenekleri: IDE veya düzenleyici

Tam ve güçlü bir IDE veya hafif ve çevik bir düzenleyici tercih ederseniz edin, Microsoft docker uygulamaları geliştirme söz konusu olduğunda size kapalı vardır.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code ve Docker CLI (Mac, Linux ve Windows için çapraz platform araçları)

Herhangi bir geliştirme dilini destekleyen hafif, çapraz platform düzenleyicisini tercih ederseniz, Visual Studio Code ve Docker CLI'yi kullanabilirsiniz. Bu ürünler, geliştirici iş akışını kolaylaştırmak için kritik öneme sahip basit ama sağlam bir deneyim sağlar. Docker geliştiricileri "Docker for Mac" veya "Docker for Windows" (geliştirme ortamı) yazılımlarını yükleyerek, hem Windows hem de Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI kullanabilirler. Ayrıca, Visual Studio Code, Docker dosyaları için IntelliSense ile Docker uzantılarını ve editörden Docker komutlarını çalıştırmak için kısayol görevlerini destekler.

> [!NOTE]
> Visual Studio Code'u <https://code.visualstudio.com/download>indirmek için .
>
> Mac ve Windows için Docker'ı <https://www.docker.com/products/docker>indirmek için .

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Docker Tools ile Visual Studio (Windows geliştirme makinesi)

Yerleşik Docker Tools etkinken Visual Studio 2017 (veya sonraki) kullanmanızı öneririz. Visual Studio ile uygulamalarınızı doğrudan seçilen Docker ortamında geliştirebilir, çalıştırabilir ve doğrulayabilirsiniz. Uygulamanızı doğrudan docker ana bilgisayarda hata ayıklamak için F5 tuşuna basın veya kapsayıcıyı yeniden oluşturmadan uygulamanızı düzenleyip yenilemek için Ctrl+F5 tuşuna basın. Windows geliştiricilerinin Linux veya Windows için Docker kapsayıcıları oluşturması en basit ve en güçlü seçimdir.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Mac için Visual Studio (Mac geliştirme makinesi)

Docker tabanlı uygulamalar geliştirirken [Mac için Visual Studio'yu](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanabilirsiniz. Mac için Visual Studio, Mac için Visual Studio Code ile karşılaştırıldığında daha zengin bir IDE sunar.

## <a name="language-and-framework-choices"></a>Dil ve çerçeve seçimleri

En modern dillere sahip Microsoft araçlarını kullanarak Docker uygulamaları geliştirebilirsiniz. Aşağıdaki bir başlangıç listesidir, ancak bununla sınırlı değildir:

- .NET Core ve ASP.NET Core
- Node.js
- Başlayın
- Java
- Ruby
- Python

Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dil kullanabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](deploy-azure-kubernetes-service.md)
>[Sonraki](docker-apps-inner-loop-workflow.md)
