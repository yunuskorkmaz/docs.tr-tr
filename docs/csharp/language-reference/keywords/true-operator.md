---
title: true İşleci (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 71f522b3860f7461f5c52dd77bb424f7ba0f9bf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275086"
---
# <a name="true-operator-c-reference"></a><span data-ttu-id="5d2b6-102">true İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5d2b6-102">true Operator (C# Reference)</span></span>
<span data-ttu-id="5d2b6-103">Döndürür [bool](../../../csharp/language-reference/keywords/bool.md) değeri `true` işleneni true olarak ayarlandığında ve döndürür belirtmek için `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is true and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="5d2b6-104">C# 2.0 önce `true` ve `false` işleçleri gibi türleri ile uyumlu kullanıcı tanımlı boş değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="5d2b6-105">Ancak, dil, boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yüklemesi yerine kullanmalısınız `true` ve `false` işleçler.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="5d2b6-106">Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d2b6-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="5d2b6-107">Boş değer atanabilir Boole değerlerini, ifade ile `a != b` mutlaka eşit değil `!(a == b)` birine veya ikisine de değerleri null olabilir çünkü.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="5d2b6-108">Her ikisi de aşırı gerek `true` ve `false` ayrı olarak ifade null değerler doğru bir şekilde tanımlamak için işleçler.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-108">You need to overload both the `true` and `false` operators separately to correctly identify the null values in the expression.</span></span> <span data-ttu-id="5d2b6-109">Aşağıdaki örnek aşırı yükleme ve nasıl kullanılacağını gösterir `true` ve `false` işleçler.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 <span data-ttu-id="5d2b6-110">Overloads türü `true` ve `false` işleçleri, denetleme ifade için kullanılabilir [varsa](../../../csharp/language-reference/keywords/if-else.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [sırada](../../../csharp/language-reference/keywords/while.md), ve [ için](../../../csharp/language-reference/keywords/for.md) deyimleri ve [koşullu ifadeler](../../../csharp/language-reference/operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5d2b6-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="5d2b6-111">Bir tür işleci tanımlıyorsa `true`, işleci tanımlamalısınız [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="5d2b6-111">If a type defines operator `true`, it must also define operator [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
 <span data-ttu-id="5d2b6-112">Bir tür doğrudan koşullu mantıksal işleçler tekrar yükleyemez ([ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)), ancak eşdeğer efekt normal aşırı yüklemesi tarafından elde edilebilir mantıksal işleçler ve işleçleri `true` ve `false`.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-112">A type cannot directly overload the conditional logical operators ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5d2b6-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5d2b6-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d2b6-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d2b6-114">See Also</span></span>  
 [<span data-ttu-id="5d2b6-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5d2b6-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5d2b6-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d2b6-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d2b6-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5d2b6-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5d2b6-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5d2b6-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="5d2b6-119">false</span><span class="sxs-lookup"><span data-stu-id="5d2b6-119">false</span></span>](../../../csharp/language-reference/keywords/false.md)
