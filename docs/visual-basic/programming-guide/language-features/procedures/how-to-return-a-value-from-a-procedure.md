---
title: 'Nasıl yapılır: Bir değer döndüren bir yordam (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 45f175de647887a406f8ae87dae492a5fe58cca9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976739"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="792af-102">Nasıl yapılır: Bir değer döndüren bir yordam (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="792af-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="792af-103">A `Function` yordamı değeri döndürür çağırma kodu yürüterek ya da bir `Return` deyimi veya karşılaşıldığında bir `Exit Function` veya `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="792af-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="792af-104">Return deyimi kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="792af-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="792af-105">PUT bir `Return` burada yordam görev tamamlandığında bir noktada deyimi.</span><span class="sxs-lookup"><span data-stu-id="792af-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="792af-106">İzleyin `Return` çağrıldığı koda döndürmek istediğiniz anahtar sözcüğü ile değer döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="792af-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="792af-107">Birden fazla aboneliğiniz `Return` aynı yordamındaki.</span><span class="sxs-lookup"><span data-stu-id="792af-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="792af-108">Aşağıdaki `Function` yordam en uzun kenar veya, dik üçgenin, hipotenüsü hesaplar ve çağıran koda döndürür.</span><span class="sxs-lookup"><span data-stu-id="792af-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="792af-109">Aşağıdaki örnek, tipik bir çağrı gösterir `hypotenuse`, döndürülen değer depolar.</span><span class="sxs-lookup"><span data-stu-id="792af-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="792af-110">Exit işlevine veya End işlevi kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="792af-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="792af-111">En az bir yerinde `Function` yordamı, bir yordam adı için bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="792af-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="792af-112">Çalıştırdığınızda bir `Exit Function` veya `End Function` deyimi, Visual Basic, en son yordam adı için atanan değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="792af-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="792af-113">Birden fazla aboneliğiniz `Exit Function` aynı yordamı ve deyiminde karıştırmak `Return` ve `Exit Function` deyimleri aynı yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="792af-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="792af-114">Tek sahip `End Function` deyiminde bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="792af-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="792af-115">Daha fazla bilgi ve örnek için "Dönüş değerini" bölümüne bakın [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="792af-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792af-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="792af-116">See also</span></span>
- [<span data-ttu-id="792af-117">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="792af-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="792af-118">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="792af-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="792af-119">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="792af-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="792af-120">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="792af-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="792af-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="792af-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="792af-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="792af-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="792af-123">Return Deyimi</span><span class="sxs-lookup"><span data-stu-id="792af-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="792af-124">Nasıl yapılır: Bir değer döndüren bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="792af-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="792af-125">Nasıl yapılır: Bir değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="792af-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
