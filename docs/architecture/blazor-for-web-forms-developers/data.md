---
title: Veri erişimi ve yönetimi
description: ASP.NET Web Forms ve Blazor ' deki verilere erişme ve verileri işleme hakkında bilgi edinin.
author: csharpfritz
ms.author: jefritz
ms.date: 04/26/2020
ms.openlocfilehash: b9805da60722de1b5d4f91107e856f647f7564a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446488"
---
# <a name="work-with-data"></a><span data-ttu-id="01ade-103">Verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="01ade-103">Work with data</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="01ade-104">Veri erişimi, bir ASP.NET Web Forms uygulamasının omurgası olur.</span><span class="sxs-lookup"><span data-stu-id="01ade-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="01ade-105">Web için form oluşturuyorsanız, bu verilere ne olur?</span><span class="sxs-lookup"><span data-stu-id="01ade-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="01ade-106">Web Forms ile, bir veritabanıyla etkileşim kurmak için kullanabileceğiniz birden fazla veri erişim tekniği vardı:</span><span class="sxs-lookup"><span data-stu-id="01ade-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="01ade-107">Data Sources</span><span class="sxs-lookup"><span data-stu-id="01ade-107">Data Sources</span></span>
- <span data-ttu-id="01ade-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="01ade-108">ADO.NET</span></span>
- <span data-ttu-id="01ade-109">Varlık Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="01ade-109">Entity Framework</span></span>

<span data-ttu-id="01ade-110">Veri kaynakları, Web Forms bir sayfada yerleştirebileceğiniz ve diğer denetimler gibi yapılandırabileceğiniz denetimleridir.</span><span class="sxs-lookup"><span data-stu-id="01ade-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="01ade-111">Visual Studio, denetimleri Web Forms sayfalarınıza yapılandırmak ve bağlamak için kolay bir iletişim kutusu kümesi sağladı.</span><span class="sxs-lookup"><span data-stu-id="01ade-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="01ade-112">Bir "düşük kod" veya "kod yok" yaklaşımı yaşayan geliştiriciler Web Forms ilk kez yayınlandığında bu tekniği tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="01ade-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![Data Sources](media/data/datasources.png)

<span data-ttu-id="01ade-114">ADO.NET, bir veritabanıyla etkileşime geçmek için düşük düzeyli yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="01ade-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="01ade-115">Uygulamalarınız, etkileşim kurmak için komutlarla, kayıt kümeleriyle ve veri kümeleriyle veritabanıyla bir bağlantı oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="01ade-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="01ade-116">Sonuçlar daha sonra çok kod olmadan ekrandaki alanlara bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="01ade-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="01ade-117">Bu yaklaşımın dezavantajı, her bir ADO.NET nesneleri ( `Connection` , `Command` ve `Recordset` ) kümesinin bir veritabanı satıcısı tarafından sunulan kitaplıklara bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="01ade-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="01ade-118">Bu bileşenlerin kullanımı, kodu rigıd yaptı ve farklı bir veritabanına geçiş yapılmasını zorlaştırıyor.</span><span class="sxs-lookup"><span data-stu-id="01ade-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="01ade-119">Varlık Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="01ade-119">Entity Framework</span></span>

<span data-ttu-id="01ade-120">Entity Framework (EF), .NET Foundation tarafından tutulan açık kaynaklı nesne ilişkisel eşleme çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="01ade-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="01ade-121">Başlangıçta .NET Framework ile yayınlanan EF, veritabanı bağlantıları, depolama şemaları ve etkileşimler için kod üretmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="01ade-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="01ade-122">Bu Soyutlamalarla, uygulamanızın iş kurallarına odaklanarak veritabanının güvenilir bir veritabanı yöneticisi tarafından yönetilmesine izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ade-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="01ade-123">.NET Core 'da, EF Core adlı ve güncelleştirilmiş bir EF sürümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ade-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="01ade-124">EF Core, komut satırı aracını kullanarak, kodunuz ve veritabanı arasındaki etkileşimleri, sizin için kullanabileceğiniz bir dizi komutla oluşturup sürdürmenize yardımcı olur `dotnet ef` .</span><span class="sxs-lookup"><span data-stu-id="01ade-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="01ade-125">Bir veritabanı ile çalışmaya başlamanızı sağlamak için birkaç örnek göz atalım.</span><span class="sxs-lookup"><span data-stu-id="01ade-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="01ade-126">EF Code First</span><span class="sxs-lookup"><span data-stu-id="01ade-126">EF Code First</span></span>

<span data-ttu-id="01ade-127">Veritabanı etkileşimlerinizi oluşturmaya başlamak için hızlı bir yol, birlikte çalışmak istediğiniz sınıf nesneleriyle başlamadır.</span><span class="sxs-lookup"><span data-stu-id="01ade-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="01ade-128">EF, sınıflarınız için uygun veritabanı kodu oluşturmaya yardımcı olacak bir araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="01ade-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="01ade-129">Bu yaklaşım, "Code First" geliştirmesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="01ade-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="01ade-130">`Product`Microsoft SQL Server gibi bir ilişkisel veritabanında depolamak istediğimiz örnek bir storefront uygulaması için aşağıdaki sınıfı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="01ade-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="01ade-131">Ürünün, veritabanımızda oluşturulacak bir birincil anahtarı ve üç ek alanı vardır:</span><span class="sxs-lookup"><span data-stu-id="01ade-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="01ade-132">EF `Id` özelliği kural tarafından birincil anahtar olarak tanımlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="01ade-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="01ade-133">`Name`, metin depolaması için yapılandırılmış bir sütunda depolanacak.</span><span class="sxs-lookup"><span data-stu-id="01ade-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="01ade-134">`[Required]`Bu özelliği dekorasyon özniteliği, `not null` özelliğin bu tanımlanmış davranışının zorlanmasını sağlamaya yardımcı olmak için bir kısıtlama ekler.</span><span class="sxs-lookup"><span data-stu-id="01ade-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="01ade-135">`Description`, metin depolaması için yapılandırılmış bir sütunda depolanacak ve özniteliği tarafından dikte edilen en fazla 4000 karakter uzunluğunda olmalıdır `[MaxLength]` .</span><span class="sxs-lookup"><span data-stu-id="01ade-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="01ade-136">Veritabanı şeması, veri türü kullanılarak adlı bir sütunla yapılandırılacaktır `MaxLength` `varchar(4000)` .</span><span class="sxs-lookup"><span data-stu-id="01ade-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="01ade-137">`Price`Özelliği para birimi olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="01ade-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="01ade-138">`[Range]`Özniteliği, veri depolamayı belirtilen en düşük ve en yüksek değerler dışında engellemek için uygun kısıtlamalar oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="01ade-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="01ade-139">Bu `Product` sınıfı, veritabanı ile bağlantı ve çeviri işlemlerini tanımlayan bir veritabanı bağlamı sınıfına eklememiz gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="01ade-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="01ade-140">`MyDbContext`Sınıfı, sınıfının erişimini ve çevirisini tanımlayan bir özelliği sağlar `Product` .</span><span class="sxs-lookup"><span data-stu-id="01ade-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="01ade-141">Uygulamanız bu sınıfı, sınıfının yönteminde aşağıdaki girişleri kullanarak veritabanıyla etkileşime yönelik olarak yapılandırır `Startup` `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="01ade-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="01ade-142">Yukarıdaki kod, belirtilen bağlantı dizesiyle bir SQL Server veritabanına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="01ade-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="01ade-143">Bağlantı dizesini *appSettings. JSON* dosyanıza, ortam değişkenlerine veya diğer yapılandırma depolama konumlarına yerleştirebilir ve bu katıştırılmış dizeyi uygun şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ade-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="01ade-144">Daha sonra aşağıdaki komutları kullanarak bu sınıf için uygun olan veritabanı tablosunu oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="01ade-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="01ade-145">İlk komut, veritabanı şemasında yaptığınız değişiklikleri, adlı yeni bir EF geçişi olarak tanımlar `Create Product table` .</span><span class="sxs-lookup"><span data-stu-id="01ade-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="01ade-146">Bir geçiş, yeni veritabanı değişikliklerinizin nasıl uygulanacağını ve kaldırılacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01ade-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="01ade-147">Uygulandıktan sonra veritabanınızda basit bir `Product` tablo ve veritabanı şemasının yönetilmesine yardımcı olan projeye eklenen bazı yeni sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="01ade-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="01ade-148">Bu oluşturulan sınıfları varsayılan olarak *geçişler*adlı yeni bir klasörde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ade-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="01ade-149">Sınıf üzerinde değişiklik yaptığınızda `Product` veya veritabanınıza etkileşimde bulunmak istediğiniz daha fazla ilgili sınıf eklediğinizde, geçiş için yeni bir adla komut satırı komutlarını yeniden çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01ade-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="01ade-150">Bu komut, veritabanı şemanızı güncelleştirmek için başka bir geçiş sınıfları kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01ade-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="01ade-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="01ade-151">EF Database First</span></span>

<span data-ttu-id="01ade-152">Mevcut veritabanları için, .NET komut satırı araçlarını kullanarak EF Core sınıfları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ade-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="01ade-153">Sınıfları kullanmak için aşağıdaki komutun bir çeşidini kullanın:</span><span class="sxs-lookup"><span data-stu-id="01ade-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="01ade-154">Önceki komut, belirtilen bağlantı dizesini ve sağlayıcıyı kullanarak veritabanına bağlanır `Microsoft.EntityFrameworkCore.SqlServer` .</span><span class="sxs-lookup"><span data-stu-id="01ade-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="01ade-155">Bağlandıktan sonra, adlı bir veritabanı bağlamı sınıfı `MyDbContext` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="01ade-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="01ade-156">Ayrıca, `Product` seçeneklerle belirtilen ve tabloları için destekleme sınıfları oluşturulur `Customer` `-t` .</span><span class="sxs-lookup"><span data-stu-id="01ade-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="01ade-157">Bu komut için, veritabanınız için uygun olan sınıf hiyerarşisini oluşturmak üzere birçok yapılandırma seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="01ade-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="01ade-158">Tüm başvurular için, [komutun belgelerine](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)bakın.</span><span class="sxs-lookup"><span data-stu-id="01ade-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="01ade-159">[EF Core](/ef/core/) hakkında daha fazla bilgi Microsoft docs sitesinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="01ade-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="01ade-160">Web hizmetleriyle etkileşim kurma</span><span class="sxs-lookup"><span data-stu-id="01ade-160">Interact with web services</span></span>

<span data-ttu-id="01ade-161">ASP.NET ilk kez yayımlandıysa, SOAP Hizmetleri Web sunucularının ve istemcilerinin verileri alışverişi için tercih edilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="01ade-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="01ade-162">Bu tarihten bu yana çok daha fazla değişti ve hizmetler ile tercih edilen etkileşimler, doğrudan HTTP istemci etkileşimlerine kaydırmıştır.</span><span class="sxs-lookup"><span data-stu-id="01ade-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="01ade-163">ASP.NET Core ve Blazor ile, yapılandırmanızı `HttpClient` `Startup` sınıfının `ConfigureServices` yöntemine kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ade-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="01ade-164">HTTP uç noktasıyla etkileşime ihtiyacınız olduğunda bu yapılandırmayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="01ade-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="01ade-165">Aşağıdaki yapılandırma kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="01ade-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="01ade-166">GitHub 'dan veriye her erişmeniz gerektiğinde, adı olan bir istemci oluşturun `github` .</span><span class="sxs-lookup"><span data-stu-id="01ade-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="01ade-167">İstemci, temel adresle yapılandırılır ve istek üst bilgileri uygun şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="01ade-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="01ade-168">`IHttpClientFactory` `@inject` Bir özelliğindeki yönergeyle veya bir özniteliğiyle Blazor bileşenlerinizi ekleyin `[Inject]` .</span><span class="sxs-lookup"><span data-stu-id="01ade-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="01ade-169">Adlandırılmış istemcinizi oluşturun ve aşağıdaki sözdizimini kullanarak hizmetlerle etkileşim kurun:</span><span class="sxs-lookup"><span data-stu-id="01ade-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="01ade-170">Bu yöntem, *DotNet/docs* GitHub deposundaki sorunların koleksiyonunu açıklayan dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="01ade-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="01ade-171">JSON biçiminde içerik döndürür ve seri durumdan uygun GitHub sorun nesnelerine seri hale gelir.</span><span class="sxs-lookup"><span data-stu-id="01ade-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="01ade-172">' Yi `HttpClientFactory` önceden yapılandırılmış nesneleri sunacak şekilde yapılandırabileceğiniz birçok yol vardır `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="01ade-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="01ade-173">`HttpClient`Birlikte çalıştığınız çeşitli Web Hizmetleri için farklı adlara ve uç noktalara sahip birden çok örnek yapılandırmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="01ade-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="01ade-174">Bu yaklaşım, bu hizmetler ile etkileşimlerinizi her sayfada birlikte çalışmaya daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="01ade-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="01ade-175">Daha fazla ayrıntı için, [ıhttpclientfactory belgelerini](/aspnet/core/fundamentals/http-requests)okuyun.</span><span class="sxs-lookup"><span data-stu-id="01ade-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="01ade-176">[Önceki](forms-validation.md) 
> [Sonraki](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="01ade-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
