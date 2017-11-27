---
title: "Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e8e205f5238aab39aa92574bc5c680e68cc8a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="770b1-102">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="770b1-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="770b1-103">Bu örnek temsilciler başka bir yordama yordam geçirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="770b1-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="770b1-104">Bir temsilci gibi herhangi bir türü kullanabileceğiniz bir türüdür [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="770b1-104">A delegate is a type that you can use like any other type in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="770b1-105">`AddressOf` İşleci bir yordam adı uygulandığında bir temsilci nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="770b1-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="770b1-106">Bu örnek bir yordamı ile elde başka bir yordam için bir başvuru yapabileceği bir temsilci parametresiyle sahip `AddressOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="770b1-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="770b1-107">Temsilci oluşturup eşleşen yordamları</span><span class="sxs-lookup"><span data-stu-id="770b1-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="770b1-108">Adlı bir temsilci oluşturma `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="770b1-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="770b1-109">Adlı bir yordam oluşturma `AddNumbers` parametreleri ve eşleşen dönüş değeri ile `MathOperator`, imzaları eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="770b1-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="770b1-110">Adlı bir yordam oluşturma `SubtractNumbers` eşleşen imzayla `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="770b1-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="770b1-111">Adlı bir yordam oluşturma `DelegateTest` temsilci bir parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="770b1-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="770b1-112">Bu yordam bir başvuru kabul edebilir `AddNumbers` veya `SubtractNumbers`, kendi imzaları eşleştiğinden `MathOperator` imza.</span><span class="sxs-lookup"><span data-stu-id="770b1-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="770b1-113">Adlı bir yordam oluşturma `Test` çağrısı `DelegateTest` için temsilci ile bir kez `AddNumbers` bir parametre olarak ve yeniden için temsilci ile `SubtractNumbers` bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="770b1-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="770b1-114">Zaman `Test` olan çağrılmadan önce sonucunu gösterir `AddNumbers` üzerinde görevi `5` ve `3`, 8 olduğu.</span><span class="sxs-lookup"><span data-stu-id="770b1-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="770b1-115">Ardından sonucunu `SubtractNumbers` üzerinde hareket `9` ve `3` görüntülenir, 6.</span><span class="sxs-lookup"><span data-stu-id="770b1-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770b1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="770b1-116">See Also</span></span>  
 [<span data-ttu-id="770b1-117">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="770b1-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="770b1-118">AddressOf işleci</span><span class="sxs-lookup"><span data-stu-id="770b1-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="770b1-119">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="770b1-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="770b1-120">Nasıl yapılır: temsilci yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="770b1-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
