---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077598"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="10ebb-101">Blazor: JSObjectReference ve JSInProcessObjectReference türleri internal olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="10ebb-101">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="10ebb-102">`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET Core 5,0 RC1 'de tanıtılan yeni ve türler olarak işaretlendi `internal` .</span><span class="sxs-lookup"><span data-stu-id="10ebb-102">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10ebb-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="10ebb-103">Version introduced</span></span>

<span data-ttu-id="10ebb-104">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="10ebb-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="10ebb-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="10ebb-105">Old behavior</span></span>

<span data-ttu-id="10ebb-106">`JSObjectReference`, İle bir JavaScript birlikte çalışma çağrısından elde edilebilir `IJSRuntime` .</span><span class="sxs-lookup"><span data-stu-id="10ebb-106">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="10ebb-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="10ebb-107">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a><span data-ttu-id="10ebb-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="10ebb-108">New behavior</span></span>

<span data-ttu-id="10ebb-109">`JSObjectReference`[iç](../../../../docs/csharp/language-reference/keywords/internal.md) erişim değiştiricisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="10ebb-109">`JSObjectReference` uses the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="10ebb-110">`public` `IJSObjectReference` Bunun yerine arabirimin kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10ebb-110">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="10ebb-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="10ebb-111">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="10ebb-112">`JSInProcessObjectReference` aynı zamanda olarak işaretlendi `internal` ve tarafından değiştirildi `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="10ebb-112">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="10ebb-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="10ebb-113">Reason for change</span></span>

<span data-ttu-id="10ebb-114">Değişiklik, JavaScript birlikte çalışma özelliğini Blazor içindeki diğer desenlerle daha tutarlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="10ebb-114">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="10ebb-115">`IJSObjectReference` , `IJSRuntime` benzer bir amaca hizmet veren ve benzer yöntemlere ve uzantılara sahip olacak şekilde benzerdir.</span><span class="sxs-lookup"><span data-stu-id="10ebb-115">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10ebb-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="10ebb-116">Recommended action</span></span>

<span data-ttu-id="10ebb-117">Ve gibi oluşumlarını `JSObjectReference` `JSInProcessObjectReference` `IJSObjectReference` sırasıyla ve ile değiştirin `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="10ebb-117">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

#### <a name="category"></a><span data-ttu-id="10ebb-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="10ebb-118">Category</span></span>

<span data-ttu-id="10ebb-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="10ebb-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10ebb-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="10ebb-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
