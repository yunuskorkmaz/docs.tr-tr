---
title: (Varlık SQL) var.
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 72d96c5f24fcedf870370de3792680831145a454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034209"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="b3467-102">(Varlık SQL) var.</span><span class="sxs-lookup"><span data-stu-id="b3467-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="b3467-103">Bir koleksiyonu boş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="b3467-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3467-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3467-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3467-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3467-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b3467-106">Bir koleksiyonu döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="b3467-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="b3467-107">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="b3467-107">NOT</span></span>  
 <span data-ttu-id="b3467-108">EXISTS sonucunu negatif olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3467-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3467-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3467-109">Return Value</span></span>  
 <span data-ttu-id="b3467-110">`true` koleksiyon boş değilse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b3467-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3467-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3467-111">Remarks</span></span>  
 <span data-ttu-id="b3467-112">EXISTS biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b3467-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="b3467-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b3467-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="b3467-114">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b3467-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3467-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3467-115">Example</span></span>  
 <span data-ttu-id="b3467-116">Aşağıdaki varlık SQL sorgu EXISTS işleci koleksiyonun boş olup olmadığını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3467-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="b3467-117">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="b3467-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b3467-118">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b3467-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b3467-119">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b3467-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b3467-120">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b3467-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="b3467-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3467-121">See also</span></span>

- [<span data-ttu-id="b3467-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b3467-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
