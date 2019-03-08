---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsü destek en önemli geliştirme aracı seçenekleri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 38a9f8209200635c752f60af90e22ef916796525
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677246"
---
# <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

## <a name="development-tools-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi, isterseniz olursa olsun Microsoft, Docker uygulamaları geliştirme geldiği zaman işinize yarayacaktır.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code ve Docker CLI'yı (Mac, Linux ve Windows için platformlar arası araçları)

Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyici tercih ederseniz, Visual Studio Code ve Docker CLI'yı kullanabilirsiniz. Bu ürünler, geliştirici iş akışını hızlandırma için kritik bir basit ama güçlü deneyimi sağlar. "Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiricileri, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz. Ayrıca, Visual Studio Code için Docker ile düzenleyiciden Docker komutlarını çalıştırmak dockerfile'ları ve kısayol görevler için IntelliSense uzantıları destekler.

> [!NOTE]
>
> Visual Studio Code'u indirmek için Git <https://code.visualstudio.com/download>.
>
> Mac ve Windows için Docker'ı indirmek için Git <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio ile Docker Araçları (Windows geliştirme makinesi)

Visual Studio 2017 (veya üstü) kullanmanızı öneririz etkin yerleşik Docker araçları ile. Visual Studio ile geliştirin, çalıştırın ve uygulamalarınızı doğrudan seçtiğiniz Docker ortamında doğrulayın. Uygulamanızda (tek kapsayıcı ya da birden çok kapsayıcı) doğrudan bir Docker konağı hata ayıklamak için F5 tuşuna basın veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için Ctrl + F5 tuşlarına basın. Linux veya Windows için Docker kapsayıcıları oluşturmak Windows geliştiricileri için basit ve en güçlü seçenek var.

### <a name="visual-studio-for-mac-mac-development-machine"></a>(Mac geliştirme makinesi) Mac için Visual Studio

Kullanabileceğiniz [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/) Docker tabanlı uygulamalar geliştirirken. Mac için Visual Studio Mac için Visual Studio Code için karşılaştırıldığında daha zengin bir IDE sunar.

## <a name="language-and-framework-choices"></a>Dil ve çerçeve seçenekleri

Microsoft araçları ile modern dilleri kullanarak Docker uygulamaları geliştirebilirsiniz. İlk bir listesi verilmiştir, ancak kendisine sınırlı değildir:

- .NET Core ve ASP.NET Core
- Node.js
- Git
- Java
- Ruby
- Python

Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dilde kullanabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](deploy-azure-kubernetes-service.md)
>[İleri](docker-apps-inner-loop-workflow.md)
