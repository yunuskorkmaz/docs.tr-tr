---
title: MSBuild kırılmaya yönelik değişiklikler
description: .NET Core için MSBuild 'teki son değişiklikleri listeler.
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159500"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="fe9e8-103">MSBuild kırılmaya yönelik değişiklikler</span><span class="sxs-lookup"><span data-stu-id="fe9e8-103">MSBuild breaking changes</span></span>

<span data-ttu-id="fe9e8-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="fe9e8-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="fe9e8-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="fe9e8-105">Breaking change</span></span> | <span data-ttu-id="fe9e8-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fe9e8-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="fe9e8-107">TargetFramework, netcoreapp 'ten net 'e değişiklik</span><span class="sxs-lookup"><span data-stu-id="fe9e8-107">TargetFramework change from netcoreapp to net</span></span>](#targetframework-change-from-netcoreapp-to-net) | <span data-ttu-id="fe9e8-108">5.0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-108">5.0</span></span> |
| [<span data-ttu-id="fe9e8-109">NETCOREAPP3_1 Önişlemci sembolü .NET 5 hedeflenirken tanımlanmaz</span><span class="sxs-lookup"><span data-stu-id="fe9e8-109">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="fe9e8-110">5.0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-110">5.0</span></span> |
| [<span data-ttu-id="fe9e8-111">PublishDepsFilePath davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="fe9e8-111">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="fe9e8-112">5.0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-112">5.0</span></span> |
| [<span data-ttu-id="fe9e8-113">Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır</span><span class="sxs-lookup"><span data-stu-id="fe9e8-113">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="fe9e8-114">5.0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-114">5.0</span></span> |
| [<span data-ttu-id="fe9e8-115">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="fe9e8-115">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="fe9e8-116">3.0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-116">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="fe9e8-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-117">.NET 5.0</span></span>

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="fe9e8-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fe9e8-118">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
