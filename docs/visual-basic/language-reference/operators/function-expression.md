---
title: İşlev İfadesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703004"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="8304f-102">İşlev İfadesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8304f-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="8304f-103">Parametreleri işlevi lambda ifadesi tanımlayan ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8304f-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8304f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8304f-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="8304f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8304f-105">Parts</span></span>  
  
|<span data-ttu-id="8304f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="8304f-106">Term</span></span>|<span data-ttu-id="8304f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="8304f-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="8304f-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8304f-108">Optional.</span></span> <span data-ttu-id="8304f-109">Bu yordamı parametrelerini temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="8304f-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="8304f-110">Liste boş olduğunda bile parantezler bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8304f-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="8304f-111">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="8304f-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="8304f-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8304f-112">Required.</span></span> <span data-ttu-id="8304f-113">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="8304f-113">A single expression.</span></span> <span data-ttu-id="8304f-114">İşlevin dönüş türü ifade türüdür.</span><span class="sxs-lookup"><span data-stu-id="8304f-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="8304f-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="8304f-115">Required.</span></span> <span data-ttu-id="8304f-116">Kullanarak bir değer döndüren deyimlerin listesini `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8304f-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="8304f-117">(Bkz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).) İşlevin dönüş türünü döndürülen değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="8304f-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8304f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8304f-118">Remarks</span></span>  
 <span data-ttu-id="8304f-119">A *lambda ifadesi* hesaplar ve bir değer döndüren bir adı olmayan bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="8304f-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="8304f-120">Bir lambda ifadesi kullandığınız her yerde bir temsilci türü dışında bir bağımsız değişken olarak kullanabilirsiniz `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="8304f-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="8304f-121">Temsilciler ve lambda ifadeleri temsilciler ile kullanımı hakkında daha fazla bilgi için bkz. [temsilci bildirimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="8304f-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="8304f-122">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8304f-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="8304f-123">Bir lambda ifadesi söz dizimi, standart bir işlev benzer.</span><span class="sxs-lookup"><span data-stu-id="8304f-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="8304f-124">Farklar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8304f-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="8304f-125">Bir lambda ifadesi, bir adı yok.</span><span class="sxs-lookup"><span data-stu-id="8304f-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="8304f-126">Lambda ifadeleri içeremez değiştiriciler, gibi `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8304f-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="8304f-127">Lambda ifadeleri kullanma bir `As` işlevin dönüş türünü belirlemek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="8304f-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="8304f-128">Bunun yerine, tek satırlı lambda ifadesinin gövdesinin değerlendiren değer veya çok satırlı lambda ifadesinin dönüş değeri türüne algılanır.</span><span class="sxs-lookup"><span data-stu-id="8304f-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="8304f-129">Örneğin, tek satırlı lambda ifadesinin gövdesinin ise `Where cust.City = "London"`, kendi dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8304f-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="8304f-130">Tek satırlı lambda ifadesinin gövdesinin deyim olmayan bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8304f-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="8304f-131">Gövdesi bir işlev yordam çağrısı, ancak bir alt yordam çağrısı değil oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8304f-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="8304f-132">Tüm parametre ya da veri türleri veya tüm anlaşılmalıdır belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8304f-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="8304f-133">İsteğe bağlı ve Paramarray parametrelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8304f-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="8304f-134">Genel Parametreler izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8304f-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8304f-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="8304f-135">Example</span></span>  
 <span data-ttu-id="8304f-136">Aşağıdaki örnekler, basit bir lambda ifadeleri oluşturmanın iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8304f-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="8304f-137">İlk kullandığı bir `Dim` işlevi için bir ad sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="8304f-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="8304f-138">İşlev çağrısı için parametre için bir değer gönderin.</span><span class="sxs-lookup"><span data-stu-id="8304f-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="8304f-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="8304f-139">Example</span></span>  
 <span data-ttu-id="8304f-140">Alternatif olarak, bildirebilir ve aynı anda işlevi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8304f-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="8304f-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="8304f-141">Example</span></span>  
 <span data-ttu-id="8304f-142">Bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8304f-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="8304f-143">Bu örnek, hem tek satır ve çok satırlı lambda ifadesi söz dizimi işlevi için gösterir.</span><span class="sxs-lookup"><span data-stu-id="8304f-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="8304f-144">Daha fazla örnek için bkz. [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8304f-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="8304f-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="8304f-145">Example</span></span>  
 <span data-ttu-id="8304f-146">Lambda ifadeleri sorgu işleçlerinin çoğu temelini oluşturan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]ve metot tabanlı sorgu açıkça kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8304f-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="8304f-147">Aşağıdaki örnekte gösterilmektedir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yöntemi biçime sorgu çevirisi tarafından izlenen sorgu.</span><span class="sxs-lookup"><span data-stu-id="8304f-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="8304f-148">Sorgu yöntemleri hakkında daha fazla bilgi için bkz. [sorguları](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="8304f-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="8304f-149">Standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8304f-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8304f-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8304f-150">See Also</span></span>  
 [<span data-ttu-id="8304f-151">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="8304f-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="8304f-152">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="8304f-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="8304f-153">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="8304f-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="8304f-154">Deyimler</span><span class="sxs-lookup"><span data-stu-id="8304f-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="8304f-155">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="8304f-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="8304f-156">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="8304f-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="8304f-157">If İşleci</span><span class="sxs-lookup"><span data-stu-id="8304f-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="8304f-158">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8304f-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
