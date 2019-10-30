---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041665"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Kimlik: UI statik Web varlıkları özelliğini kullanır

ASP.NET Core 3,0, statik bir Web varlıkları özelliği sunmuştur ve kimlik Kullanıcı arabirimi benimsemiştir.

#### <a name="change-description"></a>Açıklamayı Değiştir

Statik Web varlıkları özelliğini benimseme kimlik UI 'sinin sonucu olarak:

- Çerçeve seçimi, proje dosyanızdaki `IdentityUIFrameworkVersion` özelliği kullanılarak gerçekleştirilir.
- Bootstrap 4, kimlik Kullanıcı arabirimi için varsayılan UI çerçevesidir. Bootstrap 3 yaşam sonuna ulaştı ve desteklenen bir sürüme geçirmeyi göz önünde bulundurmanız gerekir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 3**idi. UI çerçevesi, `Startup.ConfigureServices``AddDefaultUI` yöntemi çağrısına bir parametre kullanılarak yapılandırılabilir.

#### <a name="new-behavior"></a>Yeni davranış

Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 4**' dir. Kullanıcı arabirimi çerçevesi, `AddDefaultUI` yöntemi çağrısı yerine proje dosyanızda yapılandırılmalıdır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

UI çerçevesi yapılandırmasının MSBuild 'e taşınması için statik Web varlıkları özelliğini benimseme özelliği gereklidir. Hangi çerçevenin katıştırılması, çalışma zamanı kararı değil, derleme zamanı karardır.

#### <a name="recommended-action"></a>Önerilen eylem

Yeni önyükleme 4 bileşenlerinin uyumlu olduğundan emin olmak için site Kullanıcı arabirimini gözden geçirin. Gerekirse, önyükleme 3 ' e dönmek için `IdentityUIFrameworkVersion` MSBuild özelliğini kullanın. Özelliği proje dosyanızdaki bir `<PropertyGroup>` öğesine ekleyin:

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
