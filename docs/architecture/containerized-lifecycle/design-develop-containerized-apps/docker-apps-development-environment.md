---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsünü destekleyen en önemli geliştirme aracı seçeneklerini öğrenin.
ms.date: 04/16/2020
ms.openlocfilehash: b1df16db88fa85f794407c989f5428030c4cddf7
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394896"
---
# <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

## <a name="development-tools-choices-ide-or-editor"></a>Geliştirme araçları seçimleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da hafif ve çevik bir düzenleyiciyi tercih ediyorsanız, Microsoft, Docker uygulamaları geliştirmeye ne zaman bahsedildiğinizi de kapsamıştır.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code ve Docker CLı (Mac, Linux ve Windows için platformlar arası araçlar)

Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyiciyi tercih ediyorsanız, Visual Studio Code ve Docker CLı kullanabilirsiniz. Bu ürünler, geliştirici iş akışını hızlandırma açısından kritik olan basit ancak sağlam bir deneyim sağlar. Docker geliştiricileri, "Docker for Mac" veya "Docker for Windows" (geliştirme ortamı) yükleyerek, tek bir Docker CLı kullanarak hem Windows hem de Linux (çalışma zamanı ortamı) için uygulama oluşturabilir. Ayrıca, Visual Studio Code Dockerfiles için IntelliSense ile Docker uzantılarını ve düzenleyiciden Docker komutlarını çalıştırmak için kısayol görevlerini destekler.

> [!NOTE]
> Visual Studio Code indirmek için bölümüne gidin <https://code.visualstudio.com/download> .
>
> Mac ve Windows için Docker indirmek için adresine gidin <https://www.docker.com/products/docker> .

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio ile Docker Araçları (Windows geliştirme makinesi)

Yerleşik Docker Araçları 'nın etkin olduğu Visual Studio 2019 ' i kullanmanızı öneririz. Visual Studio ile uygulamalarınızı doğrudan seçilen Docker ortamında geliştirebilir, çalıştırabilir ve doğrulayabilirsiniz. Uygulamanızda (tek kapsayıcı veya birden çok kapsayıcı) doğrudan bir Docker konağında hata ayıklamak için F5 tuşuna basın veya kapsayıcıyı yeniden oluşturmak zorunda kalmadan uygulamanızı düzenlemek ve yenilemek için CTRL + F5 tuşlarına basın. Windows geliştiricilerinin Linux veya Windows için Docker Kapsayıcıları oluşturması için kullanabileceğiniz en basit ve en güçlü seçenektir.

### <a name="visual-studio-for-mac-mac-development-machine"></a>Mac için Visual Studio (Mac geliştirme makinesi)

Docker tabanlı uygulamalar geliştirirken [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanabilirsiniz. Mac için Visual Studio, Mac için Visual Studio Code karşılaştırıldığında daha zengin bir IDE sağlar.

## <a name="language-and-framework-choices"></a>Dil ve çerçeve seçimleri

En modern dillerle Microsoft araçları 'nı kullanarak Docker uygulamaları geliştirebilirsiniz. Aşağıda bir başlangıç listesi verilmiştir ancak bunlarla sınırlı değilsiniz:

- .NET Core ve ASP.NET Core
- Node.js
- Başlayın
- Java
- Ruby
- Python

Temel olarak, Linux veya Windows 'da Docker tarafından desteklenen tüm modern dilleri kullanabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](deploy-azure-kubernetes-service.md) 
> [Sonraki](docker-apps-inner-loop-workflow.md)
