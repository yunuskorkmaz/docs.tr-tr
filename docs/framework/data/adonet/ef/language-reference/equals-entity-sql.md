---
title: = (Eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 5cdfd35450514a9699a39cf78f64c0fa6b7d5f39
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833847"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="ab257-102">= (Eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ab257-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="ab257-103">İki ifadenin eşitliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="ab257-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab257-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab257-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab257-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ab257-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ab257-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="ab257-106">Any valid expression.</span></span> <span data-ttu-id="ab257-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab257-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ab257-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="ab257-108">Result Types</span></span>  
 <span data-ttu-id="ab257-109">sol ifade sağ ifadeye eşitse `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="ab257-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab257-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab257-110">Remarks</span></span>  
 <span data-ttu-id="ab257-111">= = İşleci = = ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ab257-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab257-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab257-112">Example</span></span>  
 <span data-ttu-id="ab257-113">Aşağıdaki Entity SQL sorgusu iki ifadenin eşitliğini karşılaştırmak için = Comparison işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab257-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="ab257-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ab257-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ab257-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ab257-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ab257-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="ab257-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ab257-117">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="ab257-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ab257-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab257-118">See also</span></span>

- [<span data-ttu-id="ab257-119">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="ab257-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
