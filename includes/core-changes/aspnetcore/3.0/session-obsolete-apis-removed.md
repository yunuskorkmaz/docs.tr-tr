---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198590"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="aa1cb-101">Oturum durumu: Eski API'ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aa1cb-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="aa1cb-102">Oturum tanımlama bilgilerini yapılandırmak için eski API'ler kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="aa1cb-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="aa1cb-103">Daha fazla bilgi için [aspnet/Announcements#257'ye](https://github.com/aspnet/Announcements/issues/257)bakın.</span><span class="sxs-lookup"><span data-stu-id="aa1cb-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aa1cb-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="aa1cb-104">Version introduced</span></span>

<span data-ttu-id="aa1cb-105">3,0</span><span class="sxs-lookup"><span data-stu-id="aa1cb-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="aa1cb-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="aa1cb-106">Reason for change</span></span>

<span data-ttu-id="aa1cb-107">Bu değişiklik, tanımlama bilgileri kullanan özellikleri yapılandırmak için API'ler arasında tutarlılık zorlar.</span><span class="sxs-lookup"><span data-stu-id="aa1cb-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aa1cb-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="aa1cb-108">Recommended action</span></span>

<span data-ttu-id="aa1cb-109">Kaldırılan API'lerin kullanımını yeni değiştirmelerine geçirin.</span><span class="sxs-lookup"><span data-stu-id="aa1cb-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="aa1cb-110">Aşağıdaki örneği göz `Startup.ConfigureServices`önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="aa1cb-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(ServiceCollection services)
{
    services.AddSession(options =>
    {
        // Removed obsolete APIs
        options.CookieName = "SessionCookie";
        options.CookieDomain = "contoso.com";
        options.CookiePath = "/";
        options.CookieHttpOnly = true;
        options.CookieSecure = CookieSecurePolicy.Always;

        // new API
        options.Cookie.Name = "SessionCookie";
        options.Cookie.Domain = "contoso.com";
        options.Cookie.Path = "/";
        options.Cookie.HttpOnly = true;
        options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    });
}
```

#### <a name="category"></a><span data-ttu-id="aa1cb-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="aa1cb-111">Category</span></span>

<span data-ttu-id="aa1cb-112">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="aa1cb-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa1cb-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aa1cb-113">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure?displayProperty=fullName>

<!-- 

#### Affected APIs

- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieHttpOnly`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieName`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookiePath`
- `P:Microsoft.AspNetCore.Builder.SessionOptions.CookieSecure`

-->
