---
title: Let Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: ff298f001a2d865446436e8099a2fbbef593a00a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054204"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="75c22-102">Let Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75c22-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="75c22-103">Bir değeri hesaplar ve bir sorgu içinde yeni bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="75c22-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75c22-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="75c22-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="75c22-105">Parts</span></span>  
  
|<span data-ttu-id="75c22-106">Terim</span><span class="sxs-lookup"><span data-stu-id="75c22-106">Term</span></span>|<span data-ttu-id="75c22-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="75c22-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="75c22-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="75c22-108">Required.</span></span> <span data-ttu-id="75c22-109">Sağlanan ifade sonuçlarını başvurmak için kullanılan bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="75c22-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="75c22-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="75c22-110">Required.</span></span> <span data-ttu-id="75c22-111">Değerlendirilecek ve belirtilen değişkene atanan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="75c22-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75c22-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75c22-112">Remarks</span></span>  
 <span data-ttu-id="75c22-113">`Let` Yan tümcesi işlem değerleri her sorgu sonuç ve bir diğer ad kullanarak başvuru olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="75c22-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="75c22-114">Diğer ad diğer yan tümcelerinde gibi kullanılabilir `Where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="75c22-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="75c22-115">`Let` Yan tümcesi çünkü Sorguda ifade yan tümcesi için bir diğer ad belirtin ve ifade yan tümcesi kullanıldığında her zaman diğer adı yerine daha kolay olan bir sorgu deyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="75c22-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="75c22-116">Herhangi bir sayıda içerebilir `variable` ve `expression` atamalarını `Let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="75c22-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="75c22-117">Her atama virgülle (,) ayırın.</span><span class="sxs-lookup"><span data-stu-id="75c22-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c22-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="75c22-118">Example</span></span>  
 <span data-ttu-id="75c22-119">Aşağıdaki kod örneğinde `Let` ürünleri yüzde 10 indirim işlem yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="75c22-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="75c22-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75c22-120">See also</span></span>

- [<span data-ttu-id="75c22-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="75c22-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="75c22-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="75c22-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="75c22-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="75c22-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="75c22-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="75c22-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="75c22-125">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="75c22-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
