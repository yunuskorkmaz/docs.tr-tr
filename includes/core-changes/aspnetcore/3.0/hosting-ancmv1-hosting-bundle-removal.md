---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394150"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı

ASP.NET Core 3,0 ' den itibaren Windows barındırma paketi, AspNetCoreModule (ANCM) v1 'yi içermez.

ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.

Tartışma için bkz. [ASPNET/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095).

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

- @No__t-0 ile birlikte ANCM v1 kullanarak açıkça kabul edildi.
- @No__t-1 ile özel bir *Web. config* dosyası olmalıdır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
