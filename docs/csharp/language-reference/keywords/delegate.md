---
title: Temsilci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: 233b0255121cf6e7a5283041d594e2d843f105fb
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286474"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="ca6e2-102">delegate (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ca6e2-102">delegate (C# Reference)</span></span>

<span data-ttu-id="ca6e2-103">Bir temsilci türü bildirimi için bir yöntem imzası benzerdir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="ca6e2-104">Bu, dönüş değeri ve herhangi bir sayıda herhangi bir türde parametreleri vardır:</span><span class="sxs-lookup"><span data-stu-id="ca6e2-104">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

<span data-ttu-id="ca6e2-105">A `delegate` adlandırılmış kapsüllemek için kullanılabilecek bir başvuru türü veya anonim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="ca6e2-106">Temsilciler c++ işlev işaretçilerine benzer; Ancak, temsilciler, tür kullanımı uyumlu ve güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="ca6e2-107">Temsilciler uygulamalar için bkz [Temsilciler](../../../csharp/programming-guide/delegates/index.md) ve [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e2-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="ca6e2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca6e2-108">Remarks</span></span>

<span data-ttu-id="ca6e2-109">Temsilcileri, bir temel [olayları](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e2-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>

<span data-ttu-id="ca6e2-110">Temsilci adlandırılmış ve anonim bir yöntem ile ilişkilendirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="ca6e2-111">Daha fazla bilgi için [adlı yöntemleri](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) ve [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e2-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

<span data-ttu-id="ca6e2-112">Uyumlu bir dönüş türü ve giriş parametrelerini içeren bir yöntem veya lambda ifadesiyle, temsilci örneği gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="ca6e2-113">Yöntem imzası izin verilen fark derecesi hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e2-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="ca6e2-114">Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="ca6e2-115">Her iki yönde örnekleme temsilcilerin, bu bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-115">Both ways of instantiating delegates are discussed in this section.</span></span>

## <a name="example"></a><span data-ttu-id="ca6e2-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca6e2-116">Example</span></span>

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="ca6e2-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ca6e2-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ca6e2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-118">See also</span></span>

- [<span data-ttu-id="ca6e2-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ca6e2-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ca6e2-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ca6e2-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ca6e2-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ca6e2-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="ca6e2-122">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="ca6e2-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="ca6e2-123">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ca6e2-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="ca6e2-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ca6e2-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="ca6e2-125">Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="ca6e2-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) 
- [<span data-ttu-id="ca6e2-126">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="ca6e2-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="ca6e2-127">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ca6e2-127">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
