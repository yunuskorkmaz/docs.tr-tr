---
ms.openlocfilehash: d9489df1ba096109e60d663e3a3f4442d30b2bb1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105479"
---
### <a name="project-tools-now-included-in-sdk"></a>Proje Araçları artık SDK 'ya dahil edilmiştir

.NET Core 2,1 SDK artık ortak CLı araçları 'nı içerir ve bundan böyle bu araçlara projeden başvurmanız gerekmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,0 ' de, projeler proje ayarıyla dış .NET araçlarına başvurur `<DotNetCliToolReference>` . .NET Core 2,1 ' de, bu araçlardan bazıları .NET Core SDK eklenmiştir ve bu ayar artık gerekli değildir. Projenizde bu araçlara başvurular eklerseniz aşağıdakine benzer bir hata alırsınız: **' Microsoft. EntityFrameworkCore. Tools. DotNet ' aracı artık .NET Core SDK eklenmiştir.**

Artık .NET Core 2,1 SDK 'ya dahil edilen araçlar:

| \<DotNetCliToolReference> deeri                   | Araç                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | [DotNet-Watch](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-watch/README.md)               |
| `Microsoft.Extensions.SecretManager.Tools`     | [DotNet-Kullanıcı gizli dizileri](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [DotNet-SQL-Cache](https://github.com/dotnet/aspnetcore/blob/master/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [DotNet-EF](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core SDK 2.1.300

#### <a name="recommended-action"></a>Önerilen eylem

`<DotNetCliToolReference>`Ayarı projenizden kaldırın.

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok
