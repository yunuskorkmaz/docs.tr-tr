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
# <a name="channel-credentials"></a><span data-ttu-id="0152e-103">Kanal kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="0152e-103">Channel credentials</span></span>

<span data-ttu-id="0152e-104">Adından da anlaşılacağı gibi, kanal kimlik bilgileri altta yatan gRPC kanalına eklenir.</span><span class="sxs-lookup"><span data-stu-id="0152e-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="0152e-105">Kanal kimlik bilgilerinin standart formu istemci sertifikası kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0152e-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="0152e-106">Bu işlemde, istemci bağlantıyı yaparken bir TLS sertifikası sağlar ve sunucu herhangi bir arama yapılmasını izin vermeden önce bunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="0152e-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="0152e-107">GRPC hizmeti için kapsamlı güvenlik sağlamak için kanal kimlik bilgilerini arama kimlik bilgileriyle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0152e-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="0152e-108">Kanal kimlik bilgileri, istemci uygulamasının hizmete erişmesine izin verildiğini ve arama kimlik bilgilerinin istemci uygulamasını kullanan kişi hakkında bilgi sağladığını kanıtlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0152e-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="0152e-109">İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core için çalıştığı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="0152e-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="0152e-110">Daha fazla bilgi için ASP.NET [Core'da sertifika kimlik doğrulamasını yapılandır'a](/aspnet/core/security/authentication/certauth)bakın.</span><span class="sxs-lookup"><span data-stu-id="0152e-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="0152e-111">Geliştirme amacıyla kendi imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilir bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0152e-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="0152e-112">Sunucuya sertifika kimlik doğrulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="0152e-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="0152e-113">Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusunda) hem de ASP.NET Çekirdek ardışık alanında yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0152e-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="0152e-114">Kerkenez'de sertifika doğrulaması yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0152e-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="0152e-115">Kestrel'i (ASP.NET Core HTTP sunucusu) istemci sertifikası gerektirecek şekilde ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce verilen sertifikanın bazı doğrulamalarını gerçekleştirecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0152e-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="0152e-116">Bunu `CreateWebHostBuilder` `Program` sınıf yönteminde değil, 'de `Startup`yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="0152e-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="0152e-117">Ayar, `ClientCertificateMode.RequireCertificate` Kestrel'in istemci sertifikası sağlamayan herhangi bir bağlantı isteğini hemen reddetmesine neden olur, ancak bu ayar tek başına sağlanan bir sertifikayı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="0152e-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="0152e-118">ASP.NET `ClientCertificateValidation` Core ardışık ASP.NET önce, bağlantının yapıldığı noktada, Kestrel'in istemci sertifikasını doğrulayabilmesini sağlamak için geri aramayı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0152e-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="0152e-119">(Bu durumda, geri arama, sunucu sertifikasıyla aynı *Sertifika Yetkilisi* tarafından verilmiş olmasını sağlar.)</span><span class="sxs-lookup"><span data-stu-id="0152e-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="0152e-120">Core sertifika kimlik doğrulamaASP.NET ekleme</span><span class="sxs-lookup"><span data-stu-id="0152e-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="0152e-121">[Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi sertifika kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="0152e-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="0152e-122">`ConfigureServices` Yönteme sertifika kimlik doğrulama hizmetini ekleyin ve `Configure` yöntemdeki ASP.NET Çekirdek ardışık anlama sına kimlik doğrulama ve yetkilendirme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0152e-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="0152e-123">İstemci uygulamasında kanal kimlik bilgilerini sağlama</span><span class="sxs-lookup"><span data-stu-id="0152e-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="0152e-124">Paketle, `Grpc.Net.Client` sertifikaları bağlantı için <xref:System.Net.Http.HttpClient> `GrpcChannel` kullanılana sağlanan bir örnekte yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0152e-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="0152e-125">Kanal Kimlik Bilgilerini ve Çağrı Kimlik Bilgilerini Birleştir</span><span class="sxs-lookup"><span data-stu-id="0152e-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="0152e-126">Sunucunuzu hem sertifika hem de belirteç kimlik doğrulaması kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0152e-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="0152e-127">Bunu, sertifika değişikliklerini Kestrel sunucusuna uygulayarak ve ASP.NET Core'da JWT taşıyıcı aracını kullanarak yapın.</span><span class="sxs-lookup"><span data-stu-id="0152e-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="0152e-128">Hem de `ChannelCredentials` `CallCredentials` istemci üzerinde sağlamak `ChannelCredentials.Create` için, arama kimlik bilgilerini uygulamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0152e-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="0152e-129">Yine de örneği kullanarak sertifika kimlik <xref:System.Net.Http.HttpClient> doğrulaması uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0152e-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="0152e-130">Herhangi bir bağımsız değişkeni `SslCredentials` oluşturucuya geçirirseniz, iç istemci kodu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0152e-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="0152e-131">`SslCredentials` Parametre yalnızca paketle uyumluluğu korumak `Create` için `Grpc.Net.Client` paketin yöntemine `Grpc.Core` dahildir.</span><span class="sxs-lookup"><span data-stu-id="0152e-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="0152e-132">Bu `ChannelCredentials.Create` yöntemi, sertifika kimlik doğrulaması olmayan bir istemci için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0152e-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="0152e-133">Bu, kanalda yapılan her aramada belirteç kimlik bilgilerini geçirmenin yararlı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="0152e-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="0152e-134">[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub'dadır.</span><span class="sxs-lookup"><span data-stu-id="0152e-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0152e-135">[Önceki](call-credentials.md)
>[Sonraki](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="0152e-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
