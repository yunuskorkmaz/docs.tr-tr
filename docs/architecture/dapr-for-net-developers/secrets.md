---
title: Davpr gizli dizi oluşturma bloğu
description: Gizli dizi oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: edwinvw
ms.date: 02/07/2021
ms.openlocfilehash: a1476abc6b224a525f6bb04c78209da5d1654e66
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629479"
---
# <a name="the-dapr-secrets-building-block"></a><span data-ttu-id="0f304-103">Davpr gizli dizi oluşturma bloğu</span><span class="sxs-lookup"><span data-stu-id="0f304-103">The Dapr secrets building block</span></span>

<span data-ttu-id="0f304-104">Kurumsal uygulamalar gizli dizileri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0f304-104">Enterprise applications require secrets.</span></span> <span data-ttu-id="0f304-105">Ortak örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0f304-105">Common examples include:</span></span>

- <span data-ttu-id="0f304-106">Kullanıcı adı ve parola içeren bir veritabanı bağlantı dizesi.</span><span class="sxs-lookup"><span data-stu-id="0f304-106">A database connection string that contains a username and password.</span></span>
- <span data-ttu-id="0f304-107">Dış Web API 'SI çağırmak için bir API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0f304-107">An API key for calling an external web API.</span></span>
- <span data-ttu-id="0f304-108">Bir dış sistemde kimlik doğrulaması için bir istemci sertifikası.</span><span class="sxs-lookup"><span data-stu-id="0f304-108">A client certificate for authenticating to an external system.</span></span>

<span data-ttu-id="0f304-109">Gizli dizileri uygulamanın dışından hiçbir şekilde açıklanmayacak şekilde dikkatle yönetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0f304-109">Secrets must be carefully managed so that they're never disclosed outside of the application.</span></span>

<span data-ttu-id="0f304-110">Uzun bir süre önce, uygulama gizli dizilerini uygulama kod temelinin içindeki bir yapılandırma dosyasında depolamak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="0f304-110">Not long ago, it was popular to store application secrets in a configuration file inside the application codebase.</span></span> <span data-ttu-id="0f304-111">.NET geliştiricileri *web.config* dosyasını fonla geri çekecektir.</span><span class="sxs-lookup"><span data-stu-id="0f304-111">.NET developers will fondly recall the *web.config* file.</span></span> <span data-ttu-id="0f304-112">Basit hale getirme, parolaların kod ile birlikte ve güvenli bir şekilde tümleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="0f304-112">While simple to implement, integrating secrets to along with code was far from secure.</span></span> <span data-ttu-id="0f304-113">Yaygın bir yanıltıcı, genel bir GIT deposuna gönderilirken dosyayı eklemek ve gizli dizileri dünya çapında ortaya çıkarmıştı.</span><span class="sxs-lookup"><span data-stu-id="0f304-113">A common misstep was to include the file when pushing to a public GIT repository, exposing the secrets to the world.</span></span>

<span data-ttu-id="0f304-114">Modern dağıtılmış uygulamalar oluşturmak için yaygın olarak kabul edilen bir metodolojide [Twelve-Factor uygulamasıdır](https://12factor.net/).</span><span class="sxs-lookup"><span data-stu-id="0f304-114">A widely accepted methodology for constructing modern distributed applications is [The Twelve-Factor App](https://12factor.net/).</span></span> <span data-ttu-id="0f304-115">İlke ve en iyi uygulamalar kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0f304-115">It describes a set of principles and best practices.</span></span> <span data-ttu-id="0f304-116">Üçüncü etkeni, *yapılandırma ve parolaların kod tabanının dışında externalized olmasını önerir.*</span><span class="sxs-lookup"><span data-stu-id="0f304-116">Its third factor prescribes that *configuration and secrets be externalized outside of the code base.*</span></span>

<span data-ttu-id="0f304-117">Bu sorunu gidermek için .NET Core platformu, hassas verileri proje ağacının dışında bir fiziksel klasörde depolayan bir [gizli dizi Yöneticisi](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-117">To address this concern, the .NET Core platform includes a [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) feature that stores sensitive data in a physical folder outside of the project tree.</span></span> <span data-ttu-id="0f304-118">Gizlilikler kaynak denetimi dışında olduğundan, bu özellik verileri şifrelemez.</span><span class="sxs-lookup"><span data-stu-id="0f304-118">While secrets are outside of source control, this feature doesn't encrypt data.</span></span> <span data-ttu-id="0f304-119">Yalnızca **geliştirme amacıyla** tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f304-119">It's designed for **development purposes** only.</span></span>

<span data-ttu-id="0f304-120">Daha modern ve güvenli bir uygulama, **HashiCorp Kasası** veya **Azure Key Vault** gibi bir gizli dizi yönetim aracında gizli dizileri yalıtmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f304-120">A more modern and secure practice is to isolate secrets in a secrets management tool like **Hashicorp Vault** or **Azure Key Vault**.</span></span>  <span data-ttu-id="0f304-121">Bu araçlar, gizli dizileri dışarıda depolamanıza, ortamlarda kimlik bilgilerinin çeşitliliğine ve uygulama kodundan bunlara başvurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-121">These tools enable you to store secrets externally, vary credentials across environments, and reference them from application code.</span></span> <span data-ttu-id="0f304-122">Ancak, her aracın karmaşıklıkları ve öğrenme eğrisi vardır.</span><span class="sxs-lookup"><span data-stu-id="0f304-122">However, each tool has its complexities and learning curve.</span></span>

<span data-ttu-id="0f304-123">Davpr, gizli dizileri yönetmeyi kolaylaştıran bir yapı bloğu sunar.</span><span class="sxs-lookup"><span data-stu-id="0f304-123">Dapr offers a building block that simplifies managing secrets.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="0f304-124">Ne çözdüğü</span><span class="sxs-lookup"><span data-stu-id="0f304-124">What it solves</span></span>

<span data-ttu-id="0f304-125">DAPR [gizli dizisi oluşturma bloğu](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) , gizli dizi ve gizli yönetim araçlarıyla çalışma karmaşıklığını soyutlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-125">The Dapr [secrets building block](https://docs.dapr.io/developing-applications/building-blocks/secrets/secrets-overview/) abstracts away the complexity of working with secrets and secret management tools.</span></span>

- <span data-ttu-id="0f304-126">Birleşik bir arabirim aracılığıyla temel alınan sıhhi tesisat 'yi gizler.</span><span class="sxs-lookup"><span data-stu-id="0f304-126">It hides the underlying plumbing through a unified interface.</span></span>
- <span data-ttu-id="0f304-127">Geliştirme ve üretim arasında değişebilen çeşitli *takılabilir* gizli depolama bileşenlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="0f304-127">It supports various *pluggable* secret store components, which can vary between development and production.</span></span>
- <span data-ttu-id="0f304-128">Uygulamalar gizli depolama kitaplıklarında doğrudan bağımlılıklara gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="0f304-128">Applications don't require direct dependencies on secret store libraries.</span></span>
- <span data-ttu-id="0f304-129">Geliştiriciler her gizli depolama hakkında ayrıntılı bilgi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0f304-129">Developers don't require detailed knowledge of each secret store.</span></span>

<span data-ttu-id="0f304-130">Davpr yukarıdaki kaygıların tümünü işler.</span><span class="sxs-lookup"><span data-stu-id="0f304-130">Dapr handles all of the above concerns.</span></span>

<span data-ttu-id="0f304-131">Gizli dizi erişiminin kimlik doğrulama ve yetkilendirme aracılığıyla güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-131">Access to the secrets is secured through authentication and authorization.</span></span> <span data-ttu-id="0f304-132">Yalnızca yeterli haklara sahip bir uygulama gizli anahtarlara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-132">Only an application with sufficient rights can access secrets.</span></span> <span data-ttu-id="0f304-133">Kubernetes 'te çalışan uygulamalar, yerleşik gizli dizi yönetim mekanizmasını da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-133">Applications running in Kubernetes can also use its built-in secrets management mechanism.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="0f304-134">Nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="0f304-134">How it works</span></span>

<span data-ttu-id="0f304-135">Uygulamalar, gizli dizi oluşturma bloğunu iki şekilde kullanır:</span><span class="sxs-lookup"><span data-stu-id="0f304-135">Applications use the secrets building block in two ways:</span></span>

- <span data-ttu-id="0f304-136">Doğrudan uygulama bloğundan gizli dizi alma.</span><span class="sxs-lookup"><span data-stu-id="0f304-136">Retrieve a secret directly from the application block.</span></span>
- <span data-ttu-id="0f304-137">Bir Davpr bileşen yapılandırmasından dolaylı olarak bir gizli dizi başvurusu.</span><span class="sxs-lookup"><span data-stu-id="0f304-137">Reference a secret indirectly from a Dapr component configuration.</span></span>

<span data-ttu-id="0f304-138">Parolaların doğrudan alınması ilk olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f304-138">Retrieving secrets directly is covered first.</span></span> <span data-ttu-id="0f304-139">Bir Davpr bileşen yapılandırma dosyasından bir gizli dizi ile başvurulmaya, sonraki bir bölümde değinilmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-139">Referencing a secret from a Dapr component configuration file is addressed in a later section.</span></span>

<span data-ttu-id="0f304-140">Uygulama, gizli dizi yapı bloğu kullanılırken bir davpr sepet ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="0f304-140">The application interacts with a Dapr sidecar when using the secrets building block.</span></span> <span data-ttu-id="0f304-141">Sepet API 'sini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="0f304-141">The sidecar exposes the secrets API.</span></span> <span data-ttu-id="0f304-142">API, HTTP ya da gRPC ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-142">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="0f304-143">HTTP API 'sini çağırmak için aşağıdaki URL 'YI kullanın:</span><span class="sxs-lookup"><span data-stu-id="0f304-143">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/<name>?<metadata>
```

<span data-ttu-id="0f304-144">URL aşağıdaki segmentleri içerir:</span><span class="sxs-lookup"><span data-stu-id="0f304-144">The URL contains the following segments:</span></span>

- <span data-ttu-id="0f304-145">`<dapr-port>` Davpr dışarıdan arabasının dinlediği bağlantı noktası numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f304-145">`<dapr-port>` specifies the port number upon which the Dapr sidecar is listening.</span></span>
- <span data-ttu-id="0f304-146">`<store-name>` Davpr gizli deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f304-146">`<store-name>` specifies the name of the Dapr secret store.</span></span>
- <span data-ttu-id="0f304-147">`<name>` alınacak gizli dizi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f304-147">`<name>` specifies  the name of the secret to retrieve.</span></span>
- <span data-ttu-id="0f304-148">`<metadata>` gizli anahtar için ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-148">`<metadata>` provides additional information for the secret.</span></span> <span data-ttu-id="0f304-149">Bu bölüm isteğe bağlıdır ve meta veri özellikleri gizli depolama başına farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f304-149">This segment is optional and metadata properties differ per secret store.</span></span> <span data-ttu-id="0f304-150">Meta veri özellikleri hakkında daha fazla bilgi için bkz. [GIZLILIKLER API başvurusu]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).</span><span class="sxs-lookup"><span data-stu-id="0f304-150">For more information on metadata properties, see the [secrets API reference]([Secrets API reference | Dapr Docs](https://docs.dapr.io/reference/api/secrets_api/)).</span></span>

 > [!NOTE]
 > <span data-ttu-id="0f304-151">Yukarıdaki URL, HTTP veya gRPC 'yi destekleyen herhangi bir geliştirme platformunda kullanılabilen yerel bir Davpr API çağrısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0f304-151">The above URL represents the native Dapr API call available to any development platform that supports HTTP or gRPC.</span></span> <span data-ttu-id="0f304-152">.NET, Java ve Go gibi popüler platformlar kendi özel API 'Lerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f304-152">Popular platforms like .NET, Java, and Go have their own custom APIs.</span></span>

<span data-ttu-id="0f304-153">JSON yanıtı, gizli dizinin anahtarını ve değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-153">The JSON response contains the key and value of the secret.</span></span>

<span data-ttu-id="0f304-154">Şekil 10-1, Davpr 'nin gizli API 'ler için bir isteği nasıl işlediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="0f304-154">Figure 10-1 shows how Dapr handles a request for the secrets API:</span></span>

![Davpr gizli API 'SI kullanılarak bir gizli dizi alma diyagramı.](media/secrets/secrets-flow.png)

<span data-ttu-id="0f304-156">**Şekil 10-1**.</span><span class="sxs-lookup"><span data-stu-id="0f304-156">**Figure 10-1**.</span></span> <span data-ttu-id="0f304-157">Davpr gizli API 'SI ile gizli dizi alma.</span><span class="sxs-lookup"><span data-stu-id="0f304-157">Retrieving a secret with the Dapr secrets API.</span></span>

1. <span data-ttu-id="0f304-158">Hizmet, gizli deponun adı ve alınacak gizli anahtar ile birlikte, Davpr gizli anahtarını çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f304-158">The service calls the Dapr secrets API, along with the name of the secret store, and secret to retrieve.</span></span>
1. <span data-ttu-id="0f304-159">Davpr sepet, belirtilen gizli anahtarı gizli depolamadan alır.</span><span class="sxs-lookup"><span data-stu-id="0f304-159">The Dapr sidecar retrieves the specified secret from the secret store.</span></span>
1. <span data-ttu-id="0f304-160">Davpr sepet, gizli bilgileri hizmete geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f304-160">The Dapr sidecar returns the secret information back to the service.</span></span>

<span data-ttu-id="0f304-161">Bazı gizli depolar, birden çok anahtar/değer çiftini tek bir gizli dizi içinde depolamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="0f304-161">Some secret stores support storing multiple key/value pairs in a single secret.</span></span> <span data-ttu-id="0f304-162">Bu senaryolar için, yanıt, aşağıdaki örnekte olduğu gibi tek bir JSON yanıtında birden çok anahtar/değer çifti içerir:</span><span class="sxs-lookup"><span data-stu-id="0f304-162">For those scenarios, the response would contain multiple key/value pairs in a single JSON response as in the following example:</span></span>

```http
GET http://localhost:3500/v1.0/secrets/secret-store/interestRates?metadata.version_id=3
```

```json
{
  "tier1-percentage": "2.5",
  "tier2-percentage": "3.8",
  "tier3-percentage": "5.1"
}
```

<span data-ttu-id="0f304-163">Davpr gizli dizileri API 'SI, uygulamanın erişimi olan tüm gizli dizileri almak için de bir işlem sağlar:</span><span class="sxs-lookup"><span data-stu-id="0f304-163">The Dapr secrets API also offers an operation to retrieve all the secrets the application has access to:</span></span>

```http
http://localhost:<dapr-port>/v1.0/secrets/<store-name>/bulk
```

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="0f304-164">Davpr .NET SDK 'sını kullanma</span><span class="sxs-lookup"><span data-stu-id="0f304-164">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="0f304-165">.NET geliştiricileri için, Davpr .NET SDK 'Sı, Davpr gizli yönetimini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0f304-165">For .NET developers, the Dapr .NET SDK streamlines Dapr secret management.</span></span> <span data-ttu-id="0f304-166">Yöntemini göz önünde bulundurun `DaprClient.GetSecretAsync` .</span><span class="sxs-lookup"><span data-stu-id="0f304-166">Consider the `DaprClient.GetSecretAsync` method.</span></span> <span data-ttu-id="0f304-167">En az çabayla herhangi bir Davpr gizli deposundan doğrudan bir gizli dizi almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-167">It enables you to retrieve a secret directly from any Dapr secret store with minimal effort.</span></span> <span data-ttu-id="0f304-168">Bir SQL Server veritabanı için bağlantı dizesi gizli dizisi getirmeye bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f304-168">Here's an example of fetching a connection string secret for a SQL Server database:</span></span>

```csharp
var metadata = new Dictionary<string, string> { ["version_id"] = "3" };
Dictionary<string, string> secrets = await daprClient.GetSecretAsync("secret-store", "eshopsecrets", metadata);
string connectionString = secrets["customerdb"];
```

<span data-ttu-id="0f304-169">Yöntemi için bağımsız değişkenler `GetSecretAsync` şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="0f304-169">Arguments for the `GetSecretAsync` method include:</span></span>

- <span data-ttu-id="0f304-170">Davpr gizli deposu bileşeninin adı (' gizli-Store ')</span><span class="sxs-lookup"><span data-stu-id="0f304-170">The name of the Dapr secret store component ('secret-store')</span></span>
- <span data-ttu-id="0f304-171">Alınacak gizli dizi (' eshopsecret ')</span><span class="sxs-lookup"><span data-stu-id="0f304-171">The secret to retrieve ('eshopsecrets')</span></span>
- <span data-ttu-id="0f304-172">İsteğe bağlı meta veri anahtar/değer çiftleri (' version_id = 3 ')</span><span class="sxs-lookup"><span data-stu-id="0f304-172">Optional metadata key/value pairs ('version_id=3')</span></span>

<span data-ttu-id="0f304-173">Yöntem bir sözlük nesnesi ile yanıt verir ve bir gizli dizi birden çok anahtar/değer çifti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-173">The method responds with a dictionary object as a secret can contain multiple key/value pairs.</span></span> <span data-ttu-id="0f304-174">Yukarıdaki örnekte, adlı gizli dizinin `customerdb` bir bağlantı dizesi döndürecek şekilde koleksiyondan başvuruluyor.</span><span class="sxs-lookup"><span data-stu-id="0f304-174">In the example above, the secret named `customerdb` is referenced from the collection to return a connection string.</span></span>

<span data-ttu-id="0f304-175">Davpr .NET SDK 'Sı Ayrıca bir .NET yapılandırma sağlayıcısına de sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f304-175">The Dapr .NET SDK also features a .NET configuration provider.</span></span> <span data-ttu-id="0f304-176">Belirtilen gizli dizileri temel [.NET Core Yapılandırma API](https://docs.microsoft.com/dotnet/core/extensions/configuration)'sine yükler.</span><span class="sxs-lookup"><span data-stu-id="0f304-176">It loads specified secrets into the underlying [.NET Core configuration API](https://docs.microsoft.com/dotnet/core/extensions/configuration).</span></span> <span data-ttu-id="0f304-177">Çalışan uygulama daha sonra `IConfiguration` ASP.NET Core bağımlılık ekleme ' de kayıtlı sözlükten parolalara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-177">The running application can then reference secrets from the `IConfiguration` dictionary that is registered in ASP.NET Core dependency injection.</span></span>

<span data-ttu-id="0f304-178">Gizli dizi yapılandırma sağlayıcısı, [Dapr.Extensions.Configurlama](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet paketinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-178">The secrets configuration provider is available from the [Dapr.Extensions.Configuration](https://www.nuget.org/packages/Dapr.Extensions.Configuration) NuGet package.</span></span> <span data-ttu-id="0f304-179">Sağlayıcı, `Program.cs` bir ASP.NET Web API uygulamasında kayıtlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="0f304-179">The provider can be registered in the `Program.cs` of an ASP.NET Web API application:</span></span>  

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration(config =>
        {
            var daprClient = new DaprClientBuilder().Build();
            var secretDescriptors = new List<DaprSecretDescriptor>
            {
                new DaprSecretDescriptor("eshopsecrets")
            };
            config.AddDaprSecretStore("secret-store", secretDescriptors, daprClient);
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

<span data-ttu-id="0f304-180">Yukarıdaki örnek, `eshopsecrets` parolalar koleksiyonunu başlangıçta .NET yapılandırma sistemine yükler.</span><span class="sxs-lookup"><span data-stu-id="0f304-180">The above example loads the `eshopsecrets` secrets collection into the .NET configuration system at startup.</span></span> <span data-ttu-id="0f304-181">Sağlayıcının kaydedilmesi için bir örneği gerekir ve bu `DaprClient` , Davpr sidecar üzerinde GIZLILIKLER API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0f304-181">Registering the provider requires an instance of `DaprClient` to invoke the secrets API on the Dapr sidecar.</span></span> <span data-ttu-id="0f304-182">Diğer bağımsız değişkenler, gizli deponun adını ve `DaprSecretDescriptor` gizli dizi adına sahip bir nesnesi içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-182">The other arguments include the name of the secret store and a `DaprSecretDescriptor` object with the name of the secret.</span></span>

<span data-ttu-id="0f304-183">Yüklendikten sonra doğrudan uygulama kodundan gizli dizileri alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f304-183">Once loaded, you can retrieve secrets directly from application code:</span></span>

```csharp
public void GetCustomer(IConfiguration config)
{
    var connectionString = config["eshopsecrets"]["customerdb"];
}
```

## <a name="secret-store-components"></a><span data-ttu-id="0f304-184">Gizli mağaza bileşenleri</span><span class="sxs-lookup"><span data-stu-id="0f304-184">Secret store components</span></span>

<span data-ttu-id="0f304-185">Gizli dizi oluşturma bloğu birçok gizli depolama bileşenini destekler.</span><span class="sxs-lookup"><span data-stu-id="0f304-185">The secrets building block supports several secret store components.</span></span> <span data-ttu-id="0f304-186">Yazma sırasında, aşağıdaki gizli depolar kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0f304-186">At the time of writing, the following secret stores are available:</span></span>

- <span data-ttu-id="0f304-187">Ortam Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0f304-187">Environment Variables</span></span>
- <span data-ttu-id="0f304-188">Yerel dosya</span><span class="sxs-lookup"><span data-stu-id="0f304-188">Local file</span></span>
- <span data-ttu-id="0f304-189">Kubernetes gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="0f304-189">Kubernetes secrets</span></span>
- <span data-ttu-id="0f304-190">AWS gizli dizileri Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="0f304-190">AWS Secrets Manager</span></span>
- <span data-ttu-id="0f304-191">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="0f304-191">Azure Key Vault</span></span>
- <span data-ttu-id="0f304-192">GCP gizli Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="0f304-192">GCP Secret Manager</span></span>
- <span data-ttu-id="0f304-193">HashiCorp Kasası</span><span class="sxs-lookup"><span data-stu-id="0f304-193">HashiCorp Vault</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f304-194">Ortam değişkenleri ve yerel dosya bileşenleri yalnızca geliştirme iş yükleri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f304-194">The environment variables and local file components are designed for development workloads only.</span></span>

<span data-ttu-id="0f304-195">Aşağıdaki bölümlerde, gizli bir deponun nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0f304-195">The following sections show how to configure a secret store.</span></span>

### <a name="configuration"></a><span data-ttu-id="0f304-196">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0f304-196">Configuration</span></span>

<span data-ttu-id="0f304-197">Bir Davpr bileşen yapılandırma dosyası kullanarak gizli bir mağaza yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0f304-197">You configure a secret store using a Dapr component configuration file.</span></span> <span data-ttu-id="0f304-198">Dosyanın tipik yapısı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f304-198">The typical structure of the file is shown below:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: [component name]
  namespace: [namespace]
spec:
  type: secretstores.[secret store type]
  version: [secret store version]
  metadata:
  - name: [property name]
    value: [property value]
```

<span data-ttu-id="0f304-199">Tüm Davpr bileşen yapılandırma dosyaları `name` , isteğe bağlı bir değerle birlikte gerektirir `namespace` .</span><span class="sxs-lookup"><span data-stu-id="0f304-199">All Dapr component configuration files require a `name` along with an optional `namespace` value.</span></span> <span data-ttu-id="0f304-200">Ayrıca, `type` `spec` bölümündeki alanı gizli depo bileşeni türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f304-200">Additionally, the `type` field in the `spec` section specifies the type of secret store component.</span></span> <span data-ttu-id="0f304-201">`metadata`Bölümdeki Özellikler gizli depolama alanı başına farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f304-201">The properties in the `metadata` section differ per secret store.</span></span>

### <a name="indirectly-consume-dapr-secrets"></a><span data-ttu-id="0f304-202">Dolaylı olarak Davpr gizli dizilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0f304-202">Indirectly consume Dapr secrets</span></span>

<span data-ttu-id="0f304-203">Bu bölümde daha önce bahsedildiği gibi uygulamalar, bileşen yapılandırma dosyalarında bunlara başvurarak gizli dizileri de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-203">As mentioned earlier in this chapter, applications can also consume secrets by referencing them in component configuration files.</span></span> <span data-ttu-id="0f304-204">Durumu depolamak için Redsıs önbelleği kullanan bir [durum yönetimi bileşeni](state-management.md) düşünün:</span><span class="sxs-lookup"><span data-stu-id="0f304-204">Consider a [state management component](state-management.md) that uses Redis cache for storing state:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: e$h0p0nD@pr
```

<span data-ttu-id="0f304-205">Yukarıdaki yapılandırma dosyası Redsıs sunucusuna bağlanmak için **düz metin** bir parola içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-205">The above configuration file contains a **clear-text** password for connecting to the Redis server.</span></span> <span data-ttu-id="0f304-206">**Sabit kodlanmış** parolalar her zaman hatalı bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="0f304-206">**Hardcoded** passwords are always a bad idea.</span></span> <span data-ttu-id="0f304-207">Bu yapılandırma dosyasını bir ortak depoya göndermek, parolayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="0f304-207">Pushing this configuration file to a public repository would expose the password.</span></span> <span data-ttu-id="0f304-208">Parolayı gizli bir depoda depolamak bu senaryoyu önemli ölçüde iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="0f304-208">Storing the password in a secret store would dramatically improve this scenario.</span></span>

<span data-ttu-id="0f304-209">Aşağıdaki örneklerde, birkaç farklı gizli mağaza kullanılarak bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0f304-209">The following examples demonstrate this using several different secret stores.</span></span>

### <a name="local-file"></a><span data-ttu-id="0f304-210">Yerel dosya</span><span class="sxs-lookup"><span data-stu-id="0f304-210">Local file</span></span>

<span data-ttu-id="0f304-211">Yerel dosya bileşeni, geliştirme senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f304-211">The local file component is designed for development scenarios.</span></span> <span data-ttu-id="0f304-212">Yerel dosya sisteminde bir JSON dosyası içinde gizli dizileri depolar.</span><span class="sxs-lookup"><span data-stu-id="0f304-212">It stores secrets on the local filesystem inside a JSON file.</span></span> <span data-ttu-id="0f304-213">Adında bir örnek aşağıda verilmiştir `eshop-secrets.json` .</span><span class="sxs-lookup"><span data-stu-id="0f304-213">Here's an example named `eshop-secrets.json`.</span></span> <span data-ttu-id="0f304-214">Tek bir gizli dizi içerir: Redsıs için parola:</span><span class="sxs-lookup"><span data-stu-id="0f304-214">It contains a single secret - a password for Redis:</span></span>

```json
{
  "eShopRedisPassword": "e$h0p0nD@pr"
}
```

<span data-ttu-id="0f304-215">Bu dosyayı `components` , Davpr uygulamasını çalıştırırken belirttiğiniz bir klasöre yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f304-215">You place this file in a `components` folder that you specify when running the Dapr application.</span></span>

<span data-ttu-id="0f304-216">Aşağıdaki gizli depo yapılandırma dosyası JSON dosyasını gizli bir depo olarak tüketir.</span><span class="sxs-lookup"><span data-stu-id="0f304-216">The following secret store configuration file consumes the JSON file as a secret store.</span></span> <span data-ttu-id="0f304-217">Ayrıca klasöre de yerleştirilir `components` :</span><span class="sxs-lookup"><span data-stu-id="0f304-217">It's also placed in the `components` folder:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-local-secret-store
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secrets.json
  - name: nestedSeparator
    value: ":"
```

<span data-ttu-id="0f304-218">Bileşen türü `secretstore.local.file` .</span><span class="sxs-lookup"><span data-stu-id="0f304-218">The component type is `secretstore.local.file`.</span></span> <span data-ttu-id="0f304-219">`secretsFile`Metadata öğesi, gizli dizi dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f304-219">The `secretsFile` metadata element specifies the path to the secrets file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f304-220">Bir gizli dizi dosyası yolu mutlak veya göreli bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-220">The path to a secrets file can be a absolute or relative path.</span></span> <span data-ttu-id="0f304-221">Göreli yol, uygulamanın başladığı klasörü temel alır.</span><span class="sxs-lookup"><span data-stu-id="0f304-221">The relative path is based on the folder in which the application starts.</span></span> <span data-ttu-id="0f304-222">Örnekte, `components` klasörü .NET uygulamasını içeren dizinin bir alt klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="0f304-222">In the example, the `components` folder is a sub-folder of the directory that contains the .NET application.</span></span>

<span data-ttu-id="0f304-223">Uygulama klasöründen, `components` yolu bir komut satırı bağımsız değişkeni olarak belirten Davpr uygulamasını başlatın:</span><span class="sxs-lookup"><span data-stu-id="0f304-223">From the application folder, start the Dapr application specifying the `components` path as a command-line argument:</span></span>

```console
dapr run --app-id basket-api --components-path ./components dotnet run
```

> [!NOTE]
> <span data-ttu-id="0f304-224">Bu yukarıdaki örnek, şirket içinde barındırılan modda Davpr çalıştırmak için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0f304-224">This above example applies to running Dapr in self-hosted mode.</span></span> <span data-ttu-id="0f304-225">Kubernetes barındırma için, birim bağlama kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="0f304-225">For Kubernetes hosting, consider using volume mounts.</span></span>

<span data-ttu-id="0f304-226">`nestedSeparator`Bir Davpr yapılandırma dosyasında, BIR JSON hiyerarşisini *düzleştirmek* için bir karakter belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f304-226">The `nestedSeparator` in a Dapr configuration file specifies a character to *flatten* a JSON hierarchy.</span></span> <span data-ttu-id="0f304-227">Aşağıdaki kod parçacığını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0f304-227">Consider the following snippet:</span></span>

```json
{
    "redisPassword": "some password",
    "connectionStrings": {
        "customerdb": "some connection string",
        "productdb": "some connection string"
    }
}
```

<span data-ttu-id="0f304-228">Ayırıcı olarak bir iki nokta üst üste kullanarak, `customerdb` anahtarı kullanarak bağlantı dizesini alabilirsiniz `connectionStrings:customerdb` .</span><span class="sxs-lookup"><span data-stu-id="0f304-228">Using a colon as a separator, you can retrieve the `customerdb` connection-string using the key `connectionStrings:customerdb`.</span></span>

> [!NOTE]
> <span data-ttu-id="0f304-229">İki nokta üst üste `:` varsayılan ayırıcı değeridir.</span><span class="sxs-lookup"><span data-stu-id="0f304-229">The colon `:` is the default separator value.</span></span>

<span data-ttu-id="0f304-230">Sonraki örnekte, bir durum yönetimi yapılandırma dosyası Redsıs sunucusuna bağlanmak için parolayı almak üzere yerel gizli dizi bileşenine başvurur:</span><span class="sxs-lookup"><span data-stu-id="0f304-230">In the next example, a state management configuration file references the local secret store component to obtain the password for connecting to the Redis server:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    secretKeyRef:
      name: eShopRedisPassword
      key: eShopRedisPassword
auth:
  secretStore: eshop-local-secret-store
```

<span data-ttu-id="0f304-231">`secretKeyRef`Öğesi, parolayı içeren gizli dizi ile başvurur.</span><span class="sxs-lookup"><span data-stu-id="0f304-231">The `secretKeyRef` element references the secret containing the password.</span></span> <span data-ttu-id="0f304-232">Önceki *şifresiz metin* değerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0f304-232">It replaces the earlier *clear-text* value.</span></span> <span data-ttu-id="0f304-233">Gizli dizi adı ve anahtar adı, `eShopRedisPassword` gizli dizi başvurusu.</span><span class="sxs-lookup"><span data-stu-id="0f304-233">The secret name and the key name, `eShopRedisPassword`, reference the secret.</span></span> <span data-ttu-id="0f304-234">Gizli dizi yönetim bileşeninin adı `eshop-local-secret-store` `auth` meta veri öğesinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0f304-234">The name of the secret management component `eshop-local-secret-store` is found in the `auth` metadata element.</span></span>

<span data-ttu-id="0f304-235">`eShopRedisPassword`Gizli dizi başvurusunda hem ad hem de anahtar için neden özdeş olduğunu merak ediyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f304-235">You might wonder why `eShopRedisPassword` is identical for both the name and key in the secret reference.</span></span> <span data-ttu-id="0f304-236">Yerel dosya gizli deposunda, gizli dizileri ayrı bir adla tanımlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0f304-236">In the local file secret store, secrets aren't identified with a separate name.</span></span> <span data-ttu-id="0f304-237">Bu senaryo, Kubernetes gizli dizileri kullanılarak bir sonraki örnekte farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f304-237">The scenario will be different in the next example using Kubernetes secrets.</span></span>

### <a name="kubernetes-secret"></a><span data-ttu-id="0f304-238">Kubernetes gizli dizisi</span><span class="sxs-lookup"><span data-stu-id="0f304-238">Kubernetes secret</span></span>

<span data-ttu-id="0f304-239">Bu ikinci örnek, Kubernetes 'te çalışan bir Davpr uygulamasına odaklanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-239">This second example focuses on a Dapr application running in Kubernetes.</span></span> <span data-ttu-id="0f304-240">Kubernetes 'in sunduğu standart gizli dizileri mekanizmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-240">It uses the standard secrets mechanism that Kubernetes offers.</span></span> <span data-ttu-id="0f304-241">`kubectl`Parolayı içeren bir gizli dizi oluşturmak Için Kubernetes CLI () kullanın `eshop-redis-secret` :</span><span class="sxs-lookup"><span data-stu-id="0f304-241">Use the Kubernetes CLI (`kubectl`) to create a secret named `eshop-redis-secret` that contains the password:</span></span>

```console
kubectl create secret generic eshopsecrets --from-literal=redisPassword=e$h0p0nD@pr -n eshop
```

<span data-ttu-id="0f304-242">Oluşturulduktan sonra, durum yönetimi için bileşen yapılandırma dosyasında gizli başvuruya başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f304-242">Once created, you can reference the secret in the component configuration file for state management:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: eshopsecrets
      key: redisPassword
auth:
  secretStore: kubernetes
```

<span data-ttu-id="0f304-243">`secretKeyRef`Öğesi, Kubernetes parolasının adını ve gizli anahtarı, `eshopsecrets` , ve ' ı belirtir `redisPassword` .</span><span class="sxs-lookup"><span data-stu-id="0f304-243">The `secretKeyRef` element specifies the name of the Kubernetes secret and the secret's key, `eshopsecrets`, and `redisPassword` respectively.</span></span> <span data-ttu-id="0f304-244">`auth`Meta veri bölümü, Davpr 'Nin Kubernetes gizli anahtarları yönetim bileşenini kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0f304-244">The `auth` metadata section instructs Dapr to use the Kubernetes secrets management component.</span></span>

> [!NOTE]
> <span data-ttu-id="0f304-245">Auth, Kubernetes gizli dizileri kullanılırken varsayılan değerdir ve atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-245">Auth is the default value when using Kubernetes secrets and can be omitted.</span></span>

<span data-ttu-id="0f304-246">Bir üretim ayarında, parolalar genellikle otomatik bir CI/CD işlem hattının parçası olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f304-246">In a production setting, secrets are typically created as part of an automated CI/CD pipeline.</span></span> <span data-ttu-id="0f304-247">Böylece, yalnızca yeterli izinlere sahip kişiler erişebilir ve gizli dizileri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-247">Doing so ensures only people with sufficient permissions can access and change the secrets.</span></span> <span data-ttu-id="0f304-248">Geliştiriciler, parolaların gerçek değerini bilmeden yapılandırma dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f304-248">Developers create configuration files without knowing the actual value of the secrets.</span></span>

### <a name="azure-key-vault"></a><span data-ttu-id="0f304-249">Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="0f304-249">Azure Key Vault</span></span>

<span data-ttu-id="0f304-250">Sonraki örnek, gerçek dünyada bir üretim senaryosuna yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="0f304-250">The next example is geared toward a real-world production scenario.</span></span> <span data-ttu-id="0f304-251">Gizli depo olarak **Azure Key Vault** kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-251">It uses **Azure Key Vault** as the secret store.</span></span> <span data-ttu-id="0f304-252">Azure Key Vault, parolaların bulutta güvenli bir şekilde depolanmasını sağlayan yönetilen bir Azure hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="0f304-252">Azure Key Vault is a managed Azure service that enables secrets to be stored securely in the cloud.</span></span>

<span data-ttu-id="0f304-253">Bu örneğin çalışması için aşağıdaki önkoşulların karşılanması gerekir:</span><span class="sxs-lookup"><span data-stu-id="0f304-253">For this example to work, the following prerequisites must be satisfied:</span></span>

- <span data-ttu-id="0f304-254">Azure aboneliğine yönetici erişimini güvenli hale getirdi.</span><span class="sxs-lookup"><span data-stu-id="0f304-254">You've secured administrative access to an Azure subscription.</span></span>
- <span data-ttu-id="0f304-255">`eshopkv` `redisPassword` Redsıs sunucusuna bağlanmak için parolayı içeren adında bir gizli anahtar tutan adlı bir Azure Key Vault sağladınız.</span><span class="sxs-lookup"><span data-stu-id="0f304-255">You've provisioned an Azure Key Vault named `eshopkv` that holds a secret named `redisPassword` that contains the password for connecting to the Redis server.</span></span>
- <span data-ttu-id="0f304-256">Azure Active Directory ' de [hizmet sorumlusu](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal) oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="0f304-256">You've created [service principal](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal) in Azure Active Directory.</span></span>
- <span data-ttu-id="0f304-257">Yerel dosya sistemine bu hizmet sorumlusu için bir x509 sertifikası yüklediniz (hem ortak hem de özel anahtar içeren).</span><span class="sxs-lookup"><span data-stu-id="0f304-257">You've installed an X509 certificate for this service principal (containing both the public and private key) on the local filesystem.</span></span>

> [!NOTE]
> <span data-ttu-id="0f304-258">Hizmet sorumlusu, bir Azure hizmetinin kimliğini doğrulamak için bir uygulama tarafından kullanılabilen bir kimliktir.</span><span class="sxs-lookup"><span data-stu-id="0f304-258">A service principal is an identity that can be used by an application to authenticate an Azure service.</span></span> <span data-ttu-id="0f304-259">Hizmet sorumlusu bir x509 sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-259">The service principal uses a X509 certificate.</span></span> <span data-ttu-id="0f304-260">Uygulama, kimlik doğrulaması için kimlik bilgisi olarak bu sertifikayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-260">The application uses this certificate as a credential to authenticate itself.</span></span>

<span data-ttu-id="0f304-261">[Dadpr Azure Key Vault gizli dizi belgeleri](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) , bir Key Vault ortamı oluşturmak ve yapılandırmak için adım adım yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-261">The [Dapr Azure Key Vault secret store documentation](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault/) provides step-by-step instructions to create and configure a Key Vault environment.</span></span>

#### <a name="use-key-vault-when-running-in-self-hosted-mode"></a><span data-ttu-id="0f304-262">Kendi kendine barındırılan modda çalışırken Key Vault kullan</span><span class="sxs-lookup"><span data-stu-id="0f304-262">Use Key Vault when running in self-hosted mode</span></span>

<span data-ttu-id="0f304-263">Şirket içinde barındırılan modda Azure Key Vault tüketen aşağıdaki yapılandırma dosyası gerekir:</span><span class="sxs-lookup"><span data-stu-id="0f304-263">Consuming Azure Key Vault in Dapr self-hosted mode requires the following configuration file:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: eshopkv
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificateFile
    value : "azurekv-spn-cert.pfx"
```

<span data-ttu-id="0f304-264">Gizli depolama türü `secretstores.azure.keyvault` .</span><span class="sxs-lookup"><span data-stu-id="0f304-264">The secret store type is `secretstores.azure.keyvault`.</span></span> <span data-ttu-id="0f304-265">`metadata`Key Vault erişimi yapılandırma öğesi aşağıdaki özellikleri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0f304-265">The `metadata` element to configure access to Key Vault requires the following properties:</span></span>

- <span data-ttu-id="0f304-266">, `vaultName` Azure Key Vault adını içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-266">The `vaultName` contains the name of the Azure Key Vault.</span></span>
- <span data-ttu-id="0f304-267">, `spnTenantId` Key Vault karşı kimlik doğrulaması yapmak için kullanılan hizmet sorumlusunun *Kiracı kimliğini* içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-267">The `spnTenantId` contains the *tenant id* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="0f304-268">, `spnClientId` Key Vault göre kimlik doğrulaması yapmak için kullanılan hizmet sorumlusunun *uygulama kimliğini* içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-268">The `spnClientId` contains the *app id* of the service principal used to authenticate against the Key Vault.</span></span>
- <span data-ttu-id="0f304-269">, `spnCertificateFile` Key Vault karşı kimlik doğrulaması yapılacak hizmet sorumlusu için sertifika dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-269">The `spnCertificateFile` contains the path to the certificate file for the service principal to authenticate against the Key Vault.</span></span>

> [!TIP]
> <span data-ttu-id="0f304-270">Hizmet sorumlusu bilgilerini Azure portal veya Azure CLı 'dan kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f304-270">You can copy the service principal information from the Azure portal or Azure CLI .</span></span>

<span data-ttu-id="0f304-271">Uygulama artık Redsıs parolasını Azure Key Vault alabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-271">Now the application can retrieve the Redis password from the Azure Key Vault.</span></span>

#### <a name="use-key-vault-when-running-on-kubernetes"></a><span data-ttu-id="0f304-272">Kubernetes üzerinde çalışırken Key Vault kullan</span><span class="sxs-lookup"><span data-stu-id="0f304-272">Use Key Vault when running on Kubernetes</span></span>

<span data-ttu-id="0f304-273">Davpr ve Kubernetes ile Azure Key Vault kullanmak ayrıca, Azure Key Vault için kimlik doğrulaması yapmak üzere bir hizmet sorumlusu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0f304-273">Consuming Azure Key Vault with Dapr and Kubernetes also requires a service principal to authenticate against the Azure Key Vault.</span></span>

<span data-ttu-id="0f304-274">İlk olarak, kubectl CLı aracını kullanarak bir sertifika dosyası içeren bir *Kubernetes gizli* dizisi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0f304-274">First, create a *Kubernetes secret* that contains a certificate file using the kubectl CLI tool:</span></span>

```console
kubectl create secret generic [k8s_spn_secret_name] --from-file=[pfx_certificate_file_local_path] -n eshop
```

<span data-ttu-id="0f304-275">Komut iki komut satırı bağımsız değişkeni gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0f304-275">The command requires two command-line arguments:</span></span>

- <span data-ttu-id="0f304-276">`[k8s_spn_secret_name]` , Kubernetes gizli deposundaki gizli addır.</span><span class="sxs-lookup"><span data-stu-id="0f304-276">`[k8s_spn_secret_name]` is the secret name in Kubernetes secret store.</span></span>
- <span data-ttu-id="0f304-277">`[pfx_certificate_file_local_path]` x509 sertifika dosyasının yoludur.</span><span class="sxs-lookup"><span data-stu-id="0f304-277">`[pfx_certificate_file_local_path]` is the path of X509 certificate file.</span></span>

<span data-ttu-id="0f304-278">Oluşturulduktan sonra gizli depolama bileşeni yapılandırma dosyasında Kubernetes gizli öğesine başvurabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0f304-278">Once created, you can reference the Kubernetes secret in the secret store component configuration file:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-azurekv-secret-store
  namespace: eshop
spec:
  type: secretstores.azure.keyvault
  version: v1
  metadata:
  - name: vaultName
    value: [your_keyvault_name]
  - name: spnTenantId
    value: "619926af-a7c3-4e95-93ed-4ecc4e3e652b"
  - name: spnClientId
    value: "6cf48032-6c38-43be-9d6f-2a43ce736b09"
  - name: spnCertificate
    secretKeyRef:
      name: [k8s_spn_secret_name]
      key: [pfx_certificate_file_local_name]
auth:
    secretStore: kubernetes
```

<span data-ttu-id="0f304-279">Bu noktada, Kubernetes 'de çalışan bir uygulama, Azure Key Vault redo parolasını alabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-279">At this point, an application running in Kubernetes can retrieve the Redis password from the Azure Key Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f304-280">Hizmet sorumlusu için x509 sertifika dosyasını güvenli bir yerde tutmanız kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f304-280">It's critical to keep the X509 certificate file for the service principal in a safe place.</span></span> <span data-ttu-id="0f304-281">Bunu, kaynak kodu deposunun dışında iyi bilinen bir klasöre yerleştirmek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="0f304-281">It's best to place it in a well-known folder outside the source-code repository.</span></span> <span data-ttu-id="0f304-282">Yapılandırma dosyası daha sonra bu iyi bilinen klasörden sertifika dosyasına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-282">The configuration file can then reference the certificate file from this well-known folder.</span></span> <span data-ttu-id="0f304-283">Yerel bir geliştirme makinesinde, sertifikayı klasörüne kopyalamaktan sorumlu olursunuz.</span><span class="sxs-lookup"><span data-stu-id="0f304-283">On a local development machine, you're responsible for copying the certificate to the folder.</span></span> <span data-ttu-id="0f304-284">Otomatik dağıtımlar için, işlem hattı sertifikayı uygulamanın dağıtıldığı makineye kopyalar.</span><span class="sxs-lookup"><span data-stu-id="0f304-284">For automated deployments, the pipeline will copy the certificate to the machine where the application is deployed.</span></span> <span data-ttu-id="0f304-285">Her ortam için farklı bir hizmet sorumlusu kullanmak en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="0f304-285">It's a best practice to use a different service principal per environment.</span></span> <span data-ttu-id="0f304-286">Bunun yapılması, bir GELIŞTIRME ortamından hizmet sorumlusunun bir ÜRETIM ortamındaki gizli dizileri erişimine engel olur.</span><span class="sxs-lookup"><span data-stu-id="0f304-286">Doing so prevents the service principal from a DEVELOPMENT environment to access secrets in a PRODUCTION environment.</span></span>

<span data-ttu-id="0f304-287">Azure Kubernetes hizmeti 'nde (AKS) çalışırken, Azure Key Vault kimlik doğrulaması için bir [Azure yönetilen kimliği](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) kullanılması tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-287">When running in  Azure Kubernetes Service (AKS), it's preferable to use an [Azure Managed Identity](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) for authenticating against Azure Key Vault.</span></span> <span data-ttu-id="0f304-288">Yönetilen kimlikler bu kitabın kapsamı dışındadır, ancak [Azure Key Vault Yönetilen kimlikler](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) belgeleriyle açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f304-288">Managed identities are outside of the scope of this book, but explained in the [Azure Key Vault with managed identities](https://docs.dapr.io/operations/components/setup-secret-store/supported-secret-stores/azure-keyvault-managed-identity/) documentation.</span></span>

### <a name="scope-secrets"></a><span data-ttu-id="0f304-289">Kapsam gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="0f304-289">Scope secrets</span></span>

<span data-ttu-id="0f304-290">Gizli kapsamlar, uygulamanızın erişebileceği gizli dizileri denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-290">Secret scopes allow you to control which secrets your application can access.</span></span> <span data-ttu-id="0f304-291">Kapsamları bir davpr sepet yapılandırma dosyasında yapılandırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0f304-291">You configure scopes in a Dapr sidecar configuration file.</span></span> <span data-ttu-id="0f304-292">[Davpr yapılandırma belgeleri](https://docs.dapr.io/operations/configuration/configuration-overview/) , parolaların kapsamını belirlemek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-292">The [Dapr configuration documentation](https://docs.dapr.io/operations/configuration/configuration-overview/) provides instructions for scoping secrets.</span></span>

<span data-ttu-id="0f304-293">Gizli kapsamlar içeren bir davpr sepet yapılandırma dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f304-293">Here's an example of a Dapr sidecar configuration file that contains secret scopes:</span></span>

```yml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  secrets:
    scopes:
      - storeName: eshop-azurekv-secret-store
        defaultAccess: allow
        deniedSecrets: ["redisPassword", "apiKey"]
```

<span data-ttu-id="0f304-294">Her gizli dizi için kapsam belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f304-294">You specify scopes per secret store.</span></span> <span data-ttu-id="0f304-295">Yukarıdaki örnekte, gizli depo olarak adlandırılmıştır `eshop-azurekv-secret-store` .</span><span class="sxs-lookup"><span data-stu-id="0f304-295">In the above example, the secret store is named `eshop-azurekv-secret-store`.</span></span> <span data-ttu-id="0f304-296">Gizli dizi erişimini aşağıdaki özellikleri kullanarak yapılandırırsınız:</span><span class="sxs-lookup"><span data-stu-id="0f304-296">You configure access to secrets using the following properties:</span></span>

| <span data-ttu-id="0f304-297">Özellik</span><span class="sxs-lookup"><span data-stu-id="0f304-297">Property</span></span>         | <span data-ttu-id="0f304-298">Değer</span><span class="sxs-lookup"><span data-stu-id="0f304-298">Value</span></span>               | <span data-ttu-id="0f304-299">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f304-299">Description</span></span>                                                                                                                       |
|------------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `defaultAccess`  | <span data-ttu-id="0f304-300">`allow` veya `deny`</span><span class="sxs-lookup"><span data-stu-id="0f304-300">`allow` or `deny`</span></span>   | <span data-ttu-id="0f304-301">Belirtilen gizli depodaki *Tüm* gizli dizi erişimine izin verir veya erişimi reddeder.</span><span class="sxs-lookup"><span data-stu-id="0f304-301">Allows or denies access to *all* secrets in the specified secret store.</span></span> <span data-ttu-id="0f304-302">Bu özellik varsayılan değeri ile isteğe bağlıdır `allow` .</span><span class="sxs-lookup"><span data-stu-id="0f304-302">This property is optional with a default value of `allow`.</span></span> |
| `allowedSecrets` | <span data-ttu-id="0f304-303">Gizli anahtar listesi</span><span class="sxs-lookup"><span data-stu-id="0f304-303">List of secret keys</span></span> | <span data-ttu-id="0f304-304">Dizide belirtilen gizli dizileri erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f304-304">Secrets specified in the array will be accessible.</span></span> <span data-ttu-id="0f304-305">Bu özellik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f304-305">This property is optional.</span></span>                                                     |
| `deniedSecrets`  | <span data-ttu-id="0f304-306">Gizli anahtar listesi</span><span class="sxs-lookup"><span data-stu-id="0f304-306">List of secret keys</span></span> | <span data-ttu-id="0f304-307">Dizide belirtilen gizli dizileri erişilebilir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="0f304-307">Secrets specified in the array will NOT be accessible.</span></span> <span data-ttu-id="0f304-308">Bu özellik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0f304-308">This property is optional.</span></span>                                                 |

<span data-ttu-id="0f304-309">`allowedSecrets`Ve `deniedSecrets` özellikleri `defaultAccess` özelliğinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="0f304-309">The `allowedSecrets` and `deniedSecrets` properties take precedence over the `defaultAccess` property.</span></span> <span data-ttu-id="0f304-310">`defaultAccess: allowed`Ve bir liste belirtmeyi düşünün `allowedSecrets` .</span><span class="sxs-lookup"><span data-stu-id="0f304-310">Imagine specifying `defaultAccess: allowed` and an `allowedSecrets` list.</span></span> <span data-ttu-id="0f304-311">Bu durumda, uygulama tarafından yalnızca listedeki gizli anahtarlara `allowedSecrets` erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-311">In this case, only the secrets in the `allowedSecrets` list would be accessible by the application.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="0f304-312">Başvuru uygulaması: Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="0f304-312">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="0f304-313">Eshopondadpr başvuru uygulaması, iki gizli dizi için gizli dizi derleme bloğunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="0f304-313">The eShopOnDapr reference application uses the secrets building block for two secrets:</span></span>

- <span data-ttu-id="0f304-314">Redsıs önbelleğine bağlanmak için parola.</span><span class="sxs-lookup"><span data-stu-id="0f304-314">The password for connecting to the Redis cache.</span></span>
- <span data-ttu-id="0f304-315">Twilio SendGrid API 'sini kullanmak için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="0f304-315">The API-key for using the Twilio Sendgrid API.</span></span> <span data-ttu-id="0f304-316">Uygulama, bir Davpr çıkış bağlaması ( [bağlamalar yapı taşı](bindings.md)bölümünde açıklandığı gibi) kullanarak e-posta göndermek Için twilo kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-316">The application uses Twillio to send emails using a Dapr output binding (as described in the [bindings building block chapter](bindings.md)).</span></span>

<span data-ttu-id="0f304-317">Docker Compose kullanarak uygulamayı çalıştırırken, **yerel dosya** gizli deposu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f304-317">When running the application using Docker Compose, the **local file** secret store is used.</span></span> <span data-ttu-id="0f304-318">Bileşen yapılandırma dosyası `eshop-secretstore.yaml` `dapr/components` Eshopondadpr deposunun klasöründe bulunur:</span><span class="sxs-lookup"><span data-stu-id="0f304-318">The component configuration file `eshop-secretstore.yaml` is found in the `dapr/components` folder of the eShopOnDapr repository:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-secretstore
  namespace: eshop
spec:
  type: secretstores.local.file
  version: v1
  metadata:
  - name: secretsFile
    value: ./components/eshop-secretstore.json
```

<span data-ttu-id="0f304-319">Yapılandırma dosyası, aynı klasörde bulunan yerel depo dosyasına başvurur `eshop-secretstore.json` :</span><span class="sxs-lookup"><span data-stu-id="0f304-319">The configuration file references the local store file `eshop-secretstore.json` located in the same folder:</span></span>

```json
{
    "redisPassword": "**********",
    "sendgridAPIKey": "**********"
}
```

<span data-ttu-id="0f304-320">`components`Klasör komut satırında belirtilir ve davpr sepet kapsayıcısının içinde yerel bir klasör olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0f304-320">The `components` folder is specified in the command-line and mounted as a local folder inside the Dapr sidecar container.</span></span> <span data-ttu-id="0f304-321">`docker-compose.override.yml`Depo kökündeki, birim bağlama belirten bir kod parçacığı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f304-321">Here's a snippet from the `docker-compose.override.yml` file in the repository root that specifies the volume mount:</span></span>

```yaml
  ordering-backgroundtasks-dapr:
    command: ["./daprd",
      "-app-id", "ordering-backgroundtasks",
      "-app-port", "80",
      "-dapr-grpc-port", "50004",
      "-components-path", "/components",
      "-config", "/configuration/eshop-config.yaml"
      ]
    volumes:
      - "./dapr/components/:/components"
      - "./dapr/configuration/:/configuration"
```

> [!NOTE]
> <span data-ttu-id="0f304-322">Docker Compose geçersiz kılma dosyası çevresel özel yapılandırma değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-322">The Docker Compose override file contains environmental specific configuration values.</span></span>

<span data-ttu-id="0f304-323">`/components`Birim bağlama ve `--components-path` komut satırı bağımsız değişkeni `daprd` Başlangıç komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-323">The `/components` volume mount and `--components-path` command-line argument are passed into the `daprd` startup command.</span></span>

<span data-ttu-id="0f304-324">Yapılandırıldıktan sonra diğer bileşen yapılandırma dosyaları gizli dizileri de başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="0f304-324">Once configured, other component configuration files can also reference the secrets.</span></span> <span data-ttu-id="0f304-325">Gizli dizileri kullanan yayımla/abone ol bileşen yapılandırmasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0f304-325">Here's an example of the Publish/Subscribe component configuration consuming secrets:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: pubsub
  namespace: eshop
spec:
  type: pubsub.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="0f304-326">Yukarıdaki örnekte, yerel redin deposu gizli dizi başvurusunda bulunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f304-326">In the preceding example, the local Redis store is used to reference secrets.</span></span>

## <a name="summary"></a><span data-ttu-id="0f304-327">Özet</span><span class="sxs-lookup"><span data-stu-id="0f304-327">Summary</span></span>

<span data-ttu-id="0f304-328">Davpr gizli dizi oluşturma bloğu, parolalar ve bağlantı dizeleri gibi hassas yapılandırma ayarlarının depolanması ve alınması için yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-328">The Dapr secrets building block provides capabilities for storing and retrieving sensitive configuration settings like passwords and connection-strings.</span></span> <span data-ttu-id="0f304-329">Gizli dizileri korur ve yanlışlıkla açıklanmalarını önler.</span><span class="sxs-lookup"><span data-stu-id="0f304-329">It keeps secrets private and prevents them from being accidentally disclosed.</span></span>

<span data-ttu-id="0f304-330">Yapı taşı birçok farklı gizli depolar destekler ve DAPR gizli API 'SI ile karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="0f304-330">The building block supports several different secret stores and hides their complexity with the Dapr secrets API.</span></span>

<span data-ttu-id="0f304-331">Davpr .NET SDK, gizli dizileri `DaprClient` almak için bir nesne sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f304-331">The Dapr .NET SDK provides a `DaprClient` object to retrieve secrets.</span></span> <span data-ttu-id="0f304-332">Ayrıca .NET Core yapılandırma sistemine gizli diziler ekleyen bir .NET yapılandırma sağlayıcısı da içerir.</span><span class="sxs-lookup"><span data-stu-id="0f304-332">It also includes a .NET configuration provider that adds secrets to the .NET Core configuration system.</span></span> <span data-ttu-id="0f304-333">Yüklendikten sonra .NET kodunuzda bu gizli dizileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f304-333">Once loaded, you can consume these secrets in your .NET code.</span></span>

<span data-ttu-id="0f304-334">Belirli gizli dizileri erişimi denetlemek için gizli kapsamları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f304-334">You can use secret scopes to control access to specific secrets.</span></span>

## <a name="references"></a><span data-ttu-id="0f304-335">Başvurular</span><span class="sxs-lookup"><span data-stu-id="0f304-335">References</span></span>

- [<span data-ttu-id="0f304-336">Twelve-Factor uygulamanın ötesinde</span><span class="sxs-lookup"><span data-stu-id="0f304-336">Beyond the Twelve-Factor Application</span></span>](https://tanzu.vmware.com/content/blog/beyond-the-twelve-factor-app)

>[!div class="step-by-step"]
><span data-ttu-id="0f304-337">[Önceki](observability.md) 
> [Sonraki](summary.md)</span><span class="sxs-lookup"><span data-stu-id="0f304-337">[Previous](observability.md)
[Next](summary.md)</span></span>
