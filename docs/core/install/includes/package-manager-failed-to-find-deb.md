---
ms.openlocfilehash: 3275865cf7f4669ba7deaacea320136d02f64dda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804249"
---

<span data-ttu-id="3c3ff-101">**{DotNet-Package} paketi bulunamadı** veya **bazı paketler yüklenemediğinden** benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3c3ff-101">If you receive an error message similar to **Unable to locate package {dotnet-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="3c3ff-102">Aşağıdaki komut kümesinde iki yer tutucu vardır.</span><span class="sxs-lookup"><span data-stu-id="3c3ff-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="3c3ff-103">Bu, yüklemekte olduğunuz .NET paketini (gibi) temsil eder `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="3c3ff-103">This represents the .NET package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="3c3ff-104">Bu, aşağıdaki `sudo apt-get install` komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c3ff-104">This is used in the following `sudo apt-get install` command.</span></span>

- `{os-version}`\
<span data-ttu-id="3c3ff-105">Bu, kullandığınız dağıtım sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3c3ff-105">This represents the distribution version you're on.</span></span> <span data-ttu-id="3c3ff-106">Bu, `wget` aşağıdaki komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c3ff-106">This is used in the `wget` command below.</span></span> <span data-ttu-id="3c3ff-107">Dağıtım sürümü, `20.04` Ubuntu veya Dete gibi sayısal bir değerdir `10` .</span><span class="sxs-lookup"><span data-stu-id="3c3ff-107">The distribution version is the numerical value, such as `20.04` on Ubuntu or `10` on Debian.</span></span>

<span data-ttu-id="3c3ff-108">Önce paket listesini temizlemeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="3c3ff-108">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="3c3ff-109">Ardından, .NET 'i yeniden yüklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="3c3ff-109">Then, try to install .NET again.</span></span> <span data-ttu-id="3c3ff-110">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3c3ff-110">If that doesn't work, you can run a manual install with the following commands:</span></span>
