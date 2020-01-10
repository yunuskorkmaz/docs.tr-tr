---
title: Function İfadesi
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 454c4e3d926640934a8edc4fcb16e4308a89dd50
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632343"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="58dc2-102">İşlev İfadesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dc2-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="58dc2-103">Bir işlev lambda ifadesi tanımlayan parametreleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58dc2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58dc2-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="58dc2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="58dc2-105">Parts</span></span>  
  
|<span data-ttu-id="58dc2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="58dc2-106">Term</span></span>|<span data-ttu-id="58dc2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="58dc2-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="58dc2-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="58dc2-108">Optional.</span></span> <span data-ttu-id="58dc2-109">Bu yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi.</span><span class="sxs-lookup"><span data-stu-id="58dc2-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="58dc2-110">Liste boş olduğunda bile parantezler mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58dc2-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="58dc2-111">Bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="58dc2-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="58dc2-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="58dc2-112">Required.</span></span> <span data-ttu-id="58dc2-113">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="58dc2-113">A single expression.</span></span> <span data-ttu-id="58dc2-114">İfadenin türü, işlevin dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="58dc2-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="58dc2-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="58dc2-115">Required.</span></span> <span data-ttu-id="58dc2-116">`Return` deyimini kullanarak bir değer döndüren deyimlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="58dc2-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="58dc2-117">( [Return ifadesine](../../../visual-basic/language-reference/statements/return-statement.md)bakın.) Döndürülen değerin türü, işlevin dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="58dc2-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58dc2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58dc2-118">Remarks</span></span>  
 <span data-ttu-id="58dc2-119">*Lambda ifadesi* , bir değeri hesaplayan ve döndüren bir ad olmayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="58dc2-120">Bir lambda ifadesini, `RemoveHandler`bir bağımsız değişken hariç, temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58dc2-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="58dc2-121">Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="58dc2-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="58dc2-122">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58dc2-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="58dc2-123">Bir lambda ifadesinin sözdizimi, standart bir işleve benzer.</span><span class="sxs-lookup"><span data-stu-id="58dc2-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="58dc2-124">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="58dc2-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="58dc2-125">Lambda ifadesinin adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="58dc2-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="58dc2-126">Lambda ifadelerinde `Overloads` veya `Overrides`gibi değiştiriciler olamaz.</span><span class="sxs-lookup"><span data-stu-id="58dc2-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="58dc2-127">Lambda ifadeleri, işlevin dönüş türünü belirlemek için bir `As` yan tümcesi kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="58dc2-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="58dc2-128">Bunun yerine, tür, tek satırlık lambda ifadesinin gövdesinin değerlendirilen değerden veya çok satırlı lambda ifadesinin dönüş değerine göre algılanır.</span><span class="sxs-lookup"><span data-stu-id="58dc2-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="58dc2-129">Örneğin, tek satırlık bir lambda ifadesinin gövdesi `Where cust.City = "London"`, dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="58dc2-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="58dc2-130">Tek satırlık lambda ifadesinin gövdesi deyim değil bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58dc2-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="58dc2-131">Gövde, bir işlev yordamının bir çağrısından oluşabilir, ancak Sub yordamına çağrı olamaz.</span><span class="sxs-lookup"><span data-stu-id="58dc2-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="58dc2-132">Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58dc2-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="58dc2-133">İsteğe bağlı ve ParamArray parametrelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="58dc2-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="58dc2-134">Genel parametrelere izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="58dc2-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58dc2-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="58dc2-135">Example</span></span>  
 <span data-ttu-id="58dc2-136">Aşağıdaki örneklerde basit lambda ifadeleri oluşturmanın iki yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="58dc2-137">İlki, işlev için bir ad sağlamak üzere bir `Dim` kullanır.</span><span class="sxs-lookup"><span data-stu-id="58dc2-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="58dc2-138">İşlevini çağırmak için, parametresi için bir değer gönderin.</span><span class="sxs-lookup"><span data-stu-id="58dc2-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="58dc2-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="58dc2-139">Example</span></span>  
 <span data-ttu-id="58dc2-140">Alternatif olarak, işlevini aynı anda bildirebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58dc2-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="58dc2-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="58dc2-141">Example</span></span>  
 <span data-ttu-id="58dc2-142">Aşağıda, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesinin örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="58dc2-143">Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="58dc2-144">Daha fazla örnek için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="58dc2-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="58dc2-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="58dc2-145">Example</span></span>  
 <span data-ttu-id="58dc2-146">Lambda ifadeleri, dil ile tümleşik sorgu (LINQ) içinde sorgu işleçlerinin birçoğunu daha fazla kullanır ve Yöntem tabanlı sorgularda açık bir şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-146">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="58dc2-147">Aşağıdaki örnek tipik bir LINQ sorgusunu ve ardından sorgunun yöntem biçimine çevirisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58dc2-147">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="58dc2-148">Sorgu yöntemleri hakkında daha fazla bilgi için bkz. [sorgular](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="58dc2-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="58dc2-149">Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="58dc2-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dc2-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58dc2-150">See also</span></span>

- [<span data-ttu-id="58dc2-151">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="58dc2-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="58dc2-152">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="58dc2-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="58dc2-153">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="58dc2-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="58dc2-154">Deyimler</span><span class="sxs-lookup"><span data-stu-id="58dc2-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="58dc2-155">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="58dc2-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="58dc2-156">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="58dc2-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="58dc2-157">If İşleci</span><span class="sxs-lookup"><span data-stu-id="58dc2-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="58dc2-158">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="58dc2-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
