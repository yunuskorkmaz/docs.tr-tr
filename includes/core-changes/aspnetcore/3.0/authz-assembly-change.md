---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74101589"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Yetkilendirme: AddAuthorization aşırı yükü farklı derlemeye taşındı

Eskiden `AddAuthorization` içinde bulunan `Microsoft.AspNetCore.Authorization` temel yöntemlerin adı `AddAuthorizationCore`". Eski `AddAuthorization` yöntemler hala var, ancak `Microsoft.AspNetCore.Authorization.Policy` bunun yerine derleme bulunmaktadır. Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir. `Microsoft.AspNetCore.Authorization.Policy` Artık paylaşılan çerçevede tartışılan bağımsız bir paket yerine paylaşılan çerçevede gemilerin olduğunu [unutmayın: Derlemeler Microsoft.AspNetCore.App kaldırıldı.](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış
`AddAuthorization`metodları `Microsoft.AspNetCore.Authorization`var.

#### <a name="new-behavior"></a>Yeni davranış

`AddAuthorization`metodları `Microsoft.AspNetCore.Authorization.Policy`. `AddAuthorizationCore`eski yöntemleriçin yeni bir addır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`AddAuthorization`yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.

#### <a name="recommended-action"></a>Önerilen eylem

Bir başvuru ekleyin `Microsoft.AspNetCore.Authorization.Policy` veya `AddAuthorizationCore` bunun yerine kullanın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
