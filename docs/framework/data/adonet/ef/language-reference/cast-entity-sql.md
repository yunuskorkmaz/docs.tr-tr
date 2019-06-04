---
title: ATAMA (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 743c90cd9bc77a89051c59a217befa4275b28572
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489951"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="56460-102">ATAMA (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="56460-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="56460-103">Bir veri türündeki bir ifade diğerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="56460-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56460-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56460-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="56460-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="56460-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="56460-106">Dönüştürülebilen herhangi bir geçerli ifade `data_type`.</span><span class="sxs-lookup"><span data-stu-id="56460-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="56460-107">Hedef sistem tarafından sağlanan veri türü.</span><span class="sxs-lookup"><span data-stu-id="56460-107">The target system-supplied data type.</span></span> <span data-ttu-id="56460-108">Basit (skaler) türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56460-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="56460-109">`data_type` Kullanılan Sorgu alanı bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="56460-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="56460-110">Bir sorgu ile yürütülürse <xref:System.Data.EntityClient.EntityCommand>, kavramsal modelde tanımlı bir tür veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="56460-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="56460-111">Daha fazla bilgi için [CSDL belirtimi](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="56460-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="56460-112">Bir sorgu ile yürütülürse <xref:System.Data.Objects.ObjectQuery%601>, ortak dil çalışma zamanı (CLR) tür veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="56460-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56460-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56460-113">Return Value</span></span>  
 <span data-ttu-id="56460-114">Aynı değeri döndürür `data_type`.</span><span class="sxs-lookup"><span data-stu-id="56460-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56460-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56460-115">Remarks</span></span>  
 <span data-ttu-id="56460-116">Cast ifadesi Transact-SQL dönüştürme ifade benzer semantiğe sahip.</span><span class="sxs-lookup"><span data-stu-id="56460-116">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="56460-117">Cast ifadesi, başka bir türü bir değere bir türün bir değerini dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56460-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="56460-118">E ise bazı S ve S T için dönüştürülebilir türüdür ve ardından yukarıdaki ifadeyi geçerli atama ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="56460-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="56460-119">T (skaler) basit tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56460-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="56460-120">Kesinlik ve ölçek özellikleri, isteğe bağlı olarak tür atama olduğunda sağlanabilir değerleri `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="56460-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="56460-121">Açıkça sağlanan, kesinlik ve ölçek için varsayılan değerleri 18 ve 0, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="56460-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="56460-122">Özellikle, aşağıdaki aşırı yüklemeler için desteklenen `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="56460-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="56460-123">Cast ifadesi kullanımı açık bir dönüştürme olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="56460-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="56460-124">Açık dönüştürmeler truncate veri veya duyarlık kaybı.</span><span class="sxs-lookup"><span data-stu-id="56460-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56460-125">ATAMA, yalnızca ilkel türler ve sabit listesi üye türleri üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="56460-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56460-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="56460-126">Example</span></span>  
 <span data-ttu-id="56460-127">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu için başka bir veri türündeki bir ifadeye dönüştürmek için tür dönüştürme işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="56460-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="56460-128">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="56460-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="56460-129">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="56460-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="56460-130">Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="56460-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="56460-131">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="56460-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="56460-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56460-132">See also</span></span>

- [<span data-ttu-id="56460-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="56460-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
