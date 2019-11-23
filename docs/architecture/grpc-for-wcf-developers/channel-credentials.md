---
title: Kanal kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC kanal kimlik bilgilerini uygulama ve kullanma.
ms.date: 09/02/2019
ms.openlocfilehash: b424db49337a2dc6e3d0245d36349e3f408cdf6c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967958"
---
# <a name="channel-credentials"></a>Kanal kimlik bilgileri

Adından da anlaşılacağı gibi kanal kimlik bilgileri, temeldeki gRPC kanalına eklenir. Kanal kimlik bilgileri standart biçimi istemci sertifikası kimlik doğrulamasını kullanır, burada istemci, bağlantı kurulurken bir TLS sertifikası sağlar ve herhangi bir çağrının yapılmasına izin vermeden önce sunucu tarafından doğrulanır.

GRPC hizmeti için kapsamlı güvenlik sağlamak amacıyla kanal kimlik bilgileri, çağrı kimlik bilgileriyle birleştirilebilir. Kanal kimlik bilgileri, istemci uygulamanın hizmete erişmesine izin verildiğini kanıtlayın ve çağrı kimlik bilgileri, istemci uygulamasını kullanan kişi hakkında bilgi sağlar.

İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core çalıştığı şekilde çalışacaktır. Yapılandırma işlemi burada özetlenmiştir, ancak [ASP.NET Core 'de sertifika kimlik doğrulamasını yapılandırma](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0) makalesinde daha fazla bilgi bulunabilir.

Geliştirme amacıyla kendinden imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilen bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.

## <a name="adding-certificate-authentication-to-the-server"></a>Sunucuya sertifika kimlik doğrulaması ekleniyor

Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusu hem de ASP.NET Core işlem hattında yapılandırmanız gerekir.

### <a name="configuring-certificate-validation-on-kestrel"></a>Kestrel 'de sertifika doğrulamasını yapılandırma

Kestrel (ASP.NET Core HTTP sunucusu) bir istemci sertifikası gerektirecek şekilde yapılandırabilir ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce sağlanan sertifikanın bazı doğrulanmasını gerçekleştirebilir. Bu yapılandırma, `Startup`yerine `Program` sınıfının `CreateWebHostBuilder` yönteminde yapılır.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

`ClientCertificateMode.RequireCertificate` ayar, Kestrel istemci sertifikası sağlamayan tüm bağlantı isteklerini hemen reddetmesine neden olur, ancak sertifika doğrulanmaz. `ClientCertificateValidation` geri çağrısının eklenmesi, ASP.NET Core işlem hattının kullanılabilmesi için, Kestrel istemci sertifikasını (Bu durumda sunucu sertifikasıyla aynı *sertifika yetkilisi* tarafından verildiğini doğrulayarak) doğrulamasına olanak sağlar.

### <a name="adding-aspnet-core-certificate-authentication"></a>ASP.NET Core sertifikası kimlik doğrulaması ekleme

Sertifika kimlik doğrulaması [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi tarafından sağlanır.

`ConfigureServices` yöntemine sertifika kimlik doğrulama hizmetini ekleyin ve `Configure` yönteminde ASP.NET Core işlem hattına kimlik doğrulaması ve yetkilendirme ekleyin.

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="providing-channel-credentials-in-the-client-application"></a>İstemci uygulamasında kanal kimlik bilgilerini sağlama

`Grpc.Net.Client` paketiyle, sertifikalar, bağlantı için kullanılan `GrpcChannel` için sağlanmış bir <xref:System.Net.Http.HttpClient> örneğinde yapılandırılır.

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combining-channelcredentials-and-callcredentials"></a>ChannelCredentials ve CallCredentials birleştiriliyor

Kestrel sunucusuna sertifika değişiklikleri uygulayarak ve ASP.NET Core içindeki JWT taşıyıcı ara yazılımını kullanarak sunucunuzu hem sertifika hem de belirteç kimlik doğrulamasını kullanacak şekilde yapılandırabilirsiniz.

İstemcide hem ChannelCredentials hem de CallCredentials sağlamak için, çağrı kimlik bilgilerini uygulamak üzere `ChannelCredentials.Create` metodunu kullanın. Sertifika kimlik doğrulamasının hala <xref:System.Net.Http.HttpClient> örneği kullanılarak uygulanması gerekir: `SslCredentials` oluşturucusuna herhangi bir bağımsız değişken geçirirseniz, iç istemci kodu bir özel durum oluşturur. `SslCredentials` parametresi, `Grpc.Core` paketiyle uyumluluğu sürdürmek için yalnızca `Grpc.Net.Client` paketinin `Create` yöntemine dahil edilmiştir.

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> Kanalda yapılan her çağrıya belirteç kimlik bilgilerini geçirmek için kullanışlı bir yol olarak sertifika kimlik doğrulaması olmadan istemci için `ChannelCredentials.Create` yöntemini kullanabilirsiniz.

[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub üzerinde.

>[!div class="step-by-step"]
>[Önceki](call-credentials.md)
>[İleri](encryption.md)
