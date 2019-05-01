---
title: '>= (Büyüktür veya eşittir) (varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: b5a8a834c325cca38e2c106ca3f8ee829dd699b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034157"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="60355-102">> = (büyüktür veya eşittir) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="60355-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="60355-103">Sol ifade sağ ifade eşit veya büyük bir değer olup olmadığını belirlemek için iki deyim karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="60355-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60355-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60355-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="60355-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="60355-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="60355-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="60355-106">Any valid expression.</span></span> <span data-ttu-id="60355-107">Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60355-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="60355-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="60355-108">Result Types</span></span>  
 <span data-ttu-id="60355-109">`true` Sol ifade doğru ifade eşit veya daha büyük bir değere sahipse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="60355-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60355-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="60355-110">Example</span></span>  
 <span data-ttu-id="60355-111">Aşağıdaki varlık SQL sorgusu kullanır > = sol ifade sağ ifade eşit veya büyük bir değer olup olmadığını belirlemek için iki deyim karşılaştırmak için kullanılan karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="60355-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="60355-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="60355-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="60355-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="60355-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="60355-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="60355-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="60355-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="60355-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="60355-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60355-116">See also</span></span>

- [<span data-ttu-id="60355-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="60355-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
