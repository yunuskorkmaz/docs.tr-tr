---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802758"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="92b24-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="92b24-103">dotnet list reference</span></span>

<span data-ttu-id="92b24-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="92b24-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="92b24-105">Name</span><span class="sxs-lookup"><span data-stu-id="92b24-105">Name</span></span>

<span data-ttu-id="92b24-106">`dotnet list reference`-Projeden projeye başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="92b24-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="92b24-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="92b24-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="92b24-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92b24-108">Description</span></span>

<span data-ttu-id="92b24-109">`dotnet list reference`Komut, belirli bir proje için proje başvurularını listelemek üzere uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b24-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="92b24-110">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="92b24-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="92b24-111">Üzerinde çalışılacak proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="92b24-111">The project file to operate on.</span></span> <span data-ttu-id="92b24-112">Bir dosya belirtilmemişse, komut geçerli dizinde bir arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="92b24-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="92b24-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="92b24-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="92b24-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="92b24-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="92b24-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="92b24-115">Examples</span></span>

* <span data-ttu-id="92b24-116">Belirtilen proje için proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="92b24-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="92b24-117">Geçerli dizindeki projenin proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="92b24-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
