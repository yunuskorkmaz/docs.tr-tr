---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393945"
---
### <a name="authentication-google-deprecated-and-replaced"></a><span data-ttu-id="4f82d-101">Kimlik doğrulama: Google+ amortismana uğradı ve değiştirildi</span><span class="sxs-lookup"><span data-stu-id="4f82d-101">Authentication: Google+ deprecated and replaced</span></span>

<span data-ttu-id="4f82d-102">Google, uygulamalar için Google+ Oturum Açma'yı 28 Ocak 2019'dan itibaren [kapatmaya](https://developers.google.com/+/api-shutdown) başlıyor.</span><span class="sxs-lookup"><span data-stu-id="4f82d-102">Google is starting to [shut down](https://developers.google.com/+/api-shutdown) Google+ Sign-in for apps as early as January 28, 2019.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f82d-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="4f82d-103">Change description</span></span>

<span data-ttu-id="4f82d-104">ASP.NET 4.x ve ASP.NET Core, Google hesap kullanıcılarının web uygulamalarındaki kimliğini doğrulamak için Google+ Oturum Açma API'lerini kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="4f82d-104">ASP.NET 4.x and ASP.NET Core have been using the Google+ Sign-in APIs to authenticate Google account users in web apps.</span></span> <span data-ttu-id="4f82d-105">Etkilenen NuGet paketleri ASP.NET Web Formları ve MVC ile ASP.NET Core ve [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) için `Microsoft.Owin` [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) vardır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-105">The affected NuGet packages are [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core and [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) for `Microsoft.Owin` with ASP.NET Web Forms and MVC.</span></span>

<span data-ttu-id="4f82d-106">Google'ın yedek API'leri farklı bir veri kaynağı ve biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-106">Google's replacement APIs use a different data source and format.</span></span> <span data-ttu-id="4f82d-107">Aşağıda sağlanan azaltıcı etkenler ve çözümler yapısal değişiklikleri hesaba kattır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-107">The mitigations and solutions provided below account for the structural changes.</span></span> <span data-ttu-id="4f82d-108">Uygulamalar, verilerin gereksinimlerini hala karşıladığından doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-108">Apps should verify the data itself still satisfies their requirements.</span></span> <span data-ttu-id="4f82d-109">Örneğin, adlar, e-posta adresleri, profil bağlantıları ve profil fotoğrafları öncekinden çok farklı değerler sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-109">For example, names, email addresses, profile links, and profile photos may provide subtly different values than before.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f82d-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="4f82d-110">Version introduced</span></span>

<span data-ttu-id="4f82d-111">Tüm versiyonları.</span><span class="sxs-lookup"><span data-stu-id="4f82d-111">All versions.</span></span> <span data-ttu-id="4f82d-112">Bu değişiklik ASP.NET Core'un dışındadır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-112">This change is external to ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f82d-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4f82d-113">Recommended action</span></span>

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a><span data-ttu-id="4f82d-114">ASP.NET Web Formları ve MVC ile Owin</span><span class="sxs-lookup"><span data-stu-id="4f82d-114">Owin with ASP.NET Web Forms and MVC</span></span>

<span data-ttu-id="4f82d-115">3.1.0 ve sonrası için, `Microsoft.Owin` geçici bir azaltma [burada](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-115">For `Microsoft.Owin` 3.1.0 and later, a temporary mitigation is outlined [here](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635).</span></span> <span data-ttu-id="4f82d-116">Uygulamalar, veri biçimindeki değişiklikleri denetlemek için azaltma yla testleri tamamlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-116">Apps should complete testing with the mitigation to check for changes in the data format.</span></span> <span data-ttu-id="4f82d-117">Bir düzeltme ile `Microsoft.Owin` 4.0.1 serbest bırakmak için planlar vardır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-117">There are plans to release `Microsoft.Owin` 4.0.1 with a fix.</span></span> <span data-ttu-id="4f82d-118">Önceki sürümlerden herhangi bir sürümü kullanan uygulamaların sürüm 4.0.1'e güncellemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-118">Apps using any prior version should update to version 4.0.1.</span></span>

##### <a name="aspnet-core-1x"></a><span data-ttu-id="4f82d-119">ASP.NET Çekirdek 1.x</span><span class="sxs-lookup"><span data-stu-id="4f82d-119">ASP.NET Core 1.x</span></span>

<span data-ttu-id="4f82d-120">[ASP.NET Web Formları ve MVC ile Owin](#owin-with-aspnet-web-forms-and-mvc) azaltma core 1.x ASP.NET adapte edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-120">The mitigation in [Owin with ASP.NET Web Forms and MVC](#owin-with-aspnet-web-forms-and-mvc) can be adapted to ASP.NET Core 1.x.</span></span> <span data-ttu-id="4f82d-121">1.x [yaşam durumunun sonuna ulaştığından](https://dotnet.microsoft.com/platform/support-policy) NuGet paket düzeltme emaları planlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-121">NuGet package patches aren't planned because 1.x has reached [end of life](https://dotnet.microsoft.com/platform/support-policy) status.</span></span>

##### <a name="aspnet-core-2x"></a><span data-ttu-id="4f82d-122">ASP.NET Çekirdek 2.x</span><span class="sxs-lookup"><span data-stu-id="4f82d-122">ASP.NET Core 2.x</span></span>

<span data-ttu-id="4f82d-123">`Microsoft.AspNetCore.Authentication.Google` Sürüm 2.x için, mevcut `AddGoogle` aramanızı aşağıdaki `Startup.ConfigureServices` kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="4f82d-123">For `Microsoft.AspNetCore.Authentication.Google` version 2.x, replace your existing call to `AddGoogle` in `Startup.ConfigureServices` with the following code:</span></span>

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

<span data-ttu-id="4f82d-124">Şubat 2.1 ve 2.2 yamaları, önceki yeniden yapılandırmayı yeni varsayılan olarak içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="4f82d-124">The February 2.1 and 2.2 patches incorporated the preceding reconfiguration as the new default.</span></span> <span data-ttu-id="4f82d-125">[Yaşamın sonuna](https://dotnet.microsoft.com/platform/support-policy)ulaştığından ASP.NET Core 2.0 için hiçbir yama planlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="4f82d-125">No patch is planned for ASP.NET Core 2.0 since it has reached [end of life](https://dotnet.microsoft.com/platform/support-policy).</span></span>

##### <a name="aspnet-core-30"></a><span data-ttu-id="4f82d-126">ASP.NET Çekirdek 3.0</span><span class="sxs-lookup"><span data-stu-id="4f82d-126">ASP.NET Core 3.0</span></span>

<span data-ttu-id="4f82d-127">Core 2.x ASP.NET için verilen azaltma, Core 3.0'ı ASP.NET için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-127">The mitigation given for ASP.NET Core 2.x can also be used for ASP.NET Core 3.0.</span></span> <span data-ttu-id="4f82d-128">Gelecek 3.0 önizlemelerinde `Microsoft.AspNetCore.Authentication.Google` paket kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-128">In future 3.0 previews, the `Microsoft.AspNetCore.Authentication.Google` package may be removed.</span></span> <span data-ttu-id="4f82d-129">Kullanıcılar `Microsoft.AspNetCore.Authentication.OpenIdConnect` bunun yerine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-129">Users would be directed to `Microsoft.AspNetCore.Authentication.OpenIdConnect` instead.</span></span> <span data-ttu-id="4f82d-130">Aşağıdaki kod' un `AddGoogle` nasıl `AddOpenIdConnect` `Startup.ConfigureServices`değiştirilen ile değiştirilen</span><span class="sxs-lookup"><span data-stu-id="4f82d-130">The following code shows how to replace `AddGoogle` with `AddOpenIdConnect` in `Startup.ConfigureServices`.</span></span> <span data-ttu-id="4f82d-131">Bu değiştirme ASP.NET Core 2.0 ve daha sonra kullanılabilir ve gerektiğinde Core 1.x ASP.NET için uyarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4f82d-131">This replacement can be used with ASP.NET Core 2.0 and later and can be adapted for ASP.NET Core 1.x as needed.</span></span>

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a><span data-ttu-id="4f82d-132">Kategori</span><span class="sxs-lookup"><span data-stu-id="4f82d-132">Category</span></span>

<span data-ttu-id="4f82d-133">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="4f82d-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f82d-134">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4f82d-134">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
