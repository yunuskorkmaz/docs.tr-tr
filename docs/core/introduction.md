---
title: .NET Core tanıtımı ve genel bakış
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226588"
---
# <a name="introduction-to-net-core"></a>NET Core’a giriş

[.NET Core](about.md) , [Açık kaynaklı](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur. Windows, macOS ve Linux için, birden çok programlama dilini kullanarak x64, x, ARM32 ve ARM64 işlemcileri için .NET Core uygulamaları oluşturabilirsiniz. Çerçeveler ve API 'Ler [bulut](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [istemci kullanıcı arabirimi](../desktop-wpf/overview/index.md)ve [makine öğrenimi](/dotnet/machine-learning/)için sağlanır.

Makinenizde .NET Core 'u denemek için [.NET Core SDK indirin](https://dotnet.microsoft.com/download) . En son sürüm [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)' dir.

## <a name="download-net-core"></a>.NET Core indirin

Aşağıdaki yollarla .NET Core edinebilirsiniz:

* [Windows ve macOS yükleyicileri](https://dotnet.microsoft.com/download)
* [Linux paketleri](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Docker kapsayıcıları](https://hub.docker.com/_/microsoft-dotnet-core/)
* [ZIP 'ler ve tartopları](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Betikleri yükler](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Sürüm notları](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturun

.NET Core SDK yükledikten sonra bir komut istemi açın. Bir uygulamayı oluşturmak ve çalıştırmak için aşağıdaki komutları kullanın:

```dotnetcli
dotnet new console
dotnet run
```

Aşağıdaki çıkışı görmeniz gerekir:

```output
Hello World!
```

## <a name="contribute"></a>Katkıda Bulun

.NET Core, açık bir platformdur. Herkese katılmak için hoş geldiniz.

* [Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/61/index.html)'nda ürün sorunlarını ve soruları dosya.
* Ürün katkıları [DotNet/Runtime](https://github.com/dotnet/runtime), [DotNet/SDK](https://github.com/dotnet/sdk), [DotNet/Rosyln](https://github.com/dotnet/roslyn)veya [aspnetcore](https://github.com/dotnet/aspnetcore)gibi proje depolarından birinde yapılmalıdır. Daha fazla bilgi için bkz. [.NET Core depoları](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Destek

.NET Core, Microsoft 'un Windows, macOS ve Linux 'ta ve Red Hat Enterprise Linux üzerinde Red Hat ile desteklenir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET Core öğreticileri](tutorials/index.md)

> [!div class="nextstepaction"]
> [Tarayıcınızda .NET Core ' u deneyin](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
