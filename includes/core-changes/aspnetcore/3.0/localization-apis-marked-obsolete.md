---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032819"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Yerelleştirme: ResourceManagerWithCultureStringLocalizer ve WithCulture artık kullanılmıyor olarak işaretlendi

[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) sınıfı ve [withculture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) arabirim üyesi, genellikle yerelleştirme kullanıcıları için, özellikle kendi uygulamasını oluştururken karışıklık kaynaklarıdır `IStringLocalizer` . Bu öğeler kullanıcıya bir `IStringLocalizer` Örneğin "dil başına, kaynak başına" olan izlenimi verir. Gerçekte, örneklerin yalnızca "kaynak başına" olması gerekir. İçin aranan dil, yürütme zamanına göre belirlenir `CultureInfo.CurrentUICulture` . Karışıklık kaynağını ortadan kaldırmak için, API 'Ler ASP.NET Core 3,0 Preview 3 ' te eski olarak işaretlendi. API 'Ler gelecek bir sürümde kaldırılacak.

Bağlam için bkz. [DotNet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Tartışma için bkz. [DotNet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Yöntemler olarak işaretlenmemiş `Obsolete` .

#### <a name="new-behavior"></a>Yeni davranış

Yöntemler işaretlenir `Obsolete` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

API 'Ler önerilmeyen bir kullanım durumunu temsil eder. Yerelleştirme tasarımı hakkında karışıklık vardı.

#### <a name="recommended-action"></a>Önerilen eylem

`ResourceManagerStringLocalizer`Bunun yerine kullanılması önerilir. Kültürün tarafından ayarlanmasına izin verin `CurrentCulture` . Bu seçenek değilse, bir [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)kopyası oluşturun ve kullanın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
