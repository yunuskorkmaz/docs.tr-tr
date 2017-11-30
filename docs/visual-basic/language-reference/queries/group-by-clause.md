---
title: "Group By Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="6769b-102">Group By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6769b-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="6769b-103">Sorgu sonucu öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="6769b-103">Groups the elements of a query result.</span></span> <span data-ttu-id="6769b-104">Ayrıca her gruba toplama işlevleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6769b-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="6769b-105">Gruplandırma işlemi bir veya daha fazla anahtarları temel alır.</span><span class="sxs-lookup"><span data-stu-id="6769b-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6769b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6769b-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="6769b-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6769b-107">Parts</span></span>  
  
-   <span data-ttu-id="6769b-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="6769b-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="6769b-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6769b-109">Optional.</span></span> <span data-ttu-id="6769b-110">Bir veya daha fazla alanlar sorgu değişkeni veya açıkça gruplandırılmış sonucu dahil edilecek alanları tanımlayın değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="6769b-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="6769b-111">Hiçbir alan belirtilmedi, tüm alanlar sorgu değişkeni veya değişkenleri gruplandırılmış sonucu dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6769b-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="6769b-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6769b-112">Required.</span></span> <span data-ttu-id="6769b-113">Öğe gruplarını belirlemek için kullanılacak anahtarı tanımlayan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="6769b-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="6769b-114">Bir bileşik anahtarı belirtmek için birden fazla anahtar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6769b-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="6769b-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6769b-115">Optional.</span></span> <span data-ttu-id="6769b-116">İle birlikte bir veya daha fazla ek anahtarlar `keyExp1` bileşik bir anahtar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6769b-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="6769b-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6769b-117">Required.</span></span> <span data-ttu-id="6769b-118">Grupları nasıl toplanır tanımlayan bir veya daha fazla ifade.</span><span class="sxs-lookup"><span data-stu-id="6769b-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="6769b-119">Gruplandırılmış sonuçlar için bir üye adı tanımlamak için kullanmak `Group` anahtar sözcüğünü aşağıdaki biçimlerden birini olabilir:</span><span class="sxs-lookup"><span data-stu-id="6769b-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="6769b-120">veya</span><span class="sxs-lookup"><span data-stu-id="6769b-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="6769b-121">Gruba uygulamak için toplama işlevleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="6769b-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6769b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6769b-122">Remarks</span></span>  
 <span data-ttu-id="6769b-123">Kullanabileceğiniz `Group By` yan tümcesini bir sorgunun sonuçlarını gruplarına bölün.</span><span class="sxs-lookup"><span data-stu-id="6769b-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="6769b-124">Gruplandırma bir anahtar veya birden çok anahtarları oluşan bir bileşik anahtarı temel alan.</span><span class="sxs-lookup"><span data-stu-id="6769b-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="6769b-125">Eşleşen anahtar değerleri ile ilişkili öğeleri aynı grupta dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6769b-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="6769b-126">Kullandığınız `aggregateList` parametresinin `Into` yan tümcesi ve `Group` grubuna başvurmak için kullanılan üye adı tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6769b-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="6769b-127">Toplama işlevleri içinde dahil edebilirsiniz `Into` gruplandırılmış öğeler için değerleri hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6769b-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="6769b-128">Standart toplama işlevleri bir listesi için bkz: [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6769b-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6769b-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="6769b-129">Example</span></span>  
 <span data-ttu-id="6769b-130">Aşağıdaki kod örneğinde konumuna (ülke) bağlı müşteri listesi grupları ve her grubundaki müşterilerin sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6769b-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="6769b-131">Sonuçları ülke adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="6769b-131">The results are ordered by country name.</span></span> <span data-ttu-id="6769b-132">Gruplandırılmış sonuçları Şehir adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="6769b-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6769b-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6769b-133">See Also</span></span>  
 [<span data-ttu-id="6769b-134">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="6769b-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="6769b-135">Sorguları</span><span class="sxs-lookup"><span data-stu-id="6769b-135">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="6769b-136">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="6769b-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="6769b-137">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="6769b-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="6769b-138">Order By tümcesi</span><span class="sxs-lookup"><span data-stu-id="6769b-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="6769b-139">AGGREGATE tümcesi</span><span class="sxs-lookup"><span data-stu-id="6769b-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="6769b-140">Group Join tümcesi</span><span class="sxs-lookup"><span data-stu-id="6769b-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
