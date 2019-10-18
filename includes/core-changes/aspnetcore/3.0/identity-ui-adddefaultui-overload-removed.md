---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522678"
---
### <a name="identity-adddefaultui-method-overload-removed"></a>Kimlik: Adddefaultuı yöntemi aşırı yüklemesi kaldırıldı

ASP.NET Core 3,0 ' den başlayarak <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> yöntemi aşırı yüklemesi artık yok.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, statik Web varlıkları özelliğini benimsemenin bir sonucudur.

#### <a name="recommended-action"></a>Önerilen eylem

Aşırı yükleme yerine <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> çağırın. Önyükleme 3 kullanıyorsanız, aşağıdaki satırı proje dosyanızdaki bir `<PropertyGroup>` öğesine de ekleyin:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
