---
title: '- (Negatif) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 6e5512546faeaa9760dcf135165a999a6f95322b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311012"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="7b50d-102">-(Negatif) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="7b50d-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="7b50d-103">Negatif bir sayısal ifadenin değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b50d-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b50d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b50d-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b50d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7b50d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7b50d-106">Herhangi bir geçerli ifade herhangi birinin sayısal veri türleri.</span><span class="sxs-lookup"><span data-stu-id="7b50d-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7b50d-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="7b50d-107">Result Types</span></span>  
 <span data-ttu-id="7b50d-108">Veri türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="7b50d-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b50d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b50d-109">Remarks</span></span>  
 <span data-ttu-id="7b50d-110">Varsa `expression` işaretsiz bir türü olan sonuç türünü türüne en yakından ilişkili işaretli bir türe olacaktır `expression`.</span><span class="sxs-lookup"><span data-stu-id="7b50d-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="7b50d-111">Örneğin, varsa `expression` Byte, Int16 döndürülecek türünde bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="7b50d-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b50d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b50d-112">Example</span></span>  
 <span data-ttu-id="7b50d-113">Aşağıdaki varlık SQL sorgusu kullanır aritmetik işleç değerin sayısal ifadenin negatif döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="7b50d-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="7b50d-114">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="7b50d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7b50d-115">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="7b50d-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7b50d-116">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7b50d-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7b50d-117">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7b50d-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="7b50d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b50d-118">See also</span></span>

- [<span data-ttu-id="7b50d-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7b50d-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
