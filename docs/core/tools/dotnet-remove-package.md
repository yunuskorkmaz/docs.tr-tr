---
title: dotnet kaldırma paket komutu
description: Dotnet kaldırma paketi komutu, NuGet paket başvurularını bir projeye kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463452"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="489f7-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="489f7-103">dotnet remove package</span></span>

<span data-ttu-id="489f7-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="489f7-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="489f7-105">Adı</span><span class="sxs-lookup"><span data-stu-id="489f7-105">Name</span></span>

<span data-ttu-id="489f7-106">`dotnet remove package`- Paket başvurularını proje dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="489f7-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="489f7-107">Özet</span><span class="sxs-lookup"><span data-stu-id="489f7-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a><span data-ttu-id="489f7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="489f7-108">Description</span></span>

<span data-ttu-id="489f7-109">Komut, `dotnet remove package` bir Projeden NuGet paket başvurularını kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="489f7-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="489f7-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="489f7-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="489f7-111">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="489f7-111">Specifies the project file.</span></span> <span data-ttu-id="489f7-112">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="489f7-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="489f7-113">Kaldırılacak paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="489f7-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="489f7-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="489f7-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="489f7-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="489f7-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="489f7-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="489f7-116">Examples</span></span>

- <span data-ttu-id="489f7-117">Geçerli `Newtonsoft.Json` dizindeki projeden NuGet paketini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="489f7-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
