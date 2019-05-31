---
title: olarak - C# başvurusu
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 84e599340877ce52dc6242ea259c69672915c546
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422021"
---
# <a name="as-c-reference"></a><span data-ttu-id="f965a-102">as (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f965a-102">as (C# Reference)</span></span>
<span data-ttu-id="f965a-103">Kullanabileceğiniz `as` belirli türlerdeki uyumlu başvuru türleri arasında dönüştürmeler gerçekleştirmek için işleci veya [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="f965a-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="f965a-104">Aşağıdaki kod örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="f965a-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="f965a-105">Örnekte gösterildiği gibi sonucunu karşılaştırmak gereken `as` ifadesiyle `null` dönüştürme başarılı olup olmadığını denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="f965a-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="f965a-106">Kullanabileceğiniz C# 7.0 ile başlayarak, [olduğu](is.md) dönüştürme başarılı olduğunu test etmek ve Dönüştürme başarılı olduğunda bir değişken koşullu olarak atamak için ifadesinde iki.</span><span class="sxs-lookup"><span data-stu-id="f965a-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="f965a-107">Birçok senaryoda kullanmaktan daha kısa `as` işleci.</span><span class="sxs-lookup"><span data-stu-id="f965a-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="f965a-108">Daha fazla bilgi için [türü deseni](is.md#type) bölümünü [ `is` işleci](is.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="f965a-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="f965a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f965a-109">Remarks</span></span>  
 <span data-ttu-id="f965a-110">`as` İşleci, bir tür dönüştürme işlemini gibi.</span><span class="sxs-lookup"><span data-stu-id="f965a-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="f965a-111">Ancak, dönüştürme mümkün değilse `as` döndürür `null` yerine bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f965a-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="f965a-112">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f965a-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="f965a-113">Kod, aşağıdaki ifade hariç eşdeğerdir `expression` değişken yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f965a-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="f965a-114">Unutmayın `as` işleci, yalnızca başvuru dönüşümleri, boş değer atanabilir dönüştürmeler ve kutulama dönüştürmeleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f965a-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="f965a-115">`as` İşleci, bunun yerine cast ifadeleri kullanarak gerçekleştirilmelidir kullanıcı tanımlı dönüşümler gibi diğer dönüştürmeler gerçekleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f965a-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f965a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f965a-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="f965a-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f965a-117">C# Language Specification</span></span>  

<span data-ttu-id="f965a-118">Daha fazla bilgi için [işleci olarak](~/_csharplang/spec/expressions.md#the-as-operator) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f965a-118">For more information, see [The as operator](~/_csharplang/spec/expressions.md#the-as-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="f965a-119">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="f965a-119">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="f965a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f965a-120">See also</span></span>

- [<span data-ttu-id="f965a-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f965a-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="f965a-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f965a-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f965a-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f965a-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="f965a-124">is</span><span class="sxs-lookup"><span data-stu-id="f965a-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="f965a-125">?: İşleç</span><span class="sxs-lookup"><span data-stu-id="f965a-125">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)
