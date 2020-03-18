---
title: CQRS mikro hizmetinde okuma/sorgulama işlemleri uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Dapper kullanarak eShopOnContainers sipariş microservice CQRS sorguları tarafında uygulanmasını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 235b0e471a17e2a37a883a111cf499b7837f3ea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972083"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>CQRS microservice'de okuma/sorgu uygulama

Okuma/sorgular için, eShopOnContainers başvuru uygulamasından sipariş mikrohizmeti, sorguları DDD modeli nden ve işlem alanından bağımsız olarak uygular. Bu, öncelikle sorgu ve hareketler için talepler büyük ölçüde farklı olduğundan yapıldı. Etki alanı mantığıyla uyumlu olması gereken yürütme hareketlerini yazar. Sorgular, diğer taraftan, idempotent ve etki alanı kurallarından ayrılmış olabilir.

Yaklaşım, Şekil 7-3'te gösterildiği gibi basittir. API arabirimi, Web API denetleyicileri tarafından Dapper gibi mikro Nesne İlişkisel Haritalayıcı (ORM) gibi herhangi bir altyapı kullanılarak ve Kullanıcı Arabirimi uygulamalarının gereksinimlerine bağlı olarak dinamik Görünüm Modelleri döndürülerek uygulanır.

![Basitleştirilmiş CQRS'de üst düzey sorguları gösteren diyagram.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Şekil 7-3**. CQRS microservice sorguları için en basit yaklaşım

Basitleştirilmiş bir CQRS yaklaşımında sorgu tarafı için en basit yaklaşım, veritabanını Dapper gibi bir Micro-ORM ile sorgulayarak ve dinamik Görünüm Modelleri döndürerek uygulanabilir. Sorgu tanımları veritabanını sorgular ve her sorgu için anında oluşturulmuş dinamik bir Görünüm Modeli döndürün. Sorgular iktidara geldiğinden, sorguyu kaç kez çalıştırsanız çalıştırın verileri değiştirmez. Bu nedenle, agregalar ve diğer desenler gibi işlem tarafında kullanılan herhangi bir DDD deseni ile sınırlı olması gerekmez ve bu nedenle sorgular işlem alanından ayrılır. UI'nin gereksinim duyduğu veriler için veritabanını sorgular ve SQL deyimleri dışında herhangi bir yerde statik olarak tanımlanması gerekmeyen dinamik bir Görünüm Modeli döndürür (Görünüm Modelleri için sınıf lar yoktur).

Bu basit bir yaklaşım olduğundan, sorgu tarafı için gerekli kod [(Dapper](https://github.com/StackExchange/Dapper)gibi mikro ORM kullanarak kod gibi) [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)uygulanabilir. Şekil 7-4 bunu göstermektedir. Sorgular, eShopOnContainers çözümü ndeki **Ordering.API** microservice projesinde tanımlanır.

![Ordering.API projesinin Sorgular klasörünün ekran görüntüsü.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Şekil 7-4**. eShopOnContainers sipariş microservice sorguları

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Etki alanı modeli kısıtlamalarından bağımsız olarak, istemci uygulamaları için özel olarak yapılmış ViewModels'ı kullanma

Sorgular istemci uygulamaları tarafından gerekli verileri elde etmek için gerçekleştirildiğinden, döndürülen tür sorgular tarafından döndürülen verilere dayalı olarak istemciler için özel olarak yapılabilir. Bu modeller veya Veri Aktarım Nesneleri (DTO'lar) Görünüm Modelleri olarak adlandırılır.

Döndürülen veriler (ViewModel), veritabanındaki birden çok varlık veya tablodan gelen verileri birleştirmenin veya hatta işlem alanı için etki alanı modelinde tanımlanan birden çok agreganın bir sonucu olabilir. Bu durumda, etki alanı modelinden bağımsız sorgular oluşturduğunuziçin, toplu sınırlar ve kısıtlamalar tamamen yoksayılır ve gereksinim duyabileceğiniz tablo ve sütunları sorgulamakta özgürsunuz. Bu yaklaşım, sorguları oluşturan veya güncelleştiren geliştiriciler için büyük esneklik ve üretkenlik sağlar.

Görünüm Modelleri sınıflarda tanımlanan statik türleri olabilir. Veya geliştiriciler için çok çevik olan gerçekleştirilen sorgulara (sipariş mikrohizmetinde uygulandığı gibi) dayalı olarak dinamik olarak oluşturulabilir.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Sorguları gerçekleştirmek için Dapper'ı mikro ORM olarak kullanın

Herhangi bir mikro ORM, Entity Framework Core, hatta düz ADO.NET sorgu için kullanabilirsiniz. Örnek uygulamada, Dapper popüler bir mikro ORM iyi bir örnek olarak eShopOnContainers sipariş microservice için seçildi. Çok hafif bir çerçeve olduğu için, büyük performans ile düz SQL sorguları çalıştırabilirsiniz. Dapper'ı kullanarak, birden çok tabloya erişebilen ve birleşebilen bir SQL sorgusu yazabilirsiniz.

Dapper bir açık kaynak projesidir (orijinal Sam Saffron tarafından oluşturulan), ve [Stack Overflow](https://stackoverflow.com/)kullanılan yapı taşlarının bir parçasıdır. Dapper'ı kullanmak için, aşağıdaki şekilde gösterildiği gibi, [Dapper NuGet paketi](https://www.nuget.org/packages/Dapper)aracılığıyla yüklemeniz gerekir:

![NuGet paketleri görünümünde Dapper paketinin ekran görüntüsü.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Ayrıca, kodunuzda Dapper uzantı yöntemlerine erişebilmek için bir açıklama eklemeniz gerekir.

Kodunuzda Dapper kullandığınızda, <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient> doğrudan ad alanında kullanılabilen sınıfı kullanırsınız. QueryAsync yöntemi ve <xref:System.Data.SqlClient.SqlConnection> sınıfı genişleten diğer uzantı yöntemleri sayesinde sorguları basit ve performant bir şekilde çalıştırabilirsiniz.

## <a name="dynamic-versus-static-viewmodels"></a>Dinamik ve statik Görünüm Modelleri

ViewModels'ı sunucu tarafından istemci uygulamalarına döndürrken, Görünüm Modelleri verileri istemci uygulaması gibi tuttuğundan, varlık modelinizin iç etki alanı varlıklarından farklı olabilecek DTO'lar (Veri Aktarımı Nesneleri) olarak bu Görünüm Modelleri'ni düşünebilirsiniz Ihtiyacı var. Bu nedenle, çoğu durumda, birden çok etki alanı varlığından gelen verileri toplayabilir ve ViewModels'i istemci uygulamasının bu verilere nasıl ihtiyaç duyduğuna göre tam olarak oluşturabilirsiniz.

Bu Görünüm Modelleri veya DTO'lar, daha sonraki bir `OrderSummary` kod snippet'inde gösterilen sınıf gibi açıkça (veri tutucu sınıfları olarak) tanımlanabilir veya yalnızca sorgularınızın döndürülen özniteliklerine göre dinamik Görünüm Modelleri veya dinamik DTO'ları dinamik bir tür olarak döndürebilirsiniz.

### <a name="viewmodel-as-dynamic-type"></a>Dinamik tür olarak Görünüm Modeli

Aşağıdaki kodda gösterildiği gibi, bir `ViewModel` sorgu tarafından döndürülen öznitelikleri temel alan *dinamik* bir tür yalnızca döndürülerek sorgular tarafından doğrudan döndürülebilir. Bu, döndürülecek özniteliklerin alt kümesinin sorgunun kendisine dayandığı anlamına gelir. Bu nedenle, sorguya veya birleştirmeye yeni bir sütun eklerseniz, `ViewModel`bu veriler döndürülen verilere dinamik olarak eklenir.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

Önemli nokta, dinamik bir tür kullanılarak, döndürülen veri toplamasının ViewModel olarak dinamik olarak bir araya getirilmiş olmasıdır.

**Artıları:** Bu yaklaşım, bir sorgunun SQL cümlesini güncellediğinizde statik ViewModel sınıflarını değiştirme gereksinimini azaltır ve bu tasarım yaklaşımını kodlama, basit ve gelecekteki değişikliklerle ilgili olarak hızlı bir şekilde gelişirken oldukça çevik hale getirir.

**Eksileri:** Uzun vadede, dinamik türler bir hizmetin netliğini ve istemci uygulamalarıyla uyumluluğunu olumsuz etkileyebilir. Buna ek olarak, Swashbuckle gibi ara yazılımlar dinamik türler kullanıyorsanız iade edilen türlerde aynı düzeyde belge sağlayamaz.

### <a name="viewmodel-as-predefined-dto-classes"></a>Modeli önceden tanımlanmış DTO sınıfları olarak görüntüleme

**Artıları**: Açık DTO sınıflarına dayalı "sözleşmeler" gibi statik önceden tanımlanmış ViewModel sınıflarına sahip olmak, yalnızca aynı uygulama tarafından kullanılsa bile, kamu API'leri için değil, aynı zamanda uzun vadeli mikro hizmetler için de kesinlikle daha iyidir.

Swagger için yanıt türlerini belirtmek istiyorsanız, iade türü olarak açık DTO sınıfları kullanmanız gerekir. Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger daha zengin bilgi sunmak için izin verir. Bu, BIR API tüketirken API dokümantasyonlarını ve uyumluluğu artırır.

**Eksileri**: Daha önce de belirtildiği gibi, kodu güncellerken, DTO sınıflarını güncelleştirmek için birkaç adım daha alır.

*Deneyimlerimize Dayalı İpucu*: eShopOnContainers'daki Sipariş mikrohizmetinde uygulanan sorgularda, erken geliştirme aşamalarında çok basit ve çevik olduğu için dinamik ViewModels kullanarak geliştirmeye başladık. Ancak, geliştirme stabilize edildikten sonra, API'leri yeniden düzenlemeyi ve ViewModels için statik veya önceden tanımlanmış DTO'ları kullanmayı seçtik, çünkü microservice tüketicilerinin "sözleşme" olarak kullanılan açık DTO türlerini bilmeleri daha açıktır.

Aşağıdaki örnekte, açık bir ViewModel DTO sınıfı: OrderSummary sınıfı kullanarak sorgunun verileri nasıl döndürettiğini görebilirsiniz.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber,
                  o.[OrderDate] as [date],os.[Name] as [status],
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    }
}
```

#### <a name="describe-response-types-of-web-apis"></a>Web API'lerinin yanıt türlerini açıklayın

Web API'leri ve mikro hizmetleri tüketen geliştiriciler en çok döndürülenlerle ilgilidir — özellikle yanıt türleri ve hata kodları (standart değilse). Bunlar XML yorumlarında ve veri ek açıklamalarında işlenir.

Swagger UI'da uygun belgeler olmadan, tüketici hangi türlerin döndürüldildiği veya hangi HTTP kodlarının döndürülebileceği hakkında bilgi sahibi değildir. Bu <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>sorun, swashbuckle aşağıdaki kodda gösterildiği gibi API dönüş modeli ve değerleri hakkında daha zengin bilgi üretebilir ekleyerek giderilir:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

Ancak, `ProducesResponseType` öznitelik dinamik bir tür olarak kullanamaz, ancak aşağıdaki `OrderSummary` örnekte gösterilen ViewModel DTO gibi açık türleri kullanmayı gerektirir:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Bu, açık döndürülen türlerin uzun vadede dinamik türlerden daha iyi olmasının başka bir nedenidir. Özniteliği `ProducesResponseType` kullanırken, 200, 400, vb. gibi olası HTTP hataları/kodları açısından beklenen sonucun ne olduğunu da belirtebilirsiniz.

Aşağıdaki resimde, Swagger Kullanıcı Bira'sının Yanıt Türü bilgilerini nasıl gösterdiğini görebilirsiniz.

![Sipariş API'si için Swagger U-i II sayfasının ekran görüntüsü.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Şekil 7-5**. Yanıt türlerini ve olası HTTP durum kodlarını bir Web API'sinden gösteren Swagger UI

ViewModel türlerine ve döndürülebilen olası HTTP durum kodlarına dayalı olarak bazı örnek değerlerin üzerindeki resimde görebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Veri Noktaları - Dapper, Varlık Çerçevesi ve Karma Uygulamalar (MSDN dergisi makalesi)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Önceki](eshoponcontainers-cqrs-ddd-microservice.md)
>[Sonraki](ddd-oriented-microservice.md)
