---
title: .NET Core Kılavuzu
description: .NET core Windows, Linux ve Mac uygulamaları oluşturmak için .NET, modüler, yüksek performanslı bir uygulama olan. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: b302b6fc7e097a811c718d2244f603246cb5c259
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121044"
---
# <a name="net-core-guide"></a>.NET Core Kılavuzu

[.NET core](about.md) olduğu bir [açık kaynaklı](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) genel amaçlı bir geliştirme platformu üzerinde Microsoft ve .NET topluluk tarafından tutulan [GitHub](https://github.com/dotnet/core). Bu Windows, macOS ve Linux'ta destekleyen platformlar arası ve cihaz, Bulut ve IOT uygulamaları için kullanılabilir.

Bkz: [.NET Core hakkında](about.md) özellikleri, desteklenen diller ve çerçeveler ve API anahtarını dahil olmak üzere, .NET Core hakkında daha fazla bilgi edinmek için.

Kullanıma [.NET Core öğreticilerini](tutorials/index.md) basit bir .NET Core uygulaması oluşturmayı öğrenin. Yalnızca ilk uygulamanızı çalıştırmaya başlayın birkaç dakika sürer. .NET Core tarayıcınızda denemek istiyorsanız, bakmak [C# dilinde sayılar](https://docs.microsoft.com/dotnet/csharp/quick-starts/numbers-in-csharp) hızlı başlangıç.

## <a name="download-net-core-21"></a>.NET Core 2.1 indirme

İndirme [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) .NET Core Windows, macOS veya Linux makinenizde denemek için. Ziyaret [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) Docker kapsayıcılarını kullanmayı tercih ederseniz.

Tüm .NET Core sürümleri kullanılabilir [.NET Core indirir](https://www.microsoft.com/net/download/archives) için başka bir .NET Core sürümünün düşürmek istiyorsanız.

## <a name="net-core-21"></a>.NET core 2.1

En son sürüm [.NET Core 2.1](whats-new/dotnet-core-2-1.md). Yeni özellikler içerir: Genel araçları, yüksek performanslı API'leri (gibi <xref:System.Span%601?displayProperty=nameWithType>), katmanlı JIT derlemesi [derleme](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) ve [çalışma zamanı performans iyileştirmeleri](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), için ve Destek Alpine ve ARM32.

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturma

.NET Core SDK'yı yükledikten sonra bir komut istemi açın. Aşağıdaki komutu yazın `dotnet` oluşturma ve C# uygulama çalıştırma için komutları.

```console
dotnet new console
dotnet run
```

Aşağıdaki çıktıyı görmeniz gerekir:

```console
Hello World!
```

## <a name="support"></a>Destek

.NET Core [Microsoft tarafından desteklenen](https://www.microsoft.com/net/support/policy), Windows, macOS ve Linux'ta. Güvenlik ve kalite testinden yılda birkaç kez, genellikle aylık güncelleştirilir.

.NET core ikili dağıtımları oluşturulan ve azure'da Microsoft korunan sunucularda test edilmiş ve yalnızca tüm Microsoft Ürün gibi desteklenen.

[Red Hat destekleyen .NET Core](http://redhatloves.net/) Red Hat Enterprise Linux (RHEL) üzerinde. Red Hat kaynaktan .NET Core oluşturur ve kullanılabilir hale getirir [Red Hat yazılımı koleksiyonları](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat ve Microsoft .NET Core iyi RHEL üzerinde çalıştığından emin olmak üzere işbirliği yapıyor.
