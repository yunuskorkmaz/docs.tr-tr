---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608475"
---
### <a name="winhttphandler-removed-from-net-runtime"></a>.NET çalışma zamanından WinHttpHandler kaldırıldı

`WinHttpHandler`Sınıf *System.Net.Http.dll* derlemesinden kaldırıldı. Artık yalnızca bant dışı (OOB) [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Net.Http.WinHttpHandler> sınıfı çekirdek .net kitaplıklarının bir parçası olarak kullanılabilir. .NET 5,0 ' den başlayarak, <xref:System.Net.Http.WinHttpHandler> sınıfı yalnızca ayrı yüklenmiş bir [NuGet paketi](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)olarak kullanılabilir.

#### <a name="recommended-action"></a>Önerilen eylem

[System .net. http. WinHttpHandler NuGet paketini](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)yükler. Ya da, WinHTTP 'ye özgü özellikler gerekmiyorsa, <xref:System.Net.Http.SocketsHttpHandler> bunun yerine kullanın.

#### <a name="category"></a>Kategori

Ağ

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
