---
ms.openlocfilehash: 49aa98edec8ed1ce35dd501c57aa82e4ca4cf286
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879733"
---
### <a name="project-tools-now-included-in-sdk"></a><span data-ttu-id="f99f5-101">Proje Araçları artık SDK 'ya dahil edilmiştir</span><span class="sxs-lookup"><span data-stu-id="f99f5-101">Project tools now included in SDK</span></span>

<span data-ttu-id="f99f5-102">.NET Core 2,1 SDK artık ortak CLı araçları 'nı içerir ve bundan böyle bu araçlara projeden başvurmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f99f5-102">The .NET Core 2.1 SDK now includes common CLI tooling, and you no longer need to reference these tools from the project.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f99f5-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f99f5-103">Change description</span></span>

<span data-ttu-id="f99f5-104">.NET Core 2,0 ' de, projeler proje ayarıyla dış .NET araçlarına başvurur `<DotNetCliToolReference>` .</span><span class="sxs-lookup"><span data-stu-id="f99f5-104">In .NET Core 2.0, projects reference external .NET tools with the `<DotNetCliToolReference>` project setting.</span></span> <span data-ttu-id="f99f5-105">.NET Core 2,1 ' de, bu araçlardan bazıları .NET Core SDK eklenmiştir ve bu ayar artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f99f5-105">In .NET Core 2.1, some of these tools are included with the .NET Core SDK, and the setting is no longer needed.</span></span> <span data-ttu-id="f99f5-106">Projenizde bu araçlara başvurular eklerseniz aşağıdakine benzer bir hata alırsınız: **' Microsoft. EntityFrameworkCore. Tools. DotNet ' aracı artık .NET Core SDK eklenmiştir.**</span><span class="sxs-lookup"><span data-stu-id="f99f5-106">If you include references to these tools in your project, you'll receive an error similar to the following: **The tool 'Microsoft.EntityFrameworkCore.Tools.DotNet' is now included in the .NET Core SDK.**</span></span>

<span data-ttu-id="f99f5-107">Artık .NET Core 2,1 SDK 'ya dahil edilen araçlar:</span><span class="sxs-lookup"><span data-stu-id="f99f5-107">Tools now included in .NET Core 2.1 SDK:</span></span>

| <span data-ttu-id="f99f5-108">\<DotNetCliToolReference> deeri</span><span class="sxs-lookup"><span data-stu-id="f99f5-108">\<DotNetCliToolReference> value</span></span>                   | <span data-ttu-id="f99f5-109">Araç</span><span class="sxs-lookup"><span data-stu-id="f99f5-109">Tool</span></span>                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [<span data-ttu-id="f99f5-110">DotNet-Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="f99f5-110">dotnet-user-secrets</span></span>](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [<span data-ttu-id="f99f5-111">DotNet-SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="f99f5-111">dotnet-sql-cache</span></span>](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [<span data-ttu-id="f99f5-112">DotNet-EF</span><span class="sxs-lookup"><span data-stu-id="f99f5-112">dotnet-ef</span></span>](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a><span data-ttu-id="f99f5-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f99f5-113">Version introduced</span></span>

<span data-ttu-id="f99f5-114">.NET Core SDK 2.1.300</span><span class="sxs-lookup"><span data-stu-id="f99f5-114">.NET Core SDK 2.1.300</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f99f5-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f99f5-115">Recommended action</span></span>

<span data-ttu-id="f99f5-116">`<DotNetCliToolReference>`Ayarı projenizden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f99f5-116">Remove the `<DotNetCliToolReference>` setting from your project.</span></span>

#### <a name="category"></a><span data-ttu-id="f99f5-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="f99f5-117">Category</span></span>

<span data-ttu-id="f99f5-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="f99f5-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f99f5-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f99f5-119">Affected APIs</span></span>

<span data-ttu-id="f99f5-120">Yok</span><span class="sxs-lookup"><span data-stu-id="f99f5-120">N/A</span></span>
