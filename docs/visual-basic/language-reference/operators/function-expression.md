---
title: "İşlev İfadesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="363b5-102">İşlev İfadesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="363b5-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="363b5-103">Parametreleri ve işlev lambda ifadesi tanımlamak kod bildirir.</span><span class="sxs-lookup"><span data-stu-id="363b5-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="363b5-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="363b5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="363b5-105">Parts</span></span>  
  
|<span data-ttu-id="363b5-106">Terim</span><span class="sxs-lookup"><span data-stu-id="363b5-106">Term</span></span>|<span data-ttu-id="363b5-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="363b5-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="363b5-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="363b5-108">Optional.</span></span> <span data-ttu-id="363b5-109">Bu yordam parametreleri temsil eden yerel değişken adları listesi.</span><span class="sxs-lookup"><span data-stu-id="363b5-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="363b5-110">Parantez listesi boş olsa bile mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="363b5-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="363b5-111">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="363b5-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="363b5-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="363b5-112">Required.</span></span> <span data-ttu-id="363b5-113">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="363b5-113">A single expression.</span></span> <span data-ttu-id="363b5-114">İşlevinin dönüş türü ifade türüdür.</span><span class="sxs-lookup"><span data-stu-id="363b5-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="363b5-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="363b5-115">Required.</span></span> <span data-ttu-id="363b5-116">Kullanarak bir değer döndürür deyimleri listesini `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="363b5-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="363b5-117">(Bkz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).) İşlevinin dönüş türü döndürülen değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="363b5-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="363b5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="363b5-118">Remarks</span></span>  
 <span data-ttu-id="363b5-119">A *lambda ifadesi* hesaplar ve bir değer döndüren bir ad olmadan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="363b5-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="363b5-120">Lambda ifadesi kullanabileceğiniz her yerde bir temsilci türü dışında bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="363b5-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="363b5-121">Temsilciler ve temsilciler ile lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz: [temsilci deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="363b5-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="363b5-122">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="363b5-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="363b5-123">Lambda ifadesi sözdizimi, standart bir işlev benzer.</span><span class="sxs-lookup"><span data-stu-id="363b5-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="363b5-124">Farkları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="363b5-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="363b5-125">Lambda ifadesi bir adı yok.</span><span class="sxs-lookup"><span data-stu-id="363b5-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="363b5-126">Lambda ifadeleri olamaz değiştiriciler, gibi `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="363b5-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="363b5-127">Lambda ifadeleri kullanma bir `As` işlevin dönüş türünü atamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="363b5-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="363b5-128">Bunun yerine, türü tek satırlı lambda ifadesi gövdesi değerlendiren değeri veya çok satırlı lambda ifadesi dönüş değerini algılanır.</span><span class="sxs-lookup"><span data-stu-id="363b5-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="363b5-129">Örneğin, tek satırlı lambda ifadesi gövdesi ise `Where cust.City = "London"`, kendi dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="363b5-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="363b5-130">Tek satırlı lambda ifadesi gövdesi bir ifade, bir deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="363b5-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="363b5-131">Gövdesi bir işlev yordam çağrısı, ancak olmayan bir alt yordam çağrısı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="363b5-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="363b5-132">Veri türleri veya tüm olayla gerekir ya da tüm parametreleri belirledikten gerekir.</span><span class="sxs-lookup"><span data-stu-id="363b5-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="363b5-133">İsteğe bağlı ve Paramarray parametreleri izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="363b5-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="363b5-134">Genel Parametreler izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="363b5-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="363b5-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="363b5-135">Example</span></span>  
 <span data-ttu-id="363b5-136">Aşağıdaki örnekler basit lambda ifadeleri oluşturmanın iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="363b5-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="363b5-137">İlk kullandığı bir `Dim` işlevi için bir ad vermek için.</span><span class="sxs-lookup"><span data-stu-id="363b5-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="363b5-138">Bir işlevi çağırmak için parametre için bir değer gönderin.</span><span class="sxs-lookup"><span data-stu-id="363b5-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="363b5-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="363b5-139">Example</span></span>  
 <span data-ttu-id="363b5-140">Alternatif olarak, bildirme ve aynı anda işlevi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="363b5-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="363b5-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="363b5-141">Example</span></span>  
 <span data-ttu-id="363b5-142">Aşağıdaki bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="363b5-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="363b5-143">Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi işlevi için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="363b5-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="363b5-144">Daha fazla örnek için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="363b5-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="363b5-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="363b5-145">Example</span></span>  
 <span data-ttu-id="363b5-146">Lambda ifadeleri sorgu işleçleri çoğunu temelini oluşturan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]ve yöntem temelli sorgular açıkça kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="363b5-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="363b5-147">Aşağıdaki örnek gösterilmektedir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yöntemi biçimine sorgusunun çevirisi tarafından izlenen sorgu.</span><span class="sxs-lookup"><span data-stu-id="363b5-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="363b5-148">Sorgu yöntemleri hakkında daha fazla bilgi için bkz: [sorguları](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="363b5-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="363b5-149">Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="363b5-149">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363b5-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="363b5-150">See Also</span></span>  
 [<span data-ttu-id="363b5-151">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="363b5-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="363b5-152">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="363b5-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="363b5-153">İşleçler ve ifadeler</span><span class="sxs-lookup"><span data-stu-id="363b5-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="363b5-154">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="363b5-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="363b5-155">Değer karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="363b5-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="363b5-156">Boole ifadeleri</span><span class="sxs-lookup"><span data-stu-id="363b5-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="363b5-157">Varsa işleci</span><span class="sxs-lookup"><span data-stu-id="363b5-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="363b5-158">Gevşek temsilci dönüşümü</span><span class="sxs-lookup"><span data-stu-id="363b5-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
