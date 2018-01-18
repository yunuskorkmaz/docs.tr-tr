---
title: "Sorgu planı (varlık SQL) önbelleğe alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f3ff908102671e2b22cb3ebb5af55e86bd791c43
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="b8f99-102">Sorgu planı (varlık SQL) önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="b8f99-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="b8f99-103">Sorgu yürütme denemesi yapıldığında, sorgu ardışık düzen tam sorgu önceden derlenmiş ve kullanılabilir olup olmadığını görmek için sorgu planı önbelleğini arar.</span><span class="sxs-lookup"><span data-stu-id="b8f99-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="b8f99-104">Bu durumda, yeni bir tane oluşturmak yerine önbelleğe alınmış planı yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="b8f99-105">Eşleşen bir sorgu planı önbelleğinde bulunmazsa, sorgu derlenmiş ve önbelleğe alınmış.</span><span class="sxs-lookup"><span data-stu-id="b8f99-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="b8f99-106">Bir sorgu tarafından tanımlanan kendi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] metin ve parametre koleksiyonu (adları ve türlerini).</span><span class="sxs-lookup"><span data-stu-id="b8f99-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="b8f99-107">Tüm metin karşılaştırmaları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b8f99-108">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b8f99-108">Configuration</span></span>  
 <span data-ttu-id="b8f99-109">Sorgu planı önbelleğe alma aracılığıyla yapılandırılabilir <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="b8f99-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="b8f99-110">Etkinleştirmek veya sorgu planı aracılığıyla önbelleğe almayı devre dışı bırakmak için <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, bu özelliği ayarlamak `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="b8f99-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="b8f99-111">Plan olası tek tek dinamik sorgular için önbelleğe almayı devre dışı bırakılması daha sonra bir kez kullanılacak performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="b8f99-112">Sorgu planı aracılığıyla önbelleğe almayı etkinleştir <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8f99-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="b8f99-113">Önerilen uygulama</span><span class="sxs-lookup"><span data-stu-id="b8f99-113">Recommended Practice</span></span>  
 <span data-ttu-id="b8f99-114">Dinamik sorgular, genel kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="b8f99-115">Aşağıdaki dinamik sorgu örnek SQL ekleme saldırılarına karşı savunmasız çünkü tüm doğrulama olmadan doğrudan kullanıcı girişini alır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="b8f99-116">Dinamik olarak üretilen sorguları kullanırsanız, gereksiz bellek tüketimi yeniden başlatmasının önbellek girişlerini önlemek için sorgu planı önbelleğe almayı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b8f99-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="b8f99-117">Statik sorgulamaları önbelleğe alma ve sorguları Parametreli sorgu planı performans fayda sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b8f99-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="b8f99-118">Statik bir sorgunun bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b8f99-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="b8f99-119">Sorgu planı önbelleğinin düzgün eşleştirilmesini sorgular için bunlar aşağıdaki gereksinimlerle uyumlu olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b8f99-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
-   <span data-ttu-id="b8f99-120">Sorgu metni sabit bir desen, tercihen bir sabit dize veya bir kaynağı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
-   <span data-ttu-id="b8f99-121"><xref:System.Data.EntityClient.EntityParameter>veya <xref:System.Data.Objects.ObjectParameter> bir kullanıcı tarafından sağlanan değer geçirilmelidir her yerde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8f99-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="b8f99-122">Gereksiz yere sorgu planı önbellek yuvalarında tüketen aşağıdaki sorgu desenlerine kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b8f99-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
-   <span data-ttu-id="b8f99-123">Metindeki büyük küçük harf yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="b8f99-123">Changes to letter case in the text.</span></span>  
  
-   <span data-ttu-id="b8f99-124">Beyaz alan yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="b8f99-124">Changes to white space.</span></span>  
  
-   <span data-ttu-id="b8f99-125">Değişmez değerler geçer.</span><span class="sxs-lookup"><span data-stu-id="b8f99-125">Changes to literal values.</span></span>  
  
-   <span data-ttu-id="b8f99-126">Metin açıklamaları içinde yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="b8f99-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f99-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8f99-127">See Also</span></span>  
 [<span data-ttu-id="b8f99-128">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b8f99-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
