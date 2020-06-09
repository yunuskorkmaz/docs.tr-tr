---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602952"
---

<span data-ttu-id="bcc86-101">[DotNet yükleme betikleri](../../tools/dotnet-install-script.md) , **SDK**'nın Otomasyon ve yönetici olmayan yüklemeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcc86-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK**.</span></span> <span data-ttu-id="bcc86-102">Betiği konumundan indirebilirsiniz <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="bcc86-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="bcc86-103">Komut dosyası, .NET Core 3,1 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="bcc86-103">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="bcc86-104">(LTS) sürümü olmayan geçerli sürümü yüklemek için `-c Current` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bcc86-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="bcc86-105">SDK yerine .NET Core çalışma zamanı yüklemek için `--runtime` parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bcc86-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime
```

<span data-ttu-id="bcc86-106">Belirli sürümü göstermek için parametresini değiştirerek belirli bir sürümü yükleyebilirsiniz `-c` .</span><span class="sxs-lookup"><span data-stu-id="bcc86-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="bcc86-107">Aşağıdaki komut .NET Core SDK 3,1 ' i yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="bcc86-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="bcc86-108">Daha fazla bilgi için bkz. [DotNet-Install betikler Reference](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="bcc86-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
