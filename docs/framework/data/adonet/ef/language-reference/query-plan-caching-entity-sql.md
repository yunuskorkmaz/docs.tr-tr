---
title: Sorgu Planı Önbelleğe Alma (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149992"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="e937a-102">Sorgu Planı Önbelleğe Alma (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e937a-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="e937a-103">Sorguyu yürütme girişimi yapıldığında, sorgu ardışık lığı tam sorgunun zaten derlenip derlenmediğini ve kullanılabilir olup olmadığını görmek için sorgu planı önbelleğini arar.</span><span class="sxs-lookup"><span data-stu-id="e937a-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="e937a-104">Bu öyleyse, yeni bir plan oluşturmak yerine önbelleğe alınmış planı yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="e937a-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="e937a-105">Sorgu planı önbelleğinde eşleşme bulunmazsa, sorgu derlenir ve önbelleğe çıkar.</span><span class="sxs-lookup"><span data-stu-id="e937a-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="e937a-106">Sorgu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metin ve parametre koleksiyonu (adlar ve türleri) ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e937a-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="e937a-107">Tüm metin karşılaştırmaları büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e937a-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="e937a-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e937a-108">Configuration</span></span>  
 <span data-ttu-id="e937a-109">Sorgu planı önbelleğe alma <xref:System.Data.EntityClient.EntityCommand>yoluyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e937a-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="e937a-110">Sorgu planını etkinleştirmek veya devre <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>dışı kalım `true` sağlamak `false`için, bu özelliği veya ' ı ayarla</span><span class="sxs-lookup"><span data-stu-id="e937a-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="e937a-111">Bir kez performansı artırır daha sonra daha fazla kullanılması olası değildir bireysel dinamik sorguları için plan önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="e937a-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="e937a-112">Sorgu planı önbelleğe'yi <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e937a-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="e937a-113">Önerilen Uygulama</span><span class="sxs-lookup"><span data-stu-id="e937a-113">Recommended Practice</span></span>  
 <span data-ttu-id="e937a-114">Genel olarak dinamik sorgulardan kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e937a-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="e937a-115">Aşağıdaki dinamik sorgu örneği, kullanıcı girişini herhangi bir doğrulama olmadan doğrudan aldığından, SQL enjeksiyon saldırılarına karşı savunmasızdır.</span><span class="sxs-lookup"><span data-stu-id="e937a-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="e937a-116">Dinamik olarak oluşturulan sorgular kullanıyorsanız, yeniden kullanılma olasılığı düşük önbellek girişleri için gereksiz bellek tüketiminden kaçınmak için sorgu planı önbelleğe almamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e937a-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="e937a-117">Statik sorgularda ve parametreli sorgularda önbelleğe alma sorgusu performansı avantajları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e937a-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="e937a-118">Statik bir sorgu örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e937a-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="e937a-119">Sorguların sorgu planı önbelleği tarafından düzgün bir şekilde eşleşebilmek için aşağıdaki gereksinimlere uymaları gerekir:</span><span class="sxs-lookup"><span data-stu-id="e937a-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="e937a-120">Sorgu metni sabit bir desen, tercihen sabit bir dize veya kaynak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e937a-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="e937a-121"><xref:System.Data.EntityClient.EntityParameter>veya <xref:System.Data.Objects.ObjectParameter> kullanıcı tarafından sağlanan bir değerin geçirilmesi gereken her yerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e937a-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="e937a-122">Sorgu planı önbelleğinde gereksiz yere yuva tüketen aşağıdaki sorgu desenlerinden kaçınmalısınız:</span><span class="sxs-lookup"><span data-stu-id="e937a-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="e937a-123">Metindeki harf örneğinde değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e937a-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="e937a-124">Beyaz boşlukta değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e937a-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="e937a-125">Gerçek değerlerde değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e937a-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="e937a-126">Açıklamaların içindeki metinde yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="e937a-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e937a-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e937a-127">See also</span></span>

- [<span data-ttu-id="e937a-128">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e937a-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
