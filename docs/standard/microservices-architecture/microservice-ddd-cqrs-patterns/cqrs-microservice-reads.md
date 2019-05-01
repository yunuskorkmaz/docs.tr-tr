---
title: CQRS mikro hizmetinde okuma/sorgulama işlemleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Sıralama mikro hizmet Dapper kullanarak hizmetine CQRS modelinin sorguları tarafında uygulanması anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 104c7564b7dd29209b48d99b1dea7524c07d7e69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020081"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>CQRS mikro hizmetinde okuma/sorgulama uygulayın

Okuma/sorgulama için sıralama mikro hizmetine başvuru uygulamadan sorgularından bağımsız olarak işlem alan ve DDD modeli uygular. Öncelikle taleplerini sorgular ve işlemler için önemli ölçüde farklı olduğundan bu yapıldı. Yazma işlemleri, etki alanı mantığı ile uyumlu olması gereken işlemler yürütün. Sorgular, diğer taraftan, eşgüçlüdür ve etki alanı kurallardan ayrılmış.

Şekil 7-3'te gösterildiği gibi basit yaklaşımdır. API arabirimi, bir nesne ilişkisel Eşleyici (ORM) gibi Dapper, mikro gibi herhangi bir altyapının kullanarak ve kullanıcı Arabirimi uygulama gereksinimlerine bağlı olarak dinamik Viewmodel'lar döndüren Web APİ'si denetleyicilerinin tarafından uygulanır.

![Basitleştirilmiş bir CQRS yaklaşımı, sorguları tarafı için en kolay yaklaşım, veritabanı ile bir mikro-dinamik Viewmodel'lar döndüren ORM Dapper gibi sorgulayarak uygulanabilir.](./media/image3.png)

**Şekil 7-3**. CQRS mikro hizmet sorguları için en kolay yaklaşım

Sorgular için olası en kolay yaklaşım budur. Sorgu tanımları, bu veritabanını sorgulamanızı ve her bir sorgu için hareket halindeyken yerleşik dinamik bir ViewModel döndürür. Sorgular tekrar denenebilir yapıda olduğundan, bunlar bir sorgu çalıştırmadan kaç kez ne olursa olsun veri değişmez. Bu nedenle, toplamlar ve diğer desenleri gibi işlem tarafında kullanılan tüm DDD deseni tarafından kısıtlı gerekmez ve sorguları işlem alanından ayrılmış neden olmasıdır. Yalnızca kullanıcı Arabirimi gereken veriler için bu veritabanını sorgulamanızı ve statik türlü olması gerekmez dinamik bir ViewModel her yerden (sınıflar için Viewmodel'lar) dışında SQL deyimleri kendilerini tanımlanan döndürür.

Bu basit yaklaşım olduğundan, sorgu yan için gerekli kod (ORM gibi bir mikro kullanarak kod gibi [Dapper](https://github.com/StackExchange/Dapper)) uygulanabilir [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Şekil 7-4'te bu durum gösterilir. Sorguları tanımlanan **Ordering.API** hizmetine çözüm içinde mikro hizmet projesi.

![Çözüm Gezgini görünümü uygulamanın gösterildiği Ordering.API projenin > sorgular klasörüne.](./media/image4.png)

**Şekil 7-4**. Sıralama mikro hizmetine sorguları

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>İstemci uygulamaları için özel etki alanı modeli kısıtlamalardan bağımsız yapılan Viewmodel'lar kullanın

Sorgular, istemci uygulamalar için gerekli verileri almak için yapıldığından, döndürülen türü özellikle sorguları tarafından döndürülen verilere bağlı olarak, istemciler için yapılabilir. Bu modeller ya da veri aktarımı nesneleri (Dto'lar) Viewmodel'lar çağrılır.

Döndürülen veriler (ViewModel), birden çok varlıklar veya tablolar verileri veritabanında veya bile işlem alanı için etki alanı modelde tanımlanan birden çok toplamalar arasında birleştirme sonucu olabilir. Bu durumda, sorguları bağımsız olarak etki alanı modeli oluşturmakta olduğunuz çünkü toplamalar sınırları ve kısıtlamaları tamamen yoksayılır ve tüm tablo ve sütun ihtiyacınız olabilecek sorgulamak boş. Bu yaklaşım, oluşturma veya güncelleştirme sorguları geliştiriciler için büyük esneklik ve verimlilik sağlar.

Viewmodel'lar sınıflarında tanımlanan statik türler olabilir. Veya, geliştiriciler için çok Çevik olduğu (sıralama mikro hizmet içinde uygulanan gibi) gerçekleştirilen sorgularına göre dinamik olarak oluşturulabilir.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Dapper sorguları gerçekleştirmek için bir mikro ORM kullanın. 

Tüm mikro ORM, Entity Framework Core veya bile düz ADO.NET sorgulamak için kullanabilirsiniz. Örnek uygulamada Dapper sıralama mikro hizmetine popüler bir mikro ORM iyi bir örnek olarak seçilmiş. Çünkü çok açık bir çerçeve muhteşem bir performans ile düz SQL sorguları çalıştırabilirsiniz. Dapper kullanarak erişebilir ve birden çok tabloları birleştirme bir SQL sorgu yazabilirsiniz.

Dapper (Sam Saffron tarafından oluşturulan özgün) açık kaynaklı bir projedir ve kullanılan yapı taşlarını parçasıdır [Stack Overflow](https://stackoverflow.com/). Dapper kullanılacak aracılığıyla yüklemeniz yeterlidir [Dapper NuGet paketini](https://www.nuget.org/packages/Dapper)aşağıdaki şekilde gösterildiği gibi:

![VS manage NuGet paketleri görünümünde görüntülenen olarak Dapper paket.](./media/image4.1.png)

Kullanarak bir ekleme gerekir kodunuzu Dapper genişletme yöntemleri erişimi için deyimi.

Kodunuzda Dapper kullandığınızda, doğrudan kullanmanız <xref:System.Data.SqlClient.SqlConnection> sınıfı bulunan <xref:System.Data.SqlClient> ad alanı. QueryAsync yöntemi ve genişleten çakışabilecek genişletme yöntemlerine aracılığıyla <xref:System.Data.SqlClient.SqlConnection> sınıfı, yalnızca çalıştırabilirsiniz sorguları basit ve etkili bir şekilde.

## <a name="dynamic-versus-static-viewmodels"></a>Dinamik görünümler ve Viewmodel'lar statik

Viewmodel'lar istemci uygulamaları için sunucu tarafı döndürülürken, istemci uygulamanın bu Viewmodel'lar hakkında Viewmodel'lar veri yolu değiştiğinden, varlık model iç etki alanı varlıklarının farklı olabilir Dto'lar (veri aktarımı nesneleri) düşünebilirsiniz gerekir. Bu nedenle, çoğu durumda, birden çok etki alanı varlıklardan gelen veri toplama ve istemci uygulamanın bu verilere nasıl gerekir tam olarak göre Viewmodel'lar oluşturun.

Bu Viewmodel'lar veya Dto'lar (verilerin sahibi sınıflar) olarak açıkça gibi tanımlanabilir `OrderSummary` sınıfı bir sonraki kod parçacığı veya, gösterilen dinamik Viewmodel'lar veya yalnızca dinamik, sorgu tarafından döndürülen öznitelikleri temel alan dinamik Dto'lar yalnızca döndürebilir yazın.

### <a name="viewmodel-as-dynamic-type"></a>Dinamik tür olarak ViewModel

Aşağıdaki kodda gösterildiği gibi bir `ViewModel` yalnızca döndüren sorgular tarafından doğrudan döndürülebilir bir *dinamik* dahili olarak bir sorgu tarafından döndürülen öznitelikleri temel alan türü. Döndürülecek öznitelik alt kümesinden sorguyu temel alan, anlamına gelir. Birleştirme ve sorgu için yeni bir sütun ekleyin, bu nedenle, bu verileri dinamik ise döndürülen eklenen `ViewModel`.

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

Dinamik tür kullanarak, döndürülen verilerin toplanmasını dinamik olarak ViewModel derlendiğinden emin önemli noktasıdır.

**Uzmanları:** Bu yaklaşım, bu tasarım yaklaşımı oldukça kodlama, Çevik, basit ve hızlı in regard to gelecek değişiklikler geliştirilebilen yapmadan bir sorgunun SQL cümlenin güncelleştirdiğinizde statik ViewModel sınıfları değiştirmek için gereksinimini azaltır.

**Cons:** Uzun vadede açıklık ve uyumluluk bir hizmetin istemci uygulamaları ile dinamik türleri olumsuz yönde etkileyebilir. Buna ek olarak, Swashbuckle gibi ara yazılım belgeleri aynı düzeyde döndürülen türleri üzerinde dinamik türleri kullanıyorsanız sağlayamaz.

### <a name="viewmodel-as-predefined-dto-classes"></a>Önceden tanımlanmış DTO sınıflar olarak ViewModel

**Uzmanları**: Yalnızca aynı uygulama tarafından kullanılan bile "Sözleşme" açık DTO sınıflarında dayanan storsimple çözümü gibi statik önceden tanımlanmış ViewModel sınıfları sahip kesinlikle de uzun vadeli mikro hizmetler, ortak API'ler için iyidir.

Yanıt türleri için Swagger belirtmek istiyorsanız, dönüş türü olarak açık DTO sınıfları kullanmanız gerekir. Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger'a daha zengin bilgi sunan olanak sağlar. API belgeleri ve uyumluluğu API tüketildiğinde geliştiren.

**Cons**: Kod güncelleştirilirken daha önce belirtildiği gibi bazı daha fazla adım DTO sınıfları güncelleştirmek için alır.

*İpucu deneyimimizi üzerinde temel*: Sorgularda sıralama mikro hizmetine sırasında uygulanan çok kolay ve Çevik erken geliştirme aşamalarına üzerinde dinamik Viewmodel'lar kullanarak geliştirme Başladık. Ancak, geliştirme istikrarlı sonra "Sözleşme" kullanılan, açık DTO türleri bilmek mikro hizmet'ın Tüketiciler için nettir API'leri yeniden düzenleyin ve Viewmodel'lar için statik ya da önceden tanımlanmış bir Dto seçtik çünkü.

Aşağıdaki örnekte, bir açık ViewModel DTO sınıfını kullanarak sorgu verilerini nasıl döndürmektir görebilirsiniz: OrderSummary sınıfı.

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
            var result = await connection.QueryAsync<OrderSummary>(
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

#### <a name="describe-response-types-of-web-apis"></a>Web API yanıt türleri açıklanmaktadır

Kullanan geliştiriciler web API'leri ve mikro hizmetler hangi iade ile en ilgili — özellikle yanıt türleri ve hata kodları (standart varsa). Bunlar, XML açıklamaları ve verileri ek açıklamalar içinde işlenir.

Swagger kullanıcı arabirimini uygun belgelerinde tüketici bilgi eksik hangi tür döndürülen veya hangi HTTP kodları döndürülebilir. Ekleyerek bu sorun düzeltilene <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, Swashbuckle aşağıdaki kodda gösterildiği gibi değerleri ve API dönüş modeli hakkında daha zengin bilgi oluşturabilirsiniz:

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

Ancak, `ProducesResponseType` açık türleri gibi kullanmak için bir tür ancak gerektirdiği özniteliği dinamik kullanamaz `OrderSummary` ViewModel DTO, aşağıdaki örnekte gösterilen:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Açık döndürülen türleri ve uzun vadede dinamik türlerinden daha iyi neden başka bir nedeni budur. Kullanırken `ProducesResponseType` özniteliği, ilgili olası HTTP hataları/kodları, beklenen sonucu gibi nedir belirtebilirsiniz 200, 400, vs.

Aşağıdaki görüntüde, Swagger kullanıcı arabirimini ResponseType bilgileri gösterilmektedir görebilirsiniz.

![Swagger kullanıcı arabirimini sayfasının tarayıcı görünümünü sıralama API.](./media/image5.png)

**Şekil 7-5**. Swagger kullanıcı Arabirimi yanıt türleri ve olası HTTP durum kodları, bir Web API'si gösteriliyor

ViewModel türüne ek olarak döndürülebilecek olası HTTP durum kodları hakkında temel bazı örnek değerler yukarıdaki görüntüde görebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Dapper** \
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Veri noktaları - Dapper, Entity Framework ve karma uygulamalar (MSDN Mag. makalesi)** \
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- **ASP.NET Core Web API'si Swagger kullanan Yardım sayfaları** \
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Önceki](eshoponcontainers-cqrs-ddd-microservice.md)
>[İleri](ddd-oriented-microservice.md)
