---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804938"
---
### <a name="blazor-updated-browser-support"></a>Blazor: tarayıcı desteği güncelleştirildi

ASP.NET Core 5,0, bazıları eski tarayıcılarla uyumsuz olan [Yeni Blazor özellikleri](https://github.com/dotnet/aspnetcore/issues/21514)sunuyor. ASP.NET Core 5,0 ' de Blazor tarafından desteklenen tarayıcıların listesi, buna göre güncelleştirilmiştir.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="old-behavior"></a>Eski davranış

Blazor Server, yeterli polydolgular ile Microsoft Internet Explorer 11 ' i destekler. Blazor Server ve Blazor WebAssembly, [Microsoft Edge eski](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)sürümünde de çalışır.

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 5,0 ' deki Blazor sunucusu Microsoft Internet Explorer 11 ile desteklenmiyor. Blazor Server ve Blazor WebAssembly, Microsoft Edge eski sürümünde tam olarak işlevsel değildir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 5,0 ' deki yeni Blazor özellikleri bu eski tarayıcılarla uyumsuzdur ve bu eski tarayıcıların kullanımı, bu eski tarayıcıların kullanımına karşı azalmış olur. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

* [Microsoft Edge için Windows desteği, Ayrıca 9 Mart 2021 ' de sona eriyor](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Microsoft 365 uygulamalar ve hizmetler, Microsoft Internet Explorer 11 için 17 Ağustos 2021 ' de destek sona acaktır.](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a>Önerilen eylem

Bu eski tarayıcılardan [Yeni, Kmuum tabanlı Microsoft Edge](https://www.microsoft.com/edge)'e yükseltin. Bu eski tarayıcıları desteklemesi gereken Blazor uygulamaları için ASP.NET Core 3,1 kullanın. ASP.NET Core 3,1 ' deki Blazor için desteklenen tarayıcılar listesi değişmemiştir ve [desteklenen platformlarda](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1)belgelenmiştir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

Hiçbiri

<!--

#### Affected APIs

Not detectable via API analysis

-->
