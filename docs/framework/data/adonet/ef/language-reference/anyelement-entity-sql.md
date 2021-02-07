---
description: 'Hakkında daha fazla bilgi edinin: ANYELEMENT (Entity SQL)'
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 3330c1b0bed69084bc83c5a689762ff529539d54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697159"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="1acb9-103">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1acb9-103">ANYELEMENT (Entity SQL)</span></span>

<span data-ttu-id="1acb9-104">Çok değerli bir koleksiyondan bir öğe ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1acb9-104">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1acb9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1acb9-105">Syntax</span></span>  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1acb9-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="1acb9-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="1acb9-107">Öğesinden bir öğe Ayıklanacak bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1acb9-107">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1acb9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1acb9-108">Return Value</span></span>  

 <span data-ttu-id="1acb9-109">Koleksiyonda tek bir öğe veya koleksiyonda birden fazla varsa rastgele öğe. Koleksiyon boşsa, döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="1acb9-109">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="1acb9-110">`collection`, Türünde bir koleksiyondur `Collection<T>` , bir `ANYELEMENT(collection)` türü örneği veren geçerli bir ifadedir `T` .</span><span class="sxs-lookup"><span data-stu-id="1acb9-110">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1acb9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1acb9-111">Remarks</span></span>  

 <span data-ttu-id="1acb9-112">ANYELEMENT çok değerli bir koleksiyondaki rastgele bir öğeyi ayıklar.</span><span class="sxs-lookup"><span data-stu-id="1acb9-112">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="1acb9-113">Örneğin, aşağıdaki örnek kümeden tek bir öğe ayıklamaya çalışır `Customers` .</span><span class="sxs-lookup"><span data-stu-id="1acb9-113">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="1acb9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1acb9-114">Example</span></span>  

 <span data-ttu-id="1acb9-115">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, çok değerli bir koleksiyondan bir öğe ayıklamak IÇIN AnyElement işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1acb9-115">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="1acb9-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1acb9-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1acb9-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1acb9-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1acb9-118">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1acb9-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1acb9-119">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="1acb9-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="1acb9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1acb9-120">See also</span></span>

- [<span data-ttu-id="1acb9-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1acb9-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="1acb9-122">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="1acb9-122">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
