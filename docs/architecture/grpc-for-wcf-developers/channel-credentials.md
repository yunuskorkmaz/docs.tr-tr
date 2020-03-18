---
title: Kanal kimlik bilgileri - WCF Geliştiricileri için gRPC
description: Core 3.0'da gRPC kanal kimlik bilgilerinin nasıl uygulanacağı ve kullanılacağı ASP.NET.
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148211"
---
# <a name="channel-credentials"></a>Kanal kimlik bilgileri

Adından da anlaşılacağı gibi, kanal kimlik bilgileri altta yatan gRPC kanalına eklenir. Kanal kimlik bilgilerinin standart formu istemci sertifikası kimlik doğrulamasını kullanır. Bu işlemde, istemci bağlantıyı yaparken bir TLS sertifikası sağlar ve sunucu herhangi bir arama yapılmasını izin vermeden önce bunu doğrular.

GRPC hizmeti için kapsamlı güvenlik sağlamak için kanal kimlik bilgilerini arama kimlik bilgileriyle birleştirebilirsiniz. Kanal kimlik bilgileri, istemci uygulamasının hizmete erişmesine izin verildiğini ve arama kimlik bilgilerinin istemci uygulamasını kullanan kişi hakkında bilgi sağladığını kanıtlamaktadır.

İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core için çalıştığı şekilde çalışır. Daha fazla bilgi için ASP.NET [Core'da sertifika kimlik doğrulamasını yapılandır'a](/aspnet/core/security/authentication/certauth)bakın.

Geliştirme amacıyla kendi imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilir bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.

## <a name="add-certificate-authentication-to-the-server"></a>Sunucuya sertifika kimlik doğrulaması ekleme

Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusunda) hem de ASP.NET Çekirdek ardışık alanında yapılandırın.

### <a name="configure-certificate-validation-on-kestrel"></a>Kerkenez'de sertifika doğrulaması yapılandırma

Kestrel'i (ASP.NET Core HTTP sunucusu) istemci sertifikası gerektirecek şekilde ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce verilen sertifikanın bazı doğrulamalarını gerçekleştirecek şekilde yapılandırabilirsiniz. Bunu `CreateWebHostBuilder` `Program` sınıf yönteminde değil, 'de `Startup`yaparsınız.

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

Ayar, `ClientCertificateMode.RequireCertificate` Kestrel'in istemci sertifikası sağlamayan herhangi bir bağlantı isteğini hemen reddetmesine neden olur, ancak bu ayar tek başına sağlanan bir sertifikayı doğrulamaz. ASP.NET `ClientCertificateValidation` Core ardışık ASP.NET önce, bağlantının yapıldığı noktada, Kestrel'in istemci sertifikasını doğrulayabilmesini sağlamak için geri aramayı ekleyin. (Bu durumda, geri arama, sunucu sertifikasıyla aynı *Sertifika Yetkilisi* tarafından verilmiş olmasını sağlar.)

### <a name="add-aspnet-core-certificate-authentication"></a>Core sertifika kimlik doğrulamaASP.NET ekleme

[Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi sertifika kimlik doğrulaması sağlar.

`ConfigureServices` Yönteme sertifika kimlik doğrulama hizmetini ekleyin ve `Configure` yöntemdeki ASP.NET Çekirdek ardışık anlama sına kimlik doğrulama ve yetkilendirme ekleyin.

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

Paketle, `Grpc.Net.Client` sertifikaları bağlantı için <xref:System.Net.Http.HttpClient> `GrpcChannel` kullanılana sağlanan bir örnekte yapılandırabilirsiniz.

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

## <a name="combine-channelcredentials-and-callcredentials"></a>Kanal Kimlik Bilgilerini ve Çağrı Kimlik Bilgilerini Birleştir

Sunucunuzu hem sertifika hem de belirteç kimlik doğrulaması kullanacak şekilde yapılandırabilirsiniz. Bunu, sertifika değişikliklerini Kestrel sunucusuna uygulayarak ve ASP.NET Core'da JWT taşıyıcı aracını kullanarak yapın.

Hem de `ChannelCredentials` `CallCredentials` istemci üzerinde sağlamak `ChannelCredentials.Create` için, arama kimlik bilgilerini uygulamak için yöntemi kullanın. Yine de örneği kullanarak sertifika kimlik <xref:System.Net.Http.HttpClient> doğrulaması uygulamanız gerekir. Herhangi bir bağımsız değişkeni `SslCredentials` oluşturucuya geçirirseniz, iç istemci kodu bir özel durum oluşturur. `SslCredentials` Parametre yalnızca paketle uyumluluğu korumak `Create` için `Grpc.Net.Client` paketin yöntemine `Grpc.Core` dahildir.

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
> Bu `ChannelCredentials.Create` yöntemi, sertifika kimlik doğrulaması olmayan bir istemci için kullanabilirsiniz. Bu, kanalda yapılan her aramada belirteç kimlik bilgilerini geçirmenin yararlı bir yoludur.

[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub'dadır.

>[!div class="step-by-step"]
>[Önceki](call-credentials.md)
>[Sonraki](encryption.md)
