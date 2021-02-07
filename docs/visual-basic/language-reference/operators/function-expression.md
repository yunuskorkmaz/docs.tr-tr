---
description: 'Hakkında daha fazla bilgi edinin: Işlev Ifadesi (Visual Basic)'
title: Function İfadesi
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: bef5db7f167b615c2a0c20539521c186683da985
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666023"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="83804-103">İşlev İfadesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83804-103">Function Expression (Visual Basic)</span></span>

<span data-ttu-id="83804-104">Bir işlev lambda ifadesi tanımlayan parametreleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="83804-104">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83804-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="83804-105">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="83804-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="83804-106">Parts</span></span>  
  
|<span data-ttu-id="83804-107">Süre</span><span class="sxs-lookup"><span data-stu-id="83804-107">Term</span></span>|<span data-ttu-id="83804-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="83804-108">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="83804-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="83804-109">Optional.</span></span> <span data-ttu-id="83804-110">Bu yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi.</span><span class="sxs-lookup"><span data-stu-id="83804-110">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="83804-111">Liste boş olduğunda bile parantezler mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83804-111">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="83804-112">Bkz. [parametre listesi](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="83804-112">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="83804-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="83804-113">Required.</span></span> <span data-ttu-id="83804-114">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="83804-114">A single expression.</span></span> <span data-ttu-id="83804-115">İfadenin türü, işlevin dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="83804-115">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="83804-116">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="83804-116">Required.</span></span> <span data-ttu-id="83804-117">Deyimini kullanarak bir değer döndüren deyimlerin listesi `Return` .</span><span class="sxs-lookup"><span data-stu-id="83804-117">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="83804-118">( [Return ifadesine](../statements/return-statement.md)bakın.) Döndürülen değerin türü, işlevin dönüş türüdür.</span><span class="sxs-lookup"><span data-stu-id="83804-118">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83804-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83804-119">Remarks</span></span>  

 <span data-ttu-id="83804-120">*Lambda ifadesi* , bir değeri hesaplayan ve döndüren bir ad olmayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="83804-120">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="83804-121">Bir lambda ifadesini, için bağımsız değişken dışında bir temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="83804-121">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="83804-122">Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="83804-122">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="83804-123">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83804-123">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="83804-124">Bir lambda ifadesinin sözdizimi, standart bir işleve benzer.</span><span class="sxs-lookup"><span data-stu-id="83804-124">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="83804-125">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83804-125">The differences are as follows:</span></span>  
  
- <span data-ttu-id="83804-126">Lambda ifadesinin adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="83804-126">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="83804-127">Lambda ifadelerinin veya gibi değiştiriciler olamaz `Overloads` `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="83804-127">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="83804-128">Lambda ifadeleri `As` , işlevin dönüş türünü belirlemek için bir yan tümce kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="83804-128">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="83804-129">Bunun yerine, tür, tek satırlık lambda ifadesinin gövdesinin değerlendirilen değerden veya çok satırlı lambda ifadesinin dönüş değerine göre algılanır.</span><span class="sxs-lookup"><span data-stu-id="83804-129">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="83804-130">Örneğin, tek satırlık bir lambda ifadesinin gövdesi ise, `Where cust.City = "London"` dönüş türü olur `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="83804-130">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="83804-131">Tek satırlık lambda ifadesinin gövdesi deyim değil bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83804-131">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="83804-132">Gövde, bir işlev yordamının bir çağrısından oluşabilir, ancak Sub yordamına çağrı olamaz.</span><span class="sxs-lookup"><span data-stu-id="83804-132">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="83804-133">Tüm parametrelerin belirtilmiş veri türleri olmalıdır veya hepsi çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83804-133">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="83804-134">İsteğe bağlı ve ParamArray parametrelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="83804-134">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="83804-135">Genel parametrelere izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="83804-135">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83804-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="83804-136">Example</span></span>  

 <span data-ttu-id="83804-137">Aşağıdaki örneklerde basit lambda ifadeleri oluşturmanın iki yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83804-137">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="83804-138">İlki, `Dim` işlev için bir ad sağlamak üzere bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="83804-138">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="83804-139">İşlevini çağırmak için, parametresi için bir değer gönderin.</span><span class="sxs-lookup"><span data-stu-id="83804-139">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="83804-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="83804-140">Example</span></span>  

 <span data-ttu-id="83804-141">Alternatif olarak, işlevini aynı anda bildirebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83804-141">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="83804-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="83804-142">Example</span></span>  

 <span data-ttu-id="83804-143">Aşağıda, bağımsız değişkenini artıran ve değeri döndüren bir lambda ifadesinin örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="83804-143">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="83804-144">Örnek, bir işlev için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="83804-144">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="83804-145">Daha fazla örnek için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="83804-145">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="83804-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="83804-146">Example</span></span>  

 <span data-ttu-id="83804-147">Lambda ifadeleri Language-Integrated sorgusunda (LINQ) sorgu işleçlerinin birçoğunu alt olarak kullanır ve Yöntem tabanlı sorgularda açıkça kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83804-147">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="83804-148">Aşağıdaki örnek tipik bir LINQ sorgusunu ve ardından sorgunun yöntem biçimine çevirisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="83804-148">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="83804-149">Sorgu yöntemleri hakkında daha fazla bilgi için bkz. [sorgular](../queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="83804-149">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="83804-150">Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83804-150">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83804-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83804-151">See also</span></span>

- [<span data-ttu-id="83804-152">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="83804-152">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="83804-153">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="83804-153">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="83804-154">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="83804-154">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="83804-155">Deyimler</span><span class="sxs-lookup"><span data-stu-id="83804-155">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="83804-156">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="83804-156">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="83804-157">Boole Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="83804-157">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="83804-158">If İşleci</span><span class="sxs-lookup"><span data-stu-id="83804-158">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="83804-159">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="83804-159">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
