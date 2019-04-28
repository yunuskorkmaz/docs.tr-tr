---
title: ANYELEMENT (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: ff79417008b7807fbf206d4bcb65b4e5ea1cc576
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606042"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="1cd40-102">ANYELEMENT (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="1cd40-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="1cd40-103">Birden çok değerli bir koleksiyondan bir öğe ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1cd40-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cd40-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1cd40-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1cd40-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1cd40-106">Öğeden ayıklamak için bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="1cd40-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cd40-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1cd40-107">Return Value</span></span>  
 <span data-ttu-id="1cd40-108">Tek bir öğe koleksiyonu veya koleksiyon birden fazla varsa, rastgele bir öğe; koleksiyon boş ise döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="1cd40-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="1cd40-109">Varsa `collection` türü koleksiyonudur `Collection<T>`, ardından `ANYELEMENT(collection)` verir türünün bir örneği geçerli bir ifade `T`.</span><span class="sxs-lookup"><span data-stu-id="1cd40-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cd40-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cd40-110">Remarks</span></span>  
 <span data-ttu-id="1cd40-111">ANYELEMENT rastgele bir öğe birden çok değerli bir koleksiyondan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1cd40-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="1cd40-112">Örneğin, aşağıdaki örnekte bir singleton öğesi kümesinden ayıklamaya çalışır `Customers`.</span><span class="sxs-lookup"><span data-stu-id="1cd40-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="1cd40-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cd40-113">Example</span></span>  
 <span data-ttu-id="1cd40-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu birden çok değerli bir koleksiyondan bir öğe ayıklanacak ANYELEMENT işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cd40-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="1cd40-115">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="1cd40-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1cd40-116">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1cd40-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1cd40-117">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1cd40-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1cd40-118">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1cd40-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="1cd40-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cd40-119">See also</span></span>

- [<span data-ttu-id="1cd40-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1cd40-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="1cd40-121">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="1cd40-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
