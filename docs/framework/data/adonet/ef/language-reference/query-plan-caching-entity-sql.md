---
title: Sorgu planını önbelleğe alma (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9f042d46d9a601c1091e36f8d81ce8f933140b20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178184"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="e70bd-102">Sorgu planını önbelleğe alma (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e70bd-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="e70bd-103">Her bir sorgu yürütme girişimi yapıldığında, sorgu işlem hattındaki tam sorgu zaten derlenmiş ve kullanılabilir olup olmadığını görmek için sorgu planı önbelleği arar.</span><span class="sxs-lookup"><span data-stu-id="e70bd-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="e70bd-104">Bu durumda, yeni bir tane oluşturmak yerine önbellekteki plan kullanır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="e70bd-105">Sorgu planı önbellekte bir eşleşme bulunmazsa, sorgu derlenmiş ve önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="e70bd-106">Bir sorgu tarafından tanımlanan kendi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metin ve parametre koleksiyonu (adlarını ve türlerini).</span><span class="sxs-lookup"><span data-stu-id="e70bd-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="e70bd-107">Tüm metin karşılaştırmalar büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e70bd-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e70bd-108">Configuration</span></span>  
 <span data-ttu-id="e70bd-109">Sorgu planını önbelleğe alma aracılığıyla yapılandırılabilir <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="e70bd-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="e70bd-110">Etkinleştirme veya devre dışı aracılığıyla sorgu planını önbelleğe alma <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, bu özelliği ayarlayın `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="e70bd-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="e70bd-111">Plan düşüktür bireysel dinamik sorgular için önbelleğe alma devre dışı bırakılması daha sonra bir kez kullanılacak performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="e70bd-112">Aracılığıyla sorgu planını önbelleğe alma etkinleştirebilirsiniz <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="e70bd-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="e70bd-113">Önerilen uygulama</span><span class="sxs-lookup"><span data-stu-id="e70bd-113">Recommended Practice</span></span>  
 <span data-ttu-id="e70bd-114">Dinamik sorgular, genellikle kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="e70bd-115">Herhangi bir doğrulama olmadan doğrudan kullanıcı girişi aldığından aşağıdaki dinamik sorgu örnek SQL enjeksiyon saldırılarına karşı savunmasızdır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="e70bd-116">Dinamik olarak üretilen sorguları kullanırsanız, gereksiz bellek tüketimi için kullanılabilmeleri düşüktür önbellek girişlerinin önlemek için sorgu planını önbelleğe alma devre dışı bırakmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e70bd-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="e70bd-117">Statik sorguları önbelleğe alma ve sorgu parametreli bir sorgu planı performans avantajları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="e70bd-118">Statik bir sorgu örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e70bd-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="e70bd-119">Sorguların sorgu planı önbelleği tarafından düzgün şekilde eşlenmesi için aşağıdaki gereksinimlere uyması:</span><span class="sxs-lookup"><span data-stu-id="e70bd-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
-   <span data-ttu-id="e70bd-120">Sorgu metni, sabit bir desen, tercihen bir sabit dize veya bir kaynak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
-   <xref:System.Data.EntityClient.EntityParameter> <span data-ttu-id="e70bd-121">veya <xref:System.Data.Objects.ObjectParameter> bir kullanıcı tarafından sağlanan değer geçirilen her yerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-121">or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="e70bd-122">Sorgu planını önbelleğe yuvalarda gereksiz yere kullanmak aşağıdaki sorgu desenleri kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e70bd-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
-   <span data-ttu-id="e70bd-123">Metindeki büyük küçük harf yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e70bd-123">Changes to letter case in the text.</span></span>  
  
-   <span data-ttu-id="e70bd-124">Boşluk yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e70bd-124">Changes to white space.</span></span>  
  
-   <span data-ttu-id="e70bd-125">Değişmez değerler geçer.</span><span class="sxs-lookup"><span data-stu-id="e70bd-125">Changes to literal values.</span></span>  
  
-   <span data-ttu-id="e70bd-126">Metin açıklama içinde yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e70bd-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70bd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e70bd-127">See also</span></span>

- [<span data-ttu-id="e70bd-128">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e70bd-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
