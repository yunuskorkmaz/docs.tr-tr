---
ms.openlocfilehash: d9489df1ba096109e60d663e3a3f4442d30b2bb1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105479"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="8fb4e-101">Proje Araçları artık SDK 'ya dahil edilmiştir</span><span class="sxs-lookup"><span data-stu-id="8fb4e-101">Project tools now included in SDK</span></span>

<span data-ttu-id="8fb4e-102">.NET Core 2,1 SDK artık ortak CLı araçları 'nı içerir ve bundan böyle bu araçlara projeden başvurmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8fb4e-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="8fb4e-103">Change description</span></span>

<span data-ttu-id="8fb4e-104">.NET Core 2,0 ' de, projeler proje ayarıyla dış .NET araçlarına başvurur `<DotNetCliToolReference>` .</span><span class="sxs-lookup"><span data-stu-id="8fb4e-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="8fb4e-105">.NET Core 2,1 ' de, bu araçlardan bazıları .NET Core SDK eklenmiştir ve bu ayar artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="8fb4e-106">Projenizde bu araçlara başvurular eklerseniz aşağıdakine benzer bir hata alırsınız: **' Microsoft. EntityFrameworkCore. Tools. DotNet ' aracı artık .NET Core SDK eklenmiştir.**</span><span class="sxs-lookup"><span data-stu-id="8fb4e-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="8fb4e-107">Artık .NET Core 2,1 SDK 'ya dahil edilen araçlar:</span><span class="sxs-lookup"><span data-stu-id="8fb4e-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="8fb4e-108">\<DotNetCliToolReference> deeri</span><span class="sxs-lookup"><span data-stu-id="8fb4e-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="8fb4e-109">Araç</span><span class="sxs-lookup"><span data-stu-id="8fb4e-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | [<span data-ttu-id="8fb4e-110">DotNet-Watch</span><span class="sxs-lookup"><span data-stu-id="8fb4e-110">dotnet-watch</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-watch/README.md)               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="8fb4e-111">DotNet-Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="8fb4e-111">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="8fb4e-112">DotNet-SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="8fb4e-112">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="8fb4e-113">DotNet-EF</span><span class="sxs-lookup"><span data-stu-id="8fb4e-113">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="8fb4e-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="8fb4e-114">Version introduced</span></span>

<span data-ttu-id="8fb4e-115">.NET Core SDK 2.1.300</span><span class="sxs-lookup"><span data-stu-id="8fb4e-115">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8fb4e-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="8fb4e-116">Recommended action</span></span>

<span data-ttu-id="8fb4e-117">`<DotNetCliToolReference>`Ayarı projenizden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8fb4e-117">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="8fb4e-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="8fb4e-118">Category</span></span>

<span data-ttu-id="8fb4e-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="8fb4e-119">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8fb4e-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8fb4e-120">Affected APIs</span></span>

<span data-ttu-id="8fb4e-121">Yok</span><span class="sxs-lookup"><span data-stu-id="8fb4e-121">N/A</span></span>
