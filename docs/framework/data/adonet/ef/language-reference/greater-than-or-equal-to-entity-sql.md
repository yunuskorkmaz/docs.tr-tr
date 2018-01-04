---
title: "&gt;= (Büyüktür veya eşittir) (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 89e24b3e1a4b707ca60d798889538eb1bcd6a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="6aed1-102">&gt;= (Büyüktür veya eşittir) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="6aed1-102">&gt;= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="6aed1-103">Sol ifade sağ ifade eşit veya daha büyük bir değere sahip olup olmadığını belirlemek için iki ifadeye karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="6aed1-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aed1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6aed1-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6aed1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6aed1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6aed1-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="6aed1-106">Any valid expression.</span></span> <span data-ttu-id="6aed1-107">Her iki ifadeleri örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6aed1-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6aed1-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="6aed1-108">Result Types</span></span>  
 <span data-ttu-id="6aed1-109">`true`Sol ifade sağ ifade eşit veya daha büyük bir değere sahip olursa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="6aed1-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aed1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6aed1-110">Example</span></span>  
 <span data-ttu-id="6aed1-111">Aşağıdaki varlık SQL sorgusu kullanır > = sol ifade sağ ifade eşit veya daha büyük bir değere sahip olup olmadığını belirlemek için iki ifadeye karşılaştırmak için karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="6aed1-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="6aed1-112">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="6aed1-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6aed1-113">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6aed1-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6aed1-114">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6aed1-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6aed1-115">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="6aed1-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="6aed1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6aed1-116">See Also</span></span>  
 [<span data-ttu-id="6aed1-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6aed1-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
