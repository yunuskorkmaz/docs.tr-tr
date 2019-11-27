---
title: Alt İfade
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d284e629ea0b0a4e9b6eb9e098612bb07c38723b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350906"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="2fbc2-102">Alt İfade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fbc2-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="2fbc2-103">Bir altyordam lambda ifadesi tanımlayan parametreleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbc2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fbc2-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="2fbc2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2fbc2-105">Parts</span></span>  
  
|<span data-ttu-id="2fbc2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="2fbc2-106">Term</span></span>|<span data-ttu-id="2fbc2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2fbc2-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="2fbc2-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-108">Optional.</span></span> <span data-ttu-id="2fbc2-109">Yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="2fbc2-110">Liste boş olduğunda bile parantezler mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="2fbc2-111">Daha fazla bilgi için bkz. [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="2fbc2-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="2fbc2-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-112">Required.</span></span> <span data-ttu-id="2fbc2-113">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="2fbc2-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-114">Required.</span></span> <span data-ttu-id="2fbc2-115">Deyimler listesi.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fbc2-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fbc2-116">Remarks</span></span>  
 <span data-ttu-id="2fbc2-117">*Lambda ifadesi* , bir ada sahip olmayan ve bir veya daha fazla deyimi yürüten bir altyordam.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="2fbc2-118">Bir lambda ifadesini, `RemoveHandler`bir bağımsız değişken hariç, temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="2fbc2-119">Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="2fbc2-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="2fbc2-120">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fbc2-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="2fbc2-121">Bir lambda ifadesinin sözdizimi, standart bir alt yordamın sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="2fbc2-122">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2fbc2-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="2fbc2-123">Lambda ifadesinin adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="2fbc2-124">Lambda ifadesi `Overloads` veya `Overrides`gibi bir değiştiriciye sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="2fbc2-125">Tek satırlık lambda ifadesinin gövdesi bir ifade değil, deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="2fbc2-126">Gövde, bir alt yordam çağrısından oluşabilir, ancak bir işlev yordamına çağrı değildir.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="2fbc2-127">Bir lambda ifadesinde, tüm parametrelerin belirtilen veri türleri olmalıdır veya tüm parametrelerin çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="2fbc2-128">Lambda ifadelerinde isteğe bağlı ve `ParamArray` parametrelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="2fbc2-129">Lambda ifadelerinde genel parametrelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fbc2-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="2fbc2-130">Example</span></span>  
 <span data-ttu-id="2fbc2-131">Aşağıda, konsola bir değer yazan bir lambda ifadesinin örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="2fbc2-132">Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="2fbc2-133">Daha fazla örnek için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2fbc2-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="2fbc2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbc2-134">See also</span></span>

- [<span data-ttu-id="2fbc2-135">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2fbc2-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2fbc2-136">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="2fbc2-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="2fbc2-137">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="2fbc2-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="2fbc2-138">Deyimler</span><span class="sxs-lookup"><span data-stu-id="2fbc2-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="2fbc2-139">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2fbc2-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
