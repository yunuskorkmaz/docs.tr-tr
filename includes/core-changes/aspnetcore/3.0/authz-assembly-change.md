---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394266"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı

@No__t-1 ' de yer almak için kullanılan çekirdek `AddAuthorization` yöntemleri `AddAuthorizationCore` olarak yeniden adlandırıldı. Eski `AddAuthorization` yöntemleri hala mevcuttur, ancak bunun yerine `Microsoft.AspNetCore.Authorization.Policy` paketidir. Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir. İlke paketini kullanmayan uygulamalar `AddAuthorizationCore` ' a geçiş yapılmalıdır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization` ' de vardı.

#### <a name="new-behavior"></a>Yeni davranış

`AddAuthorization` yöntemleri `Microsoft.AspNetCore.Authorization.Policy` ' de bulunur. `AddAuthorizationCore`, eski yöntemlerin yeni adıdır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`AddAuthorization`, yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 ' a bir başvuru ekleyin ya da bunun yerine `AddAuthorizationCore` kullanın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
