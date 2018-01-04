---
title: "CAST (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 97971668430dd7721b15a4ac60e422fe06f0ed1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cast-entity-sql"></a><span data-ttu-id="bf9c4-102">CAST (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="bf9c4-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="bf9c4-103">Bir veri türünde bir ifadenin diğerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf9c4-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf9c4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bf9c4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bf9c4-106">Parametresinin geçerli bir ifade `data_type`.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="bf9c4-107">Hedef sistem tarafından sağlanan veri türü.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-107">The target system-supplied data type.</span></span> <span data-ttu-id="bf9c4-108">Basit (skaler) bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="bf9c4-109">`data_type` Kullanılan sorgu alan bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="bf9c4-110">Bir sorgu ile yürütülürse <xref:System.Data.EntityClient.EntityCommand>, kavramsal modelde tanımlanan bir türü veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="bf9c4-111">Daha fazla bilgi için bkz: [CSDL belirtimi](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="bf9c4-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="bf9c4-112">Bir sorgu ile yürütülürse <xref:System.Data.Objects.ObjectQuery%601>, bir ortak dil çalışma zamanı (CLR) türü veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf9c4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bf9c4-113">Return Value</span></span>  
 <span data-ttu-id="bf9c4-114">Aynı değeri döndürür `data_type`.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf9c4-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf9c4-115">Remarks</span></span>  
 <span data-ttu-id="bf9c4-116">Cast ifadesi benzer bir semantik vardır [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] Çevir ifade.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-116">The cast expression has similar semantics to the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT expression.</span></span> <span data-ttu-id="bf9c4-117">Cast ifadesi, başka bir türdeki bir değere bir türde bir değer dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="bf9c4-118">E ise S ve S herhangi bir tür için T dönüştürülebilir olup, ardından geçerli cast ifadesi yukarıdaki ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="bf9c4-119">T ilkel (skaler) bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="bf9c4-120">Kesinlik ve ölçek yönü, isteğe bağlı olarak tür atama zaman sağlanabilir değerleri `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="bf9c4-121">Açıkça verdiyse, varsayılan duyarlık ve ölçek 18 ve 0, sırasıyla değerler.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="bf9c4-122">Özellikle, aşağıdaki aşırı yüklemeleri için desteklenen `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="bf9c4-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="bf9c4-123">Cast ifadesi kullanımını açık bir dönüştürme olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="bf9c4-124">Açık dönüşümler veri kesme veya duyarlık kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf9c4-125">CAST yalnızca ilkel türler ve Numaralandırma üye türleri üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf9c4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf9c4-126">Example</span></span>  
 <span data-ttu-id="bf9c4-127">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ATAMA işleci için başka bir veri türünde bir ifadeyi dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="bf9c4-128">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bf9c4-129">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bf9c4-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bf9c4-130">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bf9c4-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="bf9c4-131">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="bf9c4-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="bf9c4-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf9c4-132">See Also</span></span>  
 [<span data-ttu-id="bf9c4-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bf9c4-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
