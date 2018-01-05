---
title: "! = (Eşit değildir) (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 81643b9a4a1cd49e950010c0023b27108d34180c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="0efad-102">! = (Eşit değildir) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="0efad-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="0efad-103">Sol ifade sağ ifade eşit olup olmadığını belirlemek için iki ifadeye karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="0efad-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="0efad-104">! = (Eşit değildir) işlecini eşdeğerdir <> işleci işlevsel olarak.</span><span class="sxs-lookup"><span data-stu-id="0efad-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0efad-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0efad-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0efad-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0efad-107">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="0efad-107">Any valid expression.</span></span> <span data-ttu-id="0efad-108">Her iki ifadeleri örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0efad-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0efad-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="0efad-109">Result Types</span></span>  
 <span data-ttu-id="0efad-110">`true`Sol ifade sağ ifade eşit değilse; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="0efad-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0efad-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0efad-111">Example</span></span>  
 <span data-ttu-id="0efad-112">Aşağıdaki varlık SQL sorgusu kullanır! = işleci sol ifade sağ ifade eşit olup olmadığını belirlemek için iki ifadeye karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="0efad-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="0efad-113">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0efad-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0efad-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0efad-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0efad-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0efad-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0efad-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="0efad-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="0efad-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0efad-117">See Also</span></span>  
 [<span data-ttu-id="0efad-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0efad-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
