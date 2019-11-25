---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74101589"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı

`Microsoft.AspNetCore.Authorization` içinde yer almak için kullanılan temel `AddAuthorization` yöntemleri `AddAuthorizationCore`olarak yeniden adlandırıldı. Eski `AddAuthorization` yöntemleri hala mevcuttur, ancak bunun yerine `Microsoft.AspNetCore.Authorization.Policy` bütünleştirilmiş kodunda bulunur. Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir. `Microsoft.AspNetCore.Authorization.Policy` artık paylaşılan çerçevede açıklandığı gibi, paylaşılan çerçevede ( [Microsoft. AspNetCore. app 'ten kaldırılan derlemeler](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)) kullanıma sunulmadığını unutmayın.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış
`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization` ' de vardı.

#### <a name="new-behavior"></a>Yeni davranış

`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization.Policy` ' de bulunur. `AddAuthorizationCore`, eski yöntemlerin yeni adıdır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`AddAuthorization`, yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.

#### <a name="recommended-action"></a>Önerilen eylem

`Microsoft.AspNetCore.Authorization.Policy` bir başvuru ekleyin ya da bunun yerine `AddAuthorizationCore` kullanın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
