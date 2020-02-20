---
title: DotNet paket Kaldır komutu
description: DotNet Remove Package komutu, bir projeye NuGet paket başvurusunu kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503638"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="588d8-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="588d8-103">dotnet remove package</span></span>

<span data-ttu-id="588d8-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="588d8-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="588d8-105">Adı</span><span class="sxs-lookup"><span data-stu-id="588d8-105">Name</span></span>

<span data-ttu-id="588d8-106">`dotnet remove package`-paket başvurusunu bir proje dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="588d8-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="588d8-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="588d8-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="588d8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="588d8-108">Description</span></span>

<span data-ttu-id="588d8-109">`dotnet remove package` komutu bir projeden NuGet paket başvurusunu kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="588d8-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="588d8-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="588d8-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="588d8-111">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="588d8-111">Specifies the project file.</span></span> <span data-ttu-id="588d8-112">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="588d8-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="588d8-113">Kaldırılacak paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="588d8-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="588d8-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="588d8-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="588d8-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="588d8-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="588d8-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="588d8-116">Examples</span></span>

- <span data-ttu-id="588d8-117">`Newtonsoft.Json` NuGet paketini geçerli dizindeki bir projeden kaldır:</span><span class="sxs-lookup"><span data-stu-id="588d8-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
