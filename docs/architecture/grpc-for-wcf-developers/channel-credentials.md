---
title: Kanal kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC kanal kimlik bilgilerini uygulama ve kullanma.
ms.date: 12/15/2020
ms.openlocfilehash: 3663bbf061156db957241e2a32dbb9c64562ade2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938643"
---
# <a name="channel-credentials"></a>Kanal kimlik bilgileri

Adından da anlaşılacağı gibi kanal kimlik bilgileri, temeldeki gRPC kanalına eklenir. Kanal kimlik bilgilerinin standart biçimi istemci sertifikası kimlik doğrulamasını kullanır. Bu işlemde, istemci bağlantı yaparken bir TLS sertifikası sağlar ve sonra herhangi bir çağrının yapılmasına izin vermeden önce sunucu bu sertifikayı doğrular.

Bir gRPC hizmeti için kapsamlı güvenlik sağlamak amacıyla kanal kimlik bilgilerini çağrı kimlik bilgileriyle birleştirebilirsiniz. Kanal kimlik bilgileri, istemci uygulamanın hizmete erişmesine izin verildiğini kanıtlayın ve çağrı kimlik bilgileri, istemci uygulamasını kullanan kişi hakkında bilgi sağlar.

İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core çalıştığı şekilde çalışacaktır. Daha fazla bilgi için bkz. [ASP.NET Core sertifika kimlik doğrulamasını yapılandırma](/aspnet/core/security/authentication/certauth).

Geliştirme amacıyla kendinden imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilen bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.

## <a name="add-certificate-authentication-to-the-server"></a>Sunucuya sertifika kimlik doğrulaması ekleme

Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusu) hem de ASP.NET Core ardışık düzeninde yapılandırın.

### <a name="configure-certificate-validation-on-kestrel"></a>Kestrel 'de sertifika doğrulamasını yapılandırma

Kestrel (ASP.NET Core HTTP sunucusu) bir istemci sertifikası gerektirecek şekilde yapılandırabilir ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce sağlanan sertifika için bazı doğrulama işlemleri gerçekleştirebilirsiniz. Bu yapılandırmayı `CreateWebHostBuilder` `Program` sınıfında değil, sınıfının yönteminde belirtirsiniz `Startup` .

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

`ClientCertificateMode.RequireCertificate`Ayar, Kestrel istemci sertifikası sağlamayan tüm bağlantı isteklerini hemen reddetmesine neden olur, ancak bu ayar kendisi tarafından belirtilen bir sertifikayı doğrulamaz. ASP.NET Core işlem `ClientCertificateValidation` hattının bağlantısı yapılmadan önce, bağlantının yapıldığı noktada istemci sertifikasını doğrulamak Için Kestrel özelliğini etkinleştirmek üzere geri çağırma işlemini ekleyin. (Bu durumda, geri arama, sunucu sertifikasıyla aynı *sertifika yetkilisi* tarafından verilmiş olmasını sağlar.)

### <a name="add-aspnet-core-certificate-authentication"></a>ASP.NET Core sertifikası kimlik doğrulaması ekle

[Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi sertifika kimlik doğrulaması sağlar.

Yöntemine sertifika kimlik doğrulama hizmetini ekleyin `ConfigureServices` ve yöntemdeki ASP.NET Core işlem hattına kimlik doğrulaması ve yetkilendirme ekleyin `Configure` .

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

## <a name="provide-channel-credentials-in-the-client-application"></a>İstemci uygulamasında kanal kimlik bilgilerini sağlama

`Grpc.Net.Client`Paketiyle, <xref:System.Net.Http.HttpClient> bağlantı için kullanılan bir örnekteki sertifikaları yapılandırırsınız `GrpcChannel` .

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

## <a name="combine-channelcredentials-and-callcredentials"></a>ChannelCredentials ve CallCredentials 'ı birleştirme

Sunucunuzu hem sertifika hem de belirteç kimlik doğrulamasını kullanacak şekilde yapılandırabilirsiniz. Bunu yapmak için, sertifika değişikliklerini Kestrel sunucusuna uygulayın ve ASP.NET Core ' de JWT taşıyıcı ara yazılımını kullanın.

Hem hem de `ChannelCredentials` istemcisini sağlamak için `CallCredentials` , `ChannelCredentials.Create` yöntemini kullanarak çağrı kimlik bilgilerini uygulayın. Yine de örneği kullanarak sertifika kimlik doğrulaması uygulamanız gerekir <xref:System.Net.Http.HttpClient> . Herhangi bir bağımsız değişkeni `SslCredentials` oluşturucuya geçirirseniz, iç istemci kodu bir özel durum oluşturur. `SslCredentials`Parametresi, `Grpc.Net.Client` `Create` paketiyle uyumluluğu sürdürmek için yalnızca paketin yöntemine dahil edilmiştir `Grpc.Core` .

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
> `ChannelCredentials.Create`Sertifika kimlik doğrulaması olmadan bir istemci için yöntemini kullanabilirsiniz. Bu, kanalda yapılan her çağrıya belirteç kimlik bilgilerini geçirmek için kullanışlı bir yoldur.

[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub üzerinde.

>[!div class="step-by-step"]
>[Önceki](call-credentials.md) 
> [Sonraki](encryption.md)
