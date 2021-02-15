---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: değer döndüren bir yordam çağırma (Visual Basic)'
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 74c7b6c9340537088ac631fc47f9ebf7b1a203cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466750"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="b7a27-103">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7a27-103">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="b7a27-104">`Function`Yordam, çağırma koduna bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7a27-104">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="b7a27-105">Bunun adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına veya bir ifadeye ekleyerek çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7a27-105">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="b7a27-106">Bir ifade içindeki bir Işlev yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b7a27-106">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="b7a27-107">`Function`Yordam adını, bir değişkeni kullandığınız şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7a27-107">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="b7a27-108">Bir `Function` ifadede değişken veya sabit kullanabileceğiniz her yerde bir yordam çağrısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7a27-108">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="b7a27-109">Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a27-109">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b7a27-110">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7a27-110">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="b7a27-111">Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-111">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="b7a27-112">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b7a27-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b7a27-113">Bağımsız değişkenleri `Function` yordamın ilgili parametreleri tanımladığı sırada girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b7a27-113">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="b7a27-114">Alternatif olarak, bir veya daha fazla bağımsız değişkeni ada göre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7a27-114">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="b7a27-115">Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="b7a27-115">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="b7a27-116">Yordamdan döndürülen değer, bir değişkenin veya sabitin değeri gibi ifadeye katılır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-116">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="b7a27-117">Atama deyimindeki bir Işlev yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b7a27-117">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="b7a27-118">`Function`Atama deyimindeki eşittir () işaretinden sonra yordam adını kullanın `=` .</span><span class="sxs-lookup"><span data-stu-id="b7a27-118">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="b7a27-119">Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="b7a27-119">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b7a27-120">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7a27-120">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="b7a27-121">Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-121">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="b7a27-122">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b7a27-122">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b7a27-123">Bağımsız değişkenleri, `Function` ilgili parametreleri ada göre geçirmediğiniz takdirde yordamın tanımladığı sırada girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b7a27-123">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="b7a27-124">Yordamdan döndürülen değer, atama ifadesinin sol tarafındaki değişken veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-124">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7a27-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7a27-125">Example</span></span>  

 <span data-ttu-id="b7a27-126">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeninin değerini almak için Visual Basic çağırır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-126">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="b7a27-127">İlk satır `Environ` bir ifade içinde çağrı ve ikinci satır onu bir atama deyiminde çağırır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-127">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="b7a27-128">`Environ` değişken adını tek bağımsız değişkeni olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b7a27-128">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="b7a27-129">Bu, değişkenin değerini çağıran koda döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7a27-129">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b7a27-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7a27-130">See also</span></span>

- [<span data-ttu-id="b7a27-131">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="b7a27-131">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="b7a27-132">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="b7a27-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b7a27-133">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="b7a27-133">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="b7a27-134">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b7a27-134">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="b7a27-135">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="b7a27-135">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="b7a27-136">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="b7a27-136">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
