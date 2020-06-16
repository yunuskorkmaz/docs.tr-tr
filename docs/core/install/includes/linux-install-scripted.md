---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768409"
---

[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının**Otomasyon ve yönetici olmayan yüklemeleri için kullanılır. Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .

Komut dosyası, .NET Core 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan olarak kullanılır. (LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.

```bash
./dotnet-install.sh -c Current
```

SDK yerine .NET Core çalışma zamanı yüklemek için `--runtime` parametresini kullanın.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` . Aşağıdaki komut .NET Core SDK 3,1 ' i yüklüyor.

```bash
./dotnet-install.sh -c 3.1
```

Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../../tools/dotnet-install-script.md).
