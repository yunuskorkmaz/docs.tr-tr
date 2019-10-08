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
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004734"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="24f55-102">Let Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24f55-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="24f55-103">Bir değeri hesaplar ve sorgu içindeki yeni bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="24f55-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24f55-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="24f55-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="24f55-105">Parts</span></span>  
  
|<span data-ttu-id="24f55-106">Terim</span><span class="sxs-lookup"><span data-stu-id="24f55-106">Term</span></span>|<span data-ttu-id="24f55-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="24f55-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="24f55-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="24f55-108">Required.</span></span> <span data-ttu-id="24f55-109">Sağlanan ifadenin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="24f55-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="24f55-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="24f55-110">Required.</span></span> <span data-ttu-id="24f55-111">Değerlendirilecek ve belirtilen değişkene atanacak bir ifade.</span><span class="sxs-lookup"><span data-stu-id="24f55-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24f55-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24f55-112">Remarks</span></span>  
 <span data-ttu-id="24f55-113">@No__t-0 yan tümcesi, her sorgu sonucu için değerleri hesaplamanızı ve bir diğer ad kullanarak bunları başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="24f55-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="24f55-114">Diğer ad, `Where` yan tümcesi gibi diğer yan tümcelerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24f55-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="24f55-115">@No__t-0 yan tümcesi, sorguda yer alan bir ifade yan tümcesi için bir diğer ad belirtebileceğiniz ve ifade yan tümcesinin her kullanıldığı her seferinde yerine geçecek bir sorgu deyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="24f55-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="24f55-116">@No__t-2 yan tümcesinde herhangi bir sayıda `variable` ve `expression` ataması ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24f55-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="24f55-117">Her atamayı virgülle ayırın (,).</span><span class="sxs-lookup"><span data-stu-id="24f55-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f55-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="24f55-118">Example</span></span>  
 <span data-ttu-id="24f55-119">Aşağıdaki kod örneği, ürünlerde yüzde 10 indirimi hesaplamak için `Let` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24f55-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="24f55-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24f55-120">See also</span></span>

- [<span data-ttu-id="24f55-121">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="24f55-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="24f55-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="24f55-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="24f55-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="24f55-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="24f55-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="24f55-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="24f55-125">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="24f55-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
