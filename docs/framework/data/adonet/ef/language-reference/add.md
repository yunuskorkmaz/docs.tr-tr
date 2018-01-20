---
title: + (Ekle)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6014b2b37d3574af8462ec178f943340af6d7146
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-add"></a><span data-ttu-id="3aedc-102">+ (Ekle)</span><span class="sxs-lookup"><span data-stu-id="3aedc-102">+ (Add)</span></span>
<span data-ttu-id="3aedc-103">İki sayıyı toplar.</span><span class="sxs-lookup"><span data-stu-id="3aedc-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aedc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aedc-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3aedc-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3aedc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3aedc-106">Sayısal veri türleri herhangi birinin geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="3aedc-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3aedc-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="3aedc-107">Result Types</span></span>  
 <span data-ttu-id="3aedc-108">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="3aedc-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="3aedc-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3aedc-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aedc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aedc-110">Remarks</span></span>  
 <span data-ttu-id="3aedc-111">EDM için. Dize türleri, ek birleştirme olur.</span><span class="sxs-lookup"><span data-stu-id="3aedc-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aedc-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3aedc-112">Example</span></span>  
 <span data-ttu-id="3aedc-113">Aşağıdaki varlık SQL sorgusu kullanır + iki sayı eklemek için aritmetik işleç.</span><span class="sxs-lookup"><span data-stu-id="3aedc-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="3aedc-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="3aedc-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3aedc-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3aedc-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3aedc-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3aedc-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3aedc-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3aedc-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="3aedc-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3aedc-118">See Also</span></span>  
 [<span data-ttu-id="3aedc-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3aedc-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="3aedc-120">Kavramsal Model türü (CSDL)</span><span class="sxs-lookup"><span data-stu-id="3aedc-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
