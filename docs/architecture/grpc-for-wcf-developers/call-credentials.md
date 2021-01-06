---
title: Arama kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC çağrı kimlik bilgilerini uygulama ve kullanma.
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938448"
---
# <a name="call-credentials"></a>Çağrı kimlik bilgileri

Çağrı kimlik bilgileri, her istekle birlikte meta verilerde geçirilen bir belirteci temel alır.

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core, [WSFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet paketini kullanarak WS-Federation destekler. WS-Federation, Windows kimlik doğrulaması için HTTP/2 üzerinde desteklenmeyen en yakın seçenektir. Kullanıcılar, ASP.NET Core kimlik doğrulaması için kullanılabilecek bir belirteç sağlayan Active Directory Federasyon Hizmetleri (AD FS) (AD FS) kullanılarak doğrulanır.

Bu kimlik doğrulama yöntemiyle çalışmaya başlama hakkında daha fazla bilgi için bkz. [ASP.NET Core WS-Federation kullanıcılara kimlik doğrulama](/aspnet/core/security/authentication/ws-federation).

## <a name="jwt-bearer-tokens"></a>JWT taşıyıcı belirteçleri

[JSON Web Token](https://jwt.io) (JWT) standardı, kodlanmış bir dizedeki bir Kullanıcı ve talepleri hakkında bilgi kodlamak için bir yol sağlar. Ayrıca, tüketicinin ortak anahtar şifrelemesi kullanarak belirtecin bütünlüğünü doğrulayabilmesi için bu belirteci imzalamak için bir yol sağlar. Kullanıcıların kimliğini doğrulamak ve gRPC ve HTTP API 'Leri ile kullanılacak OpenID Connect (OıDC) belirteçlerini oluşturmak için ıdentityserver4 gibi çeşitli hizmetleri kullanabilirsiniz.

5,0 ASP.NET Core, JWT taşıyıcı paketini kullanarak JWTs 'yi işleyebilir. Yapılandırma, ASP.NET Core MVC uygulaması için olduğu gibi bir gRPC uygulaması için tam olarak aynıdır. Burada, WS-Federation ' den daha kolay geliştirileceği için JWT taşıyıcı belirteçlerine odaklanacağız.

## <a name="add-authentication-and-authorization-to-the-server"></a>Sunucuya kimlik doğrulaması ve yetkilendirme ekleme

JWT taşıyıcı paketi, varsayılan olarak ASP.NET Core 5,0 ' ye dahil değildir. Uygulamanıza [Microsoft. AspNetCore. Authentication. Jwttaşıyıcı](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet paketini yükler.

Başlangıç sınıfına kimlik doğrulama hizmetini ekleyin ve JWT taşıyıcı işleyicisini yapılandırın:

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

`IssuerSigningKey`Özelliği, `Microsoft.IdentityModels.Tokens.SecurityKey` imzalı belirteçleri doğrulamak için gerekli olan şifreleme verileriyle bir uygulamasının uygulanmasını gerektirir. Bu belirteci, Azure Key Vault gibi bir *gizli dizi sunucusunda* güvenli bir şekilde depolayın.

Ardından, sisteme erişimi denetleyen yetkilendirme hizmetini ekleyin:

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
> Kimlik doğrulama ve yetkilendirme iki ayrı adımdan farklıdır. Kullanıcının kimliğini öğrenmek için kimlik doğrulaması kullanın. Kullanıcının sistemin çeşitli bölümlerine erişmesine izin verilip verilmeyeceğini belirlemek için Yetkilendirmeyi kullanırsınız.

Şimdi kimlik doğrulama ve yetkilendirme ara yazılımını yöntemdeki ASP.NET Core işlem hattına ekleyin `Configure` :

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

Son olarak, `[Authorize]` özniteliğini güvenli hale getirilmesi için herhangi bir hizmete veya yönteme uygulayın ve `User` izinleri doğrulamak için temel alınan özelliğini kullanın `HttpContext` .

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

## <a name="provide-call-credentials-in-the-client-application"></a>İstemci uygulamasında çağrı kimlik bilgilerini sağlayın

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

Artık gRPC hizmetinizi, JWT taşıyıcı belirteçlerini çağrı kimlik bilgileri olarak kullanarak güvenli hale getirdi. , [Kimlik doğrulaması ve yetkilendirme eklenmiş bir portföyleri örnek gRPC uygulamasının](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) sürümü GitHub ' dır.

>[!div class="step-by-step"]
>[Önceki](security.md) 
> [Sonraki](channel-credentials.md)
