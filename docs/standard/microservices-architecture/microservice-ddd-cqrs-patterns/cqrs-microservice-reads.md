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
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="d9c80-103">CQRS mikro hizmetinde okuma/sorgulama uygulayın</span><span class="sxs-lookup"><span data-stu-id="d9c80-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="d9c80-104">Okuma/sorgulama için sıralama mikro hizmetine başvuru uygulamadan sorgularından bağımsız olarak işlem alan ve DDD modeli uygular.</span><span class="sxs-lookup"><span data-stu-id="d9c80-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="d9c80-105">Öncelikle taleplerini sorgular ve işlemler için önemli ölçüde farklı olduğundan bu yapıldı.</span><span class="sxs-lookup"><span data-stu-id="d9c80-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="d9c80-106">Yazma işlemleri, etki alanı mantığı ile uyumlu olması gereken işlemler yürütün.</span><span class="sxs-lookup"><span data-stu-id="d9c80-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="d9c80-107">Sorgular, diğer taraftan, eşgüçlüdür ve etki alanı kurallardan ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d9c80-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="d9c80-108">Şekil 7-3'te gösterildiği gibi basit yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="d9c80-109">API arabirimi, bir nesne ilişkisel Eşleyici (ORM) gibi Dapper, mikro gibi herhangi bir altyapının kullanarak ve kullanıcı Arabirimi uygulama gereksinimlerine bağlı olarak dinamik Viewmodel'lar döndüren Web APİ'si denetleyicilerinin tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Basitleştirilmiş bir CQRS yaklaşımı, sorguları tarafı için en kolay yaklaşım, veritabanı ile bir mikro-dinamik Viewmodel'lar döndüren ORM Dapper gibi sorgulayarak uygulanabilir.](./media/image3.png)

<span data-ttu-id="d9c80-111">**Şekil 7-3**.</span><span class="sxs-lookup"><span data-stu-id="d9c80-111">**Figure 7-3**.</span></span> <span data-ttu-id="d9c80-112">CQRS mikro hizmet sorguları için en kolay yaklaşım</span><span class="sxs-lookup"><span data-stu-id="d9c80-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="d9c80-113">Sorgular için olası en kolay yaklaşım budur.</span><span class="sxs-lookup"><span data-stu-id="d9c80-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="d9c80-114">Sorgu tanımları, bu veritabanını sorgulamanızı ve her bir sorgu için hareket halindeyken yerleşik dinamik bir ViewModel döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c80-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="d9c80-115">Sorgular tekrar denenebilir yapıda olduğundan, bunlar bir sorgu çalıştırmadan kaç kez ne olursa olsun veri değişmez.</span><span class="sxs-lookup"><span data-stu-id="d9c80-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="d9c80-116">Bu nedenle, toplamlar ve diğer desenleri gibi işlem tarafında kullanılan tüm DDD deseni tarafından kısıtlı gerekmez ve sorguları işlem alanından ayrılmış neden olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="d9c80-117">Yalnızca kullanıcı Arabirimi gereken veriler için bu veritabanını sorgulamanızı ve statik türlü olması gerekmez dinamik bir ViewModel her yerden (sınıflar için Viewmodel'lar) dışında SQL deyimleri kendilerini tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c80-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="d9c80-118">Bu basit yaklaşım olduğundan, sorgu yan için gerekli kod (ORM gibi bir mikro kullanarak kod gibi [Dapper](https://github.com/StackExchange/Dapper)) uygulanabilir [aynı Web API projesi içinde](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="d9c80-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="d9c80-119">Şekil 7-4'te bu durum gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="d9c80-120">Sorguları tanımlanan **Ordering.API** hizmetine çözüm içinde mikro hizmet projesi.</span><span class="sxs-lookup"><span data-stu-id="d9c80-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Çözüm Gezgini görünümü uygulamanın gösterildiği Ordering.API projenin > sorgular klasörüne.](./media/image4.png)

<span data-ttu-id="d9c80-122">**Şekil 7-4**.</span><span class="sxs-lookup"><span data-stu-id="d9c80-122">**Figure 7-4**.</span></span> <span data-ttu-id="d9c80-123">Sıralama mikro hizmetine sorguları</span><span class="sxs-lookup"><span data-stu-id="d9c80-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="d9c80-124">İstemci uygulamaları için özel etki alanı modeli kısıtlamalardan bağımsız yapılan Viewmodel'lar kullanın</span><span class="sxs-lookup"><span data-stu-id="d9c80-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="d9c80-125">Sorgular, istemci uygulamalar için gerekli verileri almak için yapıldığından, döndürülen türü özellikle sorguları tarafından döndürülen verilere bağlı olarak, istemciler için yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="d9c80-126">Bu modeller ya da veri aktarımı nesneleri (Dto'lar) Viewmodel'lar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="d9c80-127">Döndürülen veriler (ViewModel), birden çok varlıklar veya tablolar verileri veritabanında veya bile işlem alanı için etki alanı modelde tanımlanan birden çok toplamalar arasında birleştirme sonucu olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="d9c80-128">Bu durumda, sorguları bağımsız olarak etki alanı modeli oluşturmakta olduğunuz çünkü toplamalar sınırları ve kısıtlamaları tamamen yoksayılır ve tüm tablo ve sütun ihtiyacınız olabilecek sorgulamak boş.</span><span class="sxs-lookup"><span data-stu-id="d9c80-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="d9c80-129">Bu yaklaşım, oluşturma veya güncelleştirme sorguları geliştiriciler için büyük esneklik ve verimlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9c80-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="d9c80-130">Viewmodel'lar sınıflarında tanımlanan statik türler olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="d9c80-131">Veya, geliştiriciler için çok Çevik olduğu (sıralama mikro hizmet içinde uygulanan gibi) gerçekleştirilen sorgularına göre dinamik olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="d9c80-132">Dapper sorguları gerçekleştirmek için bir mikro ORM kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9c80-132">Use Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="d9c80-133">Tüm mikro ORM, Entity Framework Core veya bile düz ADO.NET sorgulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9c80-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="d9c80-134">Örnek uygulamada Dapper sıralama mikro hizmetine popüler bir mikro ORM iyi bir örnek olarak seçilmiş.</span><span class="sxs-lookup"><span data-stu-id="d9c80-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="d9c80-135">Çünkü çok açık bir çerçeve muhteşem bir performans ile düz SQL sorguları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9c80-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="d9c80-136">Dapper kullanarak erişebilir ve birden çok tabloları birleştirme bir SQL sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9c80-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="d9c80-137">Dapper (Sam Saffron tarafından oluşturulan özgün) açık kaynaklı bir projedir ve kullanılan yapı taşlarını parçasıdır [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="d9c80-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="d9c80-138">Dapper kullanılacak aracılığıyla yüklemeniz yeterlidir [Dapper NuGet paketini](https://www.nuget.org/packages/Dapper)aşağıdaki şekilde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d9c80-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![VS manage NuGet paketleri görünümünde görüntülenen olarak Dapper paket.](./media/image4.1.png)

<span data-ttu-id="d9c80-140">Kullanarak bir ekleme gerekir kodunuzu Dapper genişletme yöntemleri erişimi için deyimi.</span><span class="sxs-lookup"><span data-stu-id="d9c80-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="d9c80-141">Kodunuzda Dapper kullandığınızda, doğrudan kullanmanız <xref:System.Data.SqlClient.SqlConnection> sınıfı bulunan <xref:System.Data.SqlClient> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d9c80-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="d9c80-142">QueryAsync yöntemi ve genişleten çakışabilecek genişletme yöntemlerine aracılığıyla <xref:System.Data.SqlClient.SqlConnection> sınıfı, yalnızca çalıştırabilirsiniz sorguları basit ve etkili bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="d9c80-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="d9c80-143">Dinamik görünümler ve Viewmodel'lar statik</span><span class="sxs-lookup"><span data-stu-id="d9c80-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="d9c80-144">Viewmodel'lar istemci uygulamaları için sunucu tarafı döndürülürken, istemci uygulamanın bu Viewmodel'lar hakkında Viewmodel'lar veri yolu değiştiğinden, varlık model iç etki alanı varlıklarının farklı olabilir Dto'lar (veri aktarımı nesneleri) düşünebilirsiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="d9c80-145">Bu nedenle, çoğu durumda, birden çok etki alanı varlıklardan gelen veri toplama ve istemci uygulamanın bu verilere nasıl gerekir tam olarak göre Viewmodel'lar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9c80-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="d9c80-146">Bu Viewmodel'lar veya Dto'lar (verilerin sahibi sınıflar) olarak açıkça gibi tanımlanabilir `OrderSummary` sınıfı bir sonraki kod parçacığı veya, gösterilen dinamik Viewmodel'lar veya yalnızca dinamik, sorgu tarafından döndürülen öznitelikleri temel alan dinamik Dto'lar yalnızca döndürebilir yazın.</span><span class="sxs-lookup"><span data-stu-id="d9c80-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="d9c80-147">Dinamik tür olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="d9c80-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="d9c80-148">Aşağıdaki kodda gösterildiği gibi bir `ViewModel` yalnızca döndüren sorgular tarafından doğrudan döndürülebilir bir *dinamik* dahili olarak bir sorgu tarafından döndürülen öznitelikleri temel alan türü.</span><span class="sxs-lookup"><span data-stu-id="d9c80-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="d9c80-149">Döndürülecek öznitelik alt kümesinden sorguyu temel alan, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="d9c80-150">Birleştirme ve sorgu için yeni bir sütun ekleyin, bu nedenle, bu verileri dinamik ise döndürülen eklenen `ViewModel`.</span><span class="sxs-lookup"><span data-stu-id="d9c80-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="d9c80-151">Dinamik tür kullanarak, döndürülen verilerin toplanmasını dinamik olarak ViewModel derlendiğinden emin önemli noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="d9c80-152">**Uzmanları:** Bu yaklaşım, bu tasarım yaklaşımı oldukça kodlama, Çevik, basit ve hızlı in regard to gelecek değişiklikler geliştirilebilen yapmadan bir sorgunun SQL cümlenin güncelleştirdiğinizde statik ViewModel sınıfları değiştirmek için gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="d9c80-153">**Cons:** Uzun vadede açıklık ve uyumluluk bir hizmetin istemci uygulamaları ile dinamik türleri olumsuz yönde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="d9c80-154">Buna ek olarak, Swashbuckle gibi ara yazılım belgeleri aynı düzeyde döndürülen türleri üzerinde dinamik türleri kullanıyorsanız sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="d9c80-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="d9c80-155">Önceden tanımlanmış DTO sınıflar olarak ViewModel</span><span class="sxs-lookup"><span data-stu-id="d9c80-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="d9c80-156">**Uzmanları**: Yalnızca aynı uygulama tarafından kullanılan bile "Sözleşme" açık DTO sınıflarında dayanan storsimple çözümü gibi statik önceden tanımlanmış ViewModel sınıfları sahip kesinlikle de uzun vadeli mikro hizmetler, ortak API'ler için iyidir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="d9c80-157">Yanıt türleri için Swagger belirtmek istiyorsanız, dönüş türü olarak açık DTO sınıfları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="d9c80-158">Bu nedenle, önceden tanımlanmış DTO sınıfları Swagger'a daha zengin bilgi sunan olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9c80-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="d9c80-159">API belgeleri ve uyumluluğu API tüketildiğinde geliştiren.</span><span class="sxs-lookup"><span data-stu-id="d9c80-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="d9c80-160">**Cons**: Kod güncelleştirilirken daha önce belirtildiği gibi bazı daha fazla adım DTO sınıfları güncelleştirmek için alır.</span><span class="sxs-lookup"><span data-stu-id="d9c80-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="d9c80-161">*İpucu deneyimimizi üzerinde temel*: Sorgularda sıralama mikro hizmetine sırasında uygulanan çok kolay ve Çevik erken geliştirme aşamalarına üzerinde dinamik Viewmodel'lar kullanarak geliştirme Başladık.</span><span class="sxs-lookup"><span data-stu-id="d9c80-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="d9c80-162">Ancak, geliştirme istikrarlı sonra "Sözleşme" kullanılan, açık DTO türleri bilmek mikro hizmet'ın Tüketiciler için nettir API'leri yeniden düzenleyin ve Viewmodel'lar için statik ya da önceden tanımlanmış bir Dto seçtik çünkü.</span><span class="sxs-lookup"><span data-stu-id="d9c80-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="d9c80-163">Aşağıdaki örnekte, bir açık ViewModel DTO sınıfını kullanarak sorgu verilerini nasıl döndürmektir görebilirsiniz: OrderSummary sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d9c80-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="d9c80-164">Web API yanıt türleri açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="d9c80-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="d9c80-165">Kullanan geliştiriciler web API'leri ve mikro hizmetler hangi iade ile en ilgili — özellikle yanıt türleri ve hata kodları (standart varsa).</span><span class="sxs-lookup"><span data-stu-id="d9c80-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="d9c80-166">Bunlar, XML açıklamaları ve verileri ek açıklamalar içinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="d9c80-167">Swagger kullanıcı arabirimini uygun belgelerinde tüketici bilgi eksik hangi tür döndürülen veya hangi HTTP kodları döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="d9c80-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="d9c80-168">Ekleyerek bu sorun düzeltilene <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, Swashbuckle aşağıdaki kodda gösterildiği gibi değerleri ve API dönüş modeli hakkında daha zengin bilgi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d9c80-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="d9c80-169">Ancak, `ProducesResponseType` açık türleri gibi kullanmak için bir tür ancak gerektirdiği özniteliği dinamik kullanamaz `OrderSummary` ViewModel DTO, aşağıdaki örnekte gösterilen:</span><span class="sxs-lookup"><span data-stu-id="d9c80-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="d9c80-170">Açık döndürülen türleri ve uzun vadede dinamik türlerinden daha iyi neden başka bir nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="d9c80-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="d9c80-171">Kullanırken `ProducesResponseType` özniteliği, ilgili olası HTTP hataları/kodları, beklenen sonucu gibi nedir belirtebilirsiniz 200, 400, vs.</span><span class="sxs-lookup"><span data-stu-id="d9c80-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="d9c80-172">Aşağıdaki görüntüde, Swagger kullanıcı arabirimini ResponseType bilgileri gösterilmektedir görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9c80-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Swagger kullanıcı arabirimini sayfasının tarayıcı görünümünü sıralama API.](./media/image5.png)

<span data-ttu-id="d9c80-174">**Şekil 7-5**.</span><span class="sxs-lookup"><span data-stu-id="d9c80-174">**Figure 7-5**.</span></span> <span data-ttu-id="d9c80-175">Swagger kullanıcı Arabirimi yanıt türleri ve olası HTTP durum kodları, bir Web API'si gösteriliyor</span><span class="sxs-lookup"><span data-stu-id="d9c80-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="d9c80-176">ViewModel türüne ek olarak döndürülebilecek olası HTTP durum kodları hakkında temel bazı örnek değerler yukarıdaki görüntüde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9c80-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d9c80-177">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d9c80-177">Additional resources</span></span>

- <span data-ttu-id="d9c80-178">**Dapper** \\</span><span class="sxs-lookup"><span data-stu-id="d9c80-178">**Dapper** \\</span></span>
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="d9c80-179">**Julie Lerman. Veri noktaları - Dapper, Entity Framework ve karma uygulamalar (MSDN Mag. makalesi)** \\</span><span class="sxs-lookup"><span data-stu-id="d9c80-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)** \\</span></span>
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- <span data-ttu-id="d9c80-180">**ASP.NET Core Web API'si Swagger kullanan Yardım sayfaları** \\</span><span class="sxs-lookup"><span data-stu-id="d9c80-180">**ASP.NET Core Web API Help Pages using Swagger** \\</span></span>
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="d9c80-181">[Önceki](eshoponcontainers-cqrs-ddd-microservice.md)
>[İleri](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="d9c80-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
