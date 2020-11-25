---
ms.openlocfilehash: 540eebd957ce8ce0928db2bd8317cb220cba30bb
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031777"
---

[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının** Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .

Komut dosyası, .NET Core 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan olarak kullanılır. (LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.

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
