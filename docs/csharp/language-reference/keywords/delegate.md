---
title: delegate (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: ba1cfdcc56b3d2301a07ffa4af793e7002da21bb
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948429"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="c27d3-102">delegate (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c27d3-102">delegate (C# Reference)</span></span>

<span data-ttu-id="c27d3-103">Bir temsilci türü bildirimi yöntemi imza benzer.</span><span class="sxs-lookup"><span data-stu-id="c27d3-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="c27d3-104">Dönüş değeri ve parametreleri herhangi bir türde herhangi bir sayıda sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c27d3-104">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

<span data-ttu-id="c27d3-105">A `delegate` adlandırılmış kapsüllemek için kullanılan bir başvuru türü veya anonim bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="c27d3-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="c27d3-106">C++'ta işlev işaretçileri temsilciler benzer; Ancak, temsilciler tür kullanımı uyumlu ve güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="c27d3-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="c27d3-107">Temsilciler uygulamalar için bkz [Temsilciler](../../../csharp/programming-guide/delegates/index.md) ve [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c27d3-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="c27d3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c27d3-108">Remarks</span></span>

<span data-ttu-id="c27d3-109">Temsilciler olan temelini [olayları](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="c27d3-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>

<span data-ttu-id="c27d3-110">Bir temsilci, herhangi bir adlandırılmış ve anonim yöntemi ile ilişkilendirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c27d3-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="c27d3-111">Daha fazla bilgi için bkz: [adlı yöntemleri](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) ve [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c27d3-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

<span data-ttu-id="c27d3-112">Temsilci uyumlu bir dönüş türü ve giriş parametreleri olan bir yöntem veya lambda ifadesi ile örneğinin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c27d3-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="c27d3-113">Yöntem imzası izin farkı derecesini hakkında daha fazla bilgi için bkz: [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c27d3-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="c27d3-114">Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="c27d3-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="c27d3-115">Her iki yönde temsilcilerin örnek oluşturma, bu bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c27d3-115">Both ways of instantiating delegates are discussed in this section.</span></span>

## <a name="example"></a><span data-ttu-id="c27d3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="c27d3-116">Example</span></span>

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="c27d3-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c27d3-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c27d3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c27d3-118">See also</span></span>

[<span data-ttu-id="c27d3-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c27d3-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="c27d3-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c27d3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="c27d3-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c27d3-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="c27d3-122">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="c27d3-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
[<span data-ttu-id="c27d3-123">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c27d3-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
[<span data-ttu-id="c27d3-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="c27d3-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
[<span data-ttu-id="c27d3-125">Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="c27d3-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
[<span data-ttu-id="c27d3-126">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="c27d3-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
