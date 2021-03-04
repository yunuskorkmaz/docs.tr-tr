---
title: MSBuild kırılmaya yönelik değişiklikler
description: .NET Core 2,1-3,1 için MSBuild 'teki son değişiklikleri listeler.
ms.date: 02/22/2021
ms.openlocfilehash: 03fcd9807a83c4f679dc659b009c857e351b9b2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105649"
---
# <a name="msbuild-breaking-changes-in-net-core-21---31"></a><span data-ttu-id="9bf4c-103">.NET Core 2,1-3,1 ' de MSBuild bölünmesi değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="9bf4c-103">MSBuild breaking changes in .NET Core 2.1 - 3.1</span></span>

<span data-ttu-id="9bf4c-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9bf4c-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9bf4c-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="9bf4c-105">Breaking change</span></span> | <span data-ttu-id="9bf4c-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9bf4c-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="9bf4c-107">Tasarım zamanı derlemeleri yalnızca üst düzey paket başvurularını döndürüyor</span><span class="sxs-lookup"><span data-stu-id="9bf4c-107">Design-time builds only return top-level package references</span></span>](#design-time-builds-only-return-top-level-package-references) | <span data-ttu-id="9bf4c-108">3,1</span><span class="sxs-lookup"><span data-stu-id="9bf4c-108">3.1</span></span> |
| [<span data-ttu-id="9bf4c-109">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="9bf4c-109">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="9bf4c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="9bf4c-110">3.0</span></span> |
| [<span data-ttu-id="9bf4c-111">Proje Araçları artık SDK 'ya dahil edilmiştir</span><span class="sxs-lookup"><span data-stu-id="9bf4c-111">Project tools now included in SDK</span></span>](#project-tools-now-included-in-sdk) | <span data-ttu-id="9bf4c-112">2.1</span><span class="sxs-lookup"><span data-stu-id="9bf4c-112">2.1</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="9bf4c-113">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9bf4c-113">.NET Core 3.1</span></span>

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="9bf4c-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9bf4c-114">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](../../../includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="9bf4c-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9bf4c-115">.NET Core 2.1</span></span>

[!INCLUDE [DotNetCliToolReference project elements removed for bundled tools](../../../includes/core-changes/msbuild/2.1/dotnetclitoolreference.md)]

***
