---
title: 'Son değişiklik: Blazor: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 43a66d204f8309dc5afc57d099b2201c477cc3ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761482"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi

`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET Core 5,0 RC1 'de tanıtılan yeni ve türler olarak işaretlendi `internal` .

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC2

## <a name="old-behavior"></a>Eski davranış

`JSObjectReference`, İle bir JavaScript birlikte çalışma çağrısından elde edilebilir `IJSRuntime` . Örnek:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a>Yeni davranış

`JSObjectReference`[iç](../../../../csharp/language-reference/keywords/internal.md) erişim değiştiricisini kullanır. `public` `IJSObjectReference` Bunun yerine arabirimin kullanılması gerekir. Örnek:

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` aynı zamanda olarak işaretlendi `internal` ve tarafından değiştirildi `IJSInProcessObjectReference` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik, JavaScript birlikte çalışma özelliğini Blazor içindeki diğer desenlerle daha tutarlı hale getirir. `IJSObjectReference` , `IJSRuntime` benzer bir amaca hizmet veren ve benzer yöntemlere ve uzantılara sahip olacak şekilde benzerdir.

## <a name="recommended-action"></a>Önerilen eylem

Ve gibi oluşumlarını `JSObjectReference` `JSInProcessObjectReference` `IJSObjectReference` sırasıyla ve ile değiştirin `IJSInProcessObjectReference` .

## <a name="affected-apis"></a>Etkilenen API’ler

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
