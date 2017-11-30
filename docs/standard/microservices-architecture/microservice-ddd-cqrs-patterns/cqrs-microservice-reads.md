---
title: "Uygulama okuma/CQRS mikro hizmet sorguları"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Uygulama okuma/CQRS mikro hizmet sorguları"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="c1112-104">Uygulama okuma/CQRS mikro hizmet sorguları</span><span class="sxs-lookup"><span data-stu-id="c1112-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="c1112-105">Okuma/sorguları, sıralama mikro hizmet eShopOnContainers başvuru uygulamadan sorgularından bağımsız olarak DDD modelini ve işlem alanı uygular.</span><span class="sxs-lookup"><span data-stu-id="c1112-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="c1112-106">Öncelikle taleplerini sorgular ve işlemler için önemli ölçüde farklı olduğu için bu gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c1112-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="c1112-107">Yazma etki alanı mantığı ile uyumlu olması gereken işlemleri yürütün.</span><span class="sxs-lookup"><span data-stu-id="c1112-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="c1112-108">Sorguları, diğer yandan ıdempotent olan ve etki alanı kurallardan yinelenmeli.</span><span class="sxs-lookup"><span data-stu-id="c1112-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="c1112-109">Şekil 9-3'te gösterildiği gibi bir yaklaşım basittir.</span><span class="sxs-lookup"><span data-stu-id="c1112-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="c1112-110">API Arabirimi (örneğin, bir mikro ORM Dapper gibi) herhangi bir altyapı kullanarak ve dinamik ViewModels UI uygulamaları gereksinimlerine bağlı olarak döndüren Web API denetleyicilerinin tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c1112-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="c1112-111">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="c1112-111">**Figure 9-3**.</span></span> <span data-ttu-id="c1112-112">CQRS mikro hizmet sorguları için en kolay yaklaşım</span><span class="sxs-lookup"><span data-stu-id="c1112-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="c1112-113">Bu mod sorguları için en basit olası yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="c1112-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="c1112-114">Sorgu tanımları veritabanını sorgulamak ve her sorgu için kolay bir şekilde yerleşik dinamik bir ViewModel döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1112-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="c1112-115">Sorguları ıdempotent olduğundan, bir sorgu çalıştırmadan kaç kez olsun verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="c1112-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="c1112-116">Bu nedenle, işlem tarafındaki toplamalar ve diğer desenleri gibi kullanılan herhangi bir DDD modeliyle tarafından kısıtlanmış gerekmez ve sorguları işlem alanından ayrılmış neden.</span><span class="sxs-lookup"><span data-stu-id="c1112-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="c1112-117">Yalnızca kullanıcı arabirimini gereken veriler için veritabanını sorgulamak ve statik olarak olması gerekmez dinamik bir ViewModel her yerden (sınıflar ViewModels için) dışındaki SQL deyimlerini kendilerini tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1112-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="c1112-118">Bu basit bir yaklaşım olduğuna göre sorguları tarafı için gerekli kod (ORM gibi bir mikro kullanarak kod gibi [Dapper](https://github.com/StackExchange/Dapper)) uygulanabilir [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="c1112-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="c1112-119">Şekil 9-4 bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1112-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="c1112-120">Sorguları tanımlanan **Ordering.API** eShopOnContainers çözümünde mikro hizmet projesi.</span><span class="sxs-lookup"><span data-stu-id="c1112-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="c1112-121">**Şekil 9-4**.</span><span class="sxs-lookup"><span data-stu-id="c1112-121">**Figure 9-4**.</span></span> <span data-ttu-id="c1112-122">Sıralama mikro hizmet eShopOnContainers içinde sorguları</span><span class="sxs-lookup"><span data-stu-id="c1112-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="c1112-123">İstemci uygulamaları, etki alanı modeli kısıtlamaları bağımsız için özellikle yapılan ViewModels kullanma</span><span class="sxs-lookup"><span data-stu-id="c1112-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="c1112-124">İstemci uygulamaları tarafından gereken verileri almak için sorgular gerçekleştirilen olduğundan, döndürülen tür özellikle sorguları tarafından döndürülen verileri temel alan istemciler için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1112-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="c1112-125">Bu modeller ya da veri aktarım nesneleri (DTOs) ViewModels denir.</span><span class="sxs-lookup"><span data-stu-id="c1112-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="c1112-126">Döndürülen veriler (ViewModel) birden çok varlık veya tablo verileri veritabanında veya bile işlem alanı için etki alanı modelinde tanımlanan birden çok toplamalar arasında birleştirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1112-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="c1112-127">Bu durumda, sorguları etki alanı modeli bağımsız oluşturmakta olduğunuz çünkü toplamalar sınırları ve kısıtlamaları tamamen yoksayılır ve tüm tablo ve sütun gereksinim duyabileceğiniz sorgu boş.</span><span class="sxs-lookup"><span data-stu-id="c1112-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="c1112-128">Bu yaklaşım, oluşturma veya güncelleştirme sorguları geliştiriciler için büyük esneklik ve verimlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1112-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="c1112-129">ViewModels sınıflarda tanımlanan statik türler olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1112-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="c1112-130">Ya da yöneticiler geliştiricileri için çok Çevik olduğu (sıralama mikro hizmet içinde uygulanan gibi) gerçekleştirilecek sorgularına göre dinamik olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c1112-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="c1112-131">Sorguları gerçekleştirmek için Dapper mikro ORM kullanma</span><span class="sxs-lookup"><span data-stu-id="c1112-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="c1112-132">Tüm mikro ORM, Entity Framework Çekirdek ya da bile düz ADO.NET sorgulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1112-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="c1112-133">Örnek uygulama için popüler bir mikro ORM iyi bir örnek olarak eShopOnContainers içinde sıralama mikro Dapper seçili.</span><span class="sxs-lookup"><span data-stu-id="c1112-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="c1112-134">Çok açık bir çerçeve olduğu için harika performans ile düz SQL sorguları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1112-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="c1112-135">Dapper kullanarak, erişebilir ve birden çok tabloyu birleştirme bir SQL sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1112-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="c1112-136">Dapper açık kaynaklı proje (Sam Saffron tarafından oluşturulan özgün) ve kullanılan yapı taşları parçası [yığın taşması](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="c1112-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="c1112-137">Dapper kullanmak için aracılığıyla yüklemeniz yeterlidir [Dapper NuGet paketi](https://www.nuget.org/packages/Dapper), aşağıdaki çizimde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="c1112-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="c1112-138">Ayrıca kullanarak bir eklemeniz gerekir, kodunuzu Dapper genişletme yöntemleri erişimi şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1112-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="c1112-139">Kodunuzda Dapper kullandığınızda, doğrudan System.Data.SqlClient ad alanında kullanılabilir SqlClient sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1112-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="c1112-140">QueryAsync yöntemi ve SqlClient sınıfını genişleten diğer genişletme yöntemleri aracılığıyla, sorguları yalnızca basit ve kullanıcı şekilde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1112-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="c1112-141">Dinamik ve statik ViewModels</span><span class="sxs-lookup"><span data-stu-id="c1112-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="c1112-142">Aşağıdaki kodu sıralama mikro hizmet ile gösterildiği gibi sorguları tarafından döndürülen ViewModels çoğunu olarak uygulanan *dinamik*.</span><span class="sxs-lookup"><span data-stu-id="c1112-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="c1112-143">Döndürülecek öznitelik alt sorguyu temel alan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c1112-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="c1112-144">Birleştirme ve sorgu için yeni bir sütun eklerseniz, bu verileri döndürülen ViewModel dinamik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="c1112-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="c1112-145">Bu yaklaşım, bu tasarım yaklaşımı daha esnek ve gelecekteki değişiklikler dayanıklı hale veri modeli, güncelleştirmelerinin yanıta sorgularda değiştirmek için gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="c1112-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

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

<span data-ttu-id="c1112-146">Dinamik tür kullanarak, döndürülen verilerin toplanmasını dinamik olarak ViewModel birleştirilen, önemli noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="c1112-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="c1112-147">Sorguların çoğu için kolay ve verimli hale getirir bunları kodlama bir DTO veya ViewModel sınıfı önceden gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c1112-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="c1112-148">Ancak, sözleşmeleri olarak daha kısıtlı bir tanımıyla ViewModels sahip olmak istiyorsanız (örneğin, önceden tanımlanmış DTOs) ViewModels önceden belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1112-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="c1112-149">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c1112-149">Additional resources</span></span>

-   <span data-ttu-id="c1112-150">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="c1112-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="c1112-151">**Julie Lerman. Veri noktaları - Dapper, Entity Framework ve karma uygulamalar (MSDN Mag. makalesi)**</span><span class="sxs-lookup"><span data-stu-id="c1112-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="c1112-152">*https://msdn.microsoft.com/en-us/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="c1112-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c1112-153">[Önceki] (eshoponcontainers-cqrs-bbb-microservice.md) [sonraki] (bbb-yönelimli-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="c1112-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
