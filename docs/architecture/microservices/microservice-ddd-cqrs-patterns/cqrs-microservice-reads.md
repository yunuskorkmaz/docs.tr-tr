---
title: CQRS mikro hizmetinde okuma/sorgulama işlemleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | CQRS 'nin sorgular tarafının, Davber kullanarak eShopOnContainers 'daki sıralama mikro hizmeti üzerinde uygulanmasını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 41932122326cf4c49b9c9e2c344d2ac17da7466b
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358901"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>CQRS mikro hizmetinde okuma/sorgu uygulama

Okuma/sorgular için, eShopOnContainers başvuru uygulamasından gelen sıralama mikro hizmeti, sorguları DDD modeli ve işlem alanından bağımsız olarak uygular. Bu, öncelikle sorgular ve işlemler için talepler büyük ölçüde farklı olduğundan yapıldı. Yazar, etki alanı mantığı ile uyumlu olması gereken işlemleri yürütür. Diğer yandan sorgular, ıdempotent ve etki alanı kurallarından ayrılmış olabilir.

Şekil 7-3 ' de gösterildiği gibi yaklaşım basittir. API arabirimi, Web API denetleyicileri tarafından, kaber gibi mikro nesne Ilişkisel Eşleyici (ORM) ve Kullanıcı arabirimi uygulamalarının ihtiyaçlarına bağlı olarak dinamik Viewmodeller gibi bir altyapı kullanılarak uygulanır.

![Basitleştirilmiş CQRS 'de üst düzey sorgu-tarafı gösteren diyagram.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Şekil 7-3**. Bir CQRS mikro hizmetindeki sorgular için en basit yaklaşım

Basitleştirilmiş bir CQRS yaklaşımında sorgu tarafı için en basit yaklaşım, bir Micro-ORM gibi, dinamik ViewModel döndüren veritabanı sorgulanarak uygulanabilir. Sorgu tanımları veritabanını sorgular ve her sorgu için anında oluşturulmuş dinamik bir ViewModel döndürür. Sorgular ıdempotent olduğundan, bir sorgu kaç kez çalıştırıldıklarından bağımsız olarak verileri değiştirmez. Bu nedenle, işlem tarafında, Toplamalar ve diğer desenler gibi kullanılan DDD deseniyle kısıtlanması gerekmez ve sorguların işlem alanından ayrılması neden olur. Kullanıcı arabiriminin gerek duyduğu verilerin veritabanını sorgular ve SQL deyimlerinin kendisi hariç her yerde statik olarak tanımlanması gerekmeyen dinamik bir ViewModel (ViewModel için sınıf olmadan) döndürür.

Bu yaklaşım basit olduğundan, sorgular tarafı için gereken kod (örneğin, mikro ORM 'yi kullanan kod [gibi)](https://github.com/StackExchange/Dapper) [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)uygulanabilir. Şekil 7-4 bunu gösterir. Sorgular, eShopOnContainers çözümünde **sıralama. API** mikro hizmet projesinde tanımlanmıştır.

![Sıralama. API projesinin sorgular klasörünün ekran görüntüsü.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Şekil 7-4**. EShopOnContainers 'da sıralama mikro hizmetindeki sorgular

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Etki alanı modeli kısıtlamalarından bağımsız olarak istemci uygulamaları için özel olarak oluşturulan Viewmodeller kullanın

Sorgular, istemci uygulamaları için gereken verileri elde etmek üzere gerçekleştirildiğinden, bu tür sorgular tarafından döndürülen verilere bağlı olarak istemciler için de yapılabilir. Bu modeller veya Veri Aktarımı nesneleri (DTOs) Viewmodeller olarak adlandırılır.

Döndürülen veriler (ViewModel), veritabanındaki birden çok varlık veya tablodan ya da işlem alanı için etki alanı modelinde tanımlanan birden çok toplama arasında veri birleştirme sonucu olabilir. Bu durumda, etki alanı modelinden bağımsız sorgular oluştururken, toplamalar sınırları ve kısıtlamaları yok sayılır ve ihtiyacınız olan herhangi bir tabloyu ve sütunu sorgulayabilirsiniz. Bu yaklaşım, sorguları oluşturan veya güncelleştiren geliştiriciler için harika esneklik ve verimlilik sağlar.

Viewmodeller sınıflarda tanımlanmış statik türler olabilir (sıralama mikro hizmetinde uygulandığı gibi). Ya da geliştiriciler için çok çevik olan gerçekleştirilen sorgulara göre dinamik olarak oluşturulabilir.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Sorguları gerçekleştirmek için mikro ORM olarak kaber kullanma

Sorgulamak için herhangi bir mikro ORM, Entity Framework Core veya hatta düz ADO.NET kullanabilirsiniz. Örnek uygulamada, Gamze 'nin eShopOnContainers 'daki sıralama mikro hizmeti, popüler mikro ORM 'nin iyi bir örneği olarak seçilmiştir. Hafif bir çatı olduğundan, harika performans ile düz SQL sorguları çalıştırabilir. Kaber kullanarak, birden fazla tabloya erişebilen ve birleştiren bir SQL sorgusu yazabilirsiniz.

Kaber, açık kaynaklı bir projem (orijinal, Sam Saffron tarafından oluşturulan) ve [Stack Overflow](https://stackoverflow.com/)' de kullanılan yapı taşlarının bir parçasıdır. Kaber 'yi kullanmak için, aşağıdaki şekilde gösterildiği gibi, bunu yalnızca [kaber NuGet paketi](https://www.nuget.org/packages/Dapper)aracılığıyla yüklemeniz gerekir:

![NuGet paketleri görünümündeki kaber paketinin ekran görüntüsü.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Ayrıca, `using` kodunuzun kaber genişletme yöntemlerine erişimi olması için bir yönerge eklemeniz gerekir.

Kodunuzda kaber kullandığınızda, <xref:System.Data.SqlClient.SqlConnection> ad alanında bulunan sınıfını doğrudan kullanırsınız <xref:System.Data.SqlClient> . QueryAsync yöntemi ve sınıfı genişleten diğer uzantı yöntemleri aracılığıyla <xref:System.Data.SqlClient.SqlConnection> sorguları basit ve performanslı bir şekilde çalıştırabilirsiniz.

## <a name="dynamic-versus-static-viewmodels"></a>Dinamik ve statik Viewmodellere karşı

Sunucu tarafından istemci uygulamalarına Viewmodeller döndürürken, Viewmodeller verileri istemci uygulamasına ihtiyaç duyduğunda tutacağından, varlık modelinizin iç etki alanı varlıklarıyla farklı olabilecek bu ViewModel (Veri Aktarımı nesneleri) olarak düşünebilirsiniz. Bu nedenle, birçok durumda, birden fazla etki alanı varlıklarından gelen verileri toplayabilir ve istemci uygulamasının bu verilere nasıl ihtiyaç duyuşına göre Viewmodellerini tam olarak oluşturabilirsiniz.

Bu Viewmodeller veya DTOs, `OrderSummary` daha sonraki bir kod parçacığında gösterilen sınıf gibi açıkça (veri sahibi sınıfları olarak) tanımlanabilir. Ya da, dinamik bir tür olarak sorgularınız tarafından döndürülen özniteliklere göre dinamik Viewmodeller veya dinamik DTOs döndürebilirsiniz.

### <a name="viewmodel-as-dynamic-type"></a>Dinamik tür olarak ViewModel

Aşağıdaki kodda gösterildiği gibi, `ViewModel` yalnızca bir sorgu tarafından döndürülen öznitelikleri temel alan *dinamik* bir tür döndürerek sorgular tarafından doğrudan döndürülebilecek. Bu, döndürülecek özniteliklerin alt kümesinin sorgunun kendisini temel aldığı anlamına gelir. Bu nedenle, sorguya veya birleşime yeni bir sütun eklerseniz, bu veriler döndürülen öğesine dinamik olarak eklenir `ViewModel` .

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

Önemli nokta, dinamik bir tür kullanarak, döndürülen veri koleksiyonu, dinamik olarak ViewModel olarak toplanır.

**Uzmanları:** Bu yaklaşım, bir sorgunun SQL cümlesini her güncelleştirdiğinizde bu tasarımın, basit ve hızlı bir şekilde geliştikçe, gelecekteki değişikliklere göre gelişdiğinde çevik hale getirilmesi durumunda statik ViewModel sınıflarını değiştirme gereksinimini azaltır.

**Dezavantajlarını:** Uzun dönemde dinamik türler, istemci uygulamalarıyla bir hizmetin netliğini ve uyumluluğunu olumsuz yönde etkileyebilir. Ayrıca, swashbuckle gibi ara yazılım yazılımı, dinamik türler kullanılıyorsa döndürülen türlerde belge düzeyini sağlayamaz.

### <a name="viewmodel-as-predefined-dto-classes"></a>Önceden tanımlanmış DTO sınıfları olarak ViewModel

**Profesyonelleri**: statik, önceden tanımlanmış ViewModel sınıfları olan "sözleşmeler" gibi açık DTO sınıfları temel alan, genel API 'ler için kesinlikle daha iyidir, ancak aynı uygulama tarafından kullanılsa bile uzun vadeli mikro hizmetler için de daha iyidir.

Swagger için yanıt türleri belirtmek isterseniz, dönüş türü olarak açık DTO sınıfları kullanmanız gerekir. Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger 'dan daha zengin bilgiler sunmanıza olanak tanır. Bu, API belgelerini ve API 'YI tükettiği uyumluluğu geliştirir.

**Dezavantajların**: daha önce belirtildiği gibi, kodu güncelleştirirken, DTO sınıflarını güncelleştirmek için bazı adımlar daha fazla sürer.

*İpucu deneyimimize göre ipucu*: eShopOnContainers 'da sıralama mikro hizmetinde uygulanan sorgularda, basit ve çevik bir geliştirme aşamasında olan dinamik görünüm modellerini kullanarak geliştirmeye başladık. Ancak, geliştirme işlemi bir kez alındıktan sonra, mikro hizmetin tüketicilerinin "sözleşmeler" olarak kullanılan açık bir tür olduğunu bilmesini sağlamak için, API 'Leri yeniden oluşturmayı ve ViewModel için statik veya önceden tanımlanmış DTOs kullanmayı seçtik.

Aşağıdaki örnekte, sorgunun nasıl veri döndürünü bir açık ViewModel DTO sınıfı kullanarak görebilirsiniz: OrderSummary sınıfı.

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

#### <a name="describe-response-types-of-web-apis"></a>Web API 'lerinin yanıt türlerini açıkla

Web API 'Leri ve mikro hizmetleri kullanan geliştiriciler, özellikle yanıt türleri ve hata kodları (Standart değilse) ile ilgili olarak en iyi şekilde verilen şeydir. Yanıt türleri XML açıklamaları ve veri ek açıklamalarında işlenir.

Swagger Kullanıcı arabiriminde doğru belgeler olmadan, tüketici hangi türlerin döndürülmekte olduğunu veya hangi HTTP kodlarının döndürüleceğini bilmede değildir. Bu sorun eklenerek düzeltildiği için <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> , swashbuckle aşağıdaki kodda gösterildiği gıbı API dönüş modeli ve değerleri hakkında daha zengin bilgiler oluşturabilir:

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

Ancak, `ProducesResponseType` öznitelik bir tür olarak dinamik kullanamaz, ancak aşağıdaki örnekte gösterildiği gibi, ViewModel gibi açık türlerin kullanılmasını gerektirir `OrderSummary` :

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Bu, açık olarak döndürülen türlerin uzun dönemde dinamik türlerden daha iyi olmasının diğer bir nedenidir. `ProducesResponseType`Özniteliğini kullanırken, OLASı HTTP hatalarını/kodlarını (200, 400 vb. gibi) hangi beklenen sonucun olduğunu de belirtebilirsiniz.

Aşağıdaki görüntüde, Swagger Kullanıcı arabiriminin ResponseType bilgilerini nasıl gösterdiğini görebilirsiniz.

![Sıralama API 'SI için Swagger Kullanıcı arabirimi sayfasının ekran görüntüsü.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Şekil 7-5**. Bir Web API 'sinden yanıt türlerini ve olası HTTP durum kodlarını gösteren Swagger Kullanıcı arabirimi

Görüntüde, ViewModel türlerine ve döndürülebilecek olası HTTP durum kodlarına göre bazı örnek değerler gösterilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Veri noktaları-kaber, Entity Framework ve hibrit uygulamalar (MSDN Magazine makalesi)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Önceki](eshoponcontainers-cqrs-ddd-microservice.md) 
> [Sonraki](ddd-oriented-microservice.md)
