---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901985"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı

ASP.NET Core 3,0 ' den itibaren Windows barındırma paketi, AspNetCoreModule (ANCM) v1 'yi içermez.

ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.

Tartışma için bkz. [DotNet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

ANCM v1, Windows barındırma paketi 'ne dahildir.

#### <a name="new-behavior"></a>Yeni davranış

ANCM v1, Windows barındırma paketi 'ne dahil değildir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 3,0 uygulamalarıyla birlikte ANCM v2 kullanın.

ANCM v1 gerekliyse, ASP.NET Core 2,1 veya 2,2 Windows barındırma paketi kullanılarak yüklenebilir.

Bu değişiklik, şu şekilde ASP.NET Core 3,0 uygulamalarını keser:

- `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`ile birlikte ANCM v1 kullanarak açık bir şekilde kabul edildi.
- `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`olan özel bir *Web. config* dosyası olmalıdır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
