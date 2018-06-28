---
title: false işleci (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027843"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="e200d-102">false işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e200d-102">false operator (C# Reference)</span></span>

<span data-ttu-id="e200d-103">Döndürür [bool](bool.md) değeri `true` işleneni olduğunu belirtmek için `false` ve döndürür `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="e200d-103">Returns the [bool](bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>

<span data-ttu-id="e200d-104">C# 2.0 önce `true` ve `false` işleçleri gibi türleri ile uyumlu kullanıcı tanımlı boş değer atanabilen değer türleri oluşturmak için kullanılan `SqlBool`.</span><span class="sxs-lookup"><span data-stu-id="e200d-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="e200d-105">Ancak, dil, boş değer atanabilen değer türleri için yerleşik destek sağlar ve mümkün olduğunda bu aşırı yüklemesi yerine kullanmalısınız `true` ve `false` işleçler.</span><span class="sxs-lookup"><span data-stu-id="e200d-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="e200d-106">Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e200d-106">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="e200d-107">Boş değer atanabilir Boole değerlerini, ifade ile `a != b` mutlaka eşit değil `!(a == b)` birine veya ikisine de değerleri null olabilir çünkü.</span><span class="sxs-lookup"><span data-stu-id="e200d-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="e200d-108">Her ikisi de aşırı yükleme zorunda `true` ve `false` işleçleri ayrı olarak ifade null değerler düzgün bir şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="e200d-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="e200d-109">Aşağıdaki örnek aşırı yükleme ve nasıl kullanılacağını gösterir `true` ve `false` işleçler.</span><span class="sxs-lookup"><span data-stu-id="e200d-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

<span data-ttu-id="e200d-110">Overloads türü `true` ve `false` işleçleri, denetleme ifade için kullanılabilir [varsa](if-else.md), [yapmak](do.md), [sırada](while.md), ve [ için](for.md) deyimleri ve [koşullu ifadeler](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e200d-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in [conditional expressions](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="e200d-111">Bir tür işleci tanımlıyorsa `false`, işleci tanımlamalısınız [doğru](true.md).</span><span class="sxs-lookup"><span data-stu-id="e200d-111">If a type defines operator `false`, it must also define operator [true](true.md).</span></span>

<span data-ttu-id="e200d-112">Bir tür doğrudan koşullu mantıksal işleçler tekrar yükleyemez [ && ](../operators/conditional-and-operator.md) ve [ &#124; &#124; ](../operators/conditional-or-operator.md), ancak eşdeğer efekt normal mantıksal işleç aşırı yüklemesi tarafından gerçekleştirilebilir. ve işleçleri `true` ve `false`.</span><span class="sxs-lookup"><span data-stu-id="e200d-112">A type cannot directly overload the conditional logical operators [&&](../operators/conditional-and-operator.md) and [&#124;&#124;](../operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e200d-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e200d-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e200d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e200d-114">See also</span></span>

[<span data-ttu-id="e200d-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e200d-115">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="e200d-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e200d-116">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="e200d-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e200d-117">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="e200d-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e200d-118">C# Operators</span></span>](../operators/index.md)  
[<span data-ttu-id="e200d-119">true</span><span class="sxs-lookup"><span data-stu-id="e200d-119">true</span></span>](true.md)  