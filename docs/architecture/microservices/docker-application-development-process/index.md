---
title: Docker Tabanlı Uygulamalar için Geliştirme İşlemi
description: Docker tabanlı uygulamalar geliştirmeye yönelik seçeneklere yönelik yüksek düzeyde bir genel bakış alın. Çoklu platform desteği (Windows, Mac ve Linux) için Windows, Mac için Visual Studio veya Visual Studio Code için istediğiniz Visual Studio 'Yu kullanma.
ms.date: 09/27/2018
ms.openlocfilehash: 6299d67299948dce1081a211b350e657b2c1b951
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770133"
---
# <a name="development-process-for-docker-based-applications"></a>Docker tabanlı uygulamalar için geliştirme süreci

*Visual Studio ve Docker için Visual Studio Araçları ve Docker CLı ve Visual Studio Code odaklanmış CLı/düzenleyici için Visual Studio ile odaklanmış bir şekilde, Kapsayıcılı .NET uygulamaları geliştirin.*

## <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

### <a name="development-tool-choices-ide-or-editor"></a>Geliştirme aracı seçimleri: IDE veya düzenleyici

Tam ve güçlü bir IDE veya hafif ve çevik bir düzenleyiciyi tercih etmeksizin, Microsoft, Docker uygulamaları geliştirmek için kullanabileceğiniz araçlara sahiptir.

**Visual Studio (Windows için).** Visual Studio ile Docker tabanlı uygulamalar geliştirirken, zaten yerleşik olan Docker Araçları ile birlikte sunulan Visual Studio 2017 sürüm 15,7 veya sonraki bir sürümünü kullanmanız önerilir. Docker Araçları, uygulamalarınızı doğrudan hedef Docker ortamında geliştirmenize, çalıştırmanıza ve doğrulamanıza olanak sağlar. F5 tuşuna basarak uygulamanızı (tek bir kapsayıcı veya birden çok kapsayıcı) doğrudan bir Docker konağına kaydedebilir ve hata ayıklamanızı sağlar veya kapsayıcıyı yeniden oluşturmak zorunda kalmadan uygulamanızı düzenlemek ve yenilemek için CTRL + F5 ' e basabilirsiniz. Bu, Docker tabanlı uygulamalar için en güçlü geliştirme seçimdir.

**Mac için Visual Studio.** Bu, macOS 'ta çalışan Xamarin Studio bir IDE, ve m2017 ' den beri Docker destekler. Bu, güçlü bir IDE kullanmak isteyen Mac makinelerde çalışan geliştiriciler için tercih edilen seçim olmalıdır.

**Visual Studio Code ve Docker CLI**. Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyiciyi tercih ediyorsanız, Microsoft Visual Studio kodu (VS Code) ve Docker CLı kullanabilirsiniz. Bu, Mac, Linux ve Windows için platformlar arası bir geliştirme yaklaşımıdır. Ayrıca, Visual Studio Code Dockerfiles için IntelliSense ve düzenleyiciden Docker komutlarını çalıştırmak için kısayol görevleri gibi Docker için uzantıları destekler.

[Docker Desktop Community Edition 'ı (CE)](https://hub.docker.com/search/?type=edition&offering=community)yükleyerek, tek bir DOCKER CLI kullanarak hem Windows hem de Linux için uygulama oluşturabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Visual Studio**. Resmi site. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Resmi site. \
  <https://code.visualstudio.com/download>

- **Windows Community Edition Için Docker Desktop (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Mac Community Edition Için Docker Desktop (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Docker kapsayıcıları için .NET dilleri ve çerçeveleri

Bu kılavuzun önceki bölümlerinde belirtildiği gibi, Docker Kapsayıcılı .NET uygulamaları geliştirirken .NET Framework, .NET Core veya açık kaynaklı mono projesi kullanabilirsiniz. Hangi .NET Framework 'ün kullanımda olduğuna bağlı olarak, Linux veya Windows kapsayıcılarını hedeflemek için C \#, F \# veya Visual Basic geliştirebilirsiniz. Daha ayrıntılı about.NET dil için bkz. [.NET dil stratejisi](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/)blog gönderisi.

>[!div class="step-by-step"]
>[Önceki](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[İleri](docker-app-development-workflow.md)
