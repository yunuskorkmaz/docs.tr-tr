---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637203"
---
### <a name="identity-adddefaultui-method-overload-removed"></a>Kimlik: AddDefaultUI yöntemi aşırı kaldırıldı

Core 3.0 ASP.NET ile başlayarak, [IdentityBuilderUIExtensions.AddDefaultUI (IdentityBuilder, UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) yöntemi aşırı artık yok.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, statik web varlıkları özelliğinin benimsenmesinin bir sonucuydu.

#### <a name="recommended-action"></a>Önerilen eylem

İki <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> bağımsız değişken gerektiren aşırı yükleme yerine arayın. Bootstrap 3 kullanıyorsanız, proje dosyanızdaki bir `<PropertyGroup>` öğeye aşağıdaki satırı da ekleyin:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

[IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
