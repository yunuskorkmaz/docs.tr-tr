---
description: 'Daha fazla bilgi edinin: CAST (Entity SQL)'
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: f6a90c0ec2557391c2da6e46511a020f90d32ab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739488"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="8c4e2-103">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8c4e2-103">CAST (Entity SQL)</span></span>

<span data-ttu-id="8c4e2-104">Bir veri türündeki bir ifadeyi bir diğerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-104">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c4e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c4e2-105">Syntax</span></span>  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c4e2-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8c4e2-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="8c4e2-107">Dönüştürülebilir herhangi bir geçerli ifade `data_type` .</span><span class="sxs-lookup"><span data-stu-id="8c4e2-107">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="8c4e2-108">Hedef sistem tarafından sağlanan veri türü.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-108">The target system-supplied data type.</span></span> <span data-ttu-id="8c4e2-109">Temel bir (skaler) türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-109">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="8c4e2-110">`data_type`Kullanılan sorgu alanına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-110">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="8c4e2-111">Bir sorgu ile yürütülürse <xref:System.Data.EntityClient.EntityCommand> , veri türü kavramsal modelde tanımlanan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-111">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="8c4e2-112">Daha fazla bilgi için bkz. [csdl belirtimi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="8c4e2-112">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span> <span data-ttu-id="8c4e2-113">Bir sorgu ile yürütülürse <xref:System.Data.Objects.ObjectQuery%601> , veri türü ortak dil çalışma zamanı (CLR) türüdür.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-113">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c4e2-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8c4e2-114">Return Value</span></span>  

 <span data-ttu-id="8c4e2-115">İle aynı değeri döndürür `data_type` .</span><span class="sxs-lookup"><span data-stu-id="8c4e2-115">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c4e2-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c4e2-116">Remarks</span></span>  

 <span data-ttu-id="8c4e2-117">Cast ifadesinin Transact-SQL CONVERT ifadesine benzer anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-117">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="8c4e2-118">Cast ifadesi bir tür değerini başka bir türün değerine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-118">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```csharp
CAST( e as T )  
```  
  
 <span data-ttu-id="8c4e2-119">E bazı tür ve S, T 'ye dönüştürülesiyse, yukarıdaki ifade geçerli bir atama ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-119">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="8c4e2-120">T, ilkel (skaler) bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-120">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="8c4e2-121">Duyarlık ve ölçek modelleri için değerler, öğesine atama sırasında isteğe bağlı olarak sağlanmayabilir `Edm.Decimal` .</span><span class="sxs-lookup"><span data-stu-id="8c4e2-121">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="8c4e2-122">Açık olarak sağlanmazsa, duyarlık ve ölçek için varsayılan değerler sırasıyla 18 ve 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-122">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="8c4e2-123">Özellikle, için aşağıdaki aşırı yüklemeler desteklenir `Decimal` :</span><span class="sxs-lookup"><span data-stu-id="8c4e2-123">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="8c4e2-124">Atama ifadesinin kullanımı açık bir dönüştürme olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-124">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="8c4e2-125">Açık dönüşümler verileri kesebilir veya duyarlık kayıplarına sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-125">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c4e2-126">CAST yalnızca ilkel türler ve numaralandırma üye türleri üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-126">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c4e2-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c4e2-127">Example</span></span>  

 <span data-ttu-id="8c4e2-128">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir veri türünün bir ifadesini diğerine dönüştürmek IÇIN cast işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-128">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="8c4e2-129">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8c4e2-130">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8c4e2-130">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8c4e2-131">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-131">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="8c4e2-132">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="8c4e2-132">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="8c4e2-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c4e2-133">See also</span></span>

- [<span data-ttu-id="8c4e2-134">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8c4e2-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
