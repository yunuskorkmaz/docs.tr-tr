---
title: MSBuild kırılmaya yönelik değişiklikler
description: .NET Core için MSBuild 'teki son değişiklikleri listeler.
ms.date: 02/10/2020
ms.openlocfilehash: b57c70d21e061c59f26b11a025d4d05ce3b8ca99
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654749"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="da53d-103">MSBuild kırılmaya yönelik değişiklikler</span><span class="sxs-lookup"><span data-stu-id="da53d-103">MSBuild breaking changes</span></span>

<span data-ttu-id="da53d-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="da53d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="da53d-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="da53d-105">Breaking change</span></span> | <span data-ttu-id="da53d-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="da53d-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="da53d-107">NETCOREAPP3_1 Önişlemci sembolü .NET 5 hedeflenirken tanımlanmaz</span><span class="sxs-lookup"><span data-stu-id="da53d-107">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="da53d-108">5.0</span><span class="sxs-lookup"><span data-stu-id="da53d-108">5.0</span></span> |
| [<span data-ttu-id="da53d-109">PublishDepsFilePath davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="da53d-109">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="da53d-110">5.0</span><span class="sxs-lookup"><span data-stu-id="da53d-110">5.0</span></span> |
| [<span data-ttu-id="da53d-111">Directory. Packages. props dosyaları varsayılan olarak içeri aktarılır</span><span class="sxs-lookup"><span data-stu-id="da53d-111">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="da53d-112">5.0</span><span class="sxs-lookup"><span data-stu-id="da53d-112">5.0</span></span> |
| [<span data-ttu-id="da53d-113">Kaynak bildirimi dosya adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="da53d-113">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="da53d-114">3.0</span><span class="sxs-lookup"><span data-stu-id="da53d-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="da53d-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="da53d-115">.NET 5.0</span></span>

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="da53d-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da53d-116">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
