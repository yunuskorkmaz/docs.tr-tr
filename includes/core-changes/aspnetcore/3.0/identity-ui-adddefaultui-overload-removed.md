---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522678"
---
### <a name="identity-adddefaultui-method-overload-removed"></a>Kimlik: AddDefaultUI yöntemi aşırı kaldırıldı

Core 3.0 ASP.NET ile <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> başlayarak, yöntem aşırı artık yok.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, statik web varlıkları özelliğinin benimsenmesinin bir sonucuydu.

#### <a name="recommended-action"></a>Önerilen eylem

Aşırı <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> yükleme yerine arayın. Bootstrap 3 kullanıyorsanız, proje dosyanızdaki bir `<PropertyGroup>` öğeye aşağıdaki satırı da ekleyin:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
