---
description: 'Daha fazla bilgi edinin: Group by yan tümcesi (Visual Basic)'
title: Group By Yan Tümcesi
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
ms.openlocfilehash: f5cfb76b0f4b1d191f959ae1812140c6872e93bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700513"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="e06bd-103">Group By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e06bd-103">Group By Clause (Visual Basic)</span></span>

<span data-ttu-id="e06bd-104">Bir sorgu sonucunun öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="e06bd-104">Groups the elements of a query result.</span></span> <span data-ttu-id="e06bd-105">, Her gruba toplam işlevleri uygulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-105">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="e06bd-106">Gruplandırma işlemi bir veya daha fazla anahtara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-106">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06bd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e06bd-107">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="e06bd-108">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e06bd-108">Parts</span></span>  
  
- <span data-ttu-id="e06bd-109">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="e06bd-109">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="e06bd-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e06bd-110">Optional.</span></span> <span data-ttu-id="e06bd-111">Gruplanmış sonuca dahil edilecek alanları açıkça tanımlayan sorgu değişkeninin veya değişkenlerinin bir veya daha fazla alanı.</span><span class="sxs-lookup"><span data-stu-id="e06bd-111">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="e06bd-112">Hiçbir alan belirtilmemişse, sorgu değişkeni veya değişkenlerinin tüm alanları gruplanmış sonuca dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-112">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="e06bd-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-113">Required.</span></span> <span data-ttu-id="e06bd-114">Öğe gruplarını belirlemekte kullanılacak anahtarı tanımlayan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e06bd-114">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="e06bd-115">Bileşik bir anahtar belirtmek için birden fazla anahtar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e06bd-115">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="e06bd-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e06bd-116">Optional.</span></span> <span data-ttu-id="e06bd-117">Bileşik anahtar oluşturmak için ile birlikte birleştirilmiş bir veya daha fazla ek anahtar `keyExp1` .</span><span class="sxs-lookup"><span data-stu-id="e06bd-117">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="e06bd-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-118">Required.</span></span> <span data-ttu-id="e06bd-119">Grupların nasıl toplanacağına ilişkin bir veya daha fazla ifade.</span><span class="sxs-lookup"><span data-stu-id="e06bd-119">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="e06bd-120">Gruplanmış sonuçların üye adını belirlemek için, `Group` aşağıdaki biçimlerden birinde olabilecek anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="e06bd-120">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="e06bd-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="e06bd-121">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="e06bd-122">Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e06bd-122">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06bd-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e06bd-123">Remarks</span></span>  

 <span data-ttu-id="e06bd-124">`Group By`Bir sorgunun sonuçlarını gruplara bölmek için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e06bd-124">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="e06bd-125">Gruplandırma bir anahtara veya birden çok anahtardan oluşan bileşik anahtara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-125">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="e06bd-126">Eşleşen anahtar değerleriyle ilişkili öğeler aynı gruba dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="e06bd-126">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="e06bd-127">`aggregateList` `Into` `Group` Gruba başvurmak için kullanılan üye adını tanımlamak için yan tümcesinin ve anahtar sözcüğünün parametresini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e06bd-127">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="e06bd-128">`Into`Gruplanmış öğeler için değerleri hesaplamak üzere yan tümcesine toplama işlevleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e06bd-128">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="e06bd-129">Standart toplama işlevlerinin bir listesi için bkz. [Aggregate yan tümcesi](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e06bd-129">For a list of standard aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e06bd-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="e06bd-130">Example</span></span>  

 <span data-ttu-id="e06bd-131">Aşağıdaki kod örneği, konumlarına (ülke/bölge) göre müşterilerin bir listesini gruplandırır ve her bir gruptaki müşterilerin sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e06bd-131">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="e06bd-132">Sonuçlar ülke/bölge adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e06bd-132">The results are ordered by country/region name.</span></span> <span data-ttu-id="e06bd-133">Gruplanmış sonuçlar şehir adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e06bd-133">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e06bd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e06bd-134">See also</span></span>

- [<span data-ttu-id="e06bd-135">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="e06bd-135">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e06bd-136">Sorgular</span><span class="sxs-lookup"><span data-stu-id="e06bd-136">Queries</span></span>](index.md)
- [<span data-ttu-id="e06bd-137">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e06bd-137">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e06bd-138">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e06bd-138">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="e06bd-139">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e06bd-139">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="e06bd-140">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e06bd-140">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="e06bd-141">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e06bd-141">Group Join Clause</span></span>](group-join-clause.md)
