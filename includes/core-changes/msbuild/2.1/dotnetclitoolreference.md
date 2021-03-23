---
ms.openlocfilehash: 49aa98edec8ed1ce35dd501c57aa82e4ca4cf286
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879733"
---
### <a name="project-tools-now-included-in-sdk"></a>Proje Araçları artık SDK 'ya dahil edilmiştir

.NET Core 2,1 SDK artık ortak CLı araçları 'nı içerir ve bundan böyle bu araçlara projeden başvurmanız gerekmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,0 ' de, projeler proje ayarıyla dış .NET araçlarına başvurur `<DotNetCliToolReference>` . .NET Core 2,1 ' de, bu araçlardan bazıları .NET Core SDK eklenmiştir ve bu ayar artık gerekli değildir. Projenizde bu araçlara başvurular eklerseniz aşağıdakine benzer bir hata alırsınız: **' Microsoft. EntityFrameworkCore. Tools. DotNet ' aracı artık .NET Core SDK eklenmiştir.**

Artık .NET Core 2,1 SDK 'ya dahil edilen araçlar:

| \<DotNetCliToolReference> deeri                   | Araç                                                                                                            |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `Microsoft.DotNet.Watcher.Tools`               | `dotnet-watch`               |
| `Microsoft.Extensions.SecretManager.Tools`     | [DotNet-Kullanıcı gizli dizileri](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-user-secrets/README.md) |
| `Microsoft.Extensions.Caching.SqlConfig.Tools` | [DotNet-SQL-Cache](https://github.com/dotnet/aspnetcore/blob/main/src/Tools/dotnet-sql-cache/README.md)       |
| `Microsoft.EntityFrameworkCore.Tools.DotNet`   | [DotNet-EF](/ef/core/miscellaneous/cli/dotnet)                                                                  |

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core SDK 2.1.300

#### <a name="recommended-action"></a>Önerilen eylem

`<DotNetCliToolReference>`Ayarı projenizden kaldırın.

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok
