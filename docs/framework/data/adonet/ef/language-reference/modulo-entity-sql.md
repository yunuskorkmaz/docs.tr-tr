---
title: (Mod) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: e2d2c4cd6fd62cf5785d6b69aa399a74f8d04d30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760486"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="b7272-102">(Mod) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="b7272-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="b7272-103">Bir başkası tarafından ayrılmış bir ifadenin kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7272-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7272-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7272-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="b7272-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b7272-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="b7272-106">Bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="b7272-106">The numeric expression to divide.</span></span> <span data-ttu-id="b7272-107">`dividend` sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="b7272-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="b7272-108">Bölünenin bölüneceği sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="b7272-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="b7272-109">`divisor` sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="b7272-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b7272-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="b7272-110">Result Types</span></span>  
 <span data-ttu-id="b7272-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="b7272-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7272-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7272-112">Example</span></span>  
 <span data-ttu-id="b7272-113">Aşağıdaki varlık SQL sorgusu % aritmetik işleç bir başkası tarafından ayrılmış tek bir ifade kalanını döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7272-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="b7272-114">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="b7272-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b7272-115">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b7272-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b7272-116">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b7272-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b7272-117">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b7272-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="b7272-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7272-118">See also</span></span>

- [<span data-ttu-id="b7272-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b7272-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
