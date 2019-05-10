---
title: İşlev Yordamları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 4fd24369380e5f8ccf8de939c36ba72a12dc872e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649609"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="ebf59-102">İşlev Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebf59-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="ebf59-103">A `Function` yordamdır kapsadığı Visual Basic deyimleri bir dizi `Function` ve `End Function` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="ebf59-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="ebf59-104">`Function` Yordamı bir görevi gerçekleştirir ve çağıran koda denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebf59-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="ebf59-105">Denetimi geri döndüğünde, ayrıca çağrıldığı koda bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebf59-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="ebf59-106">Yordam çağrıldığında, kendi deyimleri çalıştırın, her bir saat sonra yürütülebilir ilk deyimi başlayarak `Function` deyimi ve ilk görmektesiniz `End Function`, `Exit Function`, veya `Return` deyimiyle karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="ebf59-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="ebf59-107">Tanımlayabileceğiniz bir `Function` yordamda bir modül, sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="ebf59-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="ebf59-108">Bu `Public` varsayılan olarak, yani çağırabilirsiniz, her yerden uygulamanızdaki modül, sınıf veya yapının, tanımlandığı da erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ebf59-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="ebf59-109">A `Function` yordamı, sabitleri, değişkenleri veya kendisine çağıran kod tarafından geçirilen ifadeler gibi bir bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="ebf59-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="ebf59-110">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebf59-110">Declaration Syntax</span></span>  
 <span data-ttu-id="ebf59-111">Bildirmek için söz dizimi bir `Function` yordam şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="ebf59-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="ebf59-112">*Değiştiriciler* erişim düzeyi ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve gölgeleme ilgili bilgileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebf59-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="ebf59-113">Daha fazla bilgi için [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ebf59-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="ebf59-114">Her parametre için yaptığınız gibi bildirdiğiniz [alt yordamlar](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ebf59-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="ebf59-115">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ebf59-115">Data Type</span></span>  
 <span data-ttu-id="ebf59-116">Her `Function` yordamı sahip bir veri türü, yalnızca olarak her değişken yok.</span><span class="sxs-lookup"><span data-stu-id="ebf59-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="ebf59-117">Bu veri türü tarafından belirtilen `As` yan tümcesinde `Function` ifadesi ve işlevin çağrıldığı koda döndürdüğü değer veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="ebf59-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="ebf59-118">Aşağıdaki örnek bildirimleri bu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ebf59-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="ebf59-119">Daha fazla bilgi için bkz: "Bölümleri" [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ebf59-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="ebf59-120">Değerler döndüren</span><span class="sxs-lookup"><span data-stu-id="ebf59-120">Returning Values</span></span>  
 <span data-ttu-id="ebf59-121">Değer bir `Function` yordamı gönderir çağıran koda geri dönüş değeri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ebf59-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="ebf59-122">Yordam bu değer iki yoldan birini döndürür:</span><span class="sxs-lookup"><span data-stu-id="ebf59-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="ebf59-123">Kullandığı `Return` deyimi döndürür ve dönüş değeri belirtmek için çağırma program hemen denetim.</span><span class="sxs-lookup"><span data-stu-id="ebf59-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="ebf59-124">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ebf59-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="ebf59-125">Bir veya daha fazla deyim yordamın, kendi işlev adı için bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="ebf59-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="ebf59-126">Denetim kadar çağıran program döndürmez bir `Exit Function` veya `End Function` deyimi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ebf59-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="ebf59-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ebf59-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="ebf59-128">Dönüş değeri, işlev adını atama bulduğu kadar denetim yordamdan döndürmeyen avantajlarındandır bir `Exit Function` veya `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ebf59-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="ebf59-129">Bu, bir ön değer atamak ve gerekirse daha sonra ayarlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebf59-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="ebf59-130">Değerler döndüren hakkında daha fazla bilgi için bkz. [Function deyimi](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ebf59-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="ebf59-131">Dizi döndüren hakkında daha fazla bilgi için bkz [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="ebf59-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="ebf59-132">Arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ebf59-132">Calling Syntax</span></span>  
 <span data-ttu-id="ebf59-133">Çağırdığınızda bir `Function` adı ve bağımsız değişkenler veya işlecin sağ tarafındaki Atama ifadesinin veya bir ifadede ekleyerek yordamı.</span><span class="sxs-lookup"><span data-stu-id="ebf59-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="ebf59-134">İsteğe bağlı olmayan tüm bağımsız değişkenler için değerler sağlaması gerekir ve bağımsız değişken listesi parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="ebf59-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="ebf59-135">Hiçbir bağımsız değişken sağlanmadıysa, parantezler isteğe bağlı olarak atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebf59-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="ebf59-136">Bir çağrı sözdizimi bir `Function` yordam şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="ebf59-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="ebf59-137">*lvalue*`=`*functionname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="ebf59-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="ebf59-138">`If ((` *FunctionName* `[(` *argumentlist* `)] / 3) <=` *ifadesi* `) Then`</span><span class="sxs-lookup"><span data-stu-id="ebf59-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="ebf59-139">Çağırdığınızda bir `Function` yordamı sahip olmadığınız dönüş değeri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="ebf59-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="ebf59-140">Bunu yapmazsanız, işlevin tüm eylemlerin gerçekleştirildiğinden, ancak dönüş değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="ebf59-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="ebf59-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> Genellikle bu şekilde adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ebf59-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="ebf59-142">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="ebf59-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="ebf59-143">Aşağıdaki `Function` yordamı, en uzun kenar veya, diğer iki yüz için değerlerine dik üçgenin, hipotenüsü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="ebf59-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="ebf59-144">Aşağıdaki örnek, tipik bir çağrı gösterir `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="ebf59-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ebf59-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebf59-145">See also</span></span>

- [<span data-ttu-id="ebf59-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ebf59-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ebf59-147">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ebf59-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="ebf59-148">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="ebf59-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ebf59-149">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="ebf59-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ebf59-150">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ebf59-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ebf59-151">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="ebf59-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ebf59-152">Nasıl yapılır: Bir değer döndüren bir yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebf59-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="ebf59-153">Nasıl yapılır: Bir yordamdan değer döndürme</span><span class="sxs-lookup"><span data-stu-id="ebf59-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="ebf59-154">Nasıl yapılır: Bir değer döndüren bir yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="ebf59-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
