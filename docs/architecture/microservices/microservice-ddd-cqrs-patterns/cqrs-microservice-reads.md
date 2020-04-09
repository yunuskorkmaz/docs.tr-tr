---
title: CQRS mikro hizmetinde okuma/sorgulama işlemleri uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Dapper kullanarak eShopOnContainers sipariş microservice CQRS sorguları tarafında uygulanmasını anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 49f42a5035bab38f800f3ec5ea24b01fde0d2964
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988758"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="b5d3c-103">CQRS microservice'de okuma/sorgu uygulama</span><span class="sxs-lookup"><span data-stu-id="b5d3c-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="b5d3c-104">Okuma/sorgular için, eShopOnContainers başvuru uygulamasından sipariş mikrohizmeti, sorguları DDD modeli nden ve işlem alanından bağımsız olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="b5d3c-105">Bu, öncelikle sorgu ve hareketler için talepler büyük ölçüde farklı olduğundan yapıldı.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="b5d3c-106">Etki alanı mantığıyla uyumlu olması gereken yürütme hareketlerini yazar.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="b5d3c-107">Sorgular, diğer taraftan, idempotent ve etki alanı kurallarından ayrılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="b5d3c-108">Yaklaşım, Şekil 7-3'te gösterildiği gibi basittir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="b5d3c-109">API arabirimi, Web API denetleyicileri tarafından Dapper gibi mikro Nesne İlişkisel Haritalayıcı (ORM) gibi herhangi bir altyapı kullanılarak ve Kullanıcı Arabirimi uygulamalarının gereksinimlerine bağlı olarak dinamik Görünüm Modelleri döndürülerek uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Basitleştirilmiş CQRS'de üst düzey sorguları gösteren diyagram.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="b5d3c-111">**Şekil 7-3**.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-111">**Figure 7-3**.</span></span> <span data-ttu-id="b5d3c-112">CQRS microservice sorguları için en basit yaklaşım</span><span class="sxs-lookup"><span data-stu-id="b5d3c-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="b5d3c-113">Basitleştirilmiş bir CQRS yaklaşımında sorgu tarafı için en basit yaklaşım, veritabanını Dapper gibi bir Micro-ORM ile sorgulayarak ve dinamik Görünüm Modelleri döndürerek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by just querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="b5d3c-114">Sorgu tanımları veritabanını sorgular ve her sorgu için anında oluşturulmuş dinamik bir Görünüm Modeli döndürün.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="b5d3c-115">Sorgular iktidara geldiğinden, sorguyu kaç kez çalıştırsanız çalıştırın verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="b5d3c-116">Bu nedenle, agregalar ve diğer desenler gibi işlem tarafında kullanılan herhangi bir DDD deseni ile sınırlı olması gerekmez ve bu nedenle sorgular işlem alanından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="b5d3c-117">UI'nin gereksinim duyduğu veriler için veritabanını sorgular ve SQL deyimleri dışında herhangi bir yerde statik olarak tanımlanması gerekmeyen dinamik bir Görünüm Modeli döndürür (Görünüm Modelleri için sınıf lar yoktur).</span><span class="sxs-lookup"><span data-stu-id="b5d3c-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="b5d3c-118">Bu basit bir yaklaşım olduğundan, sorgu tarafı için gerekli kod [(Dapper](https://github.com/StackExchange/Dapper)gibi mikro ORM kullanarak kod gibi) [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="b5d3c-119">Şekil 7-4 bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="b5d3c-120">Sorgular, eShopOnContainers çözümü ndeki **Ordering.API** microservice projesinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Ordering.API projesinin Sorgular klasörünün ekran görüntüsü.](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="b5d3c-122">**Şekil 7-4**.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-122">**Figure 7-4**.</span></span> <span data-ttu-id="b5d3c-123">eShopOnContainers sipariş microservice sorguları</span><span class="sxs-lookup"><span data-stu-id="b5d3c-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="b5d3c-124">Etki alanı modeli kısıtlamalarından bağımsız olarak, istemci uygulamaları için özel olarak yapılmış ViewModels'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="b5d3c-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="b5d3c-125">Sorgular istemci uygulamaları tarafından gerekli verileri elde etmek için gerçekleştirildiğinden, döndürülen tür sorgular tarafından döndürülen verilere dayalı olarak istemciler için özel olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="b5d3c-126">Bu modeller veya Veri Aktarım Nesneleri (DTO'lar) Görünüm Modelleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="b5d3c-127">Döndürülen veriler (ViewModel), veritabanındaki birden çok varlık veya tablodan gelen verileri birleştirmenin veya hatta işlem alanı için etki alanı modelinde tanımlanan birden çok agreganın bir sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="b5d3c-128">Bu durumda, etki alanı modelinden bağımsız sorgular oluşturduğunuziçin, toplu sınırlar ve kısıtlamalar tamamen yoksayılır ve gereksinim duyabileceğiniz tablo ve sütunları sorgulamakta özgürsunuz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="b5d3c-129">Bu yaklaşım, sorguları oluşturan veya güncelleştiren geliştiriciler için büyük esneklik ve üretkenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="b5d3c-130">Görünüm Modelleri sınıflarda tanımlanan statik türleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="b5d3c-131">Veya geliştiriciler için çok çevik olan gerçekleştirilen sorgulara (sipariş mikrohizmetinde uygulandığı gibi) dayalı olarak dinamik olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="b5d3c-132">Sorguları gerçekleştirmek için Dapper'ı mikro ORM olarak kullanın</span><span class="sxs-lookup"><span data-stu-id="b5d3c-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="b5d3c-133">Herhangi bir mikro ORM, Entity Framework Core, hatta düz ADO.NET sorgu için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="b5d3c-134">Örnek uygulamada, Dapper popüler bir mikro ORM iyi bir örnek olarak eShopOnContainers sipariş microservice için seçildi.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="b5d3c-135">Çok hafif bir çerçeve olduğu için, büyük performans ile düz SQL sorguları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="b5d3c-136">Dapper'ı kullanarak, birden çok tabloya erişebilen ve birleşebilen bir SQL sorgusu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="b5d3c-137">Dapper bir açık kaynak projesidir (orijinal Sam Saffron tarafından oluşturulan), ve [Stack Overflow](https://stackoverflow.com/)kullanılan yapı taşlarının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="b5d3c-138">Dapper'ı kullanmak için, aşağıdaki şekilde gösterildiği gibi, [Dapper NuGet paketi](https://www.nuget.org/packages/Dapper)aracılığıyla yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b5d3c-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![NuGet paketleri görünümünde Dapper paketinin ekran görüntüsü.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="b5d3c-140">Ayrıca, kodunuzda Dapper uzantı yöntemlerine erişebilmek için bir açıklama eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="b5d3c-141">Kodunuzda Dapper kullandığınızda, <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient> doğrudan ad alanında kullanılabilen sınıfı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="b5d3c-142">QueryAsync yöntemi ve <xref:System.Data.SqlClient.SqlConnection> sınıfı genişleten diğer uzantı yöntemleri sayesinde sorguları basit ve performant bir şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="b5d3c-143">Dinamik ve statik Görünüm Modelleri</span><span class="sxs-lookup"><span data-stu-id="b5d3c-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="b5d3c-144">ViewModels'ı sunucu tarafından istemci uygulamalarına döndürrken, Görünüm Modelleri verileri istemci uygulamasının ihtiyaç duyduğu şekilde tuttuğundan, varlık modelinizin iç etki alanı varlıklarından farklı olabilecek DTo'lar (Veri Aktarımı Nesneleri) olarak bu Görünüm Modelleri'ni düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="b5d3c-145">Bu nedenle, çoğu durumda, birden çok etki alanı varlığından gelen verileri toplayabilir ve ViewModels'i istemci uygulamasının bu verilere nasıl ihtiyaç duyduğuna göre tam olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="b5d3c-146">Bu Görünüm Modelleri veya DTO'lar, daha sonraki bir `OrderSummary` kod snippet'inde gösterilen sınıf gibi açıkça (veri tutucu sınıfları olarak) tanımlanabilir veya yalnızca sorgularınızın döndürülen özniteliklerine göre dinamik Görünüm Modelleri veya dinamik DTO'ları dinamik bir tür olarak döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="b5d3c-147">Dinamik tür olarak Görünüm Modeli</span><span class="sxs-lookup"><span data-stu-id="b5d3c-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="b5d3c-148">Aşağıdaki kodda gösterildiği gibi, bir `ViewModel` sorgu tarafından döndürülen öznitelikleri temel alan *dinamik* bir tür yalnızca döndürülerek sorgular tarafından doğrudan döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="b5d3c-149">Bu, döndürülecek özniteliklerin alt kümesinin sorgunun kendisine dayandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="b5d3c-150">Bu nedenle, sorguya veya birleştirmeye yeni bir sütun eklerseniz, `ViewModel`bu veriler döndürülen verilere dinamik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="b5d3c-151">Önemli nokta, dinamik bir tür kullanılarak, döndürülen veri toplamasının ViewModel olarak dinamik olarak bir araya getirilmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="b5d3c-152">**Artıları:** Bu yaklaşım, bir sorgunun SQL cümlesini güncellediğinizde statik ViewModel sınıflarını değiştirme gereksinimini azaltır ve bu tasarım yaklaşımını kodlama, basit ve gelecekteki değişikliklerle ilgili olarak hızlı bir şekilde gelişirken oldukça çevik hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="b5d3c-153">**Eksileri:** Uzun vadede, dinamik türler bir hizmetin netliğini ve istemci uygulamalarıyla uyumluluğunu olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="b5d3c-154">Buna ek olarak, Swashbuckle gibi ara yazılımlar dinamik türler kullanıyorsanız iade edilen türlerde aynı düzeyde belge sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="b5d3c-155">Modeli önceden tanımlanmış DTO sınıfları olarak görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b5d3c-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="b5d3c-156">**Artıları**: Açık DTO sınıflarına dayalı "sözleşmeler" gibi statik önceden tanımlanmış ViewModel sınıflarına sahip olmak, yalnızca aynı uygulama tarafından kullanılsa bile, kamu API'leri için değil, aynı zamanda uzun vadeli mikro hizmetler için de kesinlikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-156">**Pros**: Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="b5d3c-157">Swagger için yanıt türlerini belirtmek istiyorsanız, iade türü olarak açık DTO sınıfları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="b5d3c-158">Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger daha zengin bilgi sunmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="b5d3c-159">Bu, BIR API tüketirken API dokümantasyonlarını ve uyumluluğu artırır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="b5d3c-160">**Eksileri**: Daha önce de belirtildiği gibi, kodu güncellerken, DTO sınıflarını güncelleştirmek için birkaç adım daha alır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="b5d3c-161">*Deneyimlerimize Dayalı İpucu*: eShopOnContainers'daki Sipariş mikrohizmetinde uygulanan sorgularda, erken geliştirme aşamalarında çok basit ve çevik olduğu için dinamik ViewModels kullanarak geliştirmeye başladık.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="b5d3c-162">Ancak, geliştirme stabilize edildikten sonra, API'leri yeniden düzenlemeyi ve ViewModels için statik veya önceden tanımlanmış DTO'ları kullanmayı seçtik, çünkü microservice tüketicilerinin "sözleşme" olarak kullanılan açık DTO türlerini bilmeleri daha açıktır.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="b5d3c-163">Aşağıdaki örnekte, açık bir ViewModel DTO sınıfı: OrderSummary sınıfı kullanarak sorgunun verileri nasıl döndürettiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="b5d3c-164">Web API'lerinin yanıt türlerini açıklayın</span><span class="sxs-lookup"><span data-stu-id="b5d3c-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="b5d3c-165">Web API'leri ve mikro hizmetleri tüketen geliştiriciler en çok döndürülenlerle ilgilidir — özellikle yanıt türleri ve hata kodları (standart değilse).</span><span class="sxs-lookup"><span data-stu-id="b5d3c-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="b5d3c-166">Bunlar XML yorumlarında ve veri ek açıklamalarında işlenir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="b5d3c-167">Swagger UI'da uygun belgeler olmadan, tüketici hangi türlerin döndürüldildiği veya hangi HTTP kodlarının döndürülebileceği hakkında bilgi sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="b5d3c-168">Bu <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>sorun, swashbuckle aşağıdaki kodda gösterildiği gibi API dönüş modeli ve değerleri hakkında daha zengin bilgi üretebilir ekleyerek giderilir:</span><span class="sxs-lookup"><span data-stu-id="b5d3c-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="b5d3c-169">Ancak, `ProducesResponseType` öznitelik dinamik bir tür olarak kullanamaz, ancak aşağıdaki `OrderSummary` örnekte gösterilen ViewModel DTO gibi açık türleri kullanmayı gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b5d3c-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="b5d3c-170">Bu, açık döndürülen türlerin uzun vadede dinamik türlerden daha iyi olmasının başka bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="b5d3c-171">Özniteliği `ProducesResponseType` kullanırken, 200, 400, vb. gibi olası HTTP hataları/kodları açısından beklenen sonucun ne olduğunu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="b5d3c-172">Aşağıdaki resimde, Swagger Kullanıcı Bira'sının Yanıt Türü bilgilerini nasıl gösterdiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Sipariş API'si için Swagger U-i II sayfasının ekran görüntüsü.](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="b5d3c-174">**Şekil 7-5**.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-174">**Figure 7-5**.</span></span> <span data-ttu-id="b5d3c-175">Yanıt türlerini ve olası HTTP durum kodlarını bir Web API'sinden gösteren Swagger UI</span><span class="sxs-lookup"><span data-stu-id="b5d3c-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="b5d3c-176">ViewModel türlerine ve döndürülebilen olası HTTP durum kodlarına dayalı olarak bazı örnek değerlerin üzerindeki resimde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5d3c-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b5d3c-177">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b5d3c-177">Additional resources</span></span>

- <span data-ttu-id="b5d3c-178">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="b5d3c-178">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="b5d3c-179">**Julie Lerman. Veri Noktaları - Dapper, Varlık Çerçevesi ve Karma Uygulamalar (MSDN dergisi makalesi)**</span><span class="sxs-lookup"><span data-stu-id="b5d3c-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="b5d3c-180">**Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**</span><span class="sxs-lookup"><span data-stu-id="b5d3c-180">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="b5d3c-181">[Önceki](eshoponcontainers-cqrs-ddd-microservice.md)
>[Sonraki](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="b5d3c-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
