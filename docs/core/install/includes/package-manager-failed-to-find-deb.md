---
ms.openlocfilehash: aba7b473af7685aa45f7e093a2f75311687593df
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506981"
---

<span data-ttu-id="019f3-101">**{DotNet-Package} paketi bulunamadı** veya **bazı paketler yüklenemediğinden** benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="019f3-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed** , run the following commands.</span></span>

<span data-ttu-id="019f3-102">Aşağıdaki komut kümesinde iki yer tutucu vardır.</span><span class="sxs-lookup"><span data-stu-id="019f3-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="019f3-103">Bu, yüklemekte olduğunuz .NET paketini (gibi) temsil eder `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="019f3-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="019f3-104">Bu, aşağıdaki `sudo apt-get install` komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="019f3-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="019f3-105">Bu, açık olduğunuz Linux sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="019f3-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="019f3-106">Bu, `wget` aşağıdaki komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="019f3-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="019f3-107">Önce paket listesini temizlemeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="019f3-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="019f3-108">Ardından, .NET 'i yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="019f3-108">Then, try to install .NET again.</span></span> <span data-ttu-id="019f3-109">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="019f3-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
