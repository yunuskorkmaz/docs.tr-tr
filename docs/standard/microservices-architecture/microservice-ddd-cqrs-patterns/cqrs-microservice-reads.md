---
title: "Uygulama okuma/CQRS mikro hizmet sorguları"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulama okuma/CQRS mikro hizmet sorguları"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ca9bcefb317d2b3c7c225b773918ca4a2484cb8f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="3607f-104">Uygulama okuma/CQRS mikro hizmet sorguları</span><span class="sxs-lookup"><span data-stu-id="3607f-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="3607f-105">Okuma/sorguları, sıralama mikro hizmet eShopOnContainers başvuru uygulamadan sorgularından bağımsız olarak DDD modelini ve işlem alanı uygular.</span><span class="sxs-lookup"><span data-stu-id="3607f-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="3607f-106">Öncelikle taleplerini sorgular ve işlemler için önemli ölçüde farklı olduğu için bu gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="3607f-107">Yazma etki alanı mantığı ile uyumlu olması gereken işlemleri yürütün.</span><span class="sxs-lookup"><span data-stu-id="3607f-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="3607f-108">Sorguları, diğer yandan ıdempotent olan ve etki alanı kurallardan yinelenmeli.</span><span class="sxs-lookup"><span data-stu-id="3607f-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="3607f-109">Şekil 9-3'te gösterildiği gibi bir yaklaşım basittir.</span><span class="sxs-lookup"><span data-stu-id="3607f-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="3607f-110">API Arabirimi mikro nesne ilişkisel Eşleyici (ORM) Dapper gibi gibi herhangi bir altyapı kullanarak ve kullanıcı Arabirimi uygulamalarını gereksinimlerine bağlı olarak dinamik ViewModels döndüren Web API denetleyicilerinin tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3607f-110">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="3607f-111">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="3607f-111">**Figure 9-3**.</span></span> <span data-ttu-id="3607f-112">CQRS mikro hizmet sorguları için en kolay yaklaşım</span><span class="sxs-lookup"><span data-stu-id="3607f-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="3607f-113">Bu mod sorguları için en basit olası yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="3607f-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="3607f-114">Sorgu tanımları veritabanını sorgulamak ve her sorgu için kolay bir şekilde yerleşik dinamik bir ViewModel döndürür.</span><span class="sxs-lookup"><span data-stu-id="3607f-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="3607f-115">Sorguları ıdempotent olduğundan, bunlar bir sorgu çalıştırmadan kaç kez olsun verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="3607f-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="3607f-116">Bu nedenle, işlem tarafındaki toplamalar ve diğer desenleri gibi kullanılan herhangi bir DDD modeliyle tarafından kısıtlanmış gerek yoktur ve sorguları işlem alanından ayrılmış neden.</span><span class="sxs-lookup"><span data-stu-id="3607f-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="3607f-117">Yalnızca kullanıcı arabirimini gereken veriler için veritabanını sorgulamak ve statik olarak olması gerekmez dinamik bir ViewModel her yerden (sınıflar ViewModels için) dışındaki SQL deyimlerini kendilerini tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="3607f-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="3607f-118">Bu basit bir yaklaşım olduğuna göre sorguları tarafı için gerekli kod (ORM gibi bir mikro kullanarak kod gibi [Dapper](https://github.com/StackExchange/Dapper)) uygulanabilir [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="3607f-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="3607f-119">Şekil 9-4 bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3607f-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="3607f-120">Sorguları tanımlanan **Ordering.API** eShopOnContainers çözümünde mikro hizmet projesi.</span><span class="sxs-lookup"><span data-stu-id="3607f-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="3607f-121">**Şekil 9-4**.</span><span class="sxs-lookup"><span data-stu-id="3607f-121">**Figure 9-4**.</span></span> <span data-ttu-id="3607f-122">Sıralama mikro hizmet eShopOnContainers içinde sorguları</span><span class="sxs-lookup"><span data-stu-id="3607f-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="3607f-123">İstemci uygulamaları, etki alanı modeli kısıtlamaları bağımsız için özellikle yapılan ViewModels kullanma</span><span class="sxs-lookup"><span data-stu-id="3607f-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="3607f-124">İstemci uygulamaları tarafından gereken verileri almak için sorgular gerçekleştirilen olduğundan, döndürülen tür özellikle sorguları tarafından döndürülen verileri temel alan istemciler için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="3607f-125">Bu modeller ya da veri aktarım nesneleri (DTOs) ViewModels denir.</span><span class="sxs-lookup"><span data-stu-id="3607f-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="3607f-126">Döndürülen veriler (ViewModel) birden çok varlık veya tablo verileri veritabanında veya bile işlem alanı için etki alanı modelinde tanımlanan birden çok toplamalar arasında birleştirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="3607f-127">Bu durumda, sorguları etki alanı modeli bağımsız oluşturmakta olduğunuz çünkü toplamalar sınırları ve kısıtlamaları tamamen yoksayılır ve tüm tablo ve sütun gereksinim duyabileceğiniz sorgu boş.</span><span class="sxs-lookup"><span data-stu-id="3607f-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="3607f-128">Bu yaklaşım, oluşturma veya güncelleştirme sorguları geliştiriciler için büyük esneklik ve verimlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3607f-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="3607f-129">ViewModels sınıflarda tanımlanan statik türler olabilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="3607f-130">Ya da yöneticiler geliştiricileri için çok Çevik olduğu (sıralama mikro hizmet içinde uygulanan gibi) gerçekleştirilecek sorgularına göre dinamik olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="3607f-131">Sorguları gerçekleştirmek için Dapper mikro ORM kullanma</span><span class="sxs-lookup"><span data-stu-id="3607f-131">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="3607f-132">Tüm mikro ORM, Entity Framework Çekirdek ya da bile düz ADO.NET sorgulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3607f-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="3607f-133">Örnek uygulama Dapper eShopOnContainers popüler mikro ORM iyi bir örnek olarak, sipariş mikro hizmet için seçilmedi.</span><span class="sxs-lookup"><span data-stu-id="3607f-133">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="3607f-134">Çok açık bir çerçeve olduğu için harika performans ile düz SQL sorguları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3607f-134">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="3607f-135">Dapper kullanarak, erişebilir ve birden çok tabloyu birleştirme bir SQL sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3607f-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="3607f-136">Dapper açık kaynaklı proje (Sam Saffron tarafından oluşturulan özgün) ve kullanılan yapı taşları parçası olan [yığın taşması](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="3607f-136">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="3607f-137">Dapper kullanmak için aracılığıyla yüklemeniz yeterlidir [Dapper NuGet paketi](https://www.nuget.org/packages/Dapper), aşağıdaki çizimde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="3607f-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="3607f-138">Ayrıca kullanarak bir eklemeniz gerekir, kodunuzu Dapper genişletme yöntemleri erişimi şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="3607f-138">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="3607f-139">Kodunuzda Dapper kullandığınızda, doğrudan kullanmanız <xref:System.Data.SqlClient.SqlConnection> sınıfı bulunan <xref:System.Data.SqlClient> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3607f-139">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="3607f-140">QueryAsync yöntemi ve genişletmek diğer genişletme yöntemleri aracılığıyla <xref:System.Data.SqlClient.SqlConnection> sınıfı, yalnızca çalıştırabilirsiniz sorguları basit ve kullanıcı bir biçimde.</span><span class="sxs-lookup"><span data-stu-id="3607f-140">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="3607f-141">Dinamik statik ViewModels karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="3607f-141">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="3607f-142">ViewModels istemci uygulamaları için sunucu tarafı döndürülürken bu ViewModels hakkında ViewModels tutma veri yolu istemci uygulaması gerektiğinden, varlık modeli iç etki alanının varlıklara farklı olabilir DTOs düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3607f-142">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="3607f-143">Bu nedenle, çoğu durumda, birden çok etki alanı varlıklardan gelen veri toplama ve istemci uygulamanın verilerin nasıl gerekir göre tam olarak ViewModels oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3607f-143">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="3607f-144">Bu ViewModels veya DTOs (olarak veri sahibi sınıfları) açıkça gibi tanımlanabilir [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) bir sonraki kod parçacığını veya, içinde gösterilen sınıfı yalnızca dinamik ViewModels veya dönen yalnızca döndürülen özniteliklerini temel alarak dinamik DTOs sorgularınızın tarafından olarak bir `dynamic` türü.</span><span class="sxs-lookup"><span data-stu-id="3607f-144">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="3607f-145">Dinamik tür olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="3607f-145">ViewModel as dynamic type</span></span>

<span data-ttu-id="3607f-146">Aşağıdaki kodda gösterildiği gibi bir ViewModel doğrudan sorgular tarafından dahili olarak bir sorgu tarafından döndürülen özniteliklerinin dayanır dinamik bir tür döndürerek döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-146">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="3607f-147">Döndürülecek öznitelik alt sorguyu temel alan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3607f-147">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="3607f-148">Bu nedenle, birleştirme ve sorgu için yeni bir sütun eklerseniz, bu verileri döndürülen ViewModel dinamik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="3607f-148">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

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

<span data-ttu-id="3607f-149">Dinamik tür kullanarak, döndürülen verilerin toplanmasını dinamik ViewModel derlendiğinden emin önemli noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="3607f-149">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="3607f-150">*Uzmanları:* bu yaklaşım kodlama, kolay ve hızlı in regard to gelecekteki değişiklikler gelişmesi bu tasarım yaklaşımı oldukça Çevik yaparak bir sorgu SQL cümle güncelleştirdiğinizde statik ViewModel sınıflarını değiştirmek için gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="3607f-150">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="3607f-151">*Cons:* uzun vadede dinamik türleri netlik olumsuz ve bir hizmetin istemci uygulamaları ile uyumluluk etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-151">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="3607f-152">Ayrıca, ara yazılımı Swagger gibi belgeleri aynı düzeyde döndürülen türlerinde dinamik türleri kullanıyorsanız sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="3607f-152">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="3607f-153">Önceden tanımlanmış DTO sınıflar olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="3607f-153">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="3607f-154">*Uzmanları:* "Sözleşme" açık DTO sınıfları esas alarak gibi statik önceden tanımlanmış ViewModel sınıfların olması için ortak API'ler de uzun vadeli mikro kesinlikle daha iyi yalnızca aynı uygulama tarafından kullanılan olsa bile.</span><span class="sxs-lookup"><span data-stu-id="3607f-154">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="3607f-155">Swagger için yanıt türlerini belirtmek istiyorsanız, dönüş türü olarak açık DTO sınıfları kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3607f-155">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="3607f-156">Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger daha zengin bilgi sunmanızı izin verin.</span><span class="sxs-lookup"><span data-stu-id="3607f-156">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="3607f-157">Bu API belgelerine ve uyumluluk bir API kullanırken artırır.</span><span class="sxs-lookup"><span data-stu-id="3607f-157">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="3607f-158">*Cons:* kodu güncelleştirirken daha önce belirtildiği gibi DTO sınıfları güncelleştirmek için daha fazla bazı adımlar alır.</span><span class="sxs-lookup"><span data-stu-id="3607f-158">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="3607f-159">*İpucu dayalı üzerinde deneyimi bizim:* eShopOnContainers içinde sıralama mikro hizmet sırasında uygulanan sorgularda biz çok basit ve Çevik üzerinde erken geliştirme aşamaları gibi dinamik ViewModels kullanarak geliştirme başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3607f-159">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="3607f-160">Ancak, geliştirme sabitlendi sonra "Sözleşme" kullanılan açık DTO türleri bilmeniz mikro 's tüketicileri nettir çünkü API'leri yeniden düzenlemeniz ve statik veya önceden tanımlanmış DTOs ViewModels için kullanmak seçtik.</span><span class="sxs-lookup"><span data-stu-id="3607f-160">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="3607f-161">Aşağıdaki örnekte, açık bir ViewModel DTO sınıfını kullanarak sorgu verileri nasıl döndürmektir görebilirsiniz: OrderSummary sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3607f-161">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="3607f-162">Web API'leri yanıt türlerini açıklayan</span><span class="sxs-lookup"><span data-stu-id="3607f-162">Describing response types of Web APIs</span></span>

<span data-ttu-id="3607f-163">Tüketen geliştiricilerin web API'ler ve mikro ne döndürülen ile en ilgili — özellikle yanıt türleri ve hata kodları (değil standart değilse).</span><span class="sxs-lookup"><span data-stu-id="3607f-163">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="3607f-164">Bunlar XML açıklamaları ve veri ek açıklamaları işlenir.</span><span class="sxs-lookup"><span data-stu-id="3607f-164">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="3607f-165">Swagger kullanıcı arabirimini uygun belgelerinde tüketici bilgi eksik hangi tür döndürülen veya hangi HTTP kodları döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3607f-165">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="3607f-166">Ekleyerek bu sorun düzeltilene <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, Swagger API dönüş modeli ve değerleri hakkında daha zengin bilgi aşağıdaki kodda gösterildiği gibi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3607f-166">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="3607f-167">Ancak, `ProducesResponseType` açık türleri gibi kullanmak için bir tür ancak gerektirdiğinden özniteliği dinamik kullanamaz `OrderSummary` ViewModel DTO, aşağıdaki örnekte gösterilen:</span><span class="sxs-lookup"><span data-stu-id="3607f-167">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="3607f-168">Açık döndürülen türleri uzun vadede dinamik türlerinden daha iyi neden başka bir neden de budur.</span><span class="sxs-lookup"><span data-stu-id="3607f-168">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="3607f-169">Kullanırken `ProducesResponseType` özniteliği, beklenen sonucu nedir belirtebilirsiniz 200,400 gibi bakımından olası HTTP hataları/kodları, vb.</span><span class="sxs-lookup"><span data-stu-id="3607f-169">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="3607f-170">Aşağıdaki görüntüde, Swagger kullanıcı arabirimini ResponseType bilgileri nasıl gösterir görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3607f-170">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="3607f-171">**Şekil 9-5**.</span><span class="sxs-lookup"><span data-stu-id="3607f-171">**Figure 9-5**.</span></span> <span data-ttu-id="3607f-172">Swagger kullanıcı Arabirimi yanıt türleri ve olası HTTP durum kodları Web API öğesinden gösterme</span><span class="sxs-lookup"><span data-stu-id="3607f-172">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="3607f-173">ViewModel türleri artı döndürülebilecek olası HTTP durum kodları temel bazı örnek değerler yukarıda görüntüsünde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3607f-173">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3607f-174">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3607f-174">Additional resources</span></span>

-   <span data-ttu-id="3607f-175">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="3607f-175">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="3607f-176">**Julie Lerman. Veri noktaları - Dapper, Entity Framework ve karma uygulamalar (MSDN Mag. makalesi)**</span><span class="sxs-lookup"><span data-stu-id="3607f-176">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="3607f-177">*https://msdn.microsoft.com/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="3607f-177">*https://msdn.microsoft.com/magazine/mt703432.aspx*</span></span>

-   <span data-ttu-id="3607f-178">**Swagger kullanan ASP.NET Core Web API Yardım Sayfaları**</span><span class="sxs-lookup"><span data-stu-id="3607f-178">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    <span data-ttu-id="3607f-179">*https://docs.microsoft.com/ASPNET/Core/Tutorials/Web-api-Help-Pages-using-swagger?Tabs=Visual-Studio*</span><span class="sxs-lookup"><span data-stu-id="3607f-179">*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="3607f-180">[Önceki] (eshoponcontainers-cqrs-bbb-microservice.md) [sonraki] (bbb-yönelimli-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="3607f-180">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
