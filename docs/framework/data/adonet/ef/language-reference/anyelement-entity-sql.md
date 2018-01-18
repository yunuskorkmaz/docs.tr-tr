---
title: "ANYELEMENT (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e74fbac9c2c57c653f55f76bf165d7eaebd9cee
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="35c5c-102">ANYELEMENT (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="35c5c-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="35c5c-103">Bir öğenin birden çok değerli bir koleksiyondan ayıklar.</span><span class="sxs-lookup"><span data-stu-id="35c5c-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35c5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35c5c-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="35c5c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="35c5c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="35c5c-106">Bir öğeyi ayıklamak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="35c5c-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35c5c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="35c5c-107">Return Value</span></span>  
 <span data-ttu-id="35c5c-108">Tek bir öğeye koleksiyon ya da birden fazla koleksiyon varsa, bir öğeye; koleksiyon boş ise, döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="35c5c-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="35c5c-109">Varsa `collection` türü koleksiyonudur `Collection<T>`, ardından `ANYELEMENT(collection)` türünün bir örneği üretir geçerli bir ifade `T`.</span><span class="sxs-lookup"><span data-stu-id="35c5c-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35c5c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35c5c-110">Remarks</span></span>  
 <span data-ttu-id="35c5c-111">ANYELEMENT birden çok değerli bir koleksiyondan bir öğeye ayıklar.</span><span class="sxs-lookup"><span data-stu-id="35c5c-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="35c5c-112">Örneğin, aşağıdaki örnekte bir singleton öğesi kümesinden ayıklamaya çalışır `Customers`.</span><span class="sxs-lookup"><span data-stu-id="35c5c-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="35c5c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="35c5c-113">Example</span></span>  
 <span data-ttu-id="35c5c-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu birden çok değerli bir koleksiyondaki bir öğe ayıklamak için ANYELEMENT işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="35c5c-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="35c5c-115">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="35c5c-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="35c5c-116">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="35c5c-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="35c5c-117">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="35c5c-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="35c5c-118">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="35c5c-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="35c5c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35c5c-119">See Also</span></span>  
 [<span data-ttu-id="35c5c-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="35c5c-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="35c5c-121">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="35c5c-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
