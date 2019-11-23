---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394418"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Yerelleştirme: ResourceManagerWithCultureStringLocalizer ve WithCulture artık kullanılmıyor olarak işaretlendi

[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) sınıfı ve [withculture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) arabirim üyesi, genellikle yerelleştirme kullanıcıları için, özellikle kendi `IStringLocalizer` uygulamasını oluştururken karışıklık kaynaklarıdır. Bu öğeler kullanıcıya bir `IStringLocalizer` örneği "dil başına, kaynak başına" olan izlenimi verir. Gerçekte, örneklerin yalnızca "kaynak başına" olması gerekir. Aranan dil, yürütme sırasında `CultureInfo.CurrentUICulture` tarafından belirlenir. Karışıklık kaynağını ortadan kaldırmak için, API 'Ler ASP.NET Core 3,0 Preview 3 ' te eski olarak işaretlendi. API 'Ler gelecek bir sürümde kaldırılacak.

Bağlam için bkz. [ASPNET/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324). Tartışma için bkz. [ASPNET/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Yöntemler `Obsolete`olarak işaretlenmedi.

#### <a name="new-behavior"></a>Yeni davranış

Yöntemler `Obsolete`olarak işaretlenir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

API 'Ler önerilmeyen bir kullanım durumunu temsil eder. Yerelleştirme tasarımı hakkında karışıklık vardı.

#### <a name="recommended-action"></a>Önerilen eylem

Bunun yerine `ResourceManagerStringLocalizer` kullanılması önerilir. Kültür `CurrentCulture`tarafından ayarlanmasına izin verin. Bu seçenek değilse, bir [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)kopyası oluşturun ve kullanın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
