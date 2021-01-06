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
# <a name="channel-credentials"></a><span data-ttu-id="b98c9-103">Kanal kimlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="b98c9-103">Channel credentials</span></span>

<span data-ttu-id="b98c9-104">Adından da anlaşılacağı gibi kanal kimlik bilgileri, temeldeki gRPC kanalına eklenir.</span><span class="sxs-lookup"><span data-stu-id="b98c9-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="b98c9-105">Kanal kimlik bilgilerinin standart biçimi istemci sertifikası kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b98c9-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="b98c9-106">Bu işlemde, istemci bağlantı yaparken bir TLS sertifikası sağlar ve sonra herhangi bir çağrının yapılmasına izin vermeden önce sunucu bu sertifikayı doğrular.</span><span class="sxs-lookup"><span data-stu-id="b98c9-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this certificate before allowing any calls to be made.</span></span>

<span data-ttu-id="b98c9-107">Bir gRPC hizmeti için kapsamlı güvenlik sağlamak amacıyla kanal kimlik bilgilerini çağrı kimlik bilgileriyle birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98c9-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="b98c9-108">Kanal kimlik bilgileri, istemci uygulamanın hizmete erişmesine izin verildiğini kanıtlayın ve çağrı kimlik bilgileri, istemci uygulamasını kullanan kişi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b98c9-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="b98c9-109">İstemci sertifikası kimlik doğrulaması, gRPC için ASP.NET Core çalıştığı şekilde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="b98c9-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="b98c9-110">Daha fazla bilgi için bkz. [ASP.NET Core sertifika kimlik doğrulamasını yapılandırma](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="b98c9-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="b98c9-111">Geliştirme amacıyla kendinden imzalı bir sertifika kullanabilirsiniz, ancak üretim için güvenilen bir yetkili tarafından imzalanmış uygun bir HTTPS sertifikası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b98c9-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="b98c9-112">Sunucuya sertifika kimlik doğrulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="b98c9-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="b98c9-113">Sertifika kimlik doğrulamasını hem ana bilgisayar düzeyinde (örneğin, Kestrel sunucusu) hem de ASP.NET Core ardışık düzeninde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b98c9-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="b98c9-114">Kestrel 'de sertifika doğrulamasını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b98c9-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="b98c9-115">Kestrel (ASP.NET Core HTTP sunucusu) bir istemci sertifikası gerektirecek şekilde yapılandırabilir ve isteğe bağlı olarak, gelen bağlantıları kabul etmeden önce sağlanan sertifika için bazı doğrulama işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98c9-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="b98c9-116">Bu yapılandırmayı `CreateWebHostBuilder` `Program` sınıfında değil, sınıfının yönteminde belirtirsiniz `Startup` .</span><span class="sxs-lookup"><span data-stu-id="b98c9-116">You specify this configuration in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="b98c9-117">`ClientCertificateMode.RequireCertificate`Ayar, Kestrel istemci sertifikası sağlamayan tüm bağlantı isteklerini hemen reddetmesine neden olur, ancak bu ayar kendisi tarafından belirtilen bir sertifikayı doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="b98c9-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="b98c9-118">ASP.NET Core işlem `ClientCertificateValidation` hattının bağlantısı yapılmadan önce, bağlantının yapıldığı noktada istemci sertifikasını doğrulamak Için Kestrel özelliğini etkinleştirmek üzere geri çağırma işlemini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b98c9-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="b98c9-119">(Bu durumda, geri arama, sunucu sertifikasıyla aynı *sertifika yetkilisi* tarafından verilmiş olmasını sağlar.)</span><span class="sxs-lookup"><span data-stu-id="b98c9-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="b98c9-120">ASP.NET Core sertifikası kimlik doğrulaması ekle</span><span class="sxs-lookup"><span data-stu-id="b98c9-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="b98c9-121">[Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet paketi sertifika kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="b98c9-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="b98c9-122">Yöntemine sertifika kimlik doğrulama hizmetini ekleyin `ConfigureServices` ve yöntemdeki ASP.NET Core işlem hattına kimlik doğrulaması ve yetkilendirme ekleyin `Configure` .</span><span class="sxs-lookup"><span data-stu-id="b98c9-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="b98c9-123">İstemci uygulamasında kanal kimlik bilgilerini sağlama</span><span class="sxs-lookup"><span data-stu-id="b98c9-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="b98c9-124">`Grpc.Net.Client`Paketiyle, <xref:System.Net.Http.HttpClient> bağlantı için kullanılan bir örnekteki sertifikaları yapılandırırsınız `GrpcChannel` .</span><span class="sxs-lookup"><span data-stu-id="b98c9-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="b98c9-125">ChannelCredentials ve CallCredentials 'ı birleştirme</span><span class="sxs-lookup"><span data-stu-id="b98c9-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="b98c9-126">Sunucunuzu hem sertifika hem de belirteç kimlik doğrulamasını kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98c9-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="b98c9-127">Bunu yapmak için, sertifika değişikliklerini Kestrel sunucusuna uygulayın ve ASP.NET Core ' de JWT taşıyıcı ara yazılımını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b98c9-127">To do this, apply the certificate changes to the Kestrel server, and use the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="b98c9-128">Hem hem de `ChannelCredentials` istemcisini sağlamak için `CallCredentials` , `ChannelCredentials.Create` yöntemini kullanarak çağrı kimlik bilgilerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b98c9-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="b98c9-129">Yine de örneği kullanarak sertifika kimlik doğrulaması uygulamanız gerekir <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="b98c9-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="b98c9-130">Herhangi bir bağımsız değişkeni `SslCredentials` oluşturucuya geçirirseniz, iç istemci kodu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b98c9-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="b98c9-131">`SslCredentials`Parametresi, `Grpc.Net.Client` `Create` paketiyle uyumluluğu sürdürmek için yalnızca paketin yöntemine dahil edilmiştir `Grpc.Core` .</span><span class="sxs-lookup"><span data-stu-id="b98c9-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="b98c9-132">`ChannelCredentials.Create`Sertifika kimlik doğrulaması olmadan bir istemci için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b98c9-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="b98c9-133">Bu, kanalda yapılan her çağrıya belirteç kimlik bilgilerini geçirmek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b98c9-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="b98c9-134">[FullStockTicker örnek gRPC uygulamasının sertifika kimlik doğrulaması eklenmiş](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) bir sürümü GitHub üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b98c9-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b98c9-135">[Önceki](call-credentials.md) 
> [Sonraki](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="b98c9-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
