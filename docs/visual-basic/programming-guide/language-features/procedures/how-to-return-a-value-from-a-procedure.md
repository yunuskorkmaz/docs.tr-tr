---
title: 'Nasıl yapılır: Bir değer döndüren bir yordam (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307892"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="76623-102">Nasıl yapılır: Bir değer döndüren bir yordam (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76623-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="76623-103">A `Function` yordamı değeri döndürür çağırma kodu yürüterek ya da bir `Return` deyimi veya karşılaşıldığında bir `Exit Function` veya `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="76623-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="76623-104">Return deyimi kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="76623-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="76623-105">PUT bir `Return` burada yordam görev tamamlandığında bir noktada deyimi.</span><span class="sxs-lookup"><span data-stu-id="76623-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="76623-106">İzleyin `Return` çağrıldığı koda döndürmek istediğiniz anahtar sözcüğü ile değer döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="76623-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="76623-107">Birden fazla aboneliğiniz `Return` aynı yordamındaki.</span><span class="sxs-lookup"><span data-stu-id="76623-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="76623-108">Aşağıdaki `Function` yordam en uzun kenar veya, dik üçgenin, hipotenüsü hesaplar ve çağıran koda döndürür.</span><span class="sxs-lookup"><span data-stu-id="76623-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="76623-109">Aşağıdaki örnek, tipik bir çağrı gösterir `hypotenuse`, döndürülen değer depolar.</span><span class="sxs-lookup"><span data-stu-id="76623-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="76623-110">Exit işlevine veya End işlevi kullanarak bir değer döndürmek için</span><span class="sxs-lookup"><span data-stu-id="76623-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="76623-111">En az bir yerinde `Function` yordamı, bir yordam adı için bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="76623-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="76623-112">Çalıştırdığınızda bir `Exit Function` veya `End Function` deyimi, Visual Basic, en son yordam adı için atanan değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="76623-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="76623-113">Birden fazla aboneliğiniz `Exit Function` aynı yordamı ve deyiminde karıştırmak `Return` ve `Exit Function` deyimleri aynı yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="76623-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="76623-114">Tek sahip `End Function` deyiminde bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="76623-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="76623-115">Daha fazla bilgi ve örnek için "Dönüş değerini" bölümüne bakın [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="76623-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76623-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76623-116">See also</span></span>

- [<span data-ttu-id="76623-117">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="76623-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="76623-118">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="76623-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="76623-119">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="76623-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="76623-120">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="76623-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="76623-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="76623-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="76623-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="76623-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="76623-123">Return Deyimi</span><span class="sxs-lookup"><span data-stu-id="76623-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="76623-124">Nasıl yapılır: Bir değer döndüren bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="76623-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="76623-125">Nasıl yapılır: Bir değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="76623-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
