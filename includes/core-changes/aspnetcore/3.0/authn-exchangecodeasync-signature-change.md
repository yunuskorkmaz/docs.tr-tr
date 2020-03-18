---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394239"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="92075-101">Kimlik doğrulama: OAuthHandler ExchangeCodeAsync imza değiştirildi</span><span class="sxs-lookup"><span data-stu-id="92075-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="92075-102">core 3.0ASP.NETde imzası `OAuthHandler.ExchangeCodeAsync` aşağıdakilerden değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="92075-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="92075-103">Hedef:</span><span class="sxs-lookup"><span data-stu-id="92075-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="92075-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="92075-104">Version introduced</span></span>

<span data-ttu-id="92075-105">3,0</span><span class="sxs-lookup"><span data-stu-id="92075-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="92075-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="92075-106">Old behavior</span></span>

<span data-ttu-id="92075-107">`code` Ve `redirectUri` dizeleri ayrı bağımsız değişkenler olarak geçirildi.</span><span class="sxs-lookup"><span data-stu-id="92075-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="92075-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="92075-108">New behavior</span></span>

<span data-ttu-id="92075-109">`Code`ve `RedirectUri` `OAuthCodeExchangeContext` `OAuthCodeExchangeContext` konstrüktör aracılığıyla ayarlanabilen özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="92075-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="92075-110">Yeni `OAuthCodeExchangeContext` tür, `OAuthHandler.ExchangeCodeAsync`''ye geçirilen tek bağımsız değişkendir.</span><span class="sxs-lookup"><span data-stu-id="92075-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="92075-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="92075-111">Reason for change</span></span>

<span data-ttu-id="92075-112">Bu değişiklik, ek parametrelerin kırılmaz bir şekilde sağlanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="92075-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="92075-113">Yeni `ExchangeCodeAsync` aşırı yüklemeler yaratmaya gerek yok.</span><span class="sxs-lookup"><span data-stu-id="92075-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="92075-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="92075-114">Recommended action</span></span>

<span data-ttu-id="92075-115">Uygun `OAuthCodeExchangeContext` `code` ve `redirectUri` değerlerle bir yapı inşa edin.</span><span class="sxs-lookup"><span data-stu-id="92075-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="92075-116">Bir <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> örnek sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92075-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="92075-117">Bu `OAuthCodeExchangeContext` tek örnek, `OAuthHandler.ExchangeCodeAsync` birden çok bağımsız değişken yerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="92075-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="92075-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="92075-118">Category</span></span>

<span data-ttu-id="92075-119">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="92075-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="92075-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="92075-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
