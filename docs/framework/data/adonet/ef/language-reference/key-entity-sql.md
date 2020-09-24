---
title: ANAHTAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 07160467dcee60377e3ef448fdc66092da4e06e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161977"
---
# <a name="key-entity-sql"></a><span data-ttu-id="8f616-102">ANAHTAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8f616-102">KEY (Entity SQL)</span></span>

<span data-ttu-id="8f616-103">Başvurunun veya bir varlık ifadesinin anahtarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="8f616-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f616-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f616-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="8f616-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f616-105">Remarks</span></span>  

 <span data-ttu-id="8f616-106">Bir varlık anahtarı, belirtilen varlık veya varlık başvurusunun doğru sırasındaki anahtar değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8f616-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="8f616-107">Birden çok varlık kümesi aynı türe dayanabileceğinden, her bir varlık kümesinde aynı anahtar görünebilir.</span><span class="sxs-lookup"><span data-stu-id="8f616-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="8f616-108">Benzersiz bir başvuru almak için kullanın `REF` .</span><span class="sxs-lookup"><span data-stu-id="8f616-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="8f616-109">ANAHTAR işlecinin dönüş türü, varlığın her anahtarı için aynı sırada bir alan içeren bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="8f616-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="8f616-110">Aşağıdaki örnekte, Key işleci, BadOrder varlığına bir başvuru geçirmiştir ve bu başvurunun anahtar bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f616-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="8f616-111">Bu durumda, özelliğine karşılık gelen tam bir alan içeren bir kayıt türü `Id` .</span><span class="sxs-lookup"><span data-stu-id="8f616-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="8f616-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f616-112">Example</span></span>  

 <span data-ttu-id="8f616-113">Aşağıdaki Entity SQL sorgusu, tür başvurusuyla bir ifadenin anahtar bölümünü ayıklamak için anahtar işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f616-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="8f616-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8f616-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8f616-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8f616-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8f616-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="8f616-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8f616-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="8f616-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="8f616-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f616-118">See also</span></span>

- [<span data-ttu-id="8f616-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8f616-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8f616-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="8f616-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="8f616-121">REF</span><span class="sxs-lookup"><span data-stu-id="8f616-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="8f616-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="8f616-122">DEREF</span></span>](deref-entity-sql.md)
