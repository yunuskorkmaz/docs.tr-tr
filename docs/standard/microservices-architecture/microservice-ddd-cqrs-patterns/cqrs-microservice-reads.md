---
title: Uygulama okuma/CQRS mikro hizmet sorguları
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulama okuma/CQRS mikro hizmet sorguları
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.openlocfilehash: 8eca01acc2308097d1684be8bdb0f07edd86832f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579112"
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Uygulama okuma/CQRS mikro hizmet sorguları

Okuma/sorguları, sıralama mikro hizmet eShopOnContainers başvuru uygulamadan sorgularından bağımsız olarak DDD modelini ve işlem alanı uygular. Öncelikle taleplerini sorgular ve işlemler için önemli ölçüde farklı olduğu için bu gerçekleştirilir. Yazma etki alanı mantığı ile uyumlu olması gereken işlemleri yürütün. Sorguları, diğer yandan ıdempotent olan ve etki alanı kurallardan yinelenmeli.

Şekil 9-3'te gösterildiği gibi bir yaklaşım basittir. API Arabirimi mikro nesne ilişkisel Eşleyici (ORM) Dapper gibi gibi herhangi bir altyapı kullanarak ve kullanıcı Arabirimi uygulamalarını gereksinimlerine bağlı olarak dinamik ViewModels döndüren Web API denetleyicilerinin tarafından uygulanır.

![](./media/image3.png)

**Şekil 9-3**. CQRS mikro hizmet sorguları için en kolay yaklaşım

Bu mod sorguları için en basit olası yaklaşımdır. Sorgu tanımları veritabanını sorgulamak ve her sorgu için kolay bir şekilde yerleşik dinamik bir ViewModel döndürür. Sorguları ıdempotent olduğundan, bunlar bir sorgu çalıştırmadan kaç kez olsun verileri değiştirmez. Bu nedenle, işlem tarafındaki toplamalar ve diğer desenleri gibi kullanılan herhangi bir DDD modeliyle tarafından kısıtlanmış gerek yoktur ve sorguları işlem alanından ayrılmış neden. Yalnızca kullanıcı arabirimini gereken veriler için veritabanını sorgulamak ve statik olarak olması gerekmez dinamik bir ViewModel her yerden (sınıflar ViewModels için) dışındaki SQL deyimlerini kendilerini tanımlanan döndürür.

Bu basit bir yaklaşım olduğuna göre sorguları tarafı için gerekli kod (ORM gibi bir mikro kullanarak kod gibi [Dapper](https://github.com/StackExchange/Dapper)) uygulanabilir [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Şekil 9-4 bu gösterir. Sorguları tanımlanan **Ordering.API** eShopOnContainers çözümünde mikro hizmet projesi.

![](./media/image4.png)

**Şekil 9-4**. Sıralama mikro hizmet eShopOnContainers içinde sorguları

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>İstemci uygulamaları, etki alanı modeli kısıtlamaları bağımsız için özellikle yapılan ViewModels kullanma

İstemci uygulamaları tarafından gereken verileri almak için sorgular gerçekleştirilen olduğundan, döndürülen tür özellikle sorguları tarafından döndürülen verileri temel alan istemciler için yapılabilir. Bu modeller ya da veri aktarım nesneleri (DTOs) ViewModels denir.

Döndürülen veriler (ViewModel) birden çok varlık veya tablo verileri veritabanında veya bile işlem alanı için etki alanı modelinde tanımlanan birden çok toplamalar arasında birleştirme sonucu olabilir. Bu durumda, sorguları etki alanı modeli bağımsız oluşturmakta olduğunuz çünkü toplamalar sınırları ve kısıtlamaları tamamen yoksayılır ve tüm tablo ve sütun gereksinim duyabileceğiniz sorgu boş. Bu yaklaşım, oluşturma veya güncelleştirme sorguları geliştiriciler için büyük esneklik ve verimlilik sağlar.

ViewModels sınıflarda tanımlanan statik türler olabilir. Ya da yöneticiler geliştiricileri için çok Çevik olduğu (sıralama mikro hizmet içinde uygulanan gibi) gerçekleştirilecek sorgularına göre dinamik olarak oluşturulabilir.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Sorguları gerçekleştirmek için Dapper mikro ORM kullanma

Tüm mikro ORM, Entity Framework Çekirdek ya da bile düz ADO.NET sorgulamak için kullanabilirsiniz. Örnek uygulama Dapper eShopOnContainers popüler mikro ORM iyi bir örnek olarak, sipariş mikro hizmet için seçilmedi. Çok açık bir çerçeve olduğu için harika performans ile düz SQL sorguları çalıştırabilirsiniz. Dapper kullanarak, erişebilir ve birden çok tabloyu birleştirme bir SQL sorgu yazabilirsiniz.

Dapper açık kaynaklı proje (Sam Saffron tarafından oluşturulan özgün) ve kullanılan yapı taşları parçası olan [yığın taşması](https://stackoverflow.com/). Dapper kullanmak için aracılığıyla yüklemeniz yeterlidir [Dapper NuGet paketi](https://www.nuget.org/packages/Dapper), aşağıdaki çizimde gösterildiği gibi:

![](./media/image4.1.png)

Ayrıca kullanarak bir eklemeniz gerekir, kodunuzu Dapper genişletme yöntemleri erişimi şekilde deyimi.

Kodunuzda Dapper kullandığınızda, doğrudan kullanmanız <xref:System.Data.SqlClient.SqlConnection> sınıfı bulunan <xref:System.Data.SqlClient> ad alanı. QueryAsync yöntemi ve genişletmek diğer genişletme yöntemleri aracılığıyla <xref:System.Data.SqlClient.SqlConnection> sınıfı, yalnızca çalıştırabilirsiniz sorguları basit ve kullanıcı bir biçimde.

## <a name="dynamic-versus-static-viewmodels"></a>Dinamik statik ViewModels karşılaştırması

ViewModels istemci uygulamaları için sunucu tarafı döndürülürken bu ViewModels hakkında ViewModels tutma veri yolu istemci uygulaması gerektiğinden, varlık modeli iç etki alanının varlıklara farklı olabilir DTOs düşünebilirsiniz. Bu nedenle, çoğu durumda, birden çok etki alanı varlıklardan gelen veri toplama ve istemci uygulamanın verilerin nasıl gerekir göre tam olarak ViewModels oluşturun.

Bu ViewModels veya DTOs (olarak veri sahibi sınıfları) açıkça gibi tanımlanabilir [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) bir sonraki kod parçacığını veya, içinde gösterilen sınıfı yalnızca dinamik ViewModels veya dönen yalnızca döndürülen özniteliklerini temel alarak dinamik DTOs sorgularınızın tarafından olarak bir `dynamic` türü.

### <a name="viewmodel-as-dynamic-type"></a>Dinamik tür olarak ViewModel

Aşağıdaki kodda gösterildiği gibi bir ViewModel doğrudan sorgular tarafından dahili olarak bir sorgu tarafından döndürülen özniteliklerinin dayanır dinamik bir tür döndürerek döndürülebilir. Döndürülecek öznitelik alt sorguyu temel alan anlamına gelir. Bu nedenle, birleştirme ve sorgu için yeni bir sütun eklerseniz, bu verileri döndürülen ViewModel dinamik olarak eklenir.

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

Dinamik tür kullanarak, döndürülen verilerin toplanmasını dinamik ViewModel derlendiğinden emin önemli noktasıdır.

*Uzmanları:* bu yaklaşım kodlama, kolay ve hızlı in regard to gelecekteki değişiklikler gelişmesi bu tasarım yaklaşımı oldukça Çevik yaparak bir sorgu SQL cümle güncelleştirdiğinizde statik ViewModel sınıflarını değiştirmek için gereksinimini azaltır.

*Cons:* uzun vadede dinamik türleri netlik olumsuz ve bir hizmetin istemci uygulamaları ile uyumluluk etkileyebilir. Ayrıca, ara yazılımı Swagger gibi belgeleri aynı düzeyde döndürülen türlerinde dinamik türleri kullanıyorsanız sağlayamaz.

### <a name="viewmodel-as-predefined-dto-classes"></a>Önceden tanımlanmış DTO sınıflar olarak ViewModel

*Uzmanları:* "Sözleşme" açık DTO sınıfları esas alarak gibi statik önceden tanımlanmış ViewModel sınıfların olması için ortak API'ler de uzun vadeli mikro kesinlikle daha iyi yalnızca aynı uygulama tarafından kullanılan olsa bile.

Swagger için yanıt türlerini belirtmek istiyorsanız, dönüş türü olarak açık DTO sınıfları kullanması gerekir. Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger daha zengin bilgi sunmanızı izin verin. Bu API belgelerine ve uyumluluk bir API kullanırken artırır.

*Cons:* kodu güncelleştirirken daha önce belirtildiği gibi DTO sınıfları güncelleştirmek için daha fazla bazı adımlar alır.

*İpucu dayalı üzerinde deneyimi bizim:* eShopOnContainers içinde sıralama mikro hizmet sırasında uygulanan sorgularda biz çok basit ve Çevik üzerinde erken geliştirme aşamaları gibi dinamik ViewModels kullanarak geliştirme başlatıldı. Ancak, geliştirme sabitlendi sonra "Sözleşme" kullanılan açık DTO türleri bilmeniz mikro 's tüketicileri nettir çünkü API'leri yeniden düzenlemeniz ve statik veya önceden tanımlanmış DTOs ViewModels için kullanmak seçtik.

Aşağıdaki örnekte, açık bir ViewModel DTO sınıfını kullanarak sorgu verileri nasıl döndürmektir görebilirsiniz: OrderSummary sınıfı.

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
            var result = await connection.QueryAsync<dynamic>(
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

#### <a name="describing-response-types-of-web-apis"></a>Web API'leri yanıt türlerini açıklayan

Tüketen geliştiricilerin web API'ler ve mikro ne döndürülen ile en ilgili — özellikle yanıt türleri ve hata kodları (değil standart değilse). Bunlar XML açıklamaları ve veri ek açıklamaları işlenir.

Swagger kullanıcı arabirimini uygun belgelerinde tüketici bilgi eksik hangi tür döndürülen veya hangi HTTP kodları döndürülebilir. Ekleyerek bu sorun düzeltilene <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, Swagger API dönüş modeli ve değerleri hakkında daha zengin bilgi aşağıdaki kodda gösterildiği gibi oluşturabilirsiniz:

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
           var orderTask = _orderQueries.GetOrdersAsync();
           var orders = await orderTask;
           return Ok(orders);
        }
    }
}
```

Ancak, `ProducesResponseType` açık türleri gibi kullanmak için bir tür ancak gerektirdiğinden özniteliği dinamik kullanamaz `OrderSummary` ViewModel DTO, aşağıdaki örnekte gösterilen:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

Açık döndürülen türleri uzun vadede dinamik türlerinden daha iyi neden başka bir neden de budur.
Kullanırken `ProducesResponseType` özniteliği, beklenen sonucu nedir belirtebilirsiniz 200,400 gibi bakımından olası HTTP hataları/kodları, vb.

Aşağıdaki görüntüde, Swagger kullanıcı arabirimini ResponseType bilgileri nasıl gösterir görebilirsiniz.

![](./media/image5.png)

**Şekil 9-5**. Swagger kullanıcı Arabirimi yanıt türleri ve olası HTTP durum kodları Web API öğesinden gösterme

ViewModel türleri artı döndürülebilecek olası HTTP durum kodları temel bazı örnek değerler yukarıda görüntüsünde görebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Veri noktaları - Dapper, Entity Framework ve karma uygulamalar (MSDN Mag. makalesi)**

    *https://msdn.microsoft.com/magazine/mt703432.aspx*

-   **Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**

    *https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*

>[!div class="step-by-step"]
[Önceki] (eshoponcontainers-cqrs-bbb-microservice.md) [sonraki] (bbb-yönelimli-microservice.md)
