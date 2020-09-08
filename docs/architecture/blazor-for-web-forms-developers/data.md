---
title: Veri erişimi ve yönetimi
description: ASP.NET Web Forms ve içindeki verilere erişme ve verileri işleme hakkında bilgi edinin Blazor .
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 09/08/2020
ms.openlocfilehash: 84e12f9890351fa46cd7ed0ee31db449f3c55e59
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515858"
---
# <a name="work-with-data"></a>Verilerle çalışma

Veri erişimi, bir ASP.NET Web Forms uygulamasının omurgası olur. Web için form oluşturuyorsanız, bu verilere ne olur? Web Forms ile, bir veritabanıyla etkileşim kurmak için kullanabileceğiniz birden fazla veri erişim tekniği vardı:

- Data Sources
- ADO.NET
- Varlık Çerçevesi

Veri kaynakları, Web Forms bir sayfada yerleştirebileceğiniz ve diğer denetimler gibi yapılandırabileceğiniz denetimleridir. Visual Studio, denetimleri Web Forms sayfalarınıza yapılandırmak ve bağlamak için kolay bir iletişim kutusu kümesi sağladı. Bir "düşük kod" veya "kod yok" yaklaşımı yaşayan geliştiriciler Web Forms ilk kez yayınlandığında bu tekniği tercih edilir.

![Data Sources](media/data/datasources.png)

ADO.NET, bir veritabanıyla etkileşime geçmek için düşük düzeyli yaklaşımdır. Uygulamalarınız, etkileşim kurmak için komutlarla, kayıt kümeleriyle ve veri kümeleriyle veritabanıyla bir bağlantı oluşturabilir. Sonuçlar daha sonra çok kod olmadan ekrandaki alanlara bağlanabilir. Bu yaklaşımın dezavantajı, her bir ADO.NET nesneleri ( `Connection` , `Command` ve `Recordset` ) kümesinin bir veritabanı satıcısı tarafından sunulan kitaplıklara bağlıydı. Bu bileşenlerin kullanımı, kodu rigıd yaptı ve farklı bir veritabanına geçiş yapılmasını zorlaştırıyor.

## <a name="entity-framework"></a>Varlık Çerçevesi

Entity Framework (EF), .NET Foundation tarafından tutulan açık kaynaklı nesne ilişkisel eşleme çerçevesidir. Başlangıçta .NET Framework ile yayınlanan EF, veritabanı bağlantıları, depolama şemaları ve etkileşimler için kod üretmesine olanak tanır. Bu Soyutlamalarla, uygulamanızın iş kurallarına odaklanarak veritabanının güvenilir bir veritabanı yöneticisi tarafından yönetilmesine izin verebilirsiniz. .NET Core 'da, EF Core adlı ve güncelleştirilmiş bir EF sürümü kullanabilirsiniz. EF Core, komut satırı aracını kullanarak, kodunuz ve veritabanı arasındaki etkileşimleri, sizin için kullanabileceğiniz bir dizi komutla oluşturup sürdürmenize yardımcı olur `dotnet ef` . Bir veritabanı ile çalışmaya başlamanızı sağlamak için birkaç örnek göz atalım.

### <a name="ef-code-first"></a>EF Code First

Veritabanı etkileşimlerinizi oluşturmaya başlamak için hızlı bir yol, birlikte çalışmak istediğiniz sınıf nesneleriyle başlamadır. EF, sınıflarınız için uygun veritabanı kodu oluşturmaya yardımcı olacak bir araç sağlar. Bu yaklaşım, "Code First" geliştirmesi olarak adlandırılır. `Product`Microsoft SQL Server gibi bir ilişkisel veritabanında depolamak istediğimiz örnek bir storefront uygulaması için aşağıdaki sınıfı göz önünde bulundurun.

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

Ürünün, veritabanımızda oluşturulacak bir birincil anahtarı ve üç ek alanı vardır:  

- EF `Id` özelliği kural tarafından birincil anahtar olarak tanımlanacaktır.
- `Name` , metin depolaması için yapılandırılmış bir sütunda depolanacak. `[Required]`Bu özelliği dekorasyon özniteliği, `not null` özelliğin bu tanımlanmış davranışının zorlanmasını sağlamaya yardımcı olmak için bir kısıtlama ekler.
- `Description` , metin depolaması için yapılandırılmış bir sütunda depolanacak ve özniteliği tarafından dikte edilen en fazla 4000 karakter uzunluğunda olmalıdır `[MaxLength]` . Veritabanı şeması, veri türü kullanılarak adlı bir sütunla yapılandırılacaktır `MaxLength` `varchar(4000)` .
- `Price`Özelliği para birimi olarak depolanır. `[Range]`Özniteliği, veri depolamayı belirtilen en düşük ve en yüksek değerler dışında engellemek için uygun kısıtlamalar oluşturacaktır.

Bu `Product` sınıfı, veritabanı ile bağlantı ve çeviri işlemlerini tanımlayan bir veritabanı bağlamı sınıfına eklememiz gerekiyor.

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

`MyDbContext`Sınıfı, sınıfının erişimini ve çevirisini tanımlayan bir özelliği sağlar `Product` .  Uygulamanız bu sınıfı, sınıfının yönteminde aşağıdaki girişleri kullanarak veritabanıyla etkileşime yönelik olarak yapılandırır `Startup` `ConfigureServices` :

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

Yukarıdaki kod, belirtilen bağlantı dizesiyle bir SQL Server veritabanına bağlanır. Bağlantı dizesini dosya, ortam değişkenleri veya diğer yapılandırma depolama konumlarına *appsettings.js* yerleştirebilir ve bu katıştırılmış dizeyi uygun şekilde değiştirebilirsiniz.

Daha sonra aşağıdaki komutları kullanarak bu sınıf için uygun olan veritabanı tablosunu oluşturabilirsiniz:

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

İlk komut, veritabanı şemasında yaptığınız değişiklikleri, adlı yeni bir EF geçişi olarak tanımlar `Create Product table` .  Bir geçiş, yeni veritabanı değişikliklerinizin nasıl uygulanacağını ve kaldırılacağını tanımlar.

Uygulandıktan sonra veritabanınızda basit bir `Product` tablo ve veritabanı şemasının yönetilmesine yardımcı olan projeye eklenen bazı yeni sınıflar vardır.  Bu oluşturulan sınıfları varsayılan olarak *geçişler*adlı yeni bir klasörde bulabilirsiniz.  Sınıf üzerinde değişiklik yaptığınızda `Product` veya veritabanınıza etkileşimde bulunmak istediğiniz daha fazla ilgili sınıf eklediğinizde, geçiş için yeni bir adla komut satırı komutlarını yeniden çalıştırmanız gerekir.  Bu komut, veritabanı şemanızı güncelleştirmek için başka bir geçiş sınıfları kümesi oluşturur.

### <a name="ef-database-first"></a>EF Database First

Mevcut veritabanları için, .NET komut satırı araçlarını kullanarak EF Core sınıfları oluşturabilirsiniz. Sınıfları kullanmak için aşağıdaki komutun bir çeşidini kullanın:

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

Önceki komut, belirtilen bağlantı dizesini ve sağlayıcıyı kullanarak veritabanına bağlanır `Microsoft.EntityFrameworkCore.SqlServer` . Bağlandıktan sonra, adlı bir veritabanı bağlamı sınıfı `MyDbContext` oluşturulur. Ayrıca, `Product` seçeneklerle belirtilen ve tabloları için destekleme sınıfları oluşturulur `Customer` `-t` . Bu komut için, veritabanınız için uygun olan sınıf hiyerarşisini oluşturmak üzere birçok yapılandırma seçeneği vardır. Tüm başvurular için, [komutun belgelerine](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)bakın.

[EF Core](/ef/core/) hakkında daha fazla bilgi Microsoft docs sitesinde bulunabilir.

## <a name="interact-with-web-services"></a>Web hizmetleriyle etkileşim kurma

ASP.NET ilk kez yayımlandıysa, SOAP Hizmetleri Web sunucularının ve istemcilerinin verileri alışverişi için tercih edilen yoldur. Bu tarihten bu yana çok daha fazla değişti ve hizmetler ile tercih edilen etkileşimler, doğrudan HTTP istemci etkileşimlerine kaydırmıştır. ASP.NET Core ve ile Blazor , `HttpClient` `Startup` sınıfının yapılandırmasını sınıfının yöntemine kaydedebilirsiniz `ConfigureServices` . HTTP uç noktasıyla etkileşime ihtiyacınız olduğunda bu yapılandırmayı kullanın. Aşağıdaki yapılandırma kodunu göz önünde bulundurun:

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

GitHub 'dan veriye her erişmeniz gerektiğinde, adı olan bir istemci oluşturun `github` . İstemci, temel adresle yapılandırılır ve istek üst bilgileri uygun şekilde ayarlanır. `IHttpClientFactory` Blazor `@inject` Bir özelliğindeki yönergeyle veya bir öznitelikle birlikte bileşenlerinizi ekleyin `[Inject]` . Adlandırılmış istemcinizi oluşturun ve aşağıdaki sözdizimini kullanarak hizmetlerle etkileşim kurun:

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = await response.Content.ReadAsStringAsync();
    }
}
```

Bu yöntem, *DotNet/docs* GitHub deposundaki sorunların koleksiyonunu açıklayan dizeyi döndürür. JSON biçiminde içerik döndürür ve seri durumdan uygun GitHub sorun nesnelerine seri hale gelir. ' Yi `HttpClientFactory` önceden yapılandırılmış nesneleri sunacak şekilde yapılandırabileceğiniz birçok yol vardır `HttpClient` . `HttpClient`Birlikte çalıştığınız çeşitli Web Hizmetleri için farklı adlara ve uç noktalara sahip birden çok örnek yapılandırmayı deneyin. Bu yaklaşım, bu hizmetler ile etkileşimlerinizi her sayfada birlikte çalışmaya daha kolay hale getirir. Daha fazla ayrıntı için, [ıhttpclientfactory belgelerini](/aspnet/core/fundamentals/http-requests)okuyun.

>[!div class="step-by-step"]
>[Önceki](forms-validation.md) 
> [Sonraki](middleware.md)
