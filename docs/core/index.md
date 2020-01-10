---
title: .NET Core kılavuzu
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740749"
---
# <a name="net-core-guide"></a>.NET Core kılavuzu

[.NET Core](about.md) , [GitHub](https://github.com/dotnet/core)'da Microsoft ve .net Community tarafından sürdürülen [Açık kaynaklı](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur. Platformlar arası bir platformdur (Windows, macOS ve Linux 'u destekleme) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.

.NET Core hakkında özellikler, desteklenen diller ve çerçeveler ve anahtar API 'Leri dahil olmak üzere .NET Core hakkında daha fazla bilgi için bkz. [.NET Core hakkında](about.md) .

[.NET Core öğreticilerine](tutorials/index.md) göz atın ve basit bir .NET Core uygulaması oluşturma hakkında bilgi edinin. İlk uygulamanızı çalışır duruma getirmek için yalnızca birkaç dakika sürer. Tarayıcınızda .NET Core 'u denemek istiyorsanız çevrimiçi öğreticideki [numaralara C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) bakın.

## <a name="download-net-core"></a>.NET Core indirin

Windows, macOS veya Linux makinenizde .NET Core 'u denemek için [.NET Core SDK](https://www.microsoft.com/net/download) indirin. Docker Kapsayıcıları kullanmayı tercih ediyorsanız, [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/)' ı ziyaret edin.

Başka bir .NET Core sürümü arıyorsanız, tüm .NET Core sürümleri [.NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core) ile kullanılabilir.

## <a name="net-core-31"></a>.NET Core 3,1

En son sürüm .NET Core 3,1 ' dir. 3,1, .NET Core 3,0 üzerinde küçük geliştirmeler içerir, ancak .NET Core 3,1 [uzun süreli desteklenen bir sürümdür](https://dotnet.microsoft.com/platform/support/policy/dotnet-core). .NET Core 3,1 sürümü hakkında daha fazla bilgi için bkz. [.net core 3,1 ' deki](./whats-new/dotnet-core-3-1.md)yenilikler.

## <a name="create-your-first-application"></a>İlk uygulamanızı oluşturun

.NET Core SDK yükledikten sonra bir komut istemi açın. Bir C# uygulamayı oluşturmak ve çalıştırmak için aşağıdaki `dotnet` komutlarını girin:

```dotnetcli
dotnet new console
dotnet run
```

Aşağıdaki çıkışı görmeniz gerekir:

```output
Hello World!
```

## <a name="support"></a>Destek

.NET Core, [Microsoft](https://dotnet.microsoft.com/platform/support/policy), Windows, MacOS ve Linux 'ta desteklenmektedir. Genellikle ayda bir yılda birkaç kez güvenlik ve kalite için güncelleştirilir.

.NET Core ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve tıpkı tüm Microsoft ürünleri gibi desteklenir.

[Red Hat](http://redhatloves.net/) Red Hat Enterprise Linux (RHEL) üzerinde .NET Core 'u destekler. Red hat, kaynaktan .NET Core 'u oluşturur ve [Red Hat yazılım koleksiyonlarında](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.
