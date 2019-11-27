---
title: 'Nasıl yapılır: Bir Yordamdan Değer Döndürme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346023"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="af14e-102">Nasıl yapılır: Bir Yordamdan Değer Döndürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af14e-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="af14e-103">`Function` yordamı, çağırma koduna bir `Return` ifadesiyle veya `Exit Function` ya da `End Function` ifadesiyle karşılaşarak bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="af14e-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="af14e-104">Return ifadesini kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="af14e-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="af14e-105">Yordamın görevinin tamamlandığı noktaya `Return` bir ifade koyun.</span><span class="sxs-lookup"><span data-stu-id="af14e-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="af14e-106">Çağırma koduna döndürmek istediğiniz değeri veren bir ifadeyle `Return` anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="af14e-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="af14e-107">Aynı yordamda birden fazla `Return` deyiminiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="af14e-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="af14e-108">Aşağıdaki `Function` yordam, sağ üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar ve bunu çağıran koda döndürür.</span><span class="sxs-lookup"><span data-stu-id="af14e-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="af14e-109">Aşağıdaki örnek, döndürülen değeri depolayan `hypotenuse`tipik bir çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af14e-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="af14e-110">Çıkış Işlevini veya End Işlevini kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="af14e-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="af14e-111">`Function` yordamında en az bir yerde, yordamın adına bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="af14e-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="af14e-112">Bir `Exit Function` veya `End Function` bildirisini çalıştırdığınızda Visual Basic yordamın adına en son atanan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="af14e-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="af14e-113">Aynı yordamda birden fazla `Exit Function` deyimi olabilir ve aynı yordamda `Return` ve `Exit Function` deyimlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af14e-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="af14e-114">Bir `Function` yordamında yalnızca bir `End Function` deyiminiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="af14e-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="af14e-115">Daha fazla bilgi ve örnek için bkz. [Function deyimindeki](../../../../visual-basic/language-reference/statements/function-statement.md)"dönüş değeri".</span><span class="sxs-lookup"><span data-stu-id="af14e-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af14e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af14e-116">See also</span></span>

- [<span data-ttu-id="af14e-117">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="af14e-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="af14e-118">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="af14e-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="af14e-119">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="af14e-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="af14e-120">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="af14e-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="af14e-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="af14e-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="af14e-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="af14e-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="af14e-123">Return Deyimi</span><span class="sxs-lookup"><span data-stu-id="af14e-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="af14e-124">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="af14e-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="af14e-125">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="af14e-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
