---
title: ÖRTÜŞMELER (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: bdee9281fd406a3d029d3a10536cbdd48d2f7a58
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319422"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="f1db1-102">ÖRTÜŞMELER (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f1db1-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="f1db1-103">İki koleksiyonun ortak öğelere sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f1db1-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1db1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1db1-104">Syntax</span></span>  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f1db1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1db1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f1db1-106">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f1db1-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="f1db1-107">Tüm ifadeler aynı türde veya ortak bir temel ya da türetilmiş türden `expression` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1db1-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1db1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1db1-108">Return Value</span></span>  
 <span data-ttu-id="f1db1-109">İki koleksiyonun ortak öğeleri varsa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="f1db1-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1db1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1db1-110">Remarks</span></span>  
 <span data-ttu-id="f1db1-111">ÖRTÜŞMELER, aşağıdaki gibi işlevsel bir eşdeğer sağlar:</span><span class="sxs-lookup"><span data-stu-id="f1db1-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="f1db1-112">ÖRTÜŞÜYOR [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="f1db1-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="f1db1-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f1db1-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="f1db1-114">@No__t-0 kümesi işleçleri için öncelik bilgisi için, bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f1db1-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1db1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1db1-115">Example</span></span>  
 <span data-ttu-id="f1db1-116">Aşağıdaki Entity SQL sorgusu, iki koleksiyonun ortak bir değere sahip olup olmadığını belirleyen ÖRTÜŞMELER işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1db1-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="f1db1-117">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f1db1-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f1db1-118">Bunu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f1db1-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="f1db1-119">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="f1db1-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f1db1-120">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="f1db1-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="f1db1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1db1-121">See also</span></span>

- [<span data-ttu-id="f1db1-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f1db1-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
