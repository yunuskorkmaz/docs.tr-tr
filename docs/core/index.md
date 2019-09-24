---
title: .NET Core Kılavuzu
description: .NET Core, Windows, Linux ve Mac uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 09/23/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 95f18ca09852ce139a4b99ed7aef4802d4883e13
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216213"
---
# <a name="net-core-guide"></a>.NET Core Kılavuzu

[.NET Core](about.md) , [GitHub](https://github.com/dotnet/core)'da Microsoft ve .net Community tarafından sürdürülen [Açık kaynaklı](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur. Platformlar arası bir platformdur (Windows, macOS ve Linux 'u destekleme) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.

.NET Core hakkında özellikler, desteklenen diller ve çerçeveler ve anahtar API 'Leri dahil olmak üzere .NET Core hakkında daha fazla bilgi için bkz. [.NET Core hakkında](about.md) .

[.NET Core öğreticilerine](tutorials/index.md) göz atın ve basit bir .NET Core uygulaması oluşturma hakkında bilgi edinin. İlk uygulamanızı çalışır duruma getirmek için yalnızca birkaç dakika sürer. Tarayıcınızda .NET Core 'u denemek istiyorsanız çevrimiçi öğreticideki [numaralara C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) bakın.

## <a name="download-net-core"></a>.NET Core indirin

Windows, macOS veya Linux makinenizde .NET Core 'u denemek için [.NET Core SDK](https://www.microsoft.com/net/download) indirin. Docker Kapsayıcıları kullanmayı tercih ediyorsanız, [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/)' ı ziyaret edin.

Başka bir .NET Core sürümü arıyorsanız, tüm .NET Core sürümleri [.NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core) ile kullanılabilir.

## <a name="net-core-30"></a>.NET Core 3.0

En son sürüm .NET Core 3,0 ' dir. Yeni özellikler Windows Presentation Foundation (WPF) ve Windows Forms ile Windows masaüstü desteği, Blazor ile tam C# yığın Web geliştirme, SignalR ve Azure SignalR hizmetine yapılan yeni geliştirmeler, 8 ile C# C# yeni dil özellikleri içerir ve çok daha fazlası. .NET Core 3,0 ' deki yeni özelliklerin tam listesi için bkz. [.net core 3,0 ' deki](./whats-new/dotnet-core-3-0.md)yenilikler.

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturma

.NET Core SDK yükledikten sonra bir komut istemi açın. Bir C# uygulama oluşturmak `dotnet` ve çalıştırmak için aşağıdaki komutları yazın:

```dotnetcli
dotnet new console
dotnet run
```

Aşağıdaki çıktıyı görmeniz gerekir:

```output
Hello World!
```

## <a name="support"></a>Destek

.NET Core, [Microsoft](https://dotnet.microsoft.com/platform/support/policy), Windows, MacOS ve Linux 'ta desteklenmektedir. Genellikle ayda bir yılda birkaç kez güvenlik ve kalite için güncelleştirilir.

.NET Core ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve tıpkı tüm Microsoft ürünleri gibi desteklenir.

[Red Hat](http://redhatloves.net/) Red Hat Enterprise Linux (RHEL) üzerinde .NET Core 'u destekler. Red hat, kaynaktan .NET Core 'u oluşturur ve [Red Hat yazılım koleksiyonlarında](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.
