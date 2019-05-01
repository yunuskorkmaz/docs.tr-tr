---
title: "Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin"
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973296"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="5507f-102">Nasıl yapılır: Visual Basic'de başka bir yordama yordam geçirin</span><span class="sxs-lookup"><span data-stu-id="5507f-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="5507f-103">Bu örnek, temsilciler başka bir yordama yordam geçirme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5507f-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="5507f-104">Bir temsilci, herhangi bir türü Visual Basic'te gibi kullanabileceğiniz bir türdür.</span><span class="sxs-lookup"><span data-stu-id="5507f-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="5507f-105">`AddressOf` İşleci bir yordam adına uygulandığında bir temsilci nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5507f-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="5507f-106">Bu örnek ile elde ettiğiniz başka bir yordama başvuru sürebilir bir temsilci parametresi içeren bir yordamı sahip `AddressOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="5507f-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="5507f-107">Temsilci ve eşleşen yordamlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="5507f-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="5507f-108">Adlı bir temsilci oluşturmak `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="5507f-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="5507f-109">Adlı bir yordam oluşturma `AddNumbers` parametreleri ve eşleşen dönüş değeri ile `MathOperator`, böylece imzalar.</span><span class="sxs-lookup"><span data-stu-id="5507f-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="5507f-110">Adlı bir yordam oluşturma `SubtractNumbers` imzayla eşleşen `MathOperator`.</span><span class="sxs-lookup"><span data-stu-id="5507f-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="5507f-111">Adlı bir yordam oluşturma `DelegateTest` , temsilci bir parametre olarak alır.</span><span class="sxs-lookup"><span data-stu-id="5507f-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="5507f-112">Bu yordam bir başvuru kabul edebilir `AddNumbers` veya `SubtractNumbers`, bunların imzalarını eşleştiğinden `MathOperator` imzası.</span><span class="sxs-lookup"><span data-stu-id="5507f-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="5507f-113">Adlı bir yordam oluşturma `Test` çağrılarının `DelegateTest` temsilcisi ile bir kez `AddNumbers` bir parametre olarak ve yeniden temsilcisi ile `SubtractNumbers` bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="5507f-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="5507f-114">Zaman `Test` olan çağrılır, ilk sonucunu görüntüler `AddNumbers` üzerinde yürüten `5` ve `3`, 8 olduğu.</span><span class="sxs-lookup"><span data-stu-id="5507f-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="5507f-115">Ardından sonucunu `SubtractNumbers` üzerinde çalışan `9` ve `3` görüntülenir, 6.</span><span class="sxs-lookup"><span data-stu-id="5507f-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5507f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5507f-116">See also</span></span>

- [<span data-ttu-id="5507f-117">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5507f-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="5507f-118">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="5507f-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="5507f-119">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="5507f-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="5507f-120">Nasıl yapılır: Bir temsilci yöntemi çağırma</span><span class="sxs-lookup"><span data-stu-id="5507f-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
