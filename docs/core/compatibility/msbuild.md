---
title: MSBuild kırılmaya yönelik değişiklikler
description: .NET Core için MSBuild 'teki son değişiklikleri listeler.
ms.date: 02/10/2020
ms.openlocfilehash: 7493516dff68b8bd45740c9877ebf21886e667ff
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679349"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="21530-103">MSBuild kırılmaya yönelik değişiklikler</span><span class="sxs-lookup"><span data-stu-id="21530-103">MSBuild breaking changes</span></span>

<span data-ttu-id="21530-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="21530-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="21530-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="21530-105">Breaking change</span></span> | <span data-ttu-id="21530-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="21530-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="21530-107">PublishDepsFilePath davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="21530-107">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="21530-108">5.0</span><span class="sxs-lookup"><span data-stu-id="21530-108">5.0</span></span> |
| [<span data-ttu-id="21530-109">Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır</span><span class="sxs-lookup"><span data-stu-id="21530-109">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="21530-110">5.0</span><span class="sxs-lookup"><span data-stu-id="21530-110">5.0</span></span> |
| [<span data-ttu-id="21530-111">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="21530-111">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="21530-112">3.0</span><span class="sxs-lookup"><span data-stu-id="21530-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="21530-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="21530-113">.NET 5.0</span></span>

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="21530-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="21530-114">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
