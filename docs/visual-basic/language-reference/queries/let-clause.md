---
title: Let Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: a6ff3fc80a2b6752c61a8b8f7d4ce62b5a46baad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869880"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="c2570-102">Let Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2570-102">Let Clause (Visual Basic)</span></span>

<span data-ttu-id="c2570-103">Bir değeri hesaplar ve sorgu içindeki yeni bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="c2570-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2570-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2570-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="c2570-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c2570-105">Parts</span></span>  
  
|<span data-ttu-id="c2570-106">Terim</span><span class="sxs-lookup"><span data-stu-id="c2570-106">Term</span></span>|<span data-ttu-id="c2570-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c2570-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="c2570-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c2570-108">Required.</span></span> <span data-ttu-id="c2570-109">Sağlanan ifadenin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="c2570-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="c2570-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c2570-110">Required.</span></span> <span data-ttu-id="c2570-111">Değerlendirilecek ve belirtilen değişkene atanacak bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c2570-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2570-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2570-112">Remarks</span></span>  

 <span data-ttu-id="c2570-113">`Let`Yan tümcesi her sorgu sonucu için değerleri hesaplamanızı ve bir diğer ad kullanarak bunları başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2570-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="c2570-114">Diğer ad yan tümce gibi diğer yan tümcelerde kullanılabilir `Where` .</span><span class="sxs-lookup"><span data-stu-id="c2570-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="c2570-115">`Let`Yan tümcesi, sorguda yer alan bir ifade yan tümcesi için bir diğer ad belirtebileceğiniz ve ifade yan tümcesinin her kullanıldığı her seferinde diğer adı yerine geçecek bir sorgu deyimi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2570-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="c2570-116">Yan tümcesine herhangi bir sayıda `variable` ve `expression` atama ekleyebilirsiniz `Let` .</span><span class="sxs-lookup"><span data-stu-id="c2570-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="c2570-117">Her atamayı virgülle ayırın (,).</span><span class="sxs-lookup"><span data-stu-id="c2570-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2570-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2570-118">Example</span></span>  

 <span data-ttu-id="c2570-119">Aşağıdaki kod örneği, `Let` ürünlerde yüzde 10 indirimli iskontoyu hesaplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2570-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="c2570-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2570-120">See also</span></span>

- [<span data-ttu-id="c2570-121">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="c2570-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c2570-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="c2570-122">Queries</span></span>](index.md)
- [<span data-ttu-id="c2570-123">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c2570-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="c2570-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c2570-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="c2570-125">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c2570-125">Where Clause</span></span>](where-clause.md)
