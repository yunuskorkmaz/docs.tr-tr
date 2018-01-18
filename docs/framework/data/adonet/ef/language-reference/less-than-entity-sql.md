---
title: "&lt;(Küçüktür) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5bf1560c0bebafcfdbf79ca9a9906c9df23b7cae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="lt-less-than-entity-sql"></a><span data-ttu-id="f8d8c-102">&lt;(Küçüktür) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="f8d8c-102">&lt; (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="f8d8c-103">Sol ifade sağ ifade'den küçük bir değer olup olmadığını belirlemek için iki ifadeye karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8d8c-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f8d8c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f8d8c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f8d8c-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-106">Any valid expression.</span></span> <span data-ttu-id="f8d8c-107">Her iki ifadeleri örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f8d8c-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="f8d8c-108">Result Types</span></span>  
 <span data-ttu-id="f8d8c-109">`true`Sol ifade sağ ifade'den küçük bir değer varsa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8d8c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8d8c-110">Example</span></span>  
 <span data-ttu-id="f8d8c-111">Aşağıdaki varlık SQL sorgusu kullanır < karşılaştırma işlecinin sol ifade sağ ifade'den küçük bir değer olup olmadığını belirlemek için iki ifadeye karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="f8d8c-112">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f8d8c-113">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f8d8c-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f8d8c-114">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f8d8c-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f8d8c-115">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="f8d8c-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="f8d8c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8d8c-116">See Also</span></span>  
 [<span data-ttu-id="f8d8c-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f8d8c-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
