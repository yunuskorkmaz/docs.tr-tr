---
title: "(Varlık SQL) dışında"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d489d95b87765d949ececa531d0169612ceb6e42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="except-entity-sql"></a><span data-ttu-id="9b3dd-102">(Varlık SQL) dışında</span><span class="sxs-lookup"><span data-stu-id="9b3dd-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="9b3dd-103">Tüm farklı değerler koleksiyonu sorgu ifadesinden de sorgu ifadesinden EXCEPT işleneni sağındaki döndürülmez EXCEPT işleneni sola döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="9b3dd-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b3dd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b3dd-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b3dd-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="9b3dd-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9b3dd-107">Başka bir sorgu ifadesinden döndürülen koleksiyonu ile karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b3dd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b3dd-108">Return Value</span></span>  
 <span data-ttu-id="9b3dd-109">Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b3dd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b3dd-110">Remarks</span></span>  
 <span data-ttu-id="9b3dd-111">DIŞINDA biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="9b3dd-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="9b3dd-113">Aşağıdaki tabloda önceliği gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="9b3dd-114">Önceliği</span><span class="sxs-lookup"><span data-stu-id="9b3dd-114">Precedence</span></span>|<span data-ttu-id="9b3dd-115">İşleçler</span><span class="sxs-lookup"><span data-stu-id="9b3dd-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="9b3dd-116">En yüksek</span><span class="sxs-lookup"><span data-stu-id="9b3dd-116">Highest</span></span>|<span data-ttu-id="9b3dd-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="9b3dd-117">INTERSECT</span></span>|  
||<span data-ttu-id="9b3dd-118">UNION</span><span class="sxs-lookup"><span data-stu-id="9b3dd-118">UNION</span></span><br /><br /> <span data-ttu-id="9b3dd-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="9b3dd-119">UNION ALL</span></span>|  
||<span data-ttu-id="9b3dd-120">DIŞINDA</span><span class="sxs-lookup"><span data-stu-id="9b3dd-120">EXCEPT</span></span>|  
|<span data-ttu-id="9b3dd-121">En düşük</span><span class="sxs-lookup"><span data-stu-id="9b3dd-121">Lowest</span></span>|<span data-ttu-id="9b3dd-122">VAR</span><span class="sxs-lookup"><span data-stu-id="9b3dd-122">EXISTS</span></span><br /><br /> <span data-ttu-id="9b3dd-123">ÇAKIŞIYOR</span><span class="sxs-lookup"><span data-stu-id="9b3dd-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="9b3dd-124">DÜZLEŞTİRME</span><span class="sxs-lookup"><span data-stu-id="9b3dd-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="9b3dd-125">AYARLAMA</span><span class="sxs-lookup"><span data-stu-id="9b3dd-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9b3dd-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b3dd-126">Example</span></span>  
 <span data-ttu-id="9b3dd-127">Aşağıdaki varlık SQL sorgusunu EXCEPT işleci gelen iki sorgu ifadeleri herhangi farklı değerler koleksiyonu döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="9b3dd-128">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9b3dd-129">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9b3dd-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9b3dd-130">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9b3dd-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9b3dd-131">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="9b3dd-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="9b3dd-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b3dd-132">See Also</span></span>  
 [<span data-ttu-id="9b3dd-133">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9b3dd-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
