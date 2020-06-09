---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602987"
---

<span data-ttu-id="a1c53-101">**{Netcore-Package} paketi bulunamıyor**hatasıyla benzer bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1c53-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="a1c53-102">Aşağıdaki komut kümesinde iki yer tutucu vardır.</span><span class="sxs-lookup"><span data-stu-id="a1c53-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="a1c53-103">Bu, yüklemekte olduğunuz .NET Core paketini (gibi) temsil eder `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="a1c53-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="a1c53-104">Bu, `sudo apt-get install` aşağıdaki komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1c53-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="a1c53-105">Bu, açık olduğunuz Linux sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1c53-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="a1c53-106">Bu, `wget` aşağıdaki komutta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1c53-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="a1c53-107">Paket listesini temizlemeyi deneyin:</span><span class="sxs-lookup"><span data-stu-id="a1c53-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="a1c53-108">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1c53-108">If that doesn't work, you can run a manual install with the following commands:</span></span>
