---
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbaaa5ed17845a7ac8847786fb10111c724015ba
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="120b4-102">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="120b4-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="120b4-103">A `Function` yordamı çağıran kodu için bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="120b4-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="120b4-104">Bu adı ve bağımsız değişkenler dahil ederek Atama ifadesinin veya bir ifade sağ taraftaki ya da çağırın.</span><span class="sxs-lookup"><span data-stu-id="120b4-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="120b4-105">Bir ifade işlevi yordamda çağırmak için</span><span class="sxs-lookup"><span data-stu-id="120b4-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="120b4-106">Kullanmak `Function` yordamı adı bir değişken kullandığınız aynı gibi.</span><span class="sxs-lookup"><span data-stu-id="120b4-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="120b4-107">Kullanabileceğiniz bir `Function` yordam çağrısı her yerden kullanabileceğiniz bir değişken veya sabit bir ifade.</span><span class="sxs-lookup"><span data-stu-id="120b4-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="120b4-108">Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="120b4-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="120b4-109">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="120b4-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="120b4-110">Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="120b4-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="120b4-111">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="120b4-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="120b4-112">Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Function` yordamı ilgili parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="120b4-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="120b4-113">Alternatif olarak, ada göre bir veya daha fazla bağımsız değişkenler geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="120b4-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="120b4-114">Daha fazla bilgi için bkz: [geçirme bağımsız değişkenleri konuma ve ada göre](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="120b4-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="120b4-115">Bir değişkenin değeri olarak yalnızca ifade yordamdan döndürülen değer katılan veya sabiti gerekir.</span><span class="sxs-lookup"><span data-stu-id="120b4-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="120b4-116">Bir işlev yordamı bir atama deyiminde çağırmak için</span><span class="sxs-lookup"><span data-stu-id="120b4-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="120b4-117">Kullanım `Function` eşittir aşağıdaki yordam adı (`=`) atama deyiminde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="120b4-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="120b4-118">Bağımsız değişken listesi kapsamak için parantez yordamı adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="120b4-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="120b4-119">Bağımsız değişkenler varsa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="120b4-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="120b4-120">Ancak, parantez kullanarak kodunuzu okumak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="120b4-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="120b4-121">Bağımsız değişkenler, virgülle ayrılmış parantez içinde bağımsız değişken listesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="120b4-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="120b4-122">Bağımsız değişkenleri aynı sırada sağladığınız emin olun, `Function` yordamı ada göre geçirme sürece ilgili parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="120b4-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="120b4-123">Yordamdan döndürülen değer değişken veya özellik Atama ifadesinin sol tarafında depolanır.</span><span class="sxs-lookup"><span data-stu-id="120b4-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="120b4-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="120b4-124">Example</span></span>  
 <span data-ttu-id="120b4-125">Aşağıdaki örnek Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeni değeri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="120b4-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="120b4-126">İlk satırı çağrıları `Environ` satır bir ifade ve saniye içinde bir atama deyiminde çağırır.</span><span class="sxs-lookup"><span data-stu-id="120b4-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="120b4-127">`Environ` tek bağımsız değişken olarak değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="120b4-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="120b4-128">Bu, çağrıyı yapan kod değişkenin değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="120b4-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="120b4-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="120b4-129">See Also</span></span>  
 [<span data-ttu-id="120b4-130">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="120b4-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="120b4-131">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="120b4-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="120b4-132">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="120b4-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="120b4-133">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="120b4-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="120b4-134">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="120b4-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="120b4-135">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="120b4-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
