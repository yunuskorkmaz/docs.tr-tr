---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901892"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Yerelleştirme: ResourceManagerWithCultureStringLocalizer ve WithCulture eski olarak işaretlenmiş

[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) sınıf ve [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) arayüz üyesi genellikle kendi `IStringLocalizer` uygulama oluştururken, yerelleştirme kullanıcıları için karışıklık kaynaklarıdır. Bu öğeler, kullanıcıya bir `IStringLocalizer` örneğin "dil başına, kaynak başına" olduğu izlenimini verir. Gerçekte, örnekleri sadece "kaynak başına" olmalıdır. Aranan dil, infaz zamanına `CultureInfo.CurrentUICulture` göre belirlenir. Karışıklığın kaynağını ortadan kaldırmak için API'ler Core 3.0 Preview 3'ASP.NET geçersiz olarak işaretlenmiştir. API'ler ileride yayınlanacak bir sürümde kaldırılacaktır.

Bağlam için [dotnet/aspnetcore#3324'e](https://github.com/dotnet/aspnetcore/issues/3324)bakın. Tartışma için [dotnet/aspnetcore#7756'ya](https://github.com/dotnet/aspnetcore/issues/7756)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Yöntemler ' olarak `Obsolete`işaretlenmemiştir.

#### <a name="new-behavior"></a>Yeni davranış

Yöntemler işaretlenir. `Obsolete`

#### <a name="reason-for-change"></a>Değişiklik nedeni

API'ler önerilmez bir kullanım örneği temsil etti. Yerelleştirme tasarımı hakkında karışıklık vardı.

#### <a name="recommended-action"></a>Önerilen eylem

Öneri bunun yerine `ResourceManagerStringLocalizer` kullanmaktır. Kültür tarafından `CurrentCulture`ayarlansın. Bu bir seçenek değilse, [KaynakYöneticisiWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)bir kopyasını oluşturun ve kullanın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
