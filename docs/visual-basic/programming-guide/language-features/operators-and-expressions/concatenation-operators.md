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
ms.openlocfilehash: 90072a3cadccd0c66b66f0ec5ff2dafd3d62eaeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490864"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="cfb34-102">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="cfb34-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="cfb34-103">Birleştirme işleçleri, tek bir dize olarak birden çok dizeyi katılın.</span><span class="sxs-lookup"><span data-stu-id="cfb34-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="cfb34-104">İki birleştirme işleçleri vardır `+` ve `&`.</span><span class="sxs-lookup"><span data-stu-id="cfb34-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="cfb34-105">Her ikisi de, aşağıdaki örnekte gösterildiği gibi temel birleştirme işleminin yürütülmesi.</span><span class="sxs-lookup"><span data-stu-id="cfb34-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="cfb34-106">Bu işleçler de bitiştirebilirsiniz `String` değişkenler, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cfb34-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="cfb34-107">İki birleştirme işleçleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="cfb34-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="cfb34-108">[+ İşleci](../../../../visual-basic/language-reference/operators/addition-operator.md) iki sayının ekleme birincil amacı vardır.</span><span class="sxs-lookup"><span data-stu-id="cfb34-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="cfb34-109">Ancak, sayısal dize işlenenleri işlenenle aynı zamanda bitiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb34-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="cfb34-110">`+` İşleci olan ekleyin, birleştirme, derleyici bir hata sinyali vermek ya da bir çalışma zamanı durum belirleyen kuralları karmaşık bir dizi <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="cfb34-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="cfb34-111">[& İşleci](../../../../visual-basic/language-reference/operators/concatenation-operator.md) yalnızca tanımlanan `String` işlenen ve her zaman işlenenleri için widens `String`ayarına bakılmaksızın `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="cfb34-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="cfb34-112">`&` İşleci, dize birleştirme için önerilir, çünkü özel olarak dizeleri için tanımlanır ve istenmeyen bir dönüştürme oluşturma olasılığınızı azaltır.</span><span class="sxs-lookup"><span data-stu-id="cfb34-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="cfb34-113">Performans: Dize ve StringBuilder</span><span class="sxs-lookup"><span data-stu-id="cfb34-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="cfb34-114">Çok sayıda değişiklik, birleştirmeler ve silme gibi bir dizesini işlemeleri yaparsanız performansınızı gelen kar <xref:System.Text.StringBuilder> sınıfını <xref:System.Text> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cfb34-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="cfb34-115">Oluşturma ve başlatma için fazladan bir yönerge alır bir <xref:System.Text.StringBuilder> nesnesi ve son değerine dönüştürmek için başka bir yönerge bir `String`, ancak bu kez kurtarma <xref:System.Text.StringBuilder> daha hızlı bir şekilde gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfb34-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb34-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfb34-116">See also</span></span>
- [<span data-ttu-id="cfb34-117">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="cfb34-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="cfb34-118">Visual Basic'de dize düzenleme yöntemlerinin türleri</span><span class="sxs-lookup"><span data-stu-id="cfb34-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="cfb34-119">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="cfb34-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="cfb34-120">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="cfb34-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="cfb34-121">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="cfb34-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
