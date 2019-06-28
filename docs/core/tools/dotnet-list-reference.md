---
title: DotNet Listele başvuru komutu
description: Dotnet listesi başvuru komut listesi projeden projeye başvurular için uygun bir seçenek sağlar.
ms.date: 06/26/2019
ms.openlocfilehash: 1f87ff89997cdaa6d0095a4db9f28a2e7cb7e6a9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421837"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="98011-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="98011-103">dotnet list reference</span></span>

<span data-ttu-id="98011-104">**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="98011-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="98011-105">Ad</span><span class="sxs-lookup"><span data-stu-id="98011-105">Name</span></span>

<span data-ttu-id="98011-106">`dotnet list reference` -Projeden projeye başvurular listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="98011-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="98011-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="98011-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="98011-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98011-108">Description</span></span>

<span data-ttu-id="98011-109">`dotnet list reference` Komut listesi proje başvurularını belirtilen proje veya çözüm için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="98011-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="98011-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="98011-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="98011-111">Başvuruları listelemek için kullanılacak proje veya çözüm dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="98011-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="98011-112">Belirtilmezse, komut, bir proje dosyasını geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="98011-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="98011-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="98011-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="98011-114">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="98011-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="98011-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="98011-115">Examples</span></span>

* <span data-ttu-id="98011-116">Belirtilen proje için proje başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="98011-116">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="98011-117">Geçerli dizinde proje için proje başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="98011-117">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```
