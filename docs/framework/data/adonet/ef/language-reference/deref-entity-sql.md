---
title: "DEREF (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e2bbac28e3f0f1149a9fa540692890512fb5941
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="deref-entity-sql"></a><span data-ttu-id="cf5b8-102">DEREF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="cf5b8-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="cf5b8-103">Bir başvuru değer ve başvuru sonucu, üretir dereferences.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf5b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf5b8-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf5b8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cf5b8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="cf5b8-106">Bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf5b8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cf5b8-107">Return Value</span></span>  
 <span data-ttu-id="cf5b8-108">Başvurulan varlık değeri.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf5b8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf5b8-109">Remarks</span></span>  
 <span data-ttu-id="cf5b8-110">DEREF işleci bir başvuru değer ve başvuru sonucu, üretir dereferences.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="cf5b8-111">Örneğin, varsa `r` türü ref başvurudur\<T >, `Deref``(r)` ifade türü olan `T` tarafından başvurulan varlık verir `r`.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-111">For example, if `r` is a reference of type ref\<T>, `Deref``(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="cf5b8-112">Başvuru değeri null veya sarkan değil (diğer bir deyişle, başvuru hedef için yok), DEREF işleci sonuç NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf5b8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf5b8-113">Example</span></span>  
 <span data-ttu-id="cf5b8-114">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu başvuru değer ve başvuru sonucu, üretim başvurulacak DEREF işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="cf5b8-115">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cf5b8-116">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="cf5b8-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cf5b8-117">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cf5b8-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="cf5b8-118">Aşağıdaki sorgu bağımsız değişken olarak ExecutePrimitiveTypeQuery yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="cf5b8-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="cf5b8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf5b8-119">See Also</span></span>  
 [<span data-ttu-id="cf5b8-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cf5b8-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="cf5b8-121">REF</span><span class="sxs-lookup"><span data-stu-id="cf5b8-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="cf5b8-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="cf5b8-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="cf5b8-123">KEY</span><span class="sxs-lookup"><span data-stu-id="cf5b8-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="cf5b8-124">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="cf5b8-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
