---
title: dotnet listesi referans komutu
description: Dotnet listesi başvuru komutu, proje başvurularını projeye listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503710"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="dcd71-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="dcd71-103">dotnet list reference</span></span>

<span data-ttu-id="dcd71-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="dcd71-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dcd71-105">Adı</span><span class="sxs-lookup"><span data-stu-id="dcd71-105">Name</span></span>

<span data-ttu-id="dcd71-106">`dotnet list reference`- Projeden projeye referansları listeler.</span><span class="sxs-lookup"><span data-stu-id="dcd71-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dcd71-107">Özet</span><span class="sxs-lookup"><span data-stu-id="dcd71-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="dcd71-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcd71-108">Description</span></span>

<span data-ttu-id="dcd71-109">Komut, `dotnet list reference` belirli bir proje veya çözüm için proje başvurularını listelemek için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="dcd71-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="dcd71-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="dcd71-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="dcd71-111">Başvuruları listeleme için kullanılacak proje veya çözüm dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcd71-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="dcd71-112">Belirtilmemişse, komut bir proje dosyası için geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="dcd71-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="dcd71-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dcd71-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="dcd71-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dcd71-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="dcd71-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dcd71-115">Examples</span></span>

* <span data-ttu-id="dcd71-116">Belirtilen proje için proje başvurularını listele:</span><span class="sxs-lookup"><span data-stu-id="dcd71-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="dcd71-117">Proje başvurularını geçerli dizindeki listele:</span><span class="sxs-lookup"><span data-stu-id="dcd71-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
