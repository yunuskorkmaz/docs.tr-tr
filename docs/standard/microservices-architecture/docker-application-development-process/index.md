---
title: Docker Tabanlı Uygulamalar için Geliştirme İşlemi
description: Seçenekler Docker tabanlı uygulamalar geliştirmeye yönelik üst düzey bir bakış edinin. Windows için Visual Studio, Visual Studio seçtiğiniz Mac ya da Visual Studio Code için çok platformlu destek için (Windows, Mac ve Linux) kullanarak.
ms.date: 09/27/2018
ms.openlocfilehash: a32b27f3d98ed7ebf63b637ec0c979c22ee8e1e8
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690624"
---
# <a name="development-process-for-docker-based-applications"></a>Docker tabanlı uygulamalar için geliştirme işlemi

*Kapsayıcılı .NET uygulamaları, istediğiniz şekilde Docker için Visual Studio ve Visual Studio Araçları ile odaklanmış IDE veya CLI/düzenleyici ile Docker CLI ve Visual Studio Code odaklı geliştirin.*

## <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

### <a name="development-tool-choices-ide-or-editor"></a>Geliştirme aracı seçenekleri: IDE veya düzenleyici

Tam ve güçlü bir IDE ya da basit ve Çevik bir düzenleyici tercih olsun, Microsoft Docker uygulamaları geliştirmek için kullanabileceğiniz araçları vardır.

**Visual Studio (Windows).** Visual Studio ile Docker tabanlı uygulamalar geliştirirken, Visual Studio Araçları ile Docker zaten yerleşik gelen 2017 sürüm 15.7 veya üzeri, kullanmak için önerilir. Geliştirin, çalıştırın ve uygulamalarınızı doğrudan hedef Docker ortamında doğrulamak için Docker araçları sağlar. F5 tuşuna basarak çalıştırın ve doğrudan bir Docker Konağı (tek kapsayıcı ya da birden çok kapsayıcı), uygulamanızın hata ayıklama veya düzenleyin ve kapsayıcıyı yeniden derlemeye gerek kalmadan uygulamanızı yenilemek için CTRL + F5 tuşlarına basın. Docker tabanlı uygulamalar için en güçlü geliştirme seçenek budur.

**Mac için Visual Studio** Bu bir IDE olan Xamarin Studio, macOS çalıştıran evrimi ve Docker mid-2017 itibarıyla destekler. Bu da güçlü bir IDE kullanmak isteyen Mac makinelerinizde çalışan geliştiriciler için tercih edilen seçenek olmalıdır.

**Visual Studio Code ve Docker CLI**. Herhangi bir geliştirme dilini destekleyen hafif ve platformlar arası bir düzenleyici tercih ederseniz, Microsoft Visual Studio Code (VS Code) ve Docker CLI'yı kullanabilirsiniz. Bu, Mac, Linux ve Windows için platformlar arası geliştirme yaklaşımdır. Ayrıca, Visual Studio Code için Docker düzenleyiciden Docker komutlarını çalıştırmak için dockerfile'ları ve kısayol görevler için IntelliSense gibi uzantıları destekler.

Yükleyerek [Docker Masaüstü Community Edition'ı (CE)](https://hub.docker.com/search/?type=edition&offering=community), hem Windows hem de Linux için uygulamalar oluşturmak için tek bir Docker CLI'yı kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Visual Studio**. Resmi sitesi. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Resmi sitesi. \
  <https://code.visualstudio.com/download>

- **Docker Masaüstü Windows Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
  
- **Docker Masaüstü Mac Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET dil ve çerçeveyi kullanabilmek için Docker kapsayıcıları

Geliştirme Docker kapsayıcılı .NET uygulamaları, bu kılavuzun önceki bölümlerde belirtildiği gibi .NET Framework, .NET Core ve açık kaynaklı Mono projesi kullanabilirsiniz. C'de geliştirebilirsiniz\#, F\#, ya da Linux veya Windows kapsayıcıları, bağlı olarak hangi .NET framework, kullanımda olan hedeflenirken VisualBasic. Daha fazla ayrıntı about.NET diller için blog gönderisine bakın [.NET dil stratejisi](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Önceki](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[İleri](docker-app-development-workflow.md)
