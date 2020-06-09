---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602952"
---

[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK**'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .

Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. (LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.

```bash
./dotnet-install.sh -c Current
```

SDK yerine .NET Core çalışma zamanı yüklemek için `--runtime` parametresini kullanın.

```bash
./dotnet-install.sh -c Current --runtime
```

Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` . Aşağıdaki komut .NET Core SDK 3,1 ' i yüklüyor.

```bash
./dotnet-install.sh -c 3.1
```

Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../../tools/dotnet-install-script.md).
