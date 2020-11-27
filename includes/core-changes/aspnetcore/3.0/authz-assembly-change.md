---
ms.openlocfilehash: 2819fb3857fa6d40a2b2e42eeaec2d9c6e50eef0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96299359"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı

`AddAuthorization`İçinde yer almak için kullanılan temel yöntemler `Microsoft.AspNetCore.Authorization` olarak yeniden adlandırıldı `AddAuthorizationCore` . Eski `AddAuthorization` Yöntemler hala mevcuttur, ancak `Microsoft.AspNetCore.Authorization.Policy` bunun yerine derlemede bulunur. Her iki yöntemi kullanan uygulamalar hiçbir etki görmemelidir. Artık paylaşılan çerçevede `Microsoft.AspNetCore.Authorization.Policy` açıklandığı gibi, paylaşılan çerçevede kullanıma sunulan bir bağımsız paket yerine, [Microsoft. Aspnetcore. app öğesinden kaldırılan derlemeler](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`AddAuthorization` Yöntemler içinde vardı `Microsoft.AspNetCore.Authorization` .

#### <a name="new-behavior"></a>Yeni davranış

`AddAuthorization` yöntemleri içinde bulunur `Microsoft.AspNetCore.Authorization.Policy` . `AddAuthorizationCore` , eski yöntemlerin yeni adıdır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

`AddAuthorization` , yetkilendirme için gereken tüm ortak hizmetleri eklemek için daha iyi bir yöntem adıdır.

#### <a name="recommended-action"></a>Önerilen eylem

Bunun yerine bir başvuru ekleyin `Microsoft.AspNetCore.Authorization.Policy` ya da kullanın `AddAuthorizationCore` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
