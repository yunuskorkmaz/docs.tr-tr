---
title: '>= (Büyüktür veya eşittir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 9e1d7e92097713ebdaf15523a5f99f98ed8be0b3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833738"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="8b4a2-102">> = (büyüktür veya eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8b4a2-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="8b4a2-103">Sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b4a2-104">Syntax</span></span>  
  
```sql  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b4a2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b4a2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8b4a2-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-106">Any valid expression.</span></span> <span data-ttu-id="8b4a2-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8b4a2-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="8b4a2-108">Result Types</span></span>  
 <span data-ttu-id="8b4a2-109">sol ifade sağ ifadeden daha büyük veya ona eşit bir değere sahipse, `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b4a2-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b4a2-110">Example</span></span>  
 <span data-ttu-id="8b4a2-111">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için > = karşılaştırma işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="8b4a2-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8b4a2-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8b4a2-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8b4a2-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8b4a2-115">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="8b4a2-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="8b4a2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b4a2-116">See also</span></span>

- [<span data-ttu-id="8b4a2-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b4a2-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
