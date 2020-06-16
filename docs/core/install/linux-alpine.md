---
title: Alp-.NET Core 'a .NET Core 'u yükler
description: .NET Core SDK ve .NET Core çalışma zamanını alp 'ye yüklemenin çeşitli yollarını gösterir.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771505"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a>Alp 'de .NET Core SDK veya .NET Core çalışma zamanı yüklemesi

Bu makalede, alp 'de .NET Core 'un nasıl yükleneceği açıklanır. Bir alp sürümü destek dışı kaldığında, .NET Core artık bu sürümle desteklenmez. Ancak, bu yönergeler desteklenmese de, bu sürümler üzerinde çalışan .NET Core 'u almanıza yardımcı olabilir.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Alp için yükleyiciler yok. [Install betiğini](#scripted-install) kullanmanız veya [el ile Install](#manual-install) yönergelerini izlemeniz gerekir.

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşana](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.

- ✔️, alp veya .NET Core sürümünün hala desteklendiğini gösterir.
- A ❌ , alp veya .NET Core sürümünün bu Alu sürümünde desteklenmediğini belirtir.
- Hem alp hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Alpine                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview |
|--------------------------|---------------|---------------|----------------|
| ✔️ 3,12  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ 3,11  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ 3,10  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ 3,9   | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌3,8   | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |

Aşağıdaki .NET Core sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

## <a name="dependencies"></a>Bağımlılıklar

Alp Linux üzerinde .NET Core aşağıdaki bağımlılıkların yüklü olmasını gerektirir:

- ICU-libs
- krb5-libs
- libintl
- libssl 1.1 (alp v 3.9 veya üzeri)
- libssl 1.0 (alp v 3.8)
- libstdc + +
- lttng-ust
- numactl (isteğe bağlı)
- zlib

## <a name="scripted-install"></a>Komut dosyalı yüklemesi

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>El ile yüklemesi

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Sonraki adımlar

- [Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
