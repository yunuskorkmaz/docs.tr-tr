---
ms.openlocfilehash: 370c6eb23a50ed388f0b10a5c5f4779ba2a1b144
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102623555"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="373fd-101">Proje Araçları artık SDK 'ya dahil edilmiştir</span><span class="sxs-lookup"><span data-stu-id="373fd-101">Project tools now included in SDK</span></span>

<span data-ttu-id="373fd-102">.NET Core 2,1 SDK artık ortak CLı araçları 'nı içerir ve bundan böyle bu araçlara projeden başvurmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="373fd-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="373fd-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="373fd-103">Change description</span></span>

<span data-ttu-id="373fd-104">.NET Core 2,0 ' de, projeler proje ayarıyla dış .NET araçlarına başvurur `<DotNetCliToolReference>` .</span><span class="sxs-lookup"><span data-stu-id="373fd-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="373fd-105">.NET Core 2,1 ' de, bu araçlardan bazıları .NET Core SDK eklenmiştir ve bu ayar artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="373fd-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="373fd-106">Projenizde bu araçlara başvurular eklerseniz aşağıdakine benzer bir hata alırsınız: **' Microsoft. EntityFrameworkCore. Tools. DotNet ' aracı artık .NET Core SDK eklenmiştir.**</span><span class="sxs-lookup"><span data-stu-id="373fd-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="373fd-107">Artık .NET Core 2,1 SDK 'ya dahil edilen araçlar:</span><span class="sxs-lookup"><span data-stu-id="373fd-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="373fd-108">\<DotNetCliToolReference> deeri</span><span class="sxs-lookup"><span data-stu-id="373fd-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="373fd-109">Araç</span><span class="sxs-lookup"><span data-stu-id="373fd-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="373fd-110">DotNet-Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="373fd-110">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="373fd-111">DotNet-SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="373fd-111">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="373fd-112">DotNet-EF</span><span class="sxs-lookup"><span data-stu-id="373fd-112">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="373fd-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="373fd-113">Version introduced</span></span>

<span data-ttu-id="373fd-114">.NET Core SDK 2.1.300</span><span class="sxs-lookup"><span data-stu-id="373fd-114">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="373fd-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="373fd-115">Recommended action</span></span>

<span data-ttu-id="373fd-116">`<DotNetCliToolReference>`Ayarı projenizden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="373fd-116">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="373fd-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="373fd-117">Category</span></span>

<span data-ttu-id="373fd-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="373fd-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="373fd-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="373fd-119">Affected APIs</span></span>

<span data-ttu-id="373fd-120">Yok</span><span class="sxs-lookup"><span data-stu-id="373fd-120">N/A</span></span>
