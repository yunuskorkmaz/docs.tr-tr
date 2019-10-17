---
ms.openlocfilehash: 8d7942ef6c36c01a9ae7ae2a9739f26dfcda5813
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394139"
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

Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 3**idi. UI çerçevesi, `Startup.ConfigureServices` ' deki `AddIdentityUI` yöntem çağrısına bir parametre kullanılarak yapılandırılabilir.

#### <a name="new-behavior"></a>Yeni davranış

Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 4**' dir. Kullanıcı arabirimi çerçevesinin, `AddIdentityUI` Yöntem çağrısında değil, proje dosyanızda yapılandırılması gerekir.

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

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)`

-->
