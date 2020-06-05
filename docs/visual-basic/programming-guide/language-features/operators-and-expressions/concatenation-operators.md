---
title: Birleştirme İşleçleri
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388796"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="01d9b-102">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="01d9b-102">Concatenation Operators in Visual Basic</span></span>

<span data-ttu-id="01d9b-103">Birleştirme işleçleri birden çok dizeyi tek bir dizeye birleştirir.</span><span class="sxs-lookup"><span data-stu-id="01d9b-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="01d9b-104">İki birleştirme işleci vardır `+` `&` .</span><span class="sxs-lookup"><span data-stu-id="01d9b-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="01d9b-105">Her ikisi de aşağıdaki örnekte gösterildiği gibi temel birleştirme işlemini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="01d9b-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

<span data-ttu-id="01d9b-106">Bu işleçler `String` , aşağıdaki örnekte gösterildiği gibi değişkenleri de birleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="01d9b-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="01d9b-107">Iki birleştirme Işleci arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="01d9b-107">Differences Between the Two Concatenation Operators</span></span>

<span data-ttu-id="01d9b-108">[+ İşlecinin](../../../language-reference/operators/addition-operator.md) iki sayı eklemenin birincil amacı vardır.</span><span class="sxs-lookup"><span data-stu-id="01d9b-108">The [+ Operator](../../../language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="01d9b-109">Ancak, sayısal işlenenleri dize işlenenleri ile de birleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="01d9b-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="01d9b-110">`+`İşlecinde, bir derleyici hatasına ekleme, birleştirme, sinyal sinyali atma veya bir çalışma zamanı özel durumu oluşturma gibi karmaşık bir kural kümesi vardır <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="01d9b-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="01d9b-111">[& işleci](../../../language-reference/operators/concatenation-operator.md) yalnızca işlenenler için tanımlanır `String` ve ayarından bağımsız olarak her zaman işlenenlerini olarak widens `String` `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="01d9b-111">The [& Operator](../../../language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="01d9b-112">`&`İşleci, dizeler için özel olarak tanımlandığından ve istenmeyen bir dönüştürme oluşturma olasılığınızı azalttığından dize birleştirme için önerilir.</span><span class="sxs-lookup"><span data-stu-id="01d9b-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>

## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="01d9b-113">Performans: dize ve StringBuilder</span><span class="sxs-lookup"><span data-stu-id="01d9b-113">Performance: String and StringBuilder</span></span>

<span data-ttu-id="01d9b-114">Birleştirmeleri, silmeler ve değişiklikler gibi bir dizede önemli sayıda değişiklik yaparsanız, performans, <xref:System.Text.StringBuilder> ad alanındaki sınıftan elde edebilir <xref:System.Text> .</span><span class="sxs-lookup"><span data-stu-id="01d9b-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="01d9b-115">Bir nesne oluşturmak ve başlatmak için ek bir yönerge <xref:System.Text.StringBuilder> ve son değerini a 'ya dönüştürmek için başka bir yönerge kullanır `String` , ancak daha hızlı bir şekilde gerçekleştirilebileceğinden bu süreyi kurtarabilirsiniz <xref:System.Text.StringBuilder> .</span><span class="sxs-lookup"><span data-stu-id="01d9b-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>

## <a name="see-also"></a><span data-ttu-id="01d9b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01d9b-116">See also</span></span>

- [<span data-ttu-id="01d9b-117">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="01d9b-117">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="01d9b-118">Visual Basic'de Dize Düzenleme Yöntemlerinin Türleri</span><span class="sxs-lookup"><span data-stu-id="01d9b-118">Types of String Manipulation Methods in Visual Basic</span></span>](../strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="01d9b-119">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="01d9b-119">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="01d9b-120">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="01d9b-120">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="01d9b-121">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="01d9b-121">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
