---
title: "İşlev Yordamları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9520a6555e65fd801a5c40d40748028e04a10739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="47f78-102">İşlev Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47f78-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="47f78-103">A `Function` yordamdır bir dizi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deyimleri içine tarafından `Function` ve `End Function` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="47f78-103">A `Function` procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="47f78-104">`Function` Yordamı bir görevi gerçekleştirir ve çağrıyı yapan kod denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="47f78-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="47f78-105">Denetim geri döndüğünde, çağrıyı yapan kod de bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="47f78-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="47f78-106">Yordam çağrıldığında çalıştırmak, kendi deyimleri her zaman ilk yürütülebilir deyimi sonra başlayarak `Function` deyimi ve ilk ile bitiş `End Function`, `Exit Function`, veya `Return` deyimiyle karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="47f78-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="47f78-107">Tanımlayabileceğiniz bir `Function` modülü, sınıf veya yapı yordamda.</span><span class="sxs-lookup"><span data-stu-id="47f78-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="47f78-108">Bu `Public` varsayılan olarak, yani çağırabilirsiniz onu yerden modülü, sınıf veya yapı içinde tanımlanan bu erişimi, uygulamanızda.</span><span class="sxs-lookup"><span data-stu-id="47f78-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="47f78-109">A `Function` yordamı sabitleri, değişkenleri veya kendisine çağrıyı yapan kod tarafından geçirilen ifadeler gibi bağımsız değişkenleri alabilir.</span><span class="sxs-lookup"><span data-stu-id="47f78-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="47f78-110">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47f78-110">Declaration Syntax</span></span>  
 <span data-ttu-id="47f78-111">Bildirme sözdizimi bir `Function` yordam aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="47f78-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="47f78-112">*Değiştiricileri* erişim düzeyini ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme ilgili bilgileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47f78-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="47f78-113">Daha fazla bilgi için bkz: [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47f78-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="47f78-114">Her bir parametreyi yapmak için aynı şekilde bildirme [alt yordamlar](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="47f78-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="47f78-115">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="47f78-115">Data Type</span></span>  
 <span data-ttu-id="47f78-116">Her `Function` yordamı sahip bir veri türü, yalnızca olarak her değişken yapar.</span><span class="sxs-lookup"><span data-stu-id="47f78-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="47f78-117">Bu veri türü tarafından belirtilen `As` yan tümcesinde `Function` deyimi ve onu işlevi çağıran kodu döndürür değerinin veri türü belirler.</span><span class="sxs-lookup"><span data-stu-id="47f78-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="47f78-118">Aşağıdaki örnek bildirimlerini bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47f78-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="47f78-119">Daha fazla bilgi için bkz: "Bölümleri" [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47f78-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="47f78-120">Dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="47f78-120">Returning Values</span></span>  
 <span data-ttu-id="47f78-121">Değer bir `Function` yordamı gönderir çağıran kodu geri dönüş değerini çağrılır.</span><span class="sxs-lookup"><span data-stu-id="47f78-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="47f78-122">Yordamın bu değer iki yoldan biriyle döndürür:</span><span class="sxs-lookup"><span data-stu-id="47f78-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="47f78-123">Kullandığı `Return` döndürür ve dönüş değeri belirtmek için deyimi kontrol hemen çağıran program.</span><span class="sxs-lookup"><span data-stu-id="47f78-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="47f78-124">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="47f78-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="47f78-125">Yordamın bir veya daha fazla deyimlerinde kendi işlev adı değeri atar.</span><span class="sxs-lookup"><span data-stu-id="47f78-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="47f78-126">Çağıran program kadar denetim döndürmez bir `Exit Function` veya `End Function` deyimi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="47f78-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="47f78-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="47f78-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="47f78-128">Dönüş değeri işlev adını atama avantajı bulduğu kadar denetim yordamdan döndürmüyor olan bir `Exit Function` veya `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="47f78-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="47f78-129">Bu, başlangıç değeri atayın ve gerekirse daha sonra ayarlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="47f78-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="47f78-130">Dönüş değerleri hakkında daha fazla bilgi için bkz: [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="47f78-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="47f78-131">Diziler döndürme hakkında daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="47f78-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="47f78-132">Arama sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47f78-132">Calling Syntax</span></span>  
 <span data-ttu-id="47f78-133">Çağırmayı bir `Function` adını ve bağımsız değişkenler ya da Atama ifadesinin veya bir ifade sağ taraftaki ekleyerek yordamı.</span><span class="sxs-lookup"><span data-stu-id="47f78-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="47f78-134">İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlayın ve bağımsız değişken listesi parantez içine alın.</span><span class="sxs-lookup"><span data-stu-id="47f78-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="47f78-135">Bağımsız değişkenler sağlandıysa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47f78-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="47f78-136">Çağrı sözdizimi bir `Function` yordam aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="47f78-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="47f78-137">*lvalue*`=`*functionname* `[(` *bağımsızdeğişkenListesi*    `)]`</span><span class="sxs-lookup"><span data-stu-id="47f78-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="47f78-138">`If ((`*functionname* `[(` *bağımsızdeğişkenListesi* `)] / 3) <=` *ifade*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="47f78-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="47f78-139">Çağırdığınızda bir `Function` yordamı, sahip olmadığınız dönüş değeri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="47f78-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="47f78-140">Bunu yapmazsanız, işlevin tüm eylemler gerçekleştirilir, ancak dönüş değeri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="47f78-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="47f78-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>Genelde bu şekilde denir.</span><span class="sxs-lookup"><span data-stu-id="47f78-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="47f78-142">Bildirim ve çağrı çizimi</span><span class="sxs-lookup"><span data-stu-id="47f78-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="47f78-143">Aşağıdaki `Function` yordamı en uzun taraf veya diğer iki kenara için değerlerine göre bir sağ üçgen hipotenüsü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="47f78-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 <span data-ttu-id="47f78-144">Aşağıdaki örnek tipik bir çağrı gösterilmektedir `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="47f78-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="47f78-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47f78-145">See Also</span></span>  
 [<span data-ttu-id="47f78-146">Yordamları</span><span class="sxs-lookup"><span data-stu-id="47f78-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="47f78-147">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="47f78-147">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="47f78-148">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="47f78-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="47f78-149">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="47f78-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="47f78-150">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="47f78-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="47f78-151">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="47f78-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="47f78-152">Nasıl yapılır: değer döndüren bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="47f78-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="47f78-153">Nasıl yapılır: bir yordamdan değer döndürme</span><span class="sxs-lookup"><span data-stu-id="47f78-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="47f78-154">Nasıl yapılır: değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="47f78-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
