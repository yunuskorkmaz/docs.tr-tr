---
title: SATıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2ab91d0c6d3c3ed3f88a7f0ddbf3a6c2f36d8b04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202272"
---
# <a name="row-entity-sql"></a><span data-ttu-id="171e4-102">SATıR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="171e4-102">ROW (Entity SQL)</span></span>

<span data-ttu-id="171e4-103">Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="171e4-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="171e4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="171e4-104">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="171e4-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="171e4-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="171e4-106">Bir satır türünde yapı için bir değer döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="171e4-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="171e4-107">Satır türünde belirtilen değer için bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="171e4-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="171e4-108">Bir diğer ad sağlanmazsa, diğer ad [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturma kurallarına göre bir diğer ad oluşturmaya çalışır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="171e4-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="171e4-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="171e4-109">Return Value</span></span>  

 <span data-ttu-id="171e4-110">Bir satır türü.</span><span class="sxs-lookup"><span data-stu-id="171e4-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="171e4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="171e4-111">Remarks</span></span>  

 <span data-ttu-id="171e4-112">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturmak için içinde satır oluşturucuları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="171e4-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="171e4-113">Bir satır oluşturucusunun sonuç türü, alan türleri satırı oluşturmak için kullanılan değerlerin türlerine karşılık gelen bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="171e4-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="171e4-114">Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)` .</span><span class="sxs-lookup"><span data-stu-id="171e4-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="171e4-115">Bir satır oluşturucusunda ifade için bir diğer ad sağlamazsanız, Entity Framework bir tane oluşturmaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="171e4-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="171e4-116">Daha fazla bilgi için, [tanımlayıcılar](identifiers-entity-sql.md) konusunun "diğer ad kuralları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="171e4-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="171e4-117">Aşağıdaki kurallar, bir satır oluşturucusunda ifade diğer ad için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="171e4-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="171e4-118">Bir satır oluşturucudaki ifadeler aynı oluşturucuda diğer diğer adlara başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="171e4-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="171e4-119">Aynı satır oluşturucusunun iki ifadesi aynı diğer ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="171e4-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="171e4-120">Sorgu oluşturucular hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="171e4-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="171e4-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="171e4-121">Example</span></span>  

 <span data-ttu-id="171e4-122">Aşağıdaki Entity SQL sorgusu, anonim ve yapısal olarak belirlenmiş kayıtlar oluşturmak için satır işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="171e4-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="171e4-123">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="171e4-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="171e4-124">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="171e4-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="171e4-125">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="171e4-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="171e4-126">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="171e4-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="171e4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="171e4-127">See also</span></span>

- [<span data-ttu-id="171e4-128">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="171e4-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="171e4-129">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="171e4-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="171e4-130">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="171e4-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
