---
title: Kanal kimlik bilgileri-WCF geliştiricileri için gRPC
description: ASP.NET Core 3,0 ' de gRPC kanal kimlik bilgilerini uygulama ve kullanma.
ms.date: 09/02/2019
ms.openlocfilehash: 133de2c732e72844f249f11bfe22b5980b828b89
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711499"
---
# <a name="channel-credentials"></a>Kanal kimlik bilgileri

Adından da anlaşılacağı gibi kanal kimlik bilgileri, temeldeki gRPC kanalına eklenir. Kanal kimlik bilgilerinin standart biçimi istemci sertifikası kimlik doğrulamasını kullanır. Bu işlemde, istemci bağlantı yaparken bir TLS sertifikası sağlar ve sonra herhangi bir çağrının yapılmasına izin vermeden önce sunucu bunu doğrular.

Bir gRPC hizmeti için kapsamlı güvenlik sağlamak amacıyla kanal kimlik bilgilerini çağrı kimlik bilgileriyle birleştirebilirsiniz. Kanal kimlik bilgileri, istemci uygulamanın hizmete erişmesine izin verildiğini kanıtlayın ve çağrı kimlik bilgileri, istemci uygulamasını kullanan kişi hakkında bilgi sağlar.

İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core çalıştığı şekilde çalışacaktır. Daha fazla bilgi için bkz. [ASP.NET Core sertifika kimlik doğrulamasını yapılandırma](/aspnet/core/security/authentication/certauth).

Geliştirme amacıyla kendinden imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilen bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.

## <a name="add-certificate-authentication-to-the-server"></a>Sunucuya sertifika kimlik doğrulaması ekleme

Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusu) hem de ASP.NET Core ardışık düzeninde yapılandırın.

### <a name="configure-certificate-validation-on-kestrel"></a>Kestrel 'de sertifika doğrulamasını yapılandırma

Kestrel (ASP.NET Core HTTP sunucusu) bir istemci sertifikası gerektirecek şekilde yapılandırabilir ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce sağlanan sertifika için bazı doğrulama işlemleri gerçekleştirebilirsiniz. Bunu, `Startup`yerine `Program` sınıfının `CreateWebHostBuilder` yönteminde yapabilirsiniz.

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

`ClientCertificateMode.RequireCertificate` ayarı, Kestrel istemci sertifikası sağlamayan tüm bağlantı isteklerini hemen reddetmesine neden olur, ancak bu ayar kendisi tarafından belirtilen bir sertifikayı doğrulamaz. ASP.NET Core işlem hattının bağlantısı yapılmadan önce, bağlantının yapıldığı noktada istemci sertifikasını doğrulamak için Kestrel 'i etkinleştirmek üzere `ClientCertificateValidation` geri çağırması ekleyin. (Bu durumda, geri arama, sunucu sertifikasıyla aynı *sertifika yetkilisi* tarafından verilmiş olmasını sağlar.) 

### <a name="add-aspnet-core-certificate-authentication"></a>ASP.NET Core sertifikası kimlik doğrulaması ekle

[Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi sertifika kimlik doğrulaması sağlar.

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

## <a name="provide-channel-credentials-in-the-client-application"></a>İstemci uygulamasında kanal kimlik bilgilerini sağlama

`Grpc.Net.Client` paketiyle, bağlantı için kullanılan `GrpcChannel` için sunulan <xref:System.Net.Http.HttpClient> bir örnek üzerindeki sertifikaları yapılandırırsınız.

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

Sunucunuzu hem sertifika hem de belirteç kimlik doğrulamasını kullanacak şekilde yapılandırabilirsiniz. Sertifika değişikliklerini Kestrel sunucusuna uygulayarak ve ASP.NET Core ' de JWT taşıyıcı ara yazılımını kullanarak bunu yapın.

İstemcide hem `ChannelCredentials` hem de `CallCredentials` sağlamak için, çağrı kimlik bilgilerini uygulamak üzere `ChannelCredentials.Create` metodunu kullanın. Hala <xref:System.Net.Http.HttpClient> örneğini kullanarak sertifika kimlik doğrulaması uygulamanız gerekir. `SslCredentials` oluşturucusuna herhangi bir bağımsız değişken geçirirseniz, iç istemci kodu bir özel durum oluşturur. `SslCredentials` parametresi, `Grpc.Core` paketiyle uyumluluğu sürdürmek için yalnızca `Grpc.Net.Client` paketinin `Create` yöntemine dahil edilmiştir.

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
> Sertifika kimlik doğrulaması olmadan istemci için `ChannelCredentials.Create` yöntemini kullanabilirsiniz. Bu, kanalda yapılan her çağrıya belirteç kimlik bilgilerini geçirmek için kullanışlı bir yoldur.

[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub üzerinde.

>[!div class="step-by-step"]
>[Önceki](call-credentials.md)
>[İleri](encryption.md)
