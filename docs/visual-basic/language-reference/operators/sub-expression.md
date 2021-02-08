---
description: 'Daha fazla bilgi edinin: alt Ifade (Visual Basic)'
title: Sub İfadesi
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e47aa8f9707701b5fd9d90fb3fabb31e9c052b53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795293"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="9c0cb-103">Alt İfade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c0cb-103">Sub Expression (Visual Basic)</span></span>

<span data-ttu-id="9c0cb-104">Bir altyordam lambda ifadesi tanımlayan parametreleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-104">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0cb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c0cb-105">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="9c0cb-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9c0cb-106">Parts</span></span>  
  
|<span data-ttu-id="9c0cb-107">Süre</span><span class="sxs-lookup"><span data-stu-id="9c0cb-107">Term</span></span>|<span data-ttu-id="9c0cb-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="9c0cb-108">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="9c0cb-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-109">Optional.</span></span> <span data-ttu-id="9c0cb-110">Yordamın parametrelerini temsil eden yerel değişken adlarının bir listesi.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-110">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="9c0cb-111">Liste boş olduğunda bile parantezler mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-111">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="9c0cb-112">Daha fazla bilgi için bkz. [parametre listesi](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="9c0cb-112">For more information, see [Parameter List](../statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="9c0cb-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-113">Required.</span></span> <span data-ttu-id="9c0cb-114">Tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-114">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="9c0cb-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-115">Required.</span></span> <span data-ttu-id="9c0cb-116">Deyimler listesi.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-116">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c0cb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c0cb-117">Remarks</span></span>  

 <span data-ttu-id="9c0cb-118">*Lambda ifadesi* , bir ada sahip olmayan ve bir veya daha fazla deyimi yürüten bir altyordam.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-118">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="9c0cb-119">Bir lambda ifadesini, için bağımsız değişken dışında bir temsilci türü kullanabileceğiniz her yerde kullanabilirsiniz `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="9c0cb-119">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="9c0cb-120">Temsilciler ve temsilcilerle lambda ifadelerinin kullanımı hakkında daha fazla bilgi için bkz. [Delegate deyimi](../statements/delegate-statement.md) ve [gevşek temsilci dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="9c0cb-120">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="9c0cb-121">Lambda İfadesi Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c0cb-121">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="9c0cb-122">Bir lambda ifadesinin sözdizimi, standart bir alt yordamın sözdizimine benzer.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-122">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="9c0cb-123">Farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9c0cb-123">The differences are as follows:</span></span>  
  
- <span data-ttu-id="9c0cb-124">Lambda ifadesinin adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-124">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="9c0cb-125">Lambda ifadesi, veya gibi bir değiştiriciye sahip olamaz `Overloads` `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="9c0cb-125">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="9c0cb-126">Tek satırlık lambda ifadesinin gövdesi bir ifade değil, deyim olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-126">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="9c0cb-127">Gövde, bir alt yordam çağrısından oluşabilir, ancak bir işlev yordamına çağrı değildir.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-127">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="9c0cb-128">Bir lambda ifadesinde, tüm parametrelerin belirtilen veri türleri olmalıdır veya tüm parametrelerin çıkarsanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-128">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="9c0cb-129">Lambda ifadelerinde isteğe bağlı ve `ParamArray` parametrelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-129">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="9c0cb-130">Lambda ifadelerinde genel parametrelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-130">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0cb-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c0cb-131">Example</span></span>  

 <span data-ttu-id="9c0cb-132">Aşağıda, konsola bir değer yazan bir lambda ifadesinin örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-132">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="9c0cb-133">Örnek, bir altyordam için hem tek satırlı hem çok satırlı lambda ifadesi sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-133">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="9c0cb-134">Daha fazla örnek için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9c0cb-134">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="9c0cb-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c0cb-135">See also</span></span>

- [<span data-ttu-id="9c0cb-136">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9c0cb-136">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="9c0cb-137">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9c0cb-137">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="9c0cb-138">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="9c0cb-138">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="9c0cb-139">Deyimler</span><span class="sxs-lookup"><span data-stu-id="9c0cb-139">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="9c0cb-140">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="9c0cb-140">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
