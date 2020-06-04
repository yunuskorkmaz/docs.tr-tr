---
title: 'Nasıl yapılır: Bir Yordamdan Değer Döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 917e52b711645fbf94a132216a3fa90b0dfc15b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414330"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="e44f2-102">Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e44f2-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="e44f2-103">`Function`Yordam, çağırma koduna, bir `Return` ifadeyi yürüterek veya bir veya ifadesiyle karşılaşarak bir değer döndürür `Exit Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="e44f2-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="e44f2-104">Return ifadesini kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="e44f2-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="e44f2-105">`Return`Yordamın görevinin tamamlandığı noktaya bir ifade koyun.</span><span class="sxs-lookup"><span data-stu-id="e44f2-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="e44f2-106">`Return`Çağırma koduna döndürmek istediğiniz değeri veren bir ifadeyle anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="e44f2-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="e44f2-107">Aynı yordamda birden fazla deyime sahip olabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="e44f2-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="e44f2-108">Aşağıdaki `Function` yordam, sağ üçgenin en uzun tarafını veya hipotenüsü hesaplar ve bunu çağıran koda döndürür.</span><span class="sxs-lookup"><span data-stu-id="e44f2-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="e44f2-109">Aşağıdaki örnek `hypotenuse` , döndürülen değeri depolayan, için tipik bir çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e44f2-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="e44f2-110">Çıkış Işlevini veya End Işlevini kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="e44f2-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="e44f2-111">Yordamda en az bir yerde `Function` , yordamın adına bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="e44f2-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="e44f2-112">Bir `Exit Function` veya `End Function` ifadesini yürüttüğünüzde, Visual Basic yordamın adına en son atanan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e44f2-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="e44f2-113">Aynı yordamda birden fazla deyime sahip olabilirsiniz `Exit Function` ve `Return` `Exit Function` aynı yordamda ve deyimlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e44f2-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="e44f2-114">Yordamda yalnızca bir `End Function` deyiminiz olabilir `Function` .</span><span class="sxs-lookup"><span data-stu-id="e44f2-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="e44f2-115">Daha fazla bilgi ve örnek için bkz. [Function deyimindeki](../../../language-reference/statements/function-statement.md)"dönüş değeri".</span><span class="sxs-lookup"><span data-stu-id="e44f2-115">For more information and an example, see "Return Value" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44f2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e44f2-116">See also</span></span>

- [<span data-ttu-id="e44f2-117">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e44f2-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e44f2-118">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e44f2-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e44f2-119">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="e44f2-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e44f2-120">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="e44f2-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e44f2-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="e44f2-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e44f2-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="e44f2-122">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="e44f2-123">Return ekstresi</span><span class="sxs-lookup"><span data-stu-id="e44f2-123">Return Statement</span></span>](../../../language-reference/statements/return-statement.md)
- [<span data-ttu-id="e44f2-124">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e44f2-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="e44f2-125">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="e44f2-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
