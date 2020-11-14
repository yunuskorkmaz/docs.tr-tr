---
ms.openlocfilehash: 07dd58c314c826c426193b829ea1f64669fb888b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594578"
---

[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının** Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .

Komut dosyası, .NET 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. (LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.

```bash
./dotnet-install.sh -c Current
```

SDK yerine .NET Runtime yüklemek için `--runtime` parametresini kullanın.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` . Aşağıdaki komut .NET SDK 5,0 'yi yüklüyor.

```bash
./dotnet-install.sh -c 5.0
```

Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../../tools/dotnet-install-script.md).
