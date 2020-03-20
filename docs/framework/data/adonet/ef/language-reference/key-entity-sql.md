---
title: ANAHTAR (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150175"
---
# <a name="key-entity-sql"></a><span data-ttu-id="3058e-102">ANAHTAR (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="3058e-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="3058e-103">Başvurunun veya varlık ifadesinin anahtarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="3058e-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3058e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3058e-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="3058e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3058e-105">Remarks</span></span>  
 <span data-ttu-id="3058e-106">Varlık anahtarı, belirtilen varlık veya varlık başvurusu doğru sırada anahtar değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3058e-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="3058e-107">Birden çok varlık kümesi aynı türü temel alabilecek olduğundan, her varlık kümesinde aynı anahtar görünebilir.</span><span class="sxs-lookup"><span data-stu-id="3058e-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="3058e-108">Benzersiz bir başvuru almak `REF`için.</span><span class="sxs-lookup"><span data-stu-id="3058e-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="3058e-109">KEY işlecinin dönüş türü, varlığın her anahtarı için aynı sırada bir alan içeren bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="3058e-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="3058e-110">Aşağıdaki örnekte, anahtar işleci BadOrder varlığına bir başvuru geçirilir ve bu başvurunun anahtar kısmını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3058e-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="3058e-111">Bu durumda, `Id` özelliğe karşılık gelen tam bir alana sahip bir kayıt türü.</span><span class="sxs-lookup"><span data-stu-id="3058e-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="3058e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3058e-112">Example</span></span>  
 <span data-ttu-id="3058e-113">Aşağıdaki Entity SQL sorgusu, tür başvurusu olan bir ifadenin anahtar bölümünü ayıklamak için KEY işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="3058e-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="3058e-114">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3058e-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3058e-115">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3058e-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3058e-116">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="3058e-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3058e-117">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="3058e-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="3058e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3058e-118">See also</span></span>

- [<span data-ttu-id="3058e-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3058e-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3058e-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="3058e-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="3058e-121">REF</span><span class="sxs-lookup"><span data-stu-id="3058e-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="3058e-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="3058e-122">DEREF</span></span>](deref-entity-sql.md)
