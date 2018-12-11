---
title: DotNet Listele başvuru komutu
description: Dotnet listesi başvuru komut listesi projeden projeye başvurular için uygun bir seçenek sağlar.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169839"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="1c68d-103">DotNet listesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="1c68d-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1c68d-104">Ad</span><span class="sxs-lookup"><span data-stu-id="1c68d-104">Name</span></span>

<span data-ttu-id="1c68d-105">`dotnet list reference` -Projeden projeye başvurular listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c68d-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1c68d-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="1c68d-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="1c68d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c68d-107">Description</span></span>

<span data-ttu-id="1c68d-108">`dotnet list reference` Komut listesi proje başvurularını belirtilen proje veya çözüm için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c68d-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="1c68d-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="1c68d-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="1c68d-110">Başvuruları listelemek için kullanılacak proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c68d-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="1c68d-111">Belirtilmezse, komut, bir proje dosyasını geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="1c68d-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="1c68d-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1c68d-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="1c68d-113">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1c68d-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1c68d-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1c68d-114">Examples</span></span>

* <span data-ttu-id="1c68d-115">Belirtilen proje için proje başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1c68d-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="1c68d-116">Geçerli dizinde proje için proje başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1c68d-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```