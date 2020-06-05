---
title: "Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme"
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 36f623068372614ae034a8a7b31bffb7496f98b1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410701"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="0195f-102">Nasıl yapılır: Visual Basic'de Başka Bir Yordama Yordam Geçirme</span><span class="sxs-lookup"><span data-stu-id="0195f-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="0195f-103">Bu örnek, bir yordamın başka bir yordama iletilmesi için temsilcilerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0195f-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="0195f-104">Temsilci, Visual Basic diğer herhangi bir tür gibi kullanabileceğiniz bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0195f-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="0195f-105">`AddressOf`İşleci bir yordam adına uygulandığında bir temsilci nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0195f-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="0195f-106">Bu örnek, işleç ile elde edilen başka bir yordama başvuru alan bir temsilci parametresi olan bir yordama sahiptir `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="0195f-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="0195f-107">Temsilci ve eşleştirme yordamlarını oluşturma</span><span class="sxs-lookup"><span data-stu-id="0195f-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="0195f-108">Adlı bir temsilci oluşturun `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="0195f-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="0195f-109">`AddNumbers`İmzaların eşleşmesi için parametreleriyle eşleşen parametre ve dönüş değeri ile adlı bir yordam oluşturun `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="0195f-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="0195f-110">İle eşleşen imzaya sahip adlı bir yordam oluşturun `SubtractNumbers` `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="0195f-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="0195f-111">Bir `DelegateTest` temsilciyi parametre olarak alan adlı bir yordam oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0195f-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="0195f-112">`AddNumbers` `SubtractNumbers` İmzaları imzayla eşleştiğinden, bu yordam veya için bir başvuruyu kabul edebilir `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="0195f-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="0195f-113">`Test`Parametresi olarak bir kez çağıran adlı bir yordam oluşturun `DelegateTest` ve bir `AddNumbers` parametre olarak için temsilciyle yeniden `SubtractNumbers` .</span><span class="sxs-lookup"><span data-stu-id="0195f-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="0195f-114">`Test`Çağrıldığında, ilk olarak, `AddNumbers` `5` 8 olan ve üzerinde işlem sonucunu görüntüler `3` .</span><span class="sxs-lookup"><span data-stu-id="0195f-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="0195f-115">Daha sonra `SubtractNumbers` `9` , ve üzerinde işlem sonucu `3` , 6 ' da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0195f-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0195f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0195f-116">See also</span></span>

- [<span data-ttu-id="0195f-117">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="0195f-117">Delegates</span></span>](index.md)
- [<span data-ttu-id="0195f-118">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="0195f-118">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="0195f-119">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="0195f-119">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="0195f-120">Nasıl yapılır: Temsilci Yöntemi Çağırma</span><span class="sxs-lookup"><span data-stu-id="0195f-120">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)
