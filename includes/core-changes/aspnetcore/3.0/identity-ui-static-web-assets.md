---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041665"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Kimlik: UI statik web varlıkları özelliğini kullanır

ASP.NET Core 3.0 statik bir web varlıkları özelliği tanıttı ve Kimlik UI bunu benimsemiştir.

#### <a name="change-description"></a>Açıklamayı değiştir

Kimlik UI statik web varlıkları özelliği benimseyen bir sonucu olarak:

- Çerçeve seçimi, proje dosyanızdaki `IdentityUIFrameworkVersion` özelliği kullanarak gerçekleştirilir.
- Bootstrap 4, Kimlik Arabirimi için varsayılan UI çerçevesidir. Bootstrap 3 yaşamın sonuna ulaştı ve desteklenen bir sürüme göç düşünmelisiniz.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Kimlik Arabirimi için varsayılan UI çerçevesi **Bootstrap 3**idi. UI çerçevesi, 'deki `AddDefaultUI` `Startup.ConfigureServices`yöntem çağrısına bir parametre kullanılarak yapılandırılabilir.

#### <a name="new-behavior"></a>Yeni davranış

Kimlik Arabirimi için varsayılan UI çerçevesi **Bootstrap**4'dür. U-UI `AddDefaultUI` çerçevesi, yöntem çağrısı yerine proje dosyanızda yapılandırılmalıdır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Statik web varlıkları özelliğinin benimsenmesi, UI çerçeve yapılandırmasının MSBuild'e taşınmasını gerektiriyordu. Hangi çerçeveye yerleştirilemeye karar verebilmek için bir yapı zamanı kararıdır, çalışma zamanı kararı değil.

#### <a name="recommended-action"></a>Önerilen eylem

Yeni Bootstrap 4 bileşenlerinin uyumlu olduğundan emin olmak için sitenizin UI'sini inceleyin. Gerekirse, Bootstrap `IdentityUIFrameworkVersion` 3'e dönmek için MSBuild özelliğini kullanın. Özelliği proje dosyanızdaki bir `<PropertyGroup>` öğeye ekleyin:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
