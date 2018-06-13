---
title: "Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme"
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: c28ac7a640ec863b37bd7407d0273a1918964ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647244"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="e9bdb-102">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="e9bdb-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="e9bdb-103">Bu örnek temsilciler başka bir yordama yordam geçirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="e9bdb-104">Bir temsilci, herhangi bir türü Visual Basic'te gibi kullanabileceğiniz bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="e9bdb-105">`AddressOf` İşleci bir yordam adı uygulandığında bir temsilci nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="e9bdb-106">Bu örnek bir yordamı ile elde başka bir yordam için bir başvuru yapabileceği bir temsilci parametresiyle sahip `AddressOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="e9bdb-107">Temsilci oluşturup eşleşen yordamları</span><span class="sxs-lookup"><span data-stu-id="e9bdb-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="e9bdb-108">Adlı bir temsilci oluşturma `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="e9bdb-109">Adlı bir yordam oluşturma `AddNumbers` parametreleri ve eşleşen dönüş değeri ile `MathOperator`, imzaları eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="e9bdb-110">Adlı bir yordam oluşturma `SubtractNumbers` eşleşen imzayla `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="e9bdb-111">Adlı bir yordam oluşturma `DelegateTest` temsilci bir parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="e9bdb-112">Bu yordam bir başvuru kabul edebilir `AddNumbers` veya `SubtractNumbers`, kendi imzaları eşleştiğinden `MathOperator` imza.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="e9bdb-113">Adlı bir yordam oluşturma `Test` çağrısı `DelegateTest` için temsilci ile bir kez `AddNumbers` bir parametre olarak ve yeniden için temsilci ile `SubtractNumbers` bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="e9bdb-114">Zaman `Test` olan çağrılmadan önce sonucunu gösterir `AddNumbers` üzerinde görevi `5` ve `3`, 8 olduğu.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="e9bdb-115">Ardından sonucunu `SubtractNumbers` üzerinde hareket `9` ve `3` görüntülenir, 6.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bdb-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-116">See Also</span></span>  
 [<span data-ttu-id="e9bdb-117">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e9bdb-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="e9bdb-118">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="e9bdb-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="e9bdb-119">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="e9bdb-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="e9bdb-120">Nasıl yapılır: Temsilci Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="e9bdb-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
