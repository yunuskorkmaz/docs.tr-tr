---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077598"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi

`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET Core 5,0 RC1 'de tanıtılan yeni ve türler olarak işaretlendi `internal` .

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

#### <a name="old-behavior"></a>Eski davranış

`JSObjectReference`, İle bir JavaScript birlikte çalışma çağrısından elde edilebilir `IJSRuntime` . Örneğin:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a>Yeni davranış

`JSObjectReference`[iç](../../../../docs/csharp/language-reference/keywords/internal.md) erişim değiştiricisini kullanır. `public` `IJSObjectReference` Bunun yerine arabirimin kullanılması gerekir. Örneğin:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` aynı zamanda olarak işaretlendi `internal` ve tarafından değiştirildi `IJSInProcessObjectReference` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik, JavaScript birlikte çalışma özelliğini Blazor içindeki diğer desenlerle daha tutarlı hale getirir. `IJSObjectReference` , `IJSRuntime` benzer bir amaca hizmet veren ve benzer yöntemlere ve uzantılara sahip olacak şekilde benzerdir.

#### <a name="recommended-action"></a>Önerilen eylem

Ve gibi oluşumlarını `JSObjectReference` `JSInProcessObjectReference` `IJSObjectReference` sırasıyla ve ile değiştirin `IJSInProcessObjectReference` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
