---
title: < (Küçüktür) (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 1ca1cbdf1282782295b659393e8f54aae3ec5649
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772313"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="11b61-102">\< (Küçüktür) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="11b61-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="11b61-103">Sol ifade sağ ifade'den küçük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="11b61-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11b61-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="11b61-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="11b61-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="11b61-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="11b61-106">Any valid expression.</span></span> <span data-ttu-id="11b61-107">Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11b61-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="11b61-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="11b61-108">Result Types</span></span>  
 <span data-ttu-id="11b61-109">`true` Sol ifade sağ ifade'den küçük bir değere sahipse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="11b61-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11b61-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="11b61-110">Example</span></span>  
 <span data-ttu-id="11b61-111">Aşağıdaki varlık SQL sorgusu kullanır < sol ifade sağ ifade'den küçük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırmak için kullanılan karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="11b61-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="11b61-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="11b61-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="11b61-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="11b61-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="11b61-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="11b61-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="11b61-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="11b61-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="11b61-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11b61-116">See also</span></span>

- [<span data-ttu-id="11b61-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="11b61-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
