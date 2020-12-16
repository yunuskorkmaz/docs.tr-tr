---
title: MSBuild kırılmaya yönelik değişiklikler
description: .NET Core 3,0-3,1 için MSBuild 'teki son değişiklikleri listeler.
ms.date: 12/14/2020
ms.openlocfilehash: 1ed5878845406fa7727c644f1e196d63a860646a
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593454"
---
# <a name="msbuild-breaking-changes-in-net-core-30---31"></a><span data-ttu-id="73393-103">.NET Core 3,0-3,1 ' de MSBuild bölünmesi değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="73393-103">MSBuild breaking changes in .NET Core 3.0 - 3.1</span></span>

<span data-ttu-id="73393-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="73393-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="73393-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="73393-105">Breaking change</span></span> | <span data-ttu-id="73393-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="73393-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="73393-107">Tasarım zamanı derlemeleri yalnızca üst düzey paket başvurularını döndürüyor</span><span class="sxs-lookup"><span data-stu-id="73393-107">Design-time builds only return top-level package references</span></span>](#design-time-builds-only-return-top-level-package-references) | <span data-ttu-id="73393-108">3,1</span><span class="sxs-lookup"><span data-stu-id="73393-108">3.1</span></span> |
| [<span data-ttu-id="73393-109">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="73393-109">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="73393-110">3,0</span><span class="sxs-lookup"><span data-stu-id="73393-110">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="73393-111">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="73393-111">.NET Core 3.1</span></span>

[!INCLUDE [design-time-builds-return-top-level-package-refs](../../../includes/core-changes/msbuild/3.1/design-time-builds-return-top-level-package-refs.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="73393-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="73393-112">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
