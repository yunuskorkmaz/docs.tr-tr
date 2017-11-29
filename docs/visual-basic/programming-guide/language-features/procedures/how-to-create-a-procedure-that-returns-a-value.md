---
title: "Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="b3972-102">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3972-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="b3972-103">Kullandığınız bir `Function` yordamı çağıran kodu için bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3972-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="b3972-104">Bir değer döndüren bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b3972-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="b3972-105">Diğer herhangi bir yordam dışında kullanmak bir `Function` deyimi, arkasından bir `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b3972-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="b3972-106">İçinde `Function` deyimi, izleyin `Function` adını yordamı ve parantez içinde parametre listesi olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="b3972-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="b3972-107">Parantezler ile izleyin bir `As` yan tümcesini döndürülen değerin veri türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="b3972-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="b3972-108">Yordam kod deyimleri arasında yerleştirin `Function` ve `End Function` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="b3972-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="b3972-109">Kullanım bir `Return` deyimi çağıran kodu değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3972-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="b3972-110">Aşağıdaki `Function` yordamı en uzun taraf veya diğer iki kenara için değerlerine göre bir sağ üçgen hipotenüsü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="b3972-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="b3972-111">Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="b3972-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b3972-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3972-112">See Also</span></span>  
 [<span data-ttu-id="b3972-113">Yordamları</span><span class="sxs-lookup"><span data-stu-id="b3972-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b3972-114">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="b3972-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="b3972-115">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="b3972-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="b3972-116">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="b3972-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="b3972-117">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b3972-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b3972-118">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="b3972-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="b3972-119">Nasıl yapılır: bir yordamdan değer döndürme</span><span class="sxs-lookup"><span data-stu-id="b3972-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="b3972-120">Nasıl yapılır: değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="b3972-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
