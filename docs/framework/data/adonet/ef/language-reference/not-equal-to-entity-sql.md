---
title: '! = (Eşit değildir) (varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: f5fdbbf2892781ce44dfe73e8cd80fbe0f74cf1c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310973"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="0f6b8-102">! = (Eşit değildir) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="0f6b8-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="0f6b8-103">Sol ifade doğru ifade eşit olup olmadığını belirlemek için iki deyim karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="0f6b8-104">! = (Eşit değildir) işlecini <> işlecine eşdeğer işleve sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f6b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f6b8-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f6b8-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0f6b8-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0f6b8-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-107">Any valid expression.</span></span> <span data-ttu-id="0f6b8-108">Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0f6b8-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="0f6b8-109">Result Types</span></span>  
 `true` <span data-ttu-id="0f6b8-110">Sol ifade doğru ifade eşit değilse, Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-110">if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6b8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f6b8-111">Example</span></span>  
 <span data-ttu-id="0f6b8-112">Aşağıdaki varlık SQL sorgusu kullanır! = işleci sol ifade doğru ifade eşit olup olmadığını belirlemek için iki deyim karşılaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="0f6b8-113">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0f6b8-114">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0f6b8-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0f6b8-115">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0f6b8-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0f6b8-116">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="0f6b8-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="0f6b8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f6b8-117">See also</span></span>

- [<span data-ttu-id="0f6b8-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0f6b8-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
