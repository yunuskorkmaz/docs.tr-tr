---
title: "VARLIĞINDAKİ (SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 00d5a309a68ad7c1c5f363d6df3cca7a0e90ce81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="in-entity-sql"></a><span data-ttu-id="180bc-102">VARLIĞINDAKİ (SQL)</span><span class="sxs-lookup"><span data-stu-id="180bc-102">IN (Entity SQL)</span></span>
<span data-ttu-id="180bc-103">Bir değer bir koleksiyondaki herhangi bir değer eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="180bc-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="180bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="180bc-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="180bc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="180bc-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="180bc-106">Eşleştirilecek değerini döndüren herhangi bir geçerli ifadeler.</span><span class="sxs-lookup"><span data-stu-id="180bc-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="180bc-107">[NOT]</span><span class="sxs-lookup"><span data-stu-id="180bc-107">[ NOT ]</span></span>  
 <span data-ttu-id="180bc-108">Belirleyen `Boolean` IN sonucunu tasarruflarını.</span><span class="sxs-lookup"><span data-stu-id="180bc-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="180bc-109">Bir eşleşme için test etmek için bir koleksiyon döndürür herhangi geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="180bc-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="180bc-110">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `value`.</span><span class="sxs-lookup"><span data-stu-id="180bc-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="180bc-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="180bc-111">Return Value</span></span>  
 <span data-ttu-id="180bc-112">`true`değer koleksiyonda bulunursa; değer null ise null ya da koleksiyon null; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="180bc-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="180bc-113">NOT ın kullanarak inç sonuçlarını üzerindeki geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="180bc-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="180bc-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="180bc-114">Example</span></span>  
 <span data-ttu-id="180bc-115">Aşağıdaki varlık SQL sorgusunu ın işleci bir değer bir koleksiyondaki herhangi bir değer eşleşip eşleşmediğini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="180bc-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="180bc-116">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="180bc-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="180bc-117">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="180bc-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="180bc-118">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="180bc-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="180bc-119">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="180bc-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="180bc-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="180bc-120">See Also</span></span>  
 [<span data-ttu-id="180bc-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="180bc-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
