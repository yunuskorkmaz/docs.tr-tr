---
title: <= (küçüktür veya eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 09f2a7f53d00739b8542cb1149397f24d3b04f42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161808"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="9033b-102">\<= (Küçüktür veya eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9033b-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="9033b-103">Sol ifadenin doğru ifadeye eşit veya ondan küçük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="9033b-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9033b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9033b-104">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9033b-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="9033b-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9033b-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="9033b-106">Any valid expression.</span></span> <span data-ttu-id="9033b-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9033b-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9033b-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="9033b-108">Result Types</span></span>  

 <span data-ttu-id="9033b-109">`true` sol ifade, doğru ifadeye eşit veya daha küçük bir değere sahipse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9033b-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9033b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9033b-110">Example</span></span>  

 <span data-ttu-id="9033b-111">Aşağıdaki Entity SQL sorgusu, sol ifadenin doğru ifadeye eşit veya daha küçük bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için <= karşılaştırma işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9033b-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="9033b-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9033b-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9033b-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9033b-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9033b-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="9033b-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9033b-115">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="9033b-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="9033b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9033b-116">See also</span></span>

- [<span data-ttu-id="9033b-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9033b-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
