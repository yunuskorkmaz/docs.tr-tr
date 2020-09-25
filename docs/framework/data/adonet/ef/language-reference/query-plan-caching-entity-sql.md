---
title: Sorgu planı önbelleğe alma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 51c5de8365819065f8e505468f37a47370ec502f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175559"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="51dad-102">Sorgu planı önbelleğe alma (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="51dad-102">Query Plan Caching (Entity SQL)</span></span>

<span data-ttu-id="51dad-103">Sorgu yürütme girişimi yapıldığında sorgu işlem hattı, tam sorgunun zaten derlenmiş ve kullanılabilir olup olmadığını görmek için kendi sorgu planı önbelleğini arar.</span><span class="sxs-lookup"><span data-stu-id="51dad-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="51dad-104">Bu durumda, yeni bir tane oluşturmak yerine önbelleğe alınmış planı yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="51dad-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="51dad-105">Sorgu planı önbelleğinde eşleşme bulunmazsa sorgu derlenir ve önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="51dad-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="51dad-106">Bir sorgu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metni ve parametre koleksiyonuyla tanımlanır (adlar ve türler).</span><span class="sxs-lookup"><span data-stu-id="51dad-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="51dad-107">Tüm metin karşılaştırmaları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="51dad-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="51dad-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="51dad-108">Configuration</span></span>  

 <span data-ttu-id="51dad-109">Sorgu planı önbelleğe alma, aracılığıyla yapılandırılabilir <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="51dad-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="51dad-110">Sorgu planını önbelleğe almayı etkinleştirmek veya devre dışı bırakmak için <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType> , bu özelliği `true` veya olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="51dad-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="51dad-111">Daha sonra çok fazla kullanılması olası dinamik sorgular için plan önbelleğe alma işlemi devre dışı bırakılıyor performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="51dad-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="51dad-112">Sorgu planı önbelleğe almayı ' de etkinleştirebilirsiniz <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A> .</span><span class="sxs-lookup"><span data-stu-id="51dad-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="51dad-113">Önerilen uygulama</span><span class="sxs-lookup"><span data-stu-id="51dad-113">Recommended Practice</span></span>  

 <span data-ttu-id="51dad-114">Dinamik sorgular, genel olarak kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51dad-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="51dad-115">Aşağıdaki dinamik sorgu örneği SQL ekleme saldırılarına karşı savunmasız olduğundan, Kullanıcı girişini herhangi bir doğrulama olmadan doğrudan alır.</span><span class="sxs-lookup"><span data-stu-id="51dad-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="51dad-116">Dinamik olarak oluşturulan sorguları kullanıyorsanız, yeniden kullanılması olası olmayan önbellek girdileri için gereksiz bellek tüketimini önlemek üzere sorgu planı önbelleğe almayı devre dışı bırakmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="51dad-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="51dad-117">Statik sorgularda ve parametreli sorgularda sorgu planı önbelleğe alma, performans avantajları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="51dad-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="51dad-118">Statik sorguya bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51dad-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="51dad-119">Sorguların sorgu planı önbelleği tarafından düzgün şekilde eşleştirileceği için, aşağıdaki gereksinimlere uymaları gerekir:</span><span class="sxs-lookup"><span data-stu-id="51dad-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="51dad-120">Sorgu metni, tercihen sabit bir dize veya kaynak olmak üzere sabit bir model olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51dad-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="51dad-121"><xref:System.Data.EntityClient.EntityParameter> ya da <xref:System.Data.Objects.ObjectParameter> Kullanıcı tarafından sağlanan değerin geçirilmesi gereken her yerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="51dad-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="51dad-122">Sorgu planı önbelleğinde gereksiz yuva kullanan aşağıdaki sorgu desenlerinden kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="51dad-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="51dad-123">Metinde harf durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="51dad-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="51dad-124">Boşluk olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="51dad-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="51dad-125">Değişmez değerler üzerindeki değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="51dad-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="51dad-126">Açıklamaların içindeki metinde yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="51dad-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51dad-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51dad-127">See also</span></span>

- [<span data-ttu-id="51dad-128">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="51dad-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
