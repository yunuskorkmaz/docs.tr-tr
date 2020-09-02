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
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="59bc6-103">CQRS mikro hizmetinde okuma/sorgu uygulama</span><span class="sxs-lookup"><span data-stu-id="59bc6-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="59bc6-104">Okuma/sorgular için, eShopOnContainers başvuru uygulamasından gelen sıralama mikro hizmeti, sorguları DDD modeli ve işlem alanından bağımsız olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="59bc6-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="59bc6-105">Bu, öncelikle sorgular ve işlemler için talepler büyük ölçüde farklı olduğundan yapıldı.</span><span class="sxs-lookup"><span data-stu-id="59bc6-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="59bc6-106">Yazar, etki alanı mantığı ile uyumlu olması gereken işlemleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="59bc6-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="59bc6-107">Diğer yandan sorgular, ıdempotent ve etki alanı kurallarından ayrılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="59bc6-108">Şekil 7-3 ' de gösterildiği gibi yaklaşım basittir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="59bc6-109">API arabirimi, Web API denetleyicileri tarafından, kaber gibi mikro nesne Ilişkisel Eşleyici (ORM) ve Kullanıcı arabirimi uygulamalarının ihtiyaçlarına bağlı olarak dinamik Viewmodeller gibi bir altyapı kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Basitleştirilmiş CQRS 'de üst düzey sorgu-tarafı gösteren diyagram.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="59bc6-111">**Şekil 7-3**.</span><span class="sxs-lookup"><span data-stu-id="59bc6-111">**Figure 7-3**.</span></span> <span data-ttu-id="59bc6-112">Bir CQRS mikro hizmetindeki sorgular için en basit yaklaşım</span><span class="sxs-lookup"><span data-stu-id="59bc6-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="59bc6-113">Basitleştirilmiş bir CQRS yaklaşımında sorgu tarafı için en basit yaklaşım, bir Micro-ORM gibi, dinamik ViewModel döndüren veritabanı sorgulanarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="59bc6-114">Sorgu tanımları veritabanını sorgular ve her sorgu için anında oluşturulmuş dinamik bir ViewModel döndürür.</span><span class="sxs-lookup"><span data-stu-id="59bc6-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="59bc6-115">Sorgular ıdempotent olduğundan, bir sorgu kaç kez çalıştırıldıklarından bağımsız olarak verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="59bc6-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="59bc6-116">Bu nedenle, işlem tarafında, Toplamalar ve diğer desenler gibi kullanılan DDD deseniyle kısıtlanması gerekmez ve sorguların işlem alanından ayrılması neden olur.</span><span class="sxs-lookup"><span data-stu-id="59bc6-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="59bc6-117">Kullanıcı arabiriminin gerek duyduğu verilerin veritabanını sorgular ve SQL deyimlerinin kendisi hariç her yerde statik olarak tanımlanması gerekmeyen dinamik bir ViewModel (ViewModel için sınıf olmadan) döndürür.</span><span class="sxs-lookup"><span data-stu-id="59bc6-117">You query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="59bc6-118">Bu yaklaşım basit olduğundan, sorgular tarafı için gereken kod (örneğin, mikro ORM 'yi kullanan kod [gibi)](https://github.com/StackExchange/Dapper) [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-118">Since this approach is simple, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="59bc6-119">Şekil 7-4 bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="59bc6-120">Sorgular, eShopOnContainers çözümünde **sıralama. API** mikro hizmet projesinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Sıralama. API projesinin sorgular klasörünün ekran görüntüsü.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="59bc6-122">**Şekil 7-4**.</span><span class="sxs-lookup"><span data-stu-id="59bc6-122">**Figure 7-4**.</span></span> <span data-ttu-id="59bc6-123">EShopOnContainers 'da sıralama mikro hizmetindeki sorgular</span><span class="sxs-lookup"><span data-stu-id="59bc6-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="59bc6-124">Etki alanı modeli kısıtlamalarından bağımsız olarak istemci uygulamaları için özel olarak oluşturulan Viewmodeller kullanın</span><span class="sxs-lookup"><span data-stu-id="59bc6-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="59bc6-125">Sorgular, istemci uygulamaları için gereken verileri elde etmek üzere gerçekleştirildiğinden, bu tür sorgular tarafından döndürülen verilere bağlı olarak istemciler için de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="59bc6-126">Bu modeller veya Veri Aktarımı nesneleri (DTOs) Viewmodeller olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="59bc6-127">Döndürülen veriler (ViewModel), veritabanındaki birden çok varlık veya tablodan ya da işlem alanı için etki alanı modelinde tanımlanan birden çok toplama arasında veri birleştirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="59bc6-128">Bu durumda, etki alanı modelinden bağımsız sorgular oluştururken, toplamalar sınırları ve kısıtlamaları yok sayılır ve ihtiyacınız olan herhangi bir tabloyu ve sütunu sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="59bc6-129">Bu yaklaşım, sorguları oluşturan veya güncelleştiren geliştiriciler için harika esneklik ve verimlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="59bc6-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="59bc6-130">Viewmodeller sınıflarda tanımlanmış statik türler olabilir (sıralama mikro hizmetinde uygulandığı gibi).</span><span class="sxs-lookup"><span data-stu-id="59bc6-130">The ViewModels can be static types defined in classes (as is implemented in the ordering microservice).</span></span> <span data-ttu-id="59bc6-131">Ya da geliştiriciler için çok çevik olan gerçekleştirilen sorgulara göre dinamik olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-131">Or they can be created dynamically based on the queries performed, which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="59bc6-132">Sorguları gerçekleştirmek için mikro ORM olarak kaber kullanma</span><span class="sxs-lookup"><span data-stu-id="59bc6-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="59bc6-133">Sorgulamak için herhangi bir mikro ORM, Entity Framework Core veya hatta düz ADO.NET kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="59bc6-134">Örnek uygulamada, Gamze 'nin eShopOnContainers 'daki sıralama mikro hizmeti, popüler mikro ORM 'nin iyi bir örneği olarak seçilmiştir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="59bc6-135">Hafif bir çatı olduğundan, harika performans ile düz SQL sorguları çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-135">It can run plain SQL queries with great performance, because it's a light framework.</span></span> <span data-ttu-id="59bc6-136">Kaber kullanarak, birden fazla tabloya erişebilen ve birleştiren bir SQL sorgusu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="59bc6-137">Kaber, açık kaynaklı bir projem (orijinal, Sam Saffron tarafından oluşturulan) ve [Stack Overflow](https://stackoverflow.com/)' de kullanılan yapı taşlarının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="59bc6-138">Kaber 'yi kullanmak için, aşağıdaki şekilde gösterildiği gibi, bunu yalnızca [kaber NuGet paketi](https://www.nuget.org/packages/Dapper)aracılığıyla yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="59bc6-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![NuGet paketleri görünümündeki kaber paketinin ekran görüntüsü.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="59bc6-140">Ayrıca, `using` kodunuzun kaber genişletme yöntemlerine erişimi olması için bir yönerge eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-140">You also need to add a `using` directive so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="59bc6-141">Kodunuzda kaber kullandığınızda, <xref:System.Data.SqlClient.SqlConnection> ad alanında bulunan sınıfını doğrudan kullanırsınız <xref:System.Data.SqlClient> .</span><span class="sxs-lookup"><span data-stu-id="59bc6-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="59bc6-142">QueryAsync yöntemi ve sınıfı genişleten diğer uzantı yöntemleri aracılığıyla <xref:System.Data.SqlClient.SqlConnection> sorguları basit ve performanslı bir şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="59bc6-143">Dinamik ve statik Viewmodellere karşı</span><span class="sxs-lookup"><span data-stu-id="59bc6-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="59bc6-144">Sunucu tarafından istemci uygulamalarına Viewmodeller döndürürken, Viewmodeller verileri istemci uygulamasına ihtiyaç duyduğunda tutacağından, varlık modelinizin iç etki alanı varlıklarıyla farklı olabilecek bu ViewModel (Veri Aktarımı nesneleri) olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="59bc6-145">Bu nedenle, birçok durumda, birden fazla etki alanı varlıklarından gelen verileri toplayabilir ve istemci uygulamasının bu verilere nasıl ihtiyaç duyuşına göre Viewmodellerini tam olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="59bc6-146">Bu Viewmodeller veya DTOs, `OrderSummary` daha sonraki bir kod parçacığında gösterilen sınıf gibi açıkça (veri sahibi sınıfları olarak) tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes), like the `OrderSummary` class shown in a later code snippet.</span></span> <span data-ttu-id="59bc6-147">Ya da, dinamik bir tür olarak sorgularınız tarafından döndürülen özniteliklere göre dinamik Viewmodeller veya dinamik DTOs döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-147">Or, you could just return dynamic ViewModels or dynamic DTOs based on the attributes returned by your queries as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="59bc6-148">Dinamik tür olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="59bc6-148">ViewModel as dynamic type</span></span>

<span data-ttu-id="59bc6-149">Aşağıdaki kodda gösterildiği gibi, `ViewModel` yalnızca bir sorgu tarafından döndürülen öznitelikleri temel alan *dinamik* bir tür döndürerek sorgular tarafından doğrudan döndürülebilecek.</span><span class="sxs-lookup"><span data-stu-id="59bc6-149">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="59bc6-150">Bu, döndürülecek özniteliklerin alt kümesinin sorgunun kendisini temel aldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-150">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="59bc6-151">Bu nedenle, sorguya veya birleşime yeni bir sütun eklerseniz, bu veriler döndürülen öğesine dinamik olarak eklenir `ViewModel` .</span><span class="sxs-lookup"><span data-stu-id="59bc6-151">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="59bc6-152">Önemli nokta, dinamik bir tür kullanarak, döndürülen veri koleksiyonu, dinamik olarak ViewModel olarak toplanır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-152">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="59bc6-153">**Uzmanları:** Bu yaklaşım, bir sorgunun SQL cümlesini her güncelleştirdiğinizde bu tasarımın, basit ve hızlı bir şekilde geliştikçe, gelecekteki değişikliklere göre gelişdiğinde çevik hale getirilmesi durumunda statik ViewModel sınıflarını değiştirme gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-153">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="59bc6-154">**Dezavantajlarını:** Uzun dönemde dinamik türler, istemci uygulamalarıyla bir hizmetin netliğini ve uyumluluğunu olumsuz yönde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-154">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="59bc6-155">Ayrıca, swashbuckle gibi ara yazılım yazılımı, dinamik türler kullanılıyorsa döndürülen türlerde belge düzeyini sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-155">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="59bc6-156">Önceden tanımlanmış DTO sınıfları olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="59bc6-156">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="59bc6-157">**Profesyonelleri**: statik, önceden tanımlanmış ViewModel sınıfları olan "sözleşmeler" gibi açık DTO sınıfları temel alan, genel API 'ler için kesinlikle daha iyidir, ancak aynı uygulama tarafından kullanılsa bile uzun vadeli mikro hizmetler için de daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-157">**Pros**: Having static, predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long-term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="59bc6-158">Swagger için yanıt türleri belirtmek isterseniz, dönüş türü olarak açık DTO sınıfları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-158">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="59bc6-159">Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger 'dan daha zengin bilgiler sunmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="59bc6-159">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="59bc6-160">Bu, API belgelerini ve API 'YI tükettiği uyumluluğu geliştirir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-160">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="59bc6-161">**Dezavantajların**: daha önce belirtildiği gibi, kodu güncelleştirirken, DTO sınıflarını güncelleştirmek için bazı adımlar daha fazla sürer.</span><span class="sxs-lookup"><span data-stu-id="59bc6-161">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="59bc6-162">*İpucu deneyimimize göre ipucu*: eShopOnContainers 'da sıralama mikro hizmetinde uygulanan sorgularda, basit ve çevik bir geliştirme aşamasında olan dinamik görünüm modellerini kullanarak geliştirmeye başladık.</span><span class="sxs-lookup"><span data-stu-id="59bc6-162">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was straightforward and agile on the early development stages.</span></span> <span data-ttu-id="59bc6-163">Ancak, geliştirme işlemi bir kez alındıktan sonra, mikro hizmetin tüketicilerinin "sözleşmeler" olarak kullanılan açık bir tür olduğunu bilmesini sağlamak için, API 'Leri yeniden oluşturmayı ve ViewModel için statik veya önceden tanımlanmış DTOs kullanmayı seçtik.</span><span class="sxs-lookup"><span data-stu-id="59bc6-163">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="59bc6-164">Aşağıdaki örnekte, sorgunun nasıl veri döndürünü bir açık ViewModel DTO sınıfı kullanarak görebilirsiniz: OrderSummary sınıfı.</span><span class="sxs-lookup"><span data-stu-id="59bc6-164">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="59bc6-165">Web API 'lerinin yanıt türlerini açıkla</span><span class="sxs-lookup"><span data-stu-id="59bc6-165">Describe response types of Web APIs</span></span>

<span data-ttu-id="59bc6-166">Web API 'Leri ve mikro hizmetleri kullanan geliştiriciler, özellikle yanıt türleri ve hata kodları (Standart değilse) ile ilgili olarak en iyi şekilde verilen şeydir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-166">Developers consuming web APIs and microservices are most concerned with what is returned—specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="59bc6-167">Yanıt türleri XML açıklamaları ve veri ek açıklamalarında işlenir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-167">The response types are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="59bc6-168">Swagger Kullanıcı arabiriminde doğru belgeler olmadan, tüketici hangi türlerin döndürülmekte olduğunu veya hangi HTTP kodlarının döndürüleceğini bilmede değildir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-168">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="59bc6-169">Bu sorun eklenerek düzeltildiği için <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> , swashbuckle aşağıdaki kodda gösterildiği gıbı API dönüş modeli ve değerleri hakkında daha zengin bilgiler oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="59bc6-169">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="59bc6-170">Ancak, `ProducesResponseType` öznitelik bir tür olarak dinamik kullanamaz, ancak aşağıdaki örnekte gösterildiği gibi, ViewModel gibi açık türlerin kullanılmasını gerektirir `OrderSummary` :</span><span class="sxs-lookup"><span data-stu-id="59bc6-170">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="59bc6-171">Bu, açık olarak döndürülen türlerin uzun dönemde dinamik türlerden daha iyi olmasının diğer bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-171">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="59bc6-172">`ProducesResponseType`Özniteliğini kullanırken, OLASı HTTP hatalarını/kodlarını (200, 400 vb. gibi) hangi beklenen sonucun olduğunu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-172">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="59bc6-173">Aşağıdaki görüntüde, Swagger Kullanıcı arabiriminin ResponseType bilgilerini nasıl gösterdiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59bc6-173">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Sıralama API 'SI için Swagger Kullanıcı arabirimi sayfasının ekran görüntüsü.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="59bc6-175">**Şekil 7-5**.</span><span class="sxs-lookup"><span data-stu-id="59bc6-175">**Figure 7-5**.</span></span> <span data-ttu-id="59bc6-176">Bir Web API 'sinden yanıt türlerini ve olası HTTP durum kodlarını gösteren Swagger Kullanıcı arabirimi</span><span class="sxs-lookup"><span data-stu-id="59bc6-176">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="59bc6-177">Görüntüde, ViewModel türlerine ve döndürülebilecek olası HTTP durum kodlarına göre bazı örnek değerler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="59bc6-177">The image shows some example values based on the ViewModel types and the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59bc6-178">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="59bc6-178">Additional resources</span></span>

- <span data-ttu-id="59bc6-179">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="59bc6-179">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="59bc6-180">**Julie Lerman. Veri noktaları-kaber, Entity Framework ve hibrit uygulamalar (MSDN Magazine makalesi)**</span><span class="sxs-lookup"><span data-stu-id="59bc6-180">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="59bc6-181">**Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**</span><span class="sxs-lookup"><span data-stu-id="59bc6-181">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="59bc6-182">[Önceki](eshoponcontainers-cqrs-ddd-microservice.md) 
> [Sonraki](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="59bc6-182">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
