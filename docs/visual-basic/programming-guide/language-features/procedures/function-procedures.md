---
title: İşlev yordamları
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388757"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="bf98d-102">İşlev yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf98d-102">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="bf98d-103">`Function`Yordam, ve deyimleri içine alınmış Visual Basic deyimlerinin bir dizisidir `Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="bf98d-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="bf98d-104">`Function`Yordam bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf98d-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="bf98d-105">Denetimi döndürdüğünde, çağıran koda de bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf98d-105">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="bf98d-106">Yordamın her çağrılışında deyimleri, deyiminden sonra ilk yürütülebilir deyimden başlayarak `Function` ve ilk `End Function` , `Exit Function` , veya ifadesiyle sona ermek üzere çalışır `Return` .</span><span class="sxs-lookup"><span data-stu-id="bf98d-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="bf98d-107">`Function`Modül, sınıf veya yapıda bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf98d-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="bf98d-108">Bu, `Public` Varsayılan olarak sizin tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bf98d-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="bf98d-109">`Function`Yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.</span><span class="sxs-lookup"><span data-stu-id="bf98d-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="bf98d-110">Bildirim söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bf98d-110">Declaration syntax</span></span>

<span data-ttu-id="bf98d-111">Bir yordamı bildirmek için sözdizimi `Function` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf98d-111">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="bf98d-112">*Değiştiriciler* , aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="bf98d-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="bf98d-113">Daha fazla bilgi için bkz. [Işlev açıklaması](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bf98d-113">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="bf98d-114">Her parametreyi [alt yordamlar](./sub-procedures.md)için yaptığınız gibi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf98d-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="bf98d-115">Veri türü</span><span class="sxs-lookup"><span data-stu-id="bf98d-115">Data type</span></span>

<span data-ttu-id="bf98d-116">Her `Function` yordamın, her değişken için olduğu gibi bir veri türü vardır.</span><span class="sxs-lookup"><span data-stu-id="bf98d-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="bf98d-117">Bu veri türü, `As` deyimindeki yan tümce tarafından belirtilir `Function` ve işlevin çağıran koda döndürdüğü değerin veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="bf98d-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="bf98d-118">Aşağıdaki örnek bildirimlerde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf98d-118">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="bf98d-119">Daha fazla bilgi için bkz. [Işlev deyimindeki](../../../language-reference/statements/function-statement.md)"parçalar".</span><span class="sxs-lookup"><span data-stu-id="bf98d-119">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="bf98d-120">Değer döndürme</span><span class="sxs-lookup"><span data-stu-id="bf98d-120">Returning values</span></span>

<span data-ttu-id="bf98d-121">`Function`Çağıran koda geri gönderen bir yordamın değeri, dönüş değeri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bf98d-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="bf98d-122">Yordam bu değeri iki şekilde döndürür:</span><span class="sxs-lookup"><span data-stu-id="bf98d-122">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="bf98d-123">`Return`Dönüş değerini belirtmek için ifadesini kullanır ve denetimi çağıran programa hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf98d-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="bf98d-124">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bf98d-124">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="bf98d-125">Yordamın bir veya daha fazla deyiminde kendi işlev adına bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="bf98d-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="bf98d-126">Denetim, bir `Exit Function` veya deyimleri yürütülene kadar çağıran programa geri dönmez `End Function` .</span><span class="sxs-lookup"><span data-stu-id="bf98d-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="bf98d-127">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bf98d-127">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="bf98d-128">İşlev adına dönüş değeri atamanın avantajı, denetimin bir veya ifadesiyle karşılaşana kadar yordamdan dönmediği avantajdır `Exit Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="bf98d-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="bf98d-129">Bu, bir ön değer atamanıza ve gerekirse daha sonra ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf98d-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="bf98d-130">Değer döndürme hakkında daha fazla bilgi için bkz. [Function deyimleri](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bf98d-130">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="bf98d-131">Dizileri döndürme hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf98d-131">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="bf98d-132">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf98d-132">Calling syntax</span></span>

<span data-ttu-id="bf98d-133">Bir `Function` yordamı, adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına ya da bir ifadeye ekleyerek çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bf98d-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="bf98d-134">İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="bf98d-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="bf98d-135">Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf98d-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="bf98d-136">Bir yordama yapılan çağrının sözdizimi aşağıdaki gibidir `Function` .</span><span class="sxs-lookup"><span data-stu-id="bf98d-136">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="bf98d-137">*lvalue* `=` *fonksiyonadı* `[(` *bağımsız değişkenler listesi*    `)]`</span><span class="sxs-lookup"><span data-stu-id="bf98d-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="bf98d-138">`If ((`*fonksiyonadı* `[(` *bağımsız değişkenler listesi* `)] / 3) <=` *ifade*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="bf98d-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="bf98d-139">Bir `Function` yordamı çağırdığınızda, dönüş değerini kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf98d-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="bf98d-140">Bunu yapmazsanız, işlevin tüm eylemleri gerçekleştirilir, ancak dönüş değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="bf98d-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="bf98d-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>genellikle bu şekilde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bf98d-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="bf98d-142">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="bf98d-142">Illustration of declaration and call</span></span>

<span data-ttu-id="bf98d-143">Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="bf98d-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="bf98d-144">Aşağıdaki örnekte, için tipik bir çağrı gösterilmektedir `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="bf98d-144">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="bf98d-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf98d-145">See also</span></span>

- [<span data-ttu-id="bf98d-146">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="bf98d-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bf98d-147">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="bf98d-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="bf98d-148">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="bf98d-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="bf98d-149">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="bf98d-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="bf98d-150">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bf98d-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bf98d-151">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf98d-151">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="bf98d-152">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf98d-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="bf98d-153">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="bf98d-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="bf98d-154">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="bf98d-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
