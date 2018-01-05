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
ms.openlocfilehash: cb1790d363755fe9b8bd711409734f7c3a405f3e
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="f430c-102">İşlev İfadesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f430c-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="f430c-103">Parametreleri ve işlev lambda ifadesi tanımlamak kod bildirir.</span><span class="sxs-lookup"><span data-stu-id="f430c-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f430c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f430c-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="f430c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f430c-105">Parts</span></span>  
  
|<span data-ttu-id="f430c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="f430c-106">Term</span></span>|<span data-ttu-id="f430c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="f430c-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="f430c-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f430c-108">Optional.</span></span> <span data-ttu-id="f430c-109">Bu yordam parametreleri temsil eden yerel değişken adları listesi.</span><span class="sxs-lookup"><span data-stu-id="f430c-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="f430c-110">Parantez listesi boş olsa bile mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f430c-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="f430c-111">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="f430c-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="f430c-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f430c-112">Required.</span></span> <span data-ttu-id="f430c-113">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="f430c-113">A single expression.</span></span> <span data-ttu-id="f430c-114">İşlevinin dönüş türü ifade türüdür.</span><span class="sxs-lookup"><span data-stu-id="f430c-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="f430c-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f430c-115">Required.</span></span> <span data-ttu-id="f430c-116">Kullanarak bir değer döndürür deyimleri listesini `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f430c-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="f430c-117">(Bkz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).) İşlevinin dönüş türü döndürülen değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="f430c-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f430c-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f430c-118">Remarks</span></span>  
 <span data-ttu-id="f430c-119">A *lambda ifadesi* hesaplar ve bir değer döndüren bir ad olmadan bir işlev değil.</span><span class="sxs-lookup"><span data-stu-id="f430c-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="f430c-120">Lambda ifadesi kullanabileceğiniz her yerde bir temsilci türü dışında bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="f430c-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="f430c-121">Temsilciler ve temsilciler ile lambda ifadeleri kullanma hakkında daha fazla bilgi için bkz: [temsilci deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="f430c-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="f430c-122">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f430c-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="f430c-123">Lambda ifadesi sözdizimi, standart bir işlev benzer.</span><span class="sxs-lookup"><span data-stu-id="f430c-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="f430c-124">Farkları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f430c-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="f430c-125">Lambda ifadesi bir adı yok.</span><span class="sxs-lookup"><span data-stu-id="f430c-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="f430c-126">Lambda ifadeleri olamaz değiştiriciler, gibi `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="f430c-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="f430c-127">Lambda ifadeleri kullanma bir `As` işlevin dönüş türünü atamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f430c-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="f430c-128">Bunun yerine, türü tek satırlı lambda ifadesi gövdesi değerlendiren değeri veya çok satırlı lambda ifadesi dönüş değerini algılanır.</span><span class="sxs-lookup"><span data-stu-id="f430c-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="f430c-129">Örneğin, tek satırlı lambda ifadesi gövdesi ise `Where cust.City = "London"`, kendi dönüş türü `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f430c-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="f430c-130">Tek satırlı lambda ifadesi gövdesi bir ifade, bir deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f430c-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="f430c-131">Gövdesi bir işlev yordam çağrısı, ancak olmayan bir alt yordam çağrısı oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f430c-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="f430c-132">Veri türleri veya tüm olayla gerekir ya da tüm parametreleri belirledikten gerekir.</span><span class="sxs-lookup"><span data-stu-id="f430c-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="f430c-133">İsteğe bağlı ve Paramarray parametreleri izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="f430c-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="f430c-134">Genel Parametreler izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="f430c-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f430c-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="f430c-135">Example</span></span>  
 <span data-ttu-id="f430c-136">Aşağıdaki örnekler basit lambda ifadeleri oluşturmanın iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f430c-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="f430c-137">İlk kullandığı bir `Dim` işlevi için bir ad vermek için.</span><span class="sxs-lookup"><span data-stu-id="f430c-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="f430c-138">Bir işlevi çağırmak için parametre için bir değer gönderin.</span><span class="sxs-lookup"><span data-stu-id="f430c-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="f430c-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="f430c-139">Example</span></span>  
 <span data-ttu-id="f430c-140">Alternatif olarak, bildirme ve aynı anda işlevi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f430c-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="f430c-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="f430c-141">Example</span></span>  
 <span data-ttu-id="f430c-142">Aşağıdaki bağımsız değişkeni artırır ve değer döndüren bir lambda ifadesi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f430c-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="f430c-143">Aşağıdaki örnekte, hem tek satırlı ve çok satırlı lambda ifadesi sözdizimi işlevi için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f430c-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="f430c-144">Daha fazla örnek için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f430c-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="f430c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="f430c-145">Example</span></span>  
 <span data-ttu-id="f430c-146">Lambda ifadeleri sorgu işleçleri çoğunu temelini oluşturan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]ve yöntem temelli sorgular açıkça kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f430c-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="f430c-147">Aşağıdaki örnek gösterilmektedir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yöntemi biçimine sorgusunun çevirisi tarafından izlenen sorgu.</span><span class="sxs-lookup"><span data-stu-id="f430c-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="f430c-148">Sorgu yöntemleri hakkında daha fazla bilgi için bkz: [sorguları](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="f430c-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="f430c-149">Standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f430c-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f430c-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f430c-150">See Also</span></span>  
 [<span data-ttu-id="f430c-151">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f430c-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="f430c-152">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f430c-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="f430c-153">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="f430c-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="f430c-154">Deyimler</span><span class="sxs-lookup"><span data-stu-id="f430c-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="f430c-155">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="f430c-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="f430c-156">Boole İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f430c-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="f430c-157">If İşleci</span><span class="sxs-lookup"><span data-stu-id="f430c-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="f430c-158">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f430c-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
