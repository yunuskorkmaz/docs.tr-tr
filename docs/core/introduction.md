---
title: .NET Core giriş ve genel bakış
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmak için .NET'in modüler, yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351703"
---
# <a name="introduction-to-net-core"></a>.NET Core'a Giriş

[.NET Core,](about.md) Microsoft ve [GitHub'daki](https://github.com/dotnet/core).NET topluluğu tarafından korunan [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur. Bu çapraz platform (Windows, macOS ve Linux destekleyen) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.

## <a name="download-net-core"></a>Karşıdan yükleme .NET Core

Windows, macOS veya Linux makinenizde .NET Core'u denemek için [.NET Core SDK'yı](https://dotnet.microsoft.com/download) indirin. Docker kapsayıcılarını kullanmayı tercih [ediyorsanız,.NET Core Docker Hub'ı](https://hub.docker.com/_/microsoft-dotnet-core/)ziyaret edin.

## <a name="net-core-31"></a>.NET Çekirdek 3.1

En son sürümü .NET Core 3.1 olduğunu. 3.1 .NET Core 3.0 üzerinde küçük iyileştirmeler içerir, ancak, .NET Core 3.1 [uzun vadeli desteklenen bir sürümdür.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .NET Core 3.1 sürümü hakkında daha fazla bilgi için [.NET Core 3.1'deki yeniliklere](./whats-new/dotnet-core-3-1.md)bakın.

.NET Core'un başka bir sürümünü arıyorsanız, tüm [sürümlere .NET Core indirmelerinde](https://dotnet.microsoft.com/download/dotnet-core)ulaşabilirsiniz.

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturun

.NET Core SDK'yı yükledikten sonra bir komut istemi açın. C# `dotnet` uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:

```dotnetcli
dotnet new console
dotnet run
```

Aşağıdaki çıktıyı görmeniz gerekir:

```output
Hello World!
```

## <a name="support"></a>Destek

.NET Core, Windows, macOS ve Linux'ta [Microsoft tarafından desteklenir.](https://dotnet.microsoft.com/platform/support/policy) Genellikle aylık olarak yılda birkaç kez güvenlik ve kalite için güncelleştirilir.

.NET Core ikili dağıtımları, Azure'da Microsoft tarafından korunan sunucularda oluşturulur ve test edilir ve tıpkı herhangi bir Microsoft ürünü gibi desteklenir.

Red Hat, Red Hat Enterprise Linux (RHEL) üzerinde [.NET Core'u destekler.](http://redhatloves.net/) Red Hat kaynaktan .NET Core oluşturur ve [Red Hat Yazılım Koleksiyonları'nda](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core'un RHEL'de iyi çalışmasını sağlamak için işbirliği içindedir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET Çekirdek eğitimleri](tutorials/index.md)

> [!div class="nextstepaction"]
> [Tarayıcınızda .NET Core'u deneyin](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
