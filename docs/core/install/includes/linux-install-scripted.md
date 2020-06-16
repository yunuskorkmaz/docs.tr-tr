---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768409"
---

<span data-ttu-id="e237d-101">[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının**Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e237d-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="e237d-102">Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="e237d-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="e237d-103">Komut dosyası, .NET Core 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e237d-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="e237d-104">(LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e237d-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="e237d-105">SDK yerine .NET Core çalışma zamanı yüklemek için `--runtime` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e237d-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="e237d-106">Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` .</span><span class="sxs-lookup"><span data-stu-id="e237d-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="e237d-107">Aşağıdaki komut .NET Core SDK 3,1 ' i yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="e237d-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="e237d-108">Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="e237d-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
