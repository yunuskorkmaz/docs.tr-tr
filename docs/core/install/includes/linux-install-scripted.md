---
ms.openlocfilehash: 07dd58c314c826c426193b829ea1f64669fb888b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594578"
---

<span data-ttu-id="28546-101">[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK** ve **çalışma zamanının** Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28546-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="28546-102">Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="28546-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="28546-103">Komut dosyası, .NET 3,1 olan en son SDK [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="28546-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET 3.1.</span></span> <span data-ttu-id="28546-104">(LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="28546-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="28546-105">SDK yerine .NET Runtime yüklemek için `--runtime` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="28546-105">To install .NET Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="28546-106">Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` .</span><span class="sxs-lookup"><span data-stu-id="28546-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="28546-107">Aşağıdaki komut .NET SDK 5,0 'yi yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="28546-107">The following command installs .NET SDK 5.0.</span></span>

```bash
./dotnet-install.sh -c 5.0
```

<span data-ttu-id="28546-108">Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="28546-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
