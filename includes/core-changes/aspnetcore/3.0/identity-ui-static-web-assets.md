---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032796"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Kimlik: UI statik Web varlıkları özelliğini kullanır

ASP.NET Core 3,0, statik bir Web varlıkları özelliği sunmuştur ve kimlik Kullanıcı arabirimi benimsemiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

Statik Web varlıkları özelliğini benimseme kimlik UI 'sinin sonucu olarak:

- Çerçeve seçimi, `IdentityUIFrameworkVersion` proje dosyanızdaki özelliği kullanılarak gerçekleştirilir.
- Bootstrap 4, kimlik Kullanıcı arabirimi için varsayılan UI çerçevesidir. Bootstrap 3 yaşam sonuna ulaştı ve desteklenen bir sürüme geçirmeyi göz önünde bulundurmanız gerekir.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 3** idi. UI çerçevesi, içindeki yöntem çağrısına bir parametre kullanılarak yapılandırılabilir `AddDefaultUI` `Startup.ConfigureServices` .

#### <a name="new-behavior"></a>Yeni davranış

Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 4**' dir. UI çerçevesi, yöntem çağrısı yerine proje dosyanızda yapılandırılmalıdır `AddDefaultUI` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

UI çerçevesi yapılandırmasının MSBuild 'e taşınması için statik Web varlıkları özelliğini benimseme özelliği gereklidir. Hangi çerçevenin katıştırılması, çalışma zamanı kararı değil, derleme zamanı karardır.

#### <a name="recommended-action"></a>Önerilen eylem

Yeni önyükleme 4 bileşenlerinin uyumlu olduğundan emin olmak için site Kullanıcı arabirimini gözden geçirin. Gerekirse, `IdentityUIFrameworkVersion` önyükleme 3 ' e dönmek için MSBuild özelliğini kullanın. Özelliği `<PropertyGroup>` proje dosyanızdaki bir öğeye ekleyin:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
