---
title: = (Eşittir) (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: ad9eda5a3544ea157d06c57876b1b0454a25dba1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215689"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="e2e4b-102">= (Eşittir) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e2e4b-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="e2e4b-103">İki ifadenin eşitlik karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2e4b-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2e4b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2e4b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e2e4b-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-106">Any valid expression.</span></span> <span data-ttu-id="e2e4b-107">Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e2e4b-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="e2e4b-108">Result Types</span></span>  
 `true` <span data-ttu-id="e2e4b-109">Sol ifade doğru ifade eşitse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-109">if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2e4b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2e4b-110">Remarks</span></span>  
 <span data-ttu-id="e2e4b-111">== İşleci, eşdeğer =.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e4b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2e4b-112">Example</span></span>  
 <span data-ttu-id="e2e4b-113">Aşağıdaki varlık SQL sorgusu kullanır = karşılaştırma işleci iki ifadenin eşitlik karşılaştırma için.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="e2e4b-114">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e2e4b-115">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e2e4b-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e2e4b-116">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e2e4b-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e2e4b-117">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e2e4b-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="e2e4b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e4b-118">See also</span></span>

- [<span data-ttu-id="e2e4b-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e2e4b-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
