---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032861"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="3f4a3-101">Oturum durumu: kullanılmayan API 'Ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="3f4a3-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="3f4a3-102">Oturum tanımlama bilgilerini yapılandırmak için kullanılmayan API 'Ler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="3f4a3-103">Daha fazla bilgi için bkz. [ASPNET/Duyurular # 257](https://github.com/aspnet/Announcements/issues/257).</span><span class="sxs-lookup"><span data-stu-id="3f4a3-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f4a3-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3f4a3-104">Version introduced</span></span>

<span data-ttu-id="3f4a3-105">3,0</span><span class="sxs-lookup"><span data-stu-id="3f4a3-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3f4a3-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3f4a3-106">Reason for change</span></span>

<span data-ttu-id="3f4a3-107">Bu değişiklik, tanımlama bilgilerini kullanan özellikleri yapılandırmak için API 'lerde tutarlılığı zorlar.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f4a3-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3f4a3-108">Recommended action</span></span>

<span data-ttu-id="3f4a3-109">Kaldırılan API 'lerin kullanımını daha yeni değişikliklere geçirin.</span><span class="sxs-lookup"><span data-stu-id="3f4a3-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="3f4a3-110">İçinde aşağıdaki örneği göz önünde bulundurun `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="3f4a3-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

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

#### <a name="category"></a><span data-ttu-id="3f4a3-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="3f4a3-111">Category</span></span>

<span data-ttu-id="3f4a3-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3f4a3-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f4a3-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3f4a3-113">Affected APIs</span></span>

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
