---
title: .NET Core Kılavuzu
description: .NET Core, Windows, Linux ve Mac uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 0007c1c6a9939c46f123535f9053ac1d4ced7266
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848937"
---
# <a name="net-core-guide"></a>.NET Core Kılavuzu

[.NET Core](about.md) , [GitHub](https://github.com/dotnet/core)'da Microsoft ve .net Community tarafından sürdürülen [Açık kaynaklı](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur. Platformlar arası bir platformdur (Windows, macOS ve Linux 'u destekleme) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.

.NET Core hakkında özellikler, desteklenen diller ve çerçeveler ve anahtar API 'Leri dahil olmak üzere .NET Core hakkında daha fazla bilgi için bkz. [.NET Core hakkında](about.md) .

[.NET Core öğreticilerine](tutorials/index.md) göz atın ve basit bir .NET Core uygulaması oluşturma hakkında bilgi edinin. İlk uygulamanızı çalışır duruma getirmek için yalnızca birkaç dakika sürer. Tarayıcınızda .NET Core 'u denemek istiyorsanız çevrimiçi öğreticideki [numaralara C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) bakın.

## <a name="download-net-core-22"></a>.NET Core 2,2 'yi indirin

Windows, macOS veya Linux makinenizde .NET Core 'u denemek için [.net core 2,2 SDK 'sını](https://dotnet.microsoft.com/download) indirin. Docker Kapsayıcıları kullanmayı tercih ediyorsanız [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) adresini ziyaret edin.

Başka bir .NET Core sürümü arıyorsanız, tüm .NET Core sürümleri [.NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core) ile kullanılabilir.

## <a name="net-core-22"></a>.NET Core 2,2

En son sürüm [.NET Core 2,2](whats-new/dotnet-core-2-2.md)' dir. Yeni özellikler şunlardır: çerçeveye bağımlı dağıtımlar, başlangıç kancaları, Azure SQL ile AAD kimlik doğrulaması ve Windows ARM32 desteği.

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturma

.NET Core SDK yükledikten sonra bir komut istemi açın. Bir C# uygulama oluşturmak `dotnet` ve çalıştırmak için aşağıdaki komutları yazın.

```console
dotnet new console
dotnet run
```

Aşağıdaki çıktıyı görmeniz gerekir:

```output
Hello World!
```

## <a name="support"></a>Destek

.NET Core, Windows, macOS ve Linux 'ta [Microsoft tarafından desteklenir](https://dotnet.microsoft.com/platform/support/policy). Genellikle ayda bir yılda birkaç kez güvenlik ve kalite için güncelleştirilir.

.NET Core ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve tıpkı tüm Microsoft ürünleri gibi desteklenir.

[Red Hat](http://redhatloves.net/) Red Hat Enterprise Linux (RHEL) üzerinde .NET Core 'u destekler. Red hat, kaynaktan .NET Core 'u oluşturur ve [Red Hat yazılım koleksiyonlarında](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.
