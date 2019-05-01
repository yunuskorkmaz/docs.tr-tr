---
title: Group By Tümcesi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 71e0ffc7f03a27a878aeb48eda9fbc58e5faae82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945333"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="1be47-102">Group By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1be47-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="1be47-103">Bir sorgu sonucunun öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="1be47-103">Groups the elements of a query result.</span></span> <span data-ttu-id="1be47-104">Ayrıca her grup için toplama işlevleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1be47-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="1be47-105">Gruplandırma işlemi, bir veya daha fazla anahtarlar üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="1be47-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be47-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1be47-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="1be47-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1be47-107">Parts</span></span>  
  
- <span data-ttu-id="1be47-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="1be47-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="1be47-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1be47-109">Optional.</span></span> <span data-ttu-id="1be47-110">Bir veya daha fazla alan sorgu değişkeni veya açıkça gruplandırılmış sonuca dahil için alanları tanımlayan değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="1be47-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="1be47-111">Sorgu değişkeni veya değişkenleri tüm alanlar, hiçbir alan belirtilmesi durumunda, gruplandırılmış sonuca dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="1be47-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="1be47-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1be47-112">Required.</span></span> <span data-ttu-id="1be47-113">Öğe grupları belirlemek için kullanılacak anahtarı tanımlayan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="1be47-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="1be47-114">Bir bileşik anahtarı belirtmek için birden fazla anahtar belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="1be47-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="1be47-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1be47-115">Optional.</span></span> <span data-ttu-id="1be47-116">İle birlikte bir veya daha fazla ek anahtarlar `keyExp1` bileşik bir anahtar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1be47-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="1be47-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1be47-117">Required.</span></span> <span data-ttu-id="1be47-118">Grupların nasıl toplanır tanımlayan bir veya daha fazla ifadeler.</span><span class="sxs-lookup"><span data-stu-id="1be47-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="1be47-119">Gruplandırılmış sonuçlar için bir üye adını tanımlamak için kullanmak `Group` anahtar sözcüğü aşağıdaki biçimlerden birini olabilir:</span><span class="sxs-lookup"><span data-stu-id="1be47-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="1be47-120">-veya-</span><span class="sxs-lookup"><span data-stu-id="1be47-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="1be47-121">Gruba uygulanacak toplama işlevleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1be47-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1be47-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1be47-122">Remarks</span></span>  
 <span data-ttu-id="1be47-123">Kullanabileceğiniz `Group By` yan bir sorgunun sonuçlarını gruplarına bölün.</span><span class="sxs-lookup"><span data-stu-id="1be47-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="1be47-124">Gruplama, bir anahtar veya birden çok anahtarlarını içeren bir bileşik anahtarı temel alır.</span><span class="sxs-lookup"><span data-stu-id="1be47-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="1be47-125">Eşleşen anahtar değerleri ile ilişkili olan öğeler aynı grupta dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="1be47-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="1be47-126">Kullandığınız `aggregateList` parametresinin `Into` yan tümcesi ve `Group` grubuna başvurmak için kullanılan bir üye adını tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1be47-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="1be47-127">Toplama işlevi de içerebilir `Into` gruplandırılmış öğeler için değeri hesaplamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="1be47-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="1be47-128">Standart toplama işlevleri bir listesi için bkz. [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1be47-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be47-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="1be47-129">Example</span></span>  
 <span data-ttu-id="1be47-130">Aşağıdaki kod örneği, bulundukları konuma göre (ülke) müşterilerin listesini gruplandırır ve her gruptaki müşterilerin sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1be47-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="1be47-131">Sonuçları ülke adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="1be47-131">The results are ordered by country name.</span></span> <span data-ttu-id="1be47-132">Gruplandırılmış sonuçlar Şehir adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="1be47-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1be47-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1be47-133">See also</span></span>

- [<span data-ttu-id="1be47-134">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="1be47-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="1be47-135">Sorgular</span><span class="sxs-lookup"><span data-stu-id="1be47-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="1be47-136">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="1be47-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="1be47-137">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="1be47-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="1be47-138">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="1be47-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="1be47-139">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="1be47-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="1be47-140">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="1be47-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
