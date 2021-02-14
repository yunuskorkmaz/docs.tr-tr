---
description: 'Daha fazla bilgi edinin: Işlev yordamları (Visual Basic)'
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
ms.openlocfilehash: 4997059fc33fb5d438519356b2c9fdd9e6a27cce
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436155"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="2da98-103">İşlev yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da98-103">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="2da98-104">`Function`Yordam, ve deyimleri içine alınmış Visual Basic deyimlerinin bir dizisidir `Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="2da98-104">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="2da98-105">`Function`Yordam bir görevi gerçekleştirir ve ardından çağıran koda denetim döndürür.</span><span class="sxs-lookup"><span data-stu-id="2da98-105">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="2da98-106">Denetimi döndürdüğünde, çağıran koda de bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="2da98-106">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="2da98-107">Yordamın her çağrılışında deyimleri, deyiminden sonra ilk yürütülebilir deyimden başlayarak `Function` ve ilk `End Function` , `Exit Function` , veya ifadesiyle sona ermek üzere çalışır `Return` .</span><span class="sxs-lookup"><span data-stu-id="2da98-107">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="2da98-108">`Function`Modül, sınıf veya yapıda bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2da98-108">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="2da98-109">Bu, `Public` Varsayılan olarak sizin tanımladığınız modüle, sınıfa veya yapıya erişimi olan uygulamanızdaki herhangi bir yerden çağırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2da98-109">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="2da98-110">`Function`Yordam, çağıran kod tarafından buna geçirilen sabitler, değişkenler veya ifadeler gibi bağımsız değişkenler alabilir.</span><span class="sxs-lookup"><span data-stu-id="2da98-110">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="2da98-111">Bildirim söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2da98-111">Declaration syntax</span></span>

<span data-ttu-id="2da98-112">Bir yordamı bildirmek için sözdizimi `Function` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2da98-112">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="2da98-113">*Değiştiriciler* , aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="2da98-113">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="2da98-114">Daha fazla bilgi için bkz. [Işlev açıklaması](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2da98-114">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="2da98-115">Her parametreyi [alt yordamlar](./sub-procedures.md)için yaptığınız gibi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2da98-115">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="2da98-116">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2da98-116">Data type</span></span>

<span data-ttu-id="2da98-117">Her `Function` yordamın, her değişken için olduğu gibi bir veri türü vardır.</span><span class="sxs-lookup"><span data-stu-id="2da98-117">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="2da98-118">Bu veri türü, `As` deyimindeki yan tümce tarafından belirtilir `Function` ve işlevin çağıran koda döndürdüğü değerin veri türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="2da98-118">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="2da98-119">Aşağıdaki örnek bildirimlerde bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2da98-119">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="2da98-120">Daha fazla bilgi için bkz. [Işlev deyimindeki](../../../language-reference/statements/function-statement.md)"parçalar".</span><span class="sxs-lookup"><span data-stu-id="2da98-120">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="2da98-121">Değer döndürme</span><span class="sxs-lookup"><span data-stu-id="2da98-121">Returning values</span></span>

<span data-ttu-id="2da98-122">`Function`Çağıran koda geri gönderen bir yordamın değeri, dönüş değeri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2da98-122">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="2da98-123">Yordam bu değeri iki şekilde döndürür:</span><span class="sxs-lookup"><span data-stu-id="2da98-123">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="2da98-124">`Return`Dönüş değerini belirtmek için ifadesini kullanır ve denetimi çağıran programa hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="2da98-124">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="2da98-125">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2da98-125">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="2da98-126">Yordamın bir veya daha fazla deyiminde kendi işlev adına bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="2da98-126">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="2da98-127">Denetim, bir `Exit Function` veya deyimleri yürütülene kadar çağıran programa geri dönmez `End Function` .</span><span class="sxs-lookup"><span data-stu-id="2da98-127">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="2da98-128">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2da98-128">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="2da98-129">İşlev adına dönüş değeri atamanın avantajı, denetimin bir veya ifadesiyle karşılaşana kadar yordamdan dönmediği avantajdır `Exit Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="2da98-129">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="2da98-130">Bu, bir ön değer atamanıza ve gerekirse daha sonra ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2da98-130">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="2da98-131">Değer döndürme hakkında daha fazla bilgi için bkz. [Function deyimleri](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2da98-131">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="2da98-132">Dizileri döndürme hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="2da98-132">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="2da98-133">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2da98-133">Calling syntax</span></span>

<span data-ttu-id="2da98-134">Bir `Function` yordamı, adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına ya da bir ifadeye ekleyerek çağırılır.</span><span class="sxs-lookup"><span data-stu-id="2da98-134">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="2da98-135">İsteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız gerekir ve bağımsız değişken listesini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="2da98-135">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="2da98-136">Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2da98-136">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="2da98-137">Bir yordama yapılan çağrının sözdizimi aşağıdaki gibidir `Function` .</span><span class="sxs-lookup"><span data-stu-id="2da98-137">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="2da98-138">*lvalue* `=` *fonksiyonadı* `[(` *bağımsız değişkenler listesi*    `)]`</span><span class="sxs-lookup"><span data-stu-id="2da98-138">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="2da98-139">`If ((`*fonksiyonadı* `[(` *bağımsız değişkenler listesi* `)] / 3) <=` *ifade*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="2da98-139">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="2da98-140">Bir `Function` yordamı çağırdığınızda, dönüş değerini kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="2da98-140">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="2da98-141">Bunu yapmazsanız, işlevin tüm eylemleri gerçekleştirilir, ancak dönüş değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2da98-141">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="2da98-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> genellikle bu şekilde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="2da98-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="2da98-143">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="2da98-143">Illustration of declaration and call</span></span>

<span data-ttu-id="2da98-144">Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2da98-144">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="2da98-145">Aşağıdaki örnekte, için tipik bir çağrı gösterilmektedir `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="2da98-145">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="2da98-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2da98-146">See also</span></span>

- [<span data-ttu-id="2da98-147">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2da98-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2da98-148">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2da98-148">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="2da98-149">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="2da98-149">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2da98-150">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="2da98-150">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2da98-151">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="2da98-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2da98-152">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2da98-152">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="2da98-153">Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2da98-153">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="2da98-154">Nasıl yapılır: Bir Yordamdan Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="2da98-154">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="2da98-155">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="2da98-155">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
