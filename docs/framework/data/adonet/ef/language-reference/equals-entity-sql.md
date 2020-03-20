---
title: = (Eşittir) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150318"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="c3798-102">= (Eşittir) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="c3798-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="c3798-103">İki ifadenin eşitliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c3798-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3798-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3798-104">Syntax</span></span>  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c3798-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c3798-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c3798-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="c3798-106">Any valid expression.</span></span> <span data-ttu-id="c3798-107">Her iki ifadede de dolaylı olarak dönüştürülebilir veri türleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3798-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c3798-108">Sonuç Türleri</span><span class="sxs-lookup"><span data-stu-id="c3798-108">Result Types</span></span>  
 <span data-ttu-id="c3798-109">`true`sol ifade doğru ifadeye eşitse; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="c3798-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3798-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3798-110">Remarks</span></span>  
 <span data-ttu-id="c3798-111">== işleci ='ya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c3798-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3798-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3798-112">Example</span></span>  
 <span data-ttu-id="c3798-113">Aşağıdaki Entity SQL sorgusu, iki ifadenin eşitliğini karşılaştırmak için = karşılaştırma işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="c3798-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="c3798-114">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3798-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c3798-115">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c3798-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c3798-116">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="c3798-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c3798-117">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="c3798-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="c3798-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3798-118">See also</span></span>

- [<span data-ttu-id="c3798-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c3798-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
