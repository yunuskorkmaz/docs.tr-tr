---
title: Arama kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC çağrı kimlik bilgilerini uygulama ve kullanma.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f29d69ec37fe60bcd7ca01391001ea9eb71e7e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846684"
---
# <a name="call-credentials"></a>Çağrı kimlik bilgileri

Çağrı kimlik bilgileri her istekle birlikte meta verilerde geçirilen bazı belirteç türlerini temel alır.

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core, [WSFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet PAKETINI kullanarak WS-Federation ' i destekler. WS-Federation, Windows kimlik doğrulaması için HTTP/2 üzerinde desteklenmeyen en yakın seçenektir. Kullanıcılar, ASP.NET Core kimlik doğrulaması için kullanılabilecek bir belirteç sağlayan Active Directory Federasyon Hizmetleri (AD FS) (ADFS) kullanılarak doğrulanır.

Bu kimlik doğrulama yöntemiyle çalışmaya başlama hakkında daha fazla bilgi için [ASP.NET Core 'de WS-Federation ile kullanıcıların kimliğini doğrulama](https://docs.microsoft.com/aspnet/core/security/authentication/ws-federation?view=aspnetcore-3.0) makalesine bakın.

## <a name="jwt-bearer-tokens"></a>JWT taşıyıcı belirteçleri

[JSON Web Token](https://jwt.io) standardı, kodlanmış bir dizedeki bir Kullanıcı ve talepleri hakkında bilgi kodlamak ve bu belirteci, tüketicinin ortak anahtar şifrelemesini kullanarak belirtecin bütünlüğünü doğrulayabilmeleri için bir yol sağlar. Kullanıcıların kimliğini doğrulamak ve gRPC ve HTTP API 'Leri ile kullanılacak OpenID Connect (OıDC) belirteçlerini oluşturmak için ıdentityserver4 gibi çeşitli hizmetleri kullanabilirsiniz.

ASP.NET Core 3,0, JWT taşıyıcı paketini kullanarak JSON Web belirteçlerini işleyebilir. Yapılandırma, ASP.NET Core MVC uygulaması olarak bir gRPC uygulaması için tam olarak aynıdır.

Bu bölüm, WS-Federation ' den daha kolay geliştirme yaparken JWT taşıyıcı belirteçlerine odaklanacaktır.

## <a name="adding-authentication-and-authorization-to-the-server"></a>Sunucuya kimlik doğrulaması ve yetkilendirme ekleme

JWT taşıyıcı paketi, varsayılan olarak ASP.NET Core 3,0 ' ye dahil değildir. Uygulamanıza [Microsoft. AspNetCore. Authentication. Jwttaşıyıcı](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet paketini yükler.

Başlangıç sınıfına kimlik doğrulama hizmetini ekleyin ve JWT taşıyıcı işleyicisini yapılandırın.

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

`IssuerSigningKey` özelliği, imzalanmış belirteçleri doğrulamak için gereken şifreleme verileriyle `Microsoft.IdentityModels.Tokens.SecurityKey` uygulanmasını gerektirir. Bu belirtecin Azure Keykasası gibi bir *gizli dizi sunucusunda* güvenli bir şekilde depolanması gerekir.

Ardından, sisteme erişimi denetleyen yetkilendirme hizmetini ekleyin.

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
> Kimlik doğrulama ve yetkilendirme iki ayrı adımdan farklıdır. Kimlik doğrulaması, kullanıcının kimliğini belirlemede kullanılır. Yetkilendirme, kullanıcının sistemin çeşitli bölümlerine erişmesine izin verilip verilmeyeceğini belirler.

Şimdi kimlik doğrulama ve yetkilendirme ara yazılımını `Configure` yönteminde ASP.NET Core işlem hattına ekleyin.

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

Son olarak, `[Authorize]` özniteliğini güvenli hale getirilmesi için herhangi bir hizmete veya yönteme uygulayın ve izinleri doğrulamak için temel alınan `HttpContext` `User` özelliğini kullanın.

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

## <a name="providing-call-credentials-in-the-client-application"></a>İstemci uygulamasında çağrı kimlik bilgileri sağlama

Bir kimlik sunucusundan JWT belirteci aldıktan sonra, bunu, çağrı üzerine bir meta veri üst bilgisi olarak ekleyerek istemciden gRPC çağrılarının kimliğini doğrulamak için kullanabilirsiniz:

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

Şimdi, çağrı kimlik bilgileri olarak JWT taşıyıcı belirteçlerini kullanarak gRPC hizmetinizi güvenli hale getirdi. , [Kimlik doğrulaması ve yetkilendirme eklenmiş bir portföyleri örnek gRPC uygulamasının](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) sürümü GitHub ' dır.

>[!div class="step-by-step"]
>[Önceki](security.md)
>[İleri](channel-credentials.md)
