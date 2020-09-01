---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132956"
---

<span data-ttu-id="fab65-101">**{Netcore-Package} paketi bulunamadı** veya **bazı paketler yüklenemediğinden**benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fab65-101">If you receive an error message similar to **Unable to locate package {netcore-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="fab65-102">Aşağıdaki komut kümesinde iki yer tutucu vardır.</span><span class="sxs-lookup"><span data-stu-id="fab65-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="fab65-103">Bu, yüklemekte olduğunuz .NET Core paketini (gibi) temsil eder `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="fab65-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="fab65-104">Bu, `sudo apt-get install` aşağıdaki komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fab65-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="fab65-105">Bu, açık olduğunuz Linux sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fab65-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="fab65-106">Bu, `wget` aşağıdaki komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fab65-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="fab65-107">Önce paket listesini temizlemeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="fab65-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="fab65-108">Ardından, .NET Core 'u yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="fab65-108">Then, try to install .NET Core again.</span></span> <span data-ttu-id="fab65-109">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fab65-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
