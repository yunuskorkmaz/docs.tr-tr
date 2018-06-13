---
title: İşlev İfadesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 29bf95a336b6f6ed5c9c310c9ea7575a91089361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604893"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="c1eb7-102">İşlev İfadesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1eb7-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="c1eb7-103">Parametreleri ve işlev lambda ifadesi tanımlamak kod bildirir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1eb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1eb7-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="c1eb7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c1eb7-105">Parts</span></span>  
  
|<span data-ttu-id="c1eb7-106">Terim</span><span class="sxs-lookup"><span data-stu-id="c1eb7-106">Term</span></span>|<span data-ttu-id="c1eb7-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c1eb7-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="c1eb7-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-108">Optional.</span></span> <span data-ttu-id="c1eb7-109">Bu yordam parametreleri temsil eden yerel değişken adları listesi.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="c1eb7-110">Parantez listesi boş olsa bile mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="c1eb7-111">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="c1eb7-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="c1eb7-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-112">Required.</span></span> <span data-ttu-id="c1eb7-113">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-113">A single expression.</span></span> <span data-ttu-id="c1eb7-114">İşlevinin dönüş türü ifade türüdür.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="c1eb7-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-115">Required.</span></span> <span data-ttu-id="c1eb7-116">Kullanarak bir değer döndürür deyimleri listesini `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="c1eb7-117">(Bkz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).) İşlevinin dönüş türü döndürülen değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1eb7-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1eb7-118">Remarks</span></span>  
 <span data-ttu-id="c1eb7-119">A *lambda ifadesi* hesaplar ve bir değer döndüren bir ad olmadan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="c1eb7-120">Lambda ifadesi kullanabileceğiniz her yerde bir temsilci türü dışında bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="c1eb7-121">Temsilciler ve temsilciler ile lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz: [temsilci deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="c1eb7-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="c1eb7-122">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1eb7-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="c1eb7-123">Lambda ifadesi sözdizimi, standart bir işlev benzer.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="c1eb7-124">Farkları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c1eb7-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="c1eb7-125">Lambda ifadesi bir adı yok.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="c1eb7-126">Lambda ifadeleri olamaz değiştiriciler, gibi `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="c1eb7-127">Lambda ifadeleri kullanma bir `As` işlevin dönüş türünü atamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="c1eb7-128">Bunun yerine, türü tek satırlı lambda ifadesi gövdesi değerlendiren değeri veya çok satırlı lambda ifadesi dönüş değerini algılanır.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="c1eb7-129">Örneğin, tek satırlı lambda ifadesi gövdesi ise `Where cust.City = "London"`, kendi dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="c1eb7-130">Tek satırlı lambda ifadesi gövdesi bir ifade, bir deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="c1eb7-131">Gövdesi bir işlev yordam çağrısı, ancak olmayan bir alt yordam çağrısı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="c1eb7-132">Veri türleri veya tüm olayla gerekir ya da tüm parametreleri belirledikten gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="c1eb7-133">İsteğe bağlı ve Paramarray parametreleri izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="c1eb7-134">Genel Parametreler izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1eb7-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1eb7-135">Example</span></span>  
 <span data-ttu-id="c1eb7-136">Aşağıdaki örnekler basit lambda ifadeleri oluşturmanın iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="c1eb7-137">İlk kullandığı bir `Dim` işlevi için bir ad vermek için.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="c1eb7-138">Bir işlevi çağırmak için parametre için bir değer gönderin.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c1eb7-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1eb7-139">Example</span></span>  
 <span data-ttu-id="c1eb7-140">Alternatif olarak, bildirme ve aynı anda işlevi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="c1eb7-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1eb7-141">Example</span></span>  
 <span data-ttu-id="c1eb7-142">Aşağıdaki bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="c1eb7-143">Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi işlevi için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="c1eb7-144">Daha fazla örnek için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c1eb7-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="c1eb7-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1eb7-145">Example</span></span>  
 <span data-ttu-id="c1eb7-146">Lambda ifadeleri sorgu işleçleri çoğunu temelini oluşturan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]ve yöntem temelli sorgular açıkça kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="c1eb7-147">Aşağıdaki örnek gösterilmektedir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yöntemi biçimine sorgusunun çevirisi tarafından izlenen sorgu.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="c1eb7-148">Sorgu yöntemleri hakkında daha fazla bilgi için bkz: [sorguları](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="c1eb7-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="c1eb7-149">Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c1eb7-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1eb7-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1eb7-150">See Also</span></span>  
 [<span data-ttu-id="c1eb7-151">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="c1eb7-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="c1eb7-152">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c1eb7-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="c1eb7-153">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="c1eb7-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="c1eb7-154">Deyimler</span><span class="sxs-lookup"><span data-stu-id="c1eb7-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="c1eb7-155">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="c1eb7-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="c1eb7-156">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c1eb7-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="c1eb7-157">If İşleci</span><span class="sxs-lookup"><span data-stu-id="c1eb7-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="c1eb7-158">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c1eb7-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
