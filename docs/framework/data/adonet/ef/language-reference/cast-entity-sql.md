---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: c16270babe4daa8e703b24b27211c6fd6f53677d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039913"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="d4f13-102">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d4f13-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="d4f13-103">Bir veri türündeki bir ifadeyi diğerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d4f13-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4f13-104">Syntax</span></span>  
  
```csharp
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4f13-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d4f13-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d4f13-106">`data_type`dönüştürülebilir geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d4f13-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="d4f13-107">Hedef sistem tarafından sağlanan veri türü.</span><span class="sxs-lookup"><span data-stu-id="d4f13-107">The target system-supplied data type.</span></span> <span data-ttu-id="d4f13-108">Temel bir (skaler) türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="d4f13-109">Kullanılan `data_type`, sorgu alanına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="d4f13-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="d4f13-110"><xref:System.Data.EntityClient.EntityCommand>bir sorgu yürütülürse, veri türü kavramsal modelde tanımlanan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="d4f13-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="d4f13-111">Daha fazla bilgi için bkz. [csdl belirtimi](csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="d4f13-111">For more information, see [CSDL Specification](csdl-specification.md).</span></span> <span data-ttu-id="d4f13-112">Bir sorgu <xref:System.Data.Objects.ObjectQuery%601>ile yürütülürse, veri türü ortak dil çalışma zamanı (CLR) türüdür.</span><span class="sxs-lookup"><span data-stu-id="d4f13-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4f13-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d4f13-113">Return Value</span></span>  
 <span data-ttu-id="d4f13-114">`data_type`ile aynı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4f13-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4f13-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4f13-115">Remarks</span></span>  
 <span data-ttu-id="d4f13-116">Cast ifadesinin Transact-SQL CONVERT ifadesine benzer anlamları vardır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-116">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="d4f13-117">Cast ifadesi bir tür değerini başka bir türün değerine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```csharp
CAST( e as T )  
```  
  
 <span data-ttu-id="d4f13-118">E bazı tür ve S, T 'ye dönüştürülesiyse, yukarıdaki ifade geçerli bir atama ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="d4f13-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="d4f13-119">T, ilkel (skaler) bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="d4f13-120">Duyarlık ve ölçek modelleri için değerler, `Edm.Decimal`çevrim sırasında isteğe bağlı olarak sağlanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d4f13-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="d4f13-121">Açık olarak sağlanmazsa, duyarlık ve ölçek için varsayılan değerler sırasıyla 18 ve 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="d4f13-122">Özellikle, `Decimal`için aşağıdaki aşırı yüklemeler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d4f13-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="d4f13-123">Atama ifadesinin kullanımı açık bir dönüştürme olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d4f13-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="d4f13-124">Açık dönüşümler verileri kesebilir veya duyarlık kayıplarına sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="d4f13-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4f13-125">CAST yalnızca ilkel türler ve numaralandırma üye türleri üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d4f13-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4f13-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4f13-126">Example</span></span>  
 <span data-ttu-id="d4f13-127">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, bir veri türü ifadesini diğerine dönüştürmek için CAST işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="d4f13-128">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="d4f13-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d4f13-129">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d4f13-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d4f13-130">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="d4f13-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="d4f13-131">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="d4f13-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="d4f13-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4f13-132">See also</span></span>

- [<span data-ttu-id="d4f13-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d4f13-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
