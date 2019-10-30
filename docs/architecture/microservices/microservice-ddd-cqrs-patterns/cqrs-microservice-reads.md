---
title: CQRS mikro hizmetinde okuma/sorgulama işlemleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | CQRS 'nin sorgular tarafının, Davber kullanarak eShopOnContainers 'daki sıralama mikro hizmeti üzerinde uygulanmasını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 6541a0cb7ce8ac3946e119483308d91158bdb522
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094061"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="f16b0-103">CQRS mikro hizmetinde okuma/sorgu uygulama</span><span class="sxs-lookup"><span data-stu-id="f16b0-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="f16b0-104">Okuma/sorgular için, eShopOnContainers başvuru uygulamasından gelen sıralama mikro hizmeti, sorguları DDD modeli ve işlem alanından bağımsız olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="f16b0-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="f16b0-105">Bu, öncelikle sorgular ve işlemler için talepler büyük ölçüde farklı olduğundan yapıldı.</span><span class="sxs-lookup"><span data-stu-id="f16b0-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="f16b0-106">Yazar, etki alanı mantığı ile uyumlu olması gereken işlemleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="f16b0-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="f16b0-107">Diğer yandan sorgular, ıdempotent ve etki alanı kurallarından ayrılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="f16b0-108">Şekil 7-3 ' de gösterildiği gibi yaklaşım basittir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="f16b0-109">API arabirimi, Web API denetleyicileri tarafından, kaber gibi mikro nesne Ilişkisel Eşleyici (ORM) ve Kullanıcı arabirimi uygulamalarının ihtiyaçlarına bağlı olarak dinamik Viewmodeller gibi bir altyapı kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Basitleştirilmiş bir CQRS yaklaşımında bulunan sorgular-tarafı için en basit yaklaşım, yalnızca bir Micro-ORM gibi, dinamik ViewModel döndüren veritabanı sorgulanarak uygulanabilir.](./media/image3.png)

<span data-ttu-id="f16b0-111">**Şekil 7-3**.</span><span class="sxs-lookup"><span data-stu-id="f16b0-111">**Figure 7-3**.</span></span> <span data-ttu-id="f16b0-112">Bir CQRS mikro hizmetindeki sorgular için en basit yaklaşım</span><span class="sxs-lookup"><span data-stu-id="f16b0-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="f16b0-113">Bu, sorgular için mümkün olan en basit yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="f16b0-114">Sorgu tanımları veritabanını sorgular ve her sorgu için anında oluşturulmuş dinamik bir ViewModel döndürür.</span><span class="sxs-lookup"><span data-stu-id="f16b0-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="f16b0-115">Sorgular ıdempotent olduğundan, bir sorgu kaç kez çalıştırıldıklarından bağımsız olarak verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="f16b0-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="f16b0-116">Bu nedenle, işlem tarafında, Toplamalar ve diğer desenler gibi kullanılan DDD deseniyle kısıtlanması gerekmez ve sorguların işlem alanından ayrılması neden olur.</span><span class="sxs-lookup"><span data-stu-id="f16b0-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="f16b0-117">Yalnızca Kullanıcı arabiriminin gerek duyduğu verilerin veritabanını sorgular ve SQL deyimlerinin kendisi hariç her yerde statik olarak tanımlanması gerekmeyen dinamik bir ViewModel (ViewModel için sınıf olmadan) döndürür.</span><span class="sxs-lookup"><span data-stu-id="f16b0-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="f16b0-118">Bu basit bir yaklaşım olduğundan, sorgular tarafı için gereken kod (örneğin, mikro ORM 'yi kullanan kod [gibi)](https://github.com/StackExchange/Dapper) [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="f16b0-119">Şekil 7-4 bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="f16b0-120">Sorgular, eShopOnContainers çözümünde **sıralama. API** mikro hizmet projesinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Uygulama > sorguları klasörünü gösteren sıralama. API projesinin Çözüm Gezgini görünümü.](./media/image4.png)

<span data-ttu-id="f16b0-122">**Şekil 7-4**.</span><span class="sxs-lookup"><span data-stu-id="f16b0-122">**Figure 7-4**.</span></span> <span data-ttu-id="f16b0-123">EShopOnContainers 'da sıralama mikro hizmetindeki sorgular</span><span class="sxs-lookup"><span data-stu-id="f16b0-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="f16b0-124">Etki alanı modeli kısıtlamalarından bağımsız olarak istemci uygulamaları için özel olarak oluşturulan Viewmodeller kullanın</span><span class="sxs-lookup"><span data-stu-id="f16b0-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="f16b0-125">Sorgular, istemci uygulamaları için gereken verileri elde etmek üzere gerçekleştirildiğinden, bu tür sorgular tarafından döndürülen verilere bağlı olarak istemciler için de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="f16b0-126">Bu modeller veya Veri Aktarımı nesneleri (DTOs) Viewmodeller olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="f16b0-127">Döndürülen veriler (ViewModel), veritabanındaki birden çok varlık veya tablodan ya da işlem alanı için etki alanı modelinde tanımlanan birden çok toplama arasında veri birleştirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="f16b0-128">Bu durumda, etki alanı modelinden bağımsız sorgular oluştururken, toplamalar sınırları ve kısıtlamaları tamamen yok sayılır ve ihtiyacınız olan herhangi bir tabloyu ve sütunu sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="f16b0-129">Bu yaklaşım, sorguları oluşturan veya güncelleştiren geliştiriciler için harika esneklik ve verimlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16b0-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="f16b0-130">Viewmodeller sınıflarda tanımlanmış statik türler olabilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="f16b0-131">Ya da geliştiriciler için çok çevik olan, gerçekleştirilen sorgulara göre dinamik olarak oluşturulabilir (sıralama mikro hizmetinde uygulandığı gibi).</span><span class="sxs-lookup"><span data-stu-id="f16b0-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="f16b0-132">Sorguları gerçekleştirmek için mikro ORM olarak kaber kullanma</span><span class="sxs-lookup"><span data-stu-id="f16b0-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="f16b0-133">Sorgulamak için herhangi bir mikro ORM, Entity Framework Core veya hatta düz ADO.NET kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="f16b0-134">Örnek uygulamada, Gamze 'nin eShopOnContainers 'daki sıralama mikro hizmeti, popüler mikro ORM 'nin iyi bir örneği olarak seçilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="f16b0-135">Çok hafif bir çerçeve olduğundan, harika performans ile düz SQL sorguları çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="f16b0-136">Kaber kullanarak, birden fazla tabloya erişebilen ve birleştiren bir SQL sorgusu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="f16b0-137">Kaber, açık kaynaklı bir projem (orijinal, Sam Saffron tarafından oluşturulan) ve [Stack Overflow](https://stackoverflow.com/)' de kullanılan yapı taşlarının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="f16b0-138">Kaber 'yi kullanmak için, aşağıdaki şekilde gösterildiği gibi, bunu yalnızca [kaber NuGet paketi](https://www.nuget.org/packages/Dapper)aracılığıyla yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="f16b0-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![VS 'de NuGet paketlerini yönet görünümünde görüntülenen kaber paketi.](./media/image4.1.png)

<span data-ttu-id="f16b0-140">Kodunuzun kaber genişletme yöntemlerine erişimi olması için using ifadesini de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="f16b0-141">Kodunuzda kaber kullandığınızda, <xref:System.Data.SqlClient> ad alanında bulunan <xref:System.Data.SqlClient.SqlConnection> sınıfını doğrudan kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f16b0-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="f16b0-142">QueryAsync yöntemi ve <xref:System.Data.SqlClient.SqlConnection> sınıfını genişleten diğer uzantı yöntemleri aracılığıyla sorguları basit ve performanslı bir şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="f16b0-143">Dinamik ve statik Viewmodellere karşı</span><span class="sxs-lookup"><span data-stu-id="f16b0-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="f16b0-144">Görüntü modellerini sunucu tarafında istemci uygulamalarına döndürürken, Viewmodeller verileri istemci uygulamayla aynı şekilde tutacağından, bu görünümleri varlık modelinizin iç etki alanı varlıklarıyla farklı olabilecek DTOs (Veri Aktarımı nesneleri) olarak düşünebilirsiniz. belirtilmesi.</span><span class="sxs-lookup"><span data-stu-id="f16b0-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="f16b0-145">Bu nedenle, birçok durumda, birden fazla etki alanı varlıklarından gelen verileri toplayabilir ve istemci uygulamasının bu verilere nasıl ihtiyaç duyuşına göre Viewmodellerini tam olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="f16b0-146">Bu Viewmodeller veya DTOs, daha sonraki bir kod parçacığında gösterilen `OrderSummary` sınıfı gibi açıkça (veri sahibi sınıfları olarak) tanımlanabilir veya yalnızca sorgularda, dinamik bir tür olarak döndürülen özniteliklere göre dinamik Viewmodeller veya dinamik DTOs döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="f16b0-147">Dinamik tür olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="f16b0-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="f16b0-148">Aşağıdaki kodda gösterildiği gibi, yalnızca bir sorgu tarafından döndürülen öznitelikleri temel alan *dinamik* bir tür döndürerek sorgu tarafından doğrudan bir `ViewModel` döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="f16b0-149">Bu, döndürülecek özniteliklerin alt kümesinin sorgunun kendisini temel aldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="f16b0-150">Bu nedenle, sorguya veya birleşime yeni bir sütun eklerseniz, bu veriler döndürülen `ViewModel` ' a dinamik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="f16b0-151">Önemli nokta, dinamik bir tür kullanarak, döndürülen veri koleksiyonu, dinamik olarak ViewModel olarak toplanır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="f16b0-152">**Uzmanları:** Bu yaklaşım, bir sorgunun SQL cümlesini her güncelleştirdiğinizde statik ViewModel sınıflarını değiştirme gereksinimini azaltır. Bu tasarımın ardından, kodlama, basit ve hızlı bir şekilde, gelecekteki değişikliklere göre geliştikçe oldukça çevik bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="f16b0-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="f16b0-153">**Dezavantajlarını:** Uzun dönemde dinamik türler, istemci uygulamalarıyla bir hizmetin netliğini ve uyumluluğunu olumsuz yönde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="f16b0-154">Ayrıca, swashbuckle gibi ara yazılım yazılımı, dinamik türler kullanılıyorsa döndürülen türlerde belge düzeyini sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="f16b0-155">Önceden tanımlanmış DTO sınıfları olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="f16b0-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="f16b0-156">**Uzmanları**: "sözleşmeler" gibi, açık DTO sınıfları temel alan "sözleşmeler" gibi, statik önceden tanımlanmış ViewModel sınıfları olması, genel API 'ler için kesinlikle daha iyidir, ancak aynı uygulama tarafından kullanılsa bile uzun süreli mikro hizmetler için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="f16b0-157">Swagger için yanıt türleri belirtmek isterseniz, dönüş türü olarak açık DTO sınıfları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="f16b0-158">Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger 'dan daha zengin bilgiler sunmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f16b0-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="f16b0-159">Bu, API belgelerini ve API 'YI tükettiği uyumluluğu geliştirir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="f16b0-160">**Dezavantajların**: daha önce belirtildiği gibi, kodu güncelleştirirken, DTO sınıflarını güncelleştirmek için bazı adımlar daha fazla sürer.</span><span class="sxs-lookup"><span data-stu-id="f16b0-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="f16b0-161">*İpucu deneyimimize göre ipucu*: eShopOnContainers 'daki sıralama mikro hizmetinde uygulanan sorgularda, dinamik görünüm modellerini kullanarak geliştirmekte ve erken geliştirme aşamalarında çok basittir ve çevik.</span><span class="sxs-lookup"><span data-stu-id="f16b0-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="f16b0-162">Ancak, geliştirme işlemi bir kez alındıktan sonra, mikro hizmetin tüketicilerinin "sözleşmeler" olarak kullanılan açık bir tür olduğunu bilmesini sağlamak için, API 'Leri yeniden oluşturmayı ve ViewModel için statik veya önceden tanımlanmış DTOs kullanmayı seçtik.</span><span class="sxs-lookup"><span data-stu-id="f16b0-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="f16b0-163">Aşağıdaki örnekte, sorgunun nasıl veri döndürünü bir açık ViewModel DTO sınıfı kullanarak görebilirsiniz: OrderSummary sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f16b0-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="f16b0-164">Web API 'lerinin yanıt türlerini açıkla</span><span class="sxs-lookup"><span data-stu-id="f16b0-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="f16b0-165">Web API 'Leri ve mikro hizmetleri kullanan geliştiriciler, özellikle yanıt türleri ve hata kodları (Standart değilse) ile ilgili olarak en iyi şekilde verilen şeydir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="f16b0-166">Bunlar XML açıklamaları ve veri ek açıklamalarında işlenir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="f16b0-167">Swagger Kullanıcı arabiriminde doğru belgeler olmadan, tüketici hangi türlerin döndürülmekte olduğunu veya hangi HTTP kodlarının döndürüleceğini bilmede değildir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="f16b0-168">Bu sorun, <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> eklenerek düzeltildiğinde, swashbuckle aşağıdaki kodda gösterildiği gibi API dönüş modeli ve değerleri hakkında daha zengin bilgiler oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="f16b0-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="f16b0-169">Ancak, `ProducesResponseType` özniteliği bir tür olarak dinamik kullanamaz, ancak aşağıdaki örnekte gösterildiği gibi, `OrderSummary` ViewModel DTO gibi açık türler kullanmayı gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f16b0-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="f16b0-170">Bu, açık olarak döndürülen türlerin uzun dönemde dinamik türlerden daha iyi olmasının diğer bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="f16b0-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="f16b0-171">`ProducesResponseType` özniteliği kullanılırken, 200, 400 gibi olası HTTP hatalarını/kodlarını dikkate alarak beklenen sonucun ne olduğunu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="f16b0-172">Aşağıdaki görüntüde, Swagger Kullanıcı arabiriminin ResponseType bilgilerini nasıl gösterdiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Sıralama API 'SI için Swagger Kullanıcı arabirimi sayfasının tarayıcı görünümü.](./media/image5.png)

<span data-ttu-id="f16b0-174">**Şekil 7-5**.</span><span class="sxs-lookup"><span data-stu-id="f16b0-174">**Figure 7-5**.</span></span> <span data-ttu-id="f16b0-175">Bir Web API 'sinden yanıt türlerini ve olası HTTP durum kodlarını gösteren Swagger Kullanıcı arabirimi</span><span class="sxs-lookup"><span data-stu-id="f16b0-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="f16b0-176">Görüntüde, ViewModel türlerine ve döndürülebilecek olası HTTP durum kodlarına göre bazı örnek değerlerin üzerine bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16b0-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f16b0-177">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f16b0-177">Additional resources</span></span>

- <span data-ttu-id="f16b0-178">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="f16b0-178">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="f16b0-179">**Julie Lerman. Veri noktaları-kaber, Entity Framework ve hibrit uygulamalar (MSDN Magazine makalesi)**</span><span class="sxs-lookup"><span data-stu-id="f16b0-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://msdn.microsoft.com/magazine/mt703432>

- <span data-ttu-id="f16b0-180">**Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**</span><span class="sxs-lookup"><span data-stu-id="f16b0-180">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="f16b0-181">[Önceki](eshoponcontainers-cqrs-ddd-microservice.md)
>[İleri](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="f16b0-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
