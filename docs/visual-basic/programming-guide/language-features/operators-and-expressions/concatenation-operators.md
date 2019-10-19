---
title: Visual Basic'de Birleştirme İşleçleri
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 789478cafc4ed7506d34fb4198531d437683075d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583305"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="78c7e-102">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="78c7e-102">Concatenation Operators in Visual Basic</span></span>

<span data-ttu-id="78c7e-103">Birleştirme işleçleri birden çok dizeyi tek bir dizeye birleştirir.</span><span class="sxs-lookup"><span data-stu-id="78c7e-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="78c7e-104">@No__t_0 ve `&` iki birleştirme işleci vardır.</span><span class="sxs-lookup"><span data-stu-id="78c7e-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="78c7e-105">Her ikisi de aşağıdaki örnekte gösterildiği gibi temel birleştirme işlemini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="78c7e-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

<span data-ttu-id="78c7e-106">Bu işleçler Ayrıca, aşağıdaki örnekte gösterildiği gibi `String` değişkenlerini de birleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="78c7e-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="78c7e-107">Iki birleştirme Işleci arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="78c7e-107">Differences Between the Two Concatenation Operators</span></span>

<span data-ttu-id="78c7e-108">[+ İşlecinin](../../../../visual-basic/language-reference/operators/addition-operator.md) iki sayı eklemenin birincil amacı vardır.</span><span class="sxs-lookup"><span data-stu-id="78c7e-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="78c7e-109">Ancak, sayısal işlenenleri dize işlenenleri ile de birleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="78c7e-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="78c7e-110">@No__t_0 işleci, bir derleyici hatasına ekleme, birleştirme, sinyal sinyali atma veya bir çalışma zamanı <xref:System.InvalidCastException> özel durumu oluşturma gibi karmaşık bir kurallar kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="78c7e-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="78c7e-111">[& işleci](../../../../visual-basic/language-reference/operators/concatenation-operator.md) yalnızca `String` işlenenleri için tanımlanır ve `Option Strict` ayarından bağımsız olarak her zaman işlenenlerini `String` olarak widens.</span><span class="sxs-lookup"><span data-stu-id="78c7e-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="78c7e-112">@No__t_0 işleci, dizeler için özel olarak tanımlandığından ve istenmeden dönüştürme oluşturma olasılığınızı azalttığından dize birleştirme için önerilir.</span><span class="sxs-lookup"><span data-stu-id="78c7e-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>

## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="78c7e-113">Performans: dize ve StringBuilder</span><span class="sxs-lookup"><span data-stu-id="78c7e-113">Performance: String and StringBuilder</span></span>

<span data-ttu-id="78c7e-114">Birleştirmeleri, silmeler ve değişiklikler gibi bir dizede önemli sayıda değişiklik yaparsanız, performans, <xref:System.Text> ad alanındaki <xref:System.Text.StringBuilder> sınıftan elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="78c7e-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="78c7e-115">@No__t_0 nesne oluşturup başlatmaya yönelik ek bir yönerge ve son değerini bir `String` dönüştürmek için başka bir yönerge kullanır, ancak <xref:System.Text.StringBuilder> daha hızlı gerçekleştirebildiğinden bu süreyi kurtarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78c7e-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>

## <a name="see-also"></a><span data-ttu-id="78c7e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c7e-116">See also</span></span>

- [<span data-ttu-id="78c7e-117">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="78c7e-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="78c7e-118">Visual Basic içindeki dize düzenleme yöntemlerinin türleri</span><span class="sxs-lookup"><span data-stu-id="78c7e-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="78c7e-119">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="78c7e-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="78c7e-120">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="78c7e-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="78c7e-121">Visual Basic mantıksal ve bit düzeyinde Işleçler</span><span class="sxs-lookup"><span data-stu-id="78c7e-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
