---
title: .NET Core kılavuzu
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmak için .NET'in modüler, yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 6d2ce5951fa01ca3945ce0e64aa58fbadc8ab5af
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546555"
---
# <a name="net-core-guide"></a>.NET Core kılavuzu

[.NET Core,](about.md) Microsoft ve [GitHub'daki](https://github.com/dotnet/core).NET topluluğu tarafından korunan [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur. Bu çapraz platform (Windows, macOS ve Linux destekleyen) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.

Özellikleri, desteklenen dilleri ve çerçeveleri ve önemli API'leri de dahil olmak üzere .NET Core hakkında daha fazla bilgi edinmek için [.NET Core](about.md) hakkında bilgi edinin.

Basit bir .NET Core uygulaması nın nasıl oluşturulacağımı öğrenmek için [.NET Core Eğitimlerine](tutorials/index.md) göz atın. İlk uygulamanızı çalışır hale getirmek yalnızca birkaç dakika nızı alır. Tarayıcınızda .NET Core'u denemek istiyorsanız, [C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online öğreticideki Sayılar'a bakın.

## <a name="download-net-core"></a>Karşıdan yükleme .NET Core

Windows, macOS veya Linux makinenizde .NET Core'u denemek için [.NET Core SDK'yı](https://dotnet.microsoft.com/download) indirin. Docker konteynerlerini kullanmayı tercih ederseniz [,NET Core Docker Hub'ı](https://hub.docker.com/_/microsoft-dotnet-core/)ziyaret edin.

Başka bir .NET Core sürümü arıyorsanız tüm .NET Core sürümleri [.NET Core İndirme sürümlerinde](https://dotnet.microsoft.com/download/dotnet-core) mevcuttur.

## <a name="net-core-31"></a>.NET Çekirdek 3.1

En son sürümü .NET Core 3.1 olduğunu. 3.1 .NET Core 3.0 üzerinde küçük iyileştirmeler içerir, ancak, .NET Core 3.1 [uzun vadeli desteklenen bir sürümdür.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .NET Core 3.1 sürümü hakkında daha fazla bilgi için [.NET Core 3.1'deki yeniliklere](./whats-new/dotnet-core-3-1.md)bakın.

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
