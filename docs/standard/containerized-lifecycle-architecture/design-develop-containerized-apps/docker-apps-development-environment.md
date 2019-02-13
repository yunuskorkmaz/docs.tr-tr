---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsü destek en önemli geliştirme aracı seçenekleri tanışın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1d22b45a8eee9198d337df9f0b8b4b78371fa31a
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220003"
---
# <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

## <a name="development-tools-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da basit ve Çevik Düzenleyicisi, isterseniz olursa olsun Microsoft, Docker uygulamaları geliştirme geldiği zaman işinize yarayacaktır.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code ve Docker CLI'yı (Mac, Linux ve Windows için platformlar arası araçları)

Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyici tercih ederseniz, Visual Studio Code ve Docker CLI'yı kullanabilirsiniz. Bu ürünler, geliştirici iş akışını hızlandırma için kritik bir basit ama güçlü deneyimi sağlar. "Docker için Mac" veya "Docker için Windows" (geliştirme ortamı) yükleyerek Docker geliştiricileri, Windows veya Linux (çalışma zamanı ortamı) için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz. Ayrıca, Visual Studio Code için Docker ile düzenleyiciden Docker komutlarını çalıştırmak dockerfile'ları ve kısayol görevler için IntelliSense uzantıları destekler.

> [!NOTE]
> Visual Studio Code'u indirmek için Git <https://code.visualstudio.com/download>.

Mac ve Windows için Docker'ı indirmek için Git <https://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio ile Docker araçları

Visual Studio 2015 kullanıyorsanız "Visual Studio için Docker araçları." eklenti araçları yükleyebilirsiniz. Visual Studio 2017 için Docker Araçları zaten yerleşik gelir. Her iki durumda da geliştirin, çalıştırın ve uygulamalarınızı doğrudan seçtiğiniz Docker ortamında doğrulayın. F5 uygulamanıza (tek kapsayıcı ya da birden çok kapsayıcı) doğrudan bir Docker hata ayıklama ile ana bilgisayar veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için Ctrl + F5 tuşlarına basın. Linux veya Windows için Docker kapsayıcıları oluşturma Windows geliştiricileri için basit ve daha güçlü seçenek budur.

> [!NOTE]
> Visual Studio için Docker araçları indirmek için Git <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Dil ve çerçeve seçenekleri

Docker uygulamaları ve Microsoft araçları en modern dilde geliştirebilirsiniz. İlk bir listesi verilmiştir, ancak kendisine sınırlı değildir:

-   .NET Core ve ASP.NET Core
-   Node.js
-   Golang
-   Java
-   Ruby
-   Python

Temel olarak, Linux veya Windows Docker tarafından desteklenen herhangi bir modern dilde kullanabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](deploy-azure-kubernetes-service.md)
>[İleri](docker-apps-inner-loop-workflow.md)