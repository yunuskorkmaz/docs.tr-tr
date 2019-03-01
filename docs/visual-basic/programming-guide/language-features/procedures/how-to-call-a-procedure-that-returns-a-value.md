---
title: 'Nasıl yapılır: (Visual Basic) bir değer döndüren bir yordam çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 10167075e903693df804cba044301e1f1bc6306e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974464"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="a5602-102">Nasıl yapılır: (Visual Basic) bir değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="a5602-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="a5602-103">A `Function` yordamın çağrıldığı koda bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5602-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="a5602-104">Bu adı ve bağımsız değişkenler dahil ederek işlecin sağ tarafındaki Atama ifadesinin veya bir ifade ya da çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="a5602-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="a5602-105">İçinde bir ifade bir işlev yordam çağırmak için</span><span class="sxs-lookup"><span data-stu-id="a5602-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="a5602-106">Kullanma `Function` yordamı kullandığınız bir değişken gibi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a5602-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="a5602-107">Kullanabileceğiniz bir `Function` kullanabileceğiniz bir değişken veya sabit bir ifadede herhangi bir yordam çağırma.</span><span class="sxs-lookup"><span data-stu-id="a5602-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="a5602-108">Parantez içine bağımsız değişken listesi için yordamın adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="a5602-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a5602-109">Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5602-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="a5602-110">Ancak, parantezler kullanarak kodunuzu okumayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a5602-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="a5602-111">Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a5602-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a5602-112">Bağımsız değişkenler aynı sırada sağladığınız emin olun, `Function` yordamı karşılık gelen parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5602-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="a5602-113">Alternatif olarak, ada göre bir veya daha fazla bağımsız değişken geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5602-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="a5602-114">Daha fazla bilgi için [geçirmeden bağımsız değişkenleri konuma ve ada göre](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="a5602-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="a5602-115">Yordamdan döndürülen değer, bir değişken değeri olarak yalnızca ifade katıldığı veya sabiti gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5602-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="a5602-116">Bir atama ifadesinde bir işlev yordam çağırmak için</span><span class="sxs-lookup"><span data-stu-id="a5602-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="a5602-117">Kullanım `Function` eşit aşağıdaki yordam adı (`=`) atama ifadesi oturum açın.</span><span class="sxs-lookup"><span data-stu-id="a5602-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="a5602-118">Parantez içine bağımsız değişken listesi için yordamın adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="a5602-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="a5602-119">Hiçbir bağımsız değişken varsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5602-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="a5602-120">Ancak, parantezler kullanarak kodunuzu okumayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a5602-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="a5602-121">Bağımsız değişken listesi parantezlerinin virgülle ayırarak yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a5602-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="a5602-122">Bağımsız değişkenler aynı sırada sağladığınız emin olun, `Function` yordamı ada göre geçirme sürece, karşılık gelen parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5602-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="a5602-123">Yordamdan döndürülen değer değişken veya özellik atama ifadesi sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="a5602-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5602-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5602-124">Example</span></span>  
 <span data-ttu-id="a5602-125">Aşağıdaki örnek, Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeninin değerini almak için.</span><span class="sxs-lookup"><span data-stu-id="a5602-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="a5602-126">İlk satırı çağrıları `Environ` satır içinde bir ifade ve ikinci bir atama ifadesinde çağırır.</span><span class="sxs-lookup"><span data-stu-id="a5602-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="a5602-127">`Environ` değişken adı, tek bir bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="a5602-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="a5602-128">Çağrıldığı koda değişken değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5602-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a5602-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5602-129">See also</span></span>
- [<span data-ttu-id="a5602-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="a5602-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a5602-131">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="a5602-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a5602-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a5602-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="a5602-133">Nasıl yapılır: Bir değer döndüren bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5602-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="a5602-134">Nasıl yapılır: Bir yordamdan değer döndürme</span><span class="sxs-lookup"><span data-stu-id="a5602-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="a5602-135">Nasıl yapılır: Bir değer döndürmeyen bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="a5602-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
