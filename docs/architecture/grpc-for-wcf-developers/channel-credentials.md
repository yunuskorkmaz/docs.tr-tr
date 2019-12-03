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
# <a name="channel-credentials"></a><span data-ttu-id="106a0-103">Kanal kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="106a0-103">Channel credentials</span></span>

<span data-ttu-id="106a0-104">Adından da anlaşılacağı gibi kanal kimlik bilgileri, temeldeki gRPC kanalına eklenir.</span><span class="sxs-lookup"><span data-stu-id="106a0-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="106a0-105">Kanal kimlik bilgilerinin standart biçimi istemci sertifikası kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="106a0-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="106a0-106">Bu işlemde, istemci bağlantı yaparken bir TLS sertifikası sağlar ve sonra herhangi bir çağrının yapılmasına izin vermeden önce sunucu bunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="106a0-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="106a0-107">Bir gRPC hizmeti için kapsamlı güvenlik sağlamak amacıyla kanal kimlik bilgilerini çağrı kimlik bilgileriyle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="106a0-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="106a0-108">Kanal kimlik bilgileri, istemci uygulamanın hizmete erişmesine izin verildiğini kanıtlayın ve çağrı kimlik bilgileri, istemci uygulamasını kullanan kişi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="106a0-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="106a0-109">İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core çalıştığı şekilde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="106a0-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="106a0-110">Daha fazla bilgi için bkz. [ASP.NET Core sertifika kimlik doğrulamasını yapılandırma](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="106a0-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="106a0-111">Geliştirme amacıyla kendinden imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilen bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="106a0-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="106a0-112">Sunucuya sertifika kimlik doğrulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="106a0-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="106a0-113">Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusu) hem de ASP.NET Core ardışık düzeninde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="106a0-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="106a0-114">Kestrel 'de sertifika doğrulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="106a0-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="106a0-115">Kestrel (ASP.NET Core HTTP sunucusu) bir istemci sertifikası gerektirecek şekilde yapılandırabilir ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce sağlanan sertifika için bazı doğrulama işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="106a0-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="106a0-116">Bunu, `Startup`yerine `Program` sınıfının `CreateWebHostBuilder` yönteminde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="106a0-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="106a0-117">`ClientCertificateMode.RequireCertificate` ayarı, Kestrel istemci sertifikası sağlamayan tüm bağlantı isteklerini hemen reddetmesine neden olur, ancak bu ayar kendisi tarafından belirtilen bir sertifikayı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="106a0-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="106a0-118">ASP.NET Core işlem hattının bağlantısı yapılmadan önce, bağlantının yapıldığı noktada istemci sertifikasını doğrulamak için Kestrel 'i etkinleştirmek üzere `ClientCertificateValidation` geri çağırması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="106a0-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="106a0-119">(Bu durumda, geri arama, sunucu sertifikasıyla aynı *sertifika yetkilisi* tarafından verilmiş olmasını sağlar.)</span><span class="sxs-lookup"><span data-stu-id="106a0-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span> 

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="106a0-120">ASP.NET Core sertifikası kimlik doğrulaması ekle</span><span class="sxs-lookup"><span data-stu-id="106a0-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="106a0-121">[Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi sertifika kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="106a0-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="106a0-122">`ConfigureServices` yöntemine sertifika kimlik doğrulama hizmetini ekleyin ve `Configure` yönteminde ASP.NET Core işlem hattına kimlik doğrulaması ve yetkilendirme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="106a0-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="106a0-123">İstemci uygulamasında kanal kimlik bilgilerini sağlama</span><span class="sxs-lookup"><span data-stu-id="106a0-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="106a0-124">`Grpc.Net.Client` paketiyle, bağlantı için kullanılan `GrpcChannel` için sunulan <xref:System.Net.Http.HttpClient> bir örnek üzerindeki sertifikaları yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="106a0-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="106a0-125">ChannelCredentials ve CallCredentials 'ı birleştirme</span><span class="sxs-lookup"><span data-stu-id="106a0-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="106a0-126">Sunucunuzu hem sertifika hem de belirteç kimlik doğrulamasını kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="106a0-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="106a0-127">Sertifika değişikliklerini Kestrel sunucusuna uygulayarak ve ASP.NET Core ' de JWT taşıyıcı ara yazılımını kullanarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="106a0-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="106a0-128">İstemcide hem `ChannelCredentials` hem de `CallCredentials` sağlamak için, çağrı kimlik bilgilerini uygulamak üzere `ChannelCredentials.Create` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="106a0-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="106a0-129">Hala <xref:System.Net.Http.HttpClient> örneğini kullanarak sertifika kimlik doğrulaması uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="106a0-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="106a0-130">`SslCredentials` oluşturucusuna herhangi bir bağımsız değişken geçirirseniz, iç istemci kodu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="106a0-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="106a0-131">`SslCredentials` parametresi, `Grpc.Core` paketiyle uyumluluğu sürdürmek için yalnızca `Grpc.Net.Client` paketinin `Create` yöntemine dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="106a0-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="106a0-132">Sertifika kimlik doğrulaması olmadan istemci için `ChannelCredentials.Create` yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="106a0-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="106a0-133">Bu, kanalda yapılan her çağrıya belirteç kimlik bilgilerini geçirmek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="106a0-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="106a0-134">[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="106a0-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="106a0-135">[Önceki](call-credentials.md)
>[İleri](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="106a0-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
