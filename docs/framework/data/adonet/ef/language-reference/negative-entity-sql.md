---
title: "- (Negatif) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2ceedd99221047ab73474ad5dc2478e527618b87
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="135e6-102">-(Olumsuz) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="135e6-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="135e6-103">Sayısal bir ifadenin değerini negatif döndürür.</span><span class="sxs-lookup"><span data-stu-id="135e6-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="135e6-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="135e6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="135e6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="135e6-106">Sayısal veri türleri herhangi birinin geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="135e6-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="135e6-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="135e6-107">Result Types</span></span>  
 <span data-ttu-id="135e6-108">Veri türü `expression`.</span><span class="sxs-lookup"><span data-stu-id="135e6-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135e6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="135e6-109">Remarks</span></span>  
 <span data-ttu-id="135e6-110">Varsa `expression` imzasız bir tür sonuç türü türüne en yakından ilişkili imzalı türü olacaktır `expression`.</span><span class="sxs-lookup"><span data-stu-id="135e6-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="135e6-111">Örneğin, varsa `expression` bayt, Int16 döndürülecek türünde bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="135e6-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="135e6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="135e6-112">Example</span></span>  
 <span data-ttu-id="135e6-113">Aşağıdaki varlık SQL sorgusu kullanır sayısal bir ifadenin değerini negatif döndürülecek aritmetik işleç.</span><span class="sxs-lookup"><span data-stu-id="135e6-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="135e6-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="135e6-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="135e6-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="135e6-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="135e6-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="135e6-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="135e6-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="135e6-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="135e6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="135e6-118">See Also</span></span>  
 [<span data-ttu-id="135e6-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="135e6-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
