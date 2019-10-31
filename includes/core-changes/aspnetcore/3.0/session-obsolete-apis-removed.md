---
ms.openlocfilehash: 4dcb357570cb6597fde86c9e8f2acb74364cfaa3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198590"
---
### <a name="session-state-obsolete-apis-removed"></a><span data-ttu-id="7af8e-101">Oturum durumu: kullanılmayan API 'Ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="7af8e-101">Session state: Obsolete APIs removed</span></span>

<span data-ttu-id="7af8e-102">Oturum tanımlama bilgilerini yapılandırmak için kullanılmayan API 'Ler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7af8e-102">Obsolete APIs for configuring session cookies were removed.</span></span> <span data-ttu-id="7af8e-103">Daha fazla bilgi için bkz. [ASPNET/Duyurular # 257](https://github.com/aspnet/Announcements/issues/257).</span><span class="sxs-lookup"><span data-stu-id="7af8e-103">For more information, see [aspnet/Announcements#257](https://github.com/aspnet/Announcements/issues/257).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7af8e-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7af8e-104">Version introduced</span></span>

<span data-ttu-id="7af8e-105">3.0</span><span class="sxs-lookup"><span data-stu-id="7af8e-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7af8e-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7af8e-106">Reason for change</span></span>

<span data-ttu-id="7af8e-107">Bu değişiklik, tanımlama bilgilerini kullanan özellikleri yapılandırmak için API 'lerde tutarlılığı zorlar.</span><span class="sxs-lookup"><span data-stu-id="7af8e-107">This change enforces consistency across APIs for configuring features that use cookies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7af8e-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7af8e-108">Recommended action</span></span>

<span data-ttu-id="7af8e-109">Kaldırılan API 'lerin kullanımını daha yeni değişikliklere geçirin.</span><span class="sxs-lookup"><span data-stu-id="7af8e-109">Migrate usage of the removed APIs to their newer replacements.</span></span> <span data-ttu-id="7af8e-110">`Startup.ConfigureServices`içinde aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7af8e-110">Consider the following example in `Startup.ConfigureServices`:</span></span>

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

#### <a name="category"></a><span data-ttu-id="7af8e-111">Kategori</span><span class="sxs-lookup"><span data-stu-id="7af8e-111">Category</span></span>

<span data-ttu-id="7af8e-112">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7af8e-112">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7af8e-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7af8e-113">Affected APIs</span></span>

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
