---
title: "delegate (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a><span data-ttu-id="06c5e-102">delegate (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="06c5e-102">delegate (C# Reference)</span></span>
<span data-ttu-id="06c5e-103">Bir temsilci türü bildirimi yöntemi imza benzer.</span><span class="sxs-lookup"><span data-stu-id="06c5e-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="06c5e-104">Dönüş değeri ve parametreleri herhangi bir türde herhangi bir sayıda sahiptir:</span><span class="sxs-lookup"><span data-stu-id="06c5e-104">It has a return value and any number of parameters of any type:</span></span>  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="06c5e-105">A `delegate` adlandırılmış kapsüllemek için kullanılan bir başvuru türü veya anonim bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="06c5e-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="06c5e-106">C++'ta işlev işaretçileri temsilciler benzer; Ancak, temsilciler tür kullanımı uyumlu ve güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="06c5e-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="06c5e-107">Temsilciler uygulamalar için bkz [Temsilciler](../../../csharp/programming-guide/delegates/index.md) ve [genel temsilciler](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="06c5e-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06c5e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06c5e-108">Remarks</span></span>  
 <span data-ttu-id="06c5e-109">Temsilciler olan temelini [olayları](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="06c5e-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="06c5e-110">Bir temsilci, herhangi bir adlandırılmış ve anonim yöntemi ile ilişkilendirerek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="06c5e-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="06c5e-111">Daha fazla bilgi için bkz: [adlı yöntemleri](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) ve [anonim yöntemler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="06c5e-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="06c5e-112">Temsilci uyumlu bir dönüş türü ve giriş parametreleri olan bir yöntem veya lambda ifadesi ile örneğinin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06c5e-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="06c5e-113">Yöntem imzası izin farkı derecesini hakkında daha fazla bilgi için bkz: [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="06c5e-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="06c5e-114">Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="06c5e-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="06c5e-115">Her iki yönde temsilcilerin örnek oluşturma, bu bölümde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="06c5e-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06c5e-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="06c5e-116">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="06c5e-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="06c5e-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06c5e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06c5e-118">See Also</span></span>  
 [<span data-ttu-id="06c5e-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="06c5e-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="06c5e-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="06c5e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="06c5e-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="06c5e-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="06c5e-122">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="06c5e-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="06c5e-123">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="06c5e-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="06c5e-124">Olayları</span><span class="sxs-lookup"><span data-stu-id="06c5e-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="06c5e-125">Temsilciler adlandırılmış vs ile. Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="06c5e-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [<span data-ttu-id="06c5e-126">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="06c5e-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
