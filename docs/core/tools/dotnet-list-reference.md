---
title: DotNet liste başvurusu komutu
description: DotNet liste başvurusu komutu, projeyi Proje başvurularına göre listelemek için kullanışlı bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733227"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="bbecc-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="bbecc-103">dotnet list reference</span></span>

<span data-ttu-id="bbecc-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="bbecc-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="bbecc-105">Name</span><span class="sxs-lookup"><span data-stu-id="bbecc-105">Name</span></span>

<span data-ttu-id="bbecc-106">`dotnet list reference`-projeden projeye başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="bbecc-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbecc-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="bbecc-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="bbecc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbecc-108">Description</span></span>

<span data-ttu-id="bbecc-109">`dotnet list reference` komutu, belirli bir proje veya çözümün proje başvurularını listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbecc-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="bbecc-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="bbecc-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="bbecc-111">Başvuruları listelemek için kullanılacak proje veya çözüm dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbecc-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="bbecc-112">Belirtilmemişse, komut geçerli dizinde bir proje dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="bbecc-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="bbecc-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="bbecc-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="bbecc-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="bbecc-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="bbecc-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bbecc-115">Examples</span></span>

* <span data-ttu-id="bbecc-116">Belirtilen proje için proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="bbecc-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="bbecc-117">Geçerli dizindeki projenin proje başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="bbecc-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
