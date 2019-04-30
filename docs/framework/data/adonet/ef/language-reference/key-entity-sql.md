---
title: ANAHTAR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 9cd3276583741f2b0261cb8a0e55f4185d20100e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780269"
---
# <a name="key-entity-sql"></a><span data-ttu-id="05bac-102">ANAHTAR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="05bac-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="05bac-103">Bir başvuru veya varlık ifade anahtarını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="05bac-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05bac-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="05bac-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05bac-105">Remarks</span></span>  
 <span data-ttu-id="05bac-106">Varlık anahtarı anahtar değerlerinin doğru sırayla belirtilen varlık veya varlık başvurusu içerir.</span><span class="sxs-lookup"><span data-stu-id="05bac-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="05bac-107">Birden çok varlık kümeleri aynı türüne göre çünkü aynı anahtarı her varlık kümesinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="05bac-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="05bac-108">Benzersiz bir başvuru almak için kullanın `REF`.</span><span class="sxs-lookup"><span data-stu-id="05bac-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="05bac-109">ANAHTAR işlecinin dönüş türü varlığın her anahtar için bir alan aynı sırada içeren bir satır türüdür.</span><span class="sxs-lookup"><span data-stu-id="05bac-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="05bac-110">Aşağıdaki örnekte, anahtar işleci BadOrder varlığına yönelik bir başvuru geçirilir ve bu başvuru anahtar bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="05bac-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="05bac-111">Bu durumda, bir kayıt türü tam olarak bir alan için karşılık gelen ile `Id` özelliği.</span><span class="sxs-lookup"><span data-stu-id="05bac-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="05bac-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="05bac-112">Example</span></span>  
 <span data-ttu-id="05bac-113">Aşağıdaki varlık SQL sorgusu anahtar işleci bir ifade tür başvurusu ile anahtar bölümünü ayıklamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="05bac-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="05bac-114">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="05bac-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="05bac-115">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="05bac-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="05bac-116">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="05bac-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="05bac-117">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="05bac-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="05bac-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05bac-118">See also</span></span>

- [<span data-ttu-id="05bac-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="05bac-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="05bac-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="05bac-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="05bac-121">REF</span><span class="sxs-lookup"><span data-stu-id="05bac-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="05bac-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="05bac-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
