---
title: true İşleci (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 54b8d764dc673598474d6adbbee82e0223a16b93
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271318"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="928aa-102">true İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="928aa-102">true Operator (C# Reference)</span></span>
<span data-ttu-id="928aa-103">Döndürür [bool](../../../csharp/language-reference/keywords/bool.md) değer `true` bir işlenen true ise ve döndürür belirtmek için `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="928aa-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is true and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="928aa-104">C# 2.0 önce `true` ve `false` işleçler gibi türleri ile uyumlu olan kullanıcı tanımlı değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="928aa-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="928aa-105">Ancak, dil artık boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yükleme yerine bu kullanması gereken `true` ve `false` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="928aa-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="928aa-106">Daha fazla bilgi için [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="928aa-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="928aa-107">Boş değer atanabilir Boole değerlerini, ifade ile `a != b` eşit değil `!(a == b)` çünkü bir veya iki değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="928aa-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="928aa-108">Her ikisi de aşırı yükleme yapmanız `true` ve `false` işleçleri ayrı olarak ifade null değerler doğru bir şekilde tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="928aa-108">You need to overload both the `true` and `false` operators separately to correctly identify the null values in the expression.</span></span> <span data-ttu-id="928aa-109">Aşağıdaki örnek, aşırı yükleme ve kullanma işlemi gösterilmektedir `true` ve `false` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="928aa-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 <span data-ttu-id="928aa-110">Aşırı bir tür `true` ve `false` işleçleri, Denetim ifadesi için kullanılabilir [varsa](../../../csharp/language-reference/keywords/if-else.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [sırada](../../../csharp/language-reference/keywords/while.md), ve [ için](../../../csharp/language-reference/keywords/for.md) deyimleri ve [koşullu ifadeler](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="928aa-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="928aa-111">İşleci bir türü tanımlıyorsa `true`, işlecini tanımlamalıdır [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="928aa-111">If a type defines operator `true`, it must also define operator [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
 <span data-ttu-id="928aa-112">Bir tür doğrudan koşullu mantıksal işleçler aşırı yüklenemez ([ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)), ancak eşdeğer efekt normal aşırı yüklenerek ulaşılabilecek mantıksal işleçler ve işleçler `true` ve `false`.</span><span class="sxs-lookup"><span data-stu-id="928aa-112">A type cannot directly overload the conditional logical operators ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="928aa-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="928aa-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="928aa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="928aa-114">See Also</span></span>

- [<span data-ttu-id="928aa-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="928aa-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="928aa-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="928aa-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="928aa-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="928aa-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="928aa-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="928aa-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="928aa-119">false</span><span class="sxs-lookup"><span data-stu-id="928aa-119">false</span></span>](../../../csharp/language-reference/keywords/false.md)
