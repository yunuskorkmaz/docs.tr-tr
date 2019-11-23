---
title: Arama kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC çağrı kimlik bilgilerini uygulama ve kullanma.
ms.date: 09/02/2019
ms.openlocfilehash: 2588fe3590a63ea6071b85ff29b3685efbfa25db
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967992"
---
# <a name="call-credentials"></a><span data-ttu-id="ef40c-103">Çağrı kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="ef40c-103">Call credentials</span></span>

<span data-ttu-id="ef40c-104">Çağrı kimlik bilgileri her istekle birlikte meta verilerde geçirilen bazı belirteç türlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-104">Call credentials are all based on some kind of token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="ef40c-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="ef40c-105">WS-Federation</span></span>

<span data-ttu-id="ef40c-106">ASP.NET Core, [WSFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet PAKETINI kullanarak WS-Federation ' i destekler.</span><span class="sxs-lookup"><span data-stu-id="ef40c-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="ef40c-107">WS-Federation, Windows kimlik doğrulaması için HTTP/2 üzerinde desteklenmeyen en yakın seçenektir.</span><span class="sxs-lookup"><span data-stu-id="ef40c-107">WS-Federation is the closest available alternative to Windows Authentication, which is not supported over HTTP/2.</span></span> <span data-ttu-id="ef40c-108">Kullanıcılar, ASP.NET Core kimlik doğrulaması için kullanılabilecek bir belirteç sağlayan Active Directory Federasyon Hizmetleri (AD FS) (ADFS) kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-108">Users are authenticated using Active Directory Federation Services (ADFS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="ef40c-109">Bu kimlik doğrulama yöntemiyle çalışmaya başlama hakkında daha fazla bilgi için [ASP.NET Core 'de WS-Federation ile kullanıcıların kimliğini doğrulama](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="ef40c-109">For more information on how to get started with this authentication method, see the [Authenticate users with WS-Federation in ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) article.</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="ef40c-110">JWT taşıyıcı belirteçleri</span><span class="sxs-lookup"><span data-stu-id="ef40c-110">JWT Bearer tokens</span></span>

<span data-ttu-id="ef40c-111">[JSON Web Token](https://jwt.io) standardı, kodlanmış bir dizedeki bir Kullanıcı ve talepleri hakkında bilgi kodlamak ve bu belirteci, tüketicinin ortak anahtar şifrelemesini kullanarak belirtecin bütünlüğünü doğrulayabilmeleri için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef40c-111">The [JSON Web Token](https://jwt.io) standard provides a way to encode information about a user and their claims in an encoded string, and to sign that token in such a way that the consumer can verify the integrity of the token using public key cryptography.</span></span> <span data-ttu-id="ef40c-112">Kullanıcıların kimliğini doğrulamak ve gRPC ve HTTP API 'Leri ile kullanılacak OpenID Connect (OıDC) belirteçlerini oluşturmak için ıdentityserver4 gibi çeşitli hizmetleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef40c-112">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="ef40c-113">ASP.NET Core 3,0, JWT taşıyıcı paketini kullanarak JSON Web belirteçlerini işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ef40c-113">ASP.NET Core 3.0 can handle JSON Web Tokens using the JWT Bearer package.</span></span> <span data-ttu-id="ef40c-114">Yapılandırma, ASP.NET Core MVC uygulaması olarak bir gRPC uygulaması için tam olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-114">The configuration is exactly the same for a gRPC application as an ASP.NET Core MVC application.</span></span>

<span data-ttu-id="ef40c-115">Bu bölüm, WS-Federation ' den daha kolay geliştirme yaparken JWT taşıyıcı belirteçlerine odaklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-115">This chapter will focus on JWT Bearer tokens as they're easier to develop with than WS-Federation.</span></span>

## <a name="adding-authentication-and-authorization-to-the-server"></a><span data-ttu-id="ef40c-116">Sunucuya kimlik doğrulaması ve yetkilendirme ekleme</span><span class="sxs-lookup"><span data-stu-id="ef40c-116">Adding authentication and authorization to the server</span></span>

<span data-ttu-id="ef40c-117">JWT taşıyıcı paketi, varsayılan olarak ASP.NET Core 3,0 ' ye dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="ef40c-117">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="ef40c-118">Uygulamanıza [Microsoft. AspNetCore. Authentication. Jwttaşıyıcı](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="ef40c-118">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="ef40c-119">Başlangıç sınıfına kimlik doğrulama hizmetini ekleyin ve JWT taşıyıcı işleyicisini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ef40c-119">Add the Authentication service in the Startup class and configure the JWT Bearer handler.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="ef40c-120">`IssuerSigningKey` özelliği, imzalanmış belirteçleri doğrulamak için gereken şifreleme verileriyle `Microsoft.IdentityModels.Tokens.SecurityKey` uygulanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ef40c-120">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="ef40c-121">Bu belirtecin Azure Keykasası gibi bir *gizli dizi sunucusunda* güvenli bir şekilde depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef40c-121">This token should be stored securely in a *secrets server* like Azure KeyVault.</span></span>

<span data-ttu-id="ef40c-122">Ardından, sisteme erişimi denetleyen yetkilendirme hizmetini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef40c-122">Next add the Authorization service, which controls access to the system.</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="ef40c-123">Kimlik doğrulama ve yetkilendirme iki ayrı adımdan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-123">Authentication and Authorization are two separate steps.</span></span> <span data-ttu-id="ef40c-124">Kimlik doğrulaması, kullanıcının kimliğini belirlemede kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-124">Authentication is used to determine the user's identity.</span></span> <span data-ttu-id="ef40c-125">Yetkilendirme, kullanıcının sistemin çeşitli bölümlerine erişmesine izin verilip verilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ef40c-125">Authorization decides whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="ef40c-126">Şimdi kimlik doğrulama ve yetkilendirme ara yazılımını `Configure` yönteminde ASP.NET Core işlem hattına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef40c-126">Now add the Authentication and Authorization middleware to the ASP.NET Core pipeline in the `Configure` method.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="ef40c-127">Son olarak, `[Authorize]` özniteliğini güvenli hale getirilmesi için herhangi bir hizmete veya yönteme uygulayın ve izinleri doğrulamak için temel alınan `HttpContext` `User` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef40c-127">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="providing-call-credentials-in-the-client-application"></a><span data-ttu-id="ef40c-128">İstemci uygulamasında çağrı kimlik bilgileri sağlama</span><span class="sxs-lookup"><span data-stu-id="ef40c-128">Providing call credentials in the client application</span></span>

<span data-ttu-id="ef40c-129">Bir kimlik sunucusundan JWT belirteci aldıktan sonra, bunu, çağrı üzerine bir meta veri üst bilgisi olarak ekleyerek istemciden gRPC çağrılarının kimliğini doğrulamak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef40c-129">Once you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="ef40c-130">Şimdi, çağrı kimlik bilgileri olarak JWT taşıyıcı belirteçlerini kullanarak gRPC hizmetinizi güvenli hale getirdi.</span><span class="sxs-lookup"><span data-stu-id="ef40c-130">Now, you've secured your gRPC service using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="ef40c-131">, [Kimlik doğrulaması ve yetkilendirme eklenmiş bir portföyleri örnek gRPC uygulamasının](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) sürümü GitHub ' dır.</span><span class="sxs-lookup"><span data-stu-id="ef40c-131">A version of the [Portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ef40c-132">[Önceki](security.md)
>[İleri](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="ef40c-132">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
