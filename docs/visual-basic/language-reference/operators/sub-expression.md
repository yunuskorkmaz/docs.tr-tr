---
title: Alt İfade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d27ca262aa2349d34d78844e0aea0f96a1ced65c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496315"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="6ffc7-102">Alt İfade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ffc7-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="6ffc7-103">Parametreleri ve kodu tanımlayan bir alt yordam lambda ifadesi bildirir.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ffc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ffc7-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="6ffc7-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6ffc7-105">Parts</span></span>  
  
|<span data-ttu-id="6ffc7-106">Terim</span><span class="sxs-lookup"><span data-stu-id="6ffc7-106">Term</span></span>|<span data-ttu-id="6ffc7-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="6ffc7-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="6ffc7-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-108">Optional.</span></span> <span data-ttu-id="6ffc7-109">Yordam parametreleri temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="6ffc7-110">Liste boş olduğunda bile parantezler bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="6ffc7-111">Daha fazla bilgi için [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="6ffc7-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="6ffc7-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-112">Required.</span></span> <span data-ttu-id="6ffc7-113">Tek bir deyim.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="6ffc7-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-114">Required.</span></span> <span data-ttu-id="6ffc7-115">Deyimleri listesi.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ffc7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ffc7-116">Remarks</span></span>  
 <span data-ttu-id="6ffc7-117">A *lambda ifadesi* bir ada sahip bir alt yordam olduğunu ve, bir veya daha fazla deyimi yürütür.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="6ffc7-118">Bir lambda ifadesi her yerde kullanabilirsiniz, bir temsilci türü dışında bir bağımsız değişken olarak kullanabileceğiniz `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="6ffc7-119">Temsilciler ve lambda ifadeleri temsilciler ile kullanımı hakkında daha fazla bilgi için bkz. [temsilci bildirimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="6ffc7-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="6ffc7-120">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ffc7-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="6ffc7-121">Bir lambda ifadesi söz dizimi, standart bir alt yordam benzer.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="6ffc7-122">Farklar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6ffc7-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="6ffc7-123">Bir lambda ifadesi, bir adı yok.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="6ffc7-124">Bir lambda ifadesi bir değiştirici gibi olamaz `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="6ffc7-125">Tek satırlı lambda ifadesinin gövdesi bir deyim, bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="6ffc7-126">Gövde, bir alt yordam çağrısı, ancak bir işlev yordam çağrısı değil, oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="6ffc7-127">Bir lambda ifadesinde veri türleri veya tüm parametreleri anlaşılmalıdır tüm parametre ya da belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="6ffc7-128">İsteğe bağlı ve `ParamArray` parametreleri lambda ifadelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="6ffc7-129">Genel Parametreler lambda ifadelerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ffc7-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ffc7-130">Example</span></span>  
 <span data-ttu-id="6ffc7-131">Bir değer konsola yazar bir lambda ifadesi örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="6ffc7-132">Bu örnek, hem tek satır ve çok satırlı lambda ifadesi sözdizimi bir alt yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="6ffc7-133">Daha fazla örnek için bkz. [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6ffc7-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ffc7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ffc7-134">See also</span></span>
- [<span data-ttu-id="6ffc7-135">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="6ffc7-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6ffc7-136">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6ffc7-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="6ffc7-137">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="6ffc7-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="6ffc7-138">Deyimler</span><span class="sxs-lookup"><span data-stu-id="6ffc7-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="6ffc7-139">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6ffc7-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
