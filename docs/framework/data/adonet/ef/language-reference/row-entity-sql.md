---
description: 'Daha fazla bilgi edinin: satır (Entity SQL)'
title: SATıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: 2d0bcf3c5be8ef3b67e170af5159ae7dd8744630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739280"
---
# <a name="row-entity-sql"></a><span data-ttu-id="2d719-103">SATıR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2d719-103">ROW (Entity SQL)</span></span>

<span data-ttu-id="2d719-104">Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d719-104">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d719-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d719-105">Syntax</span></span>  
  
```sql  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2d719-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2d719-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2d719-107">Bir satır türünde yapı için bir değer döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2d719-107">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="2d719-108">Satır türünde belirtilen değer için bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d719-108">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="2d719-109">Bir diğer ad sağlanmazsa, diğer ad [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturma kurallarına göre bir diğer ad oluşturmaya çalışır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2d719-109">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d719-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d719-110">Return Value</span></span>  

 <span data-ttu-id="2d719-111">Bir satır türü.</span><span class="sxs-lookup"><span data-stu-id="2d719-111">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d719-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d719-112">Remarks</span></span>  

 <span data-ttu-id="2d719-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturmak için içinde satır oluşturucuları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2d719-113">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="2d719-114">Bir satır oluşturucusunun sonuç türü, alan türleri satırı oluşturmak için kullanılan değerlerin türlerine karşılık gelen bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="2d719-114">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="2d719-115">Örneğin, aşağıdaki ifade türünde bir değer oluşturur `Record(a int, b string, c int)` .</span><span class="sxs-lookup"><span data-stu-id="2d719-115">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```sql  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="2d719-116">Bir satır oluşturucusunda ifade için bir diğer ad sağlamazsanız, Entity Framework bir tane oluşturmaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="2d719-116">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="2d719-117">Daha fazla bilgi için, [tanımlayıcılar](identifiers-entity-sql.md) konusunun "diğer ad kuralları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2d719-117">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="2d719-118">Aşağıdaki kurallar, bir satır oluşturucusunda ifade diğer ad için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="2d719-118">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="2d719-119">Bir satır oluşturucudaki ifadeler aynı oluşturucuda diğer diğer adlara başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="2d719-119">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="2d719-120">Aynı satır oluşturucusunun iki ifadesi aynı diğer ada sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="2d719-120">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="2d719-121">Sorgu oluşturucular hakkında daha fazla bilgi için bkz. [tür](constructing-types-entity-sql.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2d719-121">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d719-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d719-122">Example</span></span>  

 <span data-ttu-id="2d719-123">Aşağıdaki Entity SQL sorgusu, anonim ve yapısal olarak belirlenmiş kayıtlar oluşturmak için satır işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d719-123">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="2d719-124">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2d719-124">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2d719-125">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2d719-125">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2d719-126">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2d719-126">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2d719-127">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2d719-127">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ROW](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#row)]  
  
## <a name="see-also"></a><span data-ttu-id="2d719-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d719-128">See also</span></span>

- [<span data-ttu-id="2d719-129">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="2d719-129">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="2d719-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2d719-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2d719-131">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="2d719-131">Type Definitions</span></span>](type-definitions-entity-sql.md)
