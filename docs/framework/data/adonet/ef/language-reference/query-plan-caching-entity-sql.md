---
description: 'Daha fazla bilgi edinin: sorgu planı önbelleğe alma (Entity SQL)'
title: Sorgu planı önbelleğe alma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: eee8e3afcd6f97b7e6021389d59a8ce03507fb9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802105"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="21d1c-103">Sorgu planı önbelleğe alma (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="21d1c-103">Query Plan Caching (Entity SQL)</span></span>

<span data-ttu-id="21d1c-104">Sorgu yürütme girişimi yapıldığında sorgu işlem hattı, tam sorgunun zaten derlenmiş ve kullanılabilir olup olmadığını görmek için kendi sorgu planı önbelleğini arar.</span><span class="sxs-lookup"><span data-stu-id="21d1c-104">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="21d1c-105">Bu durumda, yeni bir tane oluşturmak yerine önbelleğe alınmış planı yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-105">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="21d1c-106">Sorgu planı önbelleğinde eşleşme bulunmazsa sorgu derlenir ve önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-106">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="21d1c-107">Bir sorgu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metni ve parametre koleksiyonuyla tanımlanır (adlar ve türler).</span><span class="sxs-lookup"><span data-stu-id="21d1c-107">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="21d1c-108">Tüm metin karşılaştırmaları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-108">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="21d1c-109">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="21d1c-109">Configuration</span></span>  

 <span data-ttu-id="21d1c-110">Sorgu planı önbelleğe alma, aracılığıyla yapılandırılabilir <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="21d1c-110">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="21d1c-111">Sorgu planını önbelleğe almayı etkinleştirmek veya devre dışı bırakmak için <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType> , bu özelliği `true` veya olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="21d1c-111">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="21d1c-112">Daha sonra çok fazla kullanılması olası dinamik sorgular için plan önbelleğe alma işlemi devre dışı bırakılıyor performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="21d1c-112">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="21d1c-113">Sorgu planı önbelleğe almayı ' de etkinleştirebilirsiniz <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A> .</span><span class="sxs-lookup"><span data-stu-id="21d1c-113">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="21d1c-114">Önerilen uygulama</span><span class="sxs-lookup"><span data-stu-id="21d1c-114">Recommended Practice</span></span>  

 <span data-ttu-id="21d1c-115">Dinamik sorgular, genel olarak kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-115">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="21d1c-116">Aşağıdaki dinamik sorgu örneği SQL ekleme saldırılarına karşı savunmasız olduğundan, Kullanıcı girişini herhangi bir doğrulama olmadan doğrudan alır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-116">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="21d1c-117">Dinamik olarak oluşturulan sorguları kullanıyorsanız, yeniden kullanılması olası olmayan önbellek girdileri için gereksiz bellek tüketimini önlemek üzere sorgu planı önbelleğe almayı devre dışı bırakmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="21d1c-117">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="21d1c-118">Statik sorgularda ve parametreli sorgularda sorgu planı önbelleğe alma, performans avantajları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="21d1c-118">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="21d1c-119">Statik sorguya bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="21d1c-119">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="21d1c-120">Sorguların sorgu planı önbelleği tarafından düzgün şekilde eşleştirileceği için, aşağıdaki gereksinimlere uymaları gerekir:</span><span class="sxs-lookup"><span data-stu-id="21d1c-120">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="21d1c-121">Sorgu metni, tercihen sabit bir dize veya kaynak olmak üzere sabit bir model olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-121">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="21d1c-122"><xref:System.Data.EntityClient.EntityParameter> ya da <xref:System.Data.Objects.ObjectParameter> Kullanıcı tarafından sağlanan değerin geçirilmesi gereken her yerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21d1c-122"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="21d1c-123">Sorgu planı önbelleğinde gereksiz yuva kullanan aşağıdaki sorgu desenlerinden kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="21d1c-123">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="21d1c-124">Metinde harf durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="21d1c-124">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="21d1c-125">Boşluk olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="21d1c-125">Changes to white space.</span></span>  
  
- <span data-ttu-id="21d1c-126">Değişmez değerler üzerindeki değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="21d1c-126">Changes to literal values.</span></span>  
  
- <span data-ttu-id="21d1c-127">Açıklamaların içindeki metinde yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="21d1c-127">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d1c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21d1c-128">See also</span></span>

- [<span data-ttu-id="21d1c-129">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="21d1c-129">Entity SQL Overview</span></span>](entity-sql-overview.md)
