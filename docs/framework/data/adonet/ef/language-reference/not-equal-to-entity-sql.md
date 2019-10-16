---
title: '! = (Eşit değildir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3f6f66d38eb9650e1adb06fa3ef5edbccf110374
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319504"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="c03b1-102">! = (Eşit değildir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c03b1-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="c03b1-103">Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c03b1-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="c03b1-104">! = (Eşit değildir) işleci, < > işlecine işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c03b1-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c03b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c03b1-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c03b1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="c03b1-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c03b1-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="c03b1-107">Any valid expression.</span></span> <span data-ttu-id="c03b1-108">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c03b1-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c03b1-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="c03b1-109">Result Types</span></span>  
 <span data-ttu-id="c03b1-110">sol ifade sağ ifadeye eşit değilse, `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="c03b1-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c03b1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c03b1-111">Example</span></span>  
 <span data-ttu-id="c03b1-112">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeye eşit olup olmadığını belirleyebilmek üzere iki ifadeyi karşılaştırmak için! = işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c03b1-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="c03b1-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="c03b1-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c03b1-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c03b1-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c03b1-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="c03b1-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c03b1-116">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="c03b1-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="c03b1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c03b1-117">See also</span></span>

- [<span data-ttu-id="c03b1-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c03b1-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
