---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388770"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="d10a5-102">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d10a5-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="d10a5-103">`Function`Yordam, çağırma koduna bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="d10a5-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="d10a5-104">Bunun adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına veya bir ifadeye ekleyerek çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a5-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="d10a5-105">Bir ifade içindeki bir Işlev yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="d10a5-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="d10a5-106">`Function`Yordam adını, bir değişkeni kullandığınız şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d10a5-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="d10a5-107">Bir `Function` ifadede değişken veya sabit kullanabileceğiniz her yerde bir yordam çağrısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a5-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="d10a5-108">Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="d10a5-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d10a5-109">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a5-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="d10a5-110">Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="d10a5-111">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d10a5-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d10a5-112">Bağımsız değişkenleri `Function` yordamın ilgili parametreleri tanımladığı sırada girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d10a5-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="d10a5-113">Alternatif olarak, bir veya daha fazla bağımsız değişkeni ada göre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a5-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="d10a5-114">Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="d10a5-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="d10a5-115">Yordamdan döndürülen değer, bir değişkenin veya sabitin değeri gibi ifadeye katılır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="d10a5-116">Atama deyimindeki bir Işlev yordamını çağırmak için</span><span class="sxs-lookup"><span data-stu-id="d10a5-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="d10a5-117">`Function`Atama deyimindeki eşittir () işaretinden sonra yordam adını kullanın `=` .</span><span class="sxs-lookup"><span data-stu-id="d10a5-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="d10a5-118">Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="d10a5-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d10a5-119">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a5-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="d10a5-120">Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="d10a5-121">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d10a5-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d10a5-122">Bağımsız değişkenleri, `Function` ilgili parametreleri ada göre geçirmediğiniz takdirde yordamın tanımladığı sırada girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d10a5-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="d10a5-123">Yordamdan döndürülen değer, atama ifadesinin sol tarafındaki değişken veya özellikte saklanır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d10a5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d10a5-124">Example</span></span>  
 <span data-ttu-id="d10a5-125">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeninin değerini almak için Visual Basic çağırır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="d10a5-126">İlk satır `Environ` bir ifade içinde çağrı ve ikinci satır onu bir atama deyiminde çağırır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="d10a5-127">`Environ`değişken adını tek bağımsız değişkeni olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d10a5-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="d10a5-128">Bu, değişkenin değerini çağıran koda döndürür.</span><span class="sxs-lookup"><span data-stu-id="d10a5-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d10a5-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d10a5-129">See also</span></span>

- [<span data-ttu-id="d10a5-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="d10a5-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d10a5-131">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d10a5-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d10a5-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d10a5-132">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="d10a5-133">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d10a5-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="d10a5-134">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="d10a5-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="d10a5-135">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="d10a5-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
