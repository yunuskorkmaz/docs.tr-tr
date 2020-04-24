---
title: .NET Core giriş ve genel bakış
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmak için .NET'in modüler, yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f99b446bbd38b2b814c13afa13ab34cd5c9aa086
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645517"
---
# <a name="introduction-to-net-core"></a>NET Core’a giriş

[.NET Core](about.md) [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur. Birden çok programlama dilini kullanarak x64, x86, ARM32 ve ARM64 işlemcileri için Windows, macOS ve Linux için .NET Core uygulamaları oluşturabilirsiniz. Çerçeveler ve API'ler [bulut,](/aspnet/core/) [IoT,](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) [istemci UI](../desktop-wpf/overview/index.md)ve [makine öğrenimi](/dotnet/machine-learning/)için sağlanmaktadır.

.NET Core'u makinenizde denemek için [.NET Core SDK'yı indirin.](https://dotnet.microsoft.com/download) En son sürümü [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Karşıdan yükleme .NET Core

.NET Core'u aşağıdaki yollarla alabilirsiniz:

* [Windows ve macOS için yükleyiciler](https://dotnet.microsoft.com/download)
* [Linux paketleri](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Docker kapsayıcıları](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Fermuarlar ve katran topları](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Komut dosyalarını yükleme](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Sürüm notları](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturun

.NET Core SDK'yı yükledikten sonra bir komut istemi açın. Bir uygulama oluşturmak ve çalıştırmak için aşağıdaki komutları kullanın:

```dotnetcli
dotnet new console
dotnet run
```

Aşağıdaki çıktıyı görmeniz gerekir:

```output
Hello World!
```

## <a name="contribute"></a>Katkıda Bulun

.NET Core açık bir platformdur. Herkes katılabilir.

* [Geliştirici Topluluğu'nda](https://developercommunity.visualstudio.com/spaces/61/index.html)ürün sorunlarını ve sorularını dosyalayın.
* Ürün katkıları, proje depolarından birinde yapılmalıdır, örneğin [dotnet/runtime,](https://github.com/dotnet/runtime) [dotnet/sdk,](https://github.com/dotnet/sdk) [dotnet/rosyln](https://github.com/dotnet/roslyn)veya [aspnetcore.](https://github.com/dotnet/aspnetcore) Daha fazla bilgi için [bkz.](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)

## <a name="support"></a>Destek

.NET Core, Windows, macOS ve Linux'ta Microsoft tarafından ve Red Hat Enterprise Linux'ta Red Hat tarafından desteklenir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET Çekirdek eğitimleri](tutorials/index.md)

> [!div class="nextstepaction"]
> [Tarayıcınızda .NET Core'u deneyin](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
