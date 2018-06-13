---
title: SATIR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: eb5062399eec9d8453d8922e05698ca9124d94d7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765613"
---
# <a name="row-entity-sql"></a><span data-ttu-id="b1ebd-102">SATIR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="b1ebd-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="b1ebd-103">Bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ebd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1ebd-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b1ebd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b1ebd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b1ebd-106">Bir satır türü oluşturmak için bir değer döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="b1ebd-107">Bir satır türü için belirtilen değer için bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="b1ebd-108">Bir diğer ad sağlanmazsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dayalı bir diğer ad oluşturmak çalışır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer adı oluşturma kuralları.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1ebd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1ebd-109">Return Value</span></span>  
 <span data-ttu-id="b1ebd-110">Satır türü.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1ebd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1ebd-111">Remarks</span></span>  
 <span data-ttu-id="b1ebd-112">Satır kurucularda kullandığınız [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="b1ebd-113">Bir satır oluşturucusunda sonuç türü, alan türlerini satır oluşturmak için kullanılan değerlerin türü için karşılık gelen bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="b1ebd-114">Örneğin, aşağıdaki deyim türünde bir değer oluşturur `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="b1ebd-115">Row kurucusunda bir ifade için bir diğer ad belirtmezseniz, Entity Framework oluşturur dener.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="b1ebd-116">Daha fazla bilgi için "Diğer ad kuralları" bölümüne bakın [tanımlayıcıları](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-116">For more information, see the "Aliasing Rules" section of the [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="b1ebd-117">Row kurucusunda ifade yumuşatma aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b1ebd-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
-   <span data-ttu-id="b1ebd-118">Bir satır oluşturucusunda ifadelerinde başka diğer adlar aynı oluşturucuda başvuruda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
-   <span data-ttu-id="b1ebd-119">İki ifadeye aynı row kurucusunda aynı ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="b1ebd-120">Sorgu oluşturucular hakkında daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b1ebd-120">For more information about query constructors, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ebd-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1ebd-121">Example</span></span>  
 <span data-ttu-id="b1ebd-122">Aşağıdaki varlık SQL sorgu satırı işleci anonim, yapısal olarak yazılan kayıtları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="b1ebd-123">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b1ebd-124">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b1ebd-124">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b1ebd-125">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b1ebd-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b1ebd-126">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b1ebd-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="b1ebd-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ebd-127">See Also</span></span>  
 [<span data-ttu-id="b1ebd-128">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="b1ebd-128">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="b1ebd-129">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b1ebd-129">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b1ebd-130">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="b1ebd-130">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
