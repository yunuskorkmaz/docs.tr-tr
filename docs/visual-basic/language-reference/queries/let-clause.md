---
description: 'Daha fazla bilgi edinin: Let tümcesi (Visual Basic)'
title: Let Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88a7d96bb790a1e6ec5adfa4337c51f807930168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653647"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="e5112-103">Let Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5112-103">Let Clause (Visual Basic)</span></span>

<span data-ttu-id="e5112-104">Bir değeri hesaplar ve sorgu içindeki yeni bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="e5112-104">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5112-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5112-105">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="e5112-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5112-106">Parts</span></span>  
  
|<span data-ttu-id="e5112-107">Süre</span><span class="sxs-lookup"><span data-stu-id="e5112-107">Term</span></span>|<span data-ttu-id="e5112-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="e5112-108">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="e5112-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5112-109">Required.</span></span> <span data-ttu-id="e5112-110">Sağlanan ifadenin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="e5112-110">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="e5112-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5112-111">Required.</span></span> <span data-ttu-id="e5112-112">Değerlendirilecek ve belirtilen değişkene atanacak bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e5112-112">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5112-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5112-113">Remarks</span></span>  

 <span data-ttu-id="e5112-114">`Let`Yan tümcesi her sorgu sonucu için değerleri hesaplamanızı ve bir diğer ad kullanarak bunları başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5112-114">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="e5112-115">Diğer ad yan tümce gibi diğer yan tümcelerde kullanılabilir `Where` .</span><span class="sxs-lookup"><span data-stu-id="e5112-115">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="e5112-116">`Let`Yan tümcesi, sorguda yer alan bir ifade yan tümcesi için bir diğer ad belirtebileceğiniz ve ifade yan tümcesinin her kullanıldığı her seferinde diğer adı yerine geçecek bir sorgu deyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5112-116">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="e5112-117">Yan tümcesine herhangi bir sayıda `variable` ve `expression` atama ekleyebilirsiniz `Let` .</span><span class="sxs-lookup"><span data-stu-id="e5112-117">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="e5112-118">Her atamayı virgülle ayırın (,).</span><span class="sxs-lookup"><span data-stu-id="e5112-118">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5112-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5112-119">Example</span></span>  

 <span data-ttu-id="e5112-120">Aşağıdaki kod örneği, `Let` ürünlerde yüzde 10 indirimli iskontoyu hesaplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5112-120">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="e5112-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5112-121">See also</span></span>

- [<span data-ttu-id="e5112-122">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="e5112-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e5112-123">Sorgular</span><span class="sxs-lookup"><span data-stu-id="e5112-123">Queries</span></span>](index.md)
- [<span data-ttu-id="e5112-124">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e5112-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e5112-125">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e5112-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="e5112-126">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e5112-126">Where Clause</span></span>](where-clause.md)
