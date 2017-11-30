---
title: "Visual Basic'de Birleştirme İşleçleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a444cca76fbc41807b0c8b69bcbaedbd75c36eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="f0ec9-102">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f0ec9-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="f0ec9-103">Birleştirme işleçleri, tek bir dize halinde birden çok dizenin katılın.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="f0ec9-104">İki birleştirme işleçleri vardır `+` ve `&`.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="f0ec9-105">Her ikisi de, aşağıdaki örnekte gösterildiği gibi temel birleştirme işlemi gerçekleştiremeyen.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="f0ec9-106">Bu işleçlere de birleştirme `String` aşağıdaki örnekte gösterildiği gibi değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="f0ec9-107">İki birleştirme işleçleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="f0ec9-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="f0ec9-108">[+ İşleci](../../../../visual-basic/language-reference/operators/addition-operator.md) iki sayı ekleme birincil amacı vardır.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="f0ec9-109">Ancak, bu da dize işlenenleri sayısal işlenen bir arada kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="f0ec9-110">`+` Sahip eklemek, birleştirme, bir derleyici hatası sinyal ya da bir çalışma zamanı throw belirleyen kuralları karmaşık bir dizi <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="f0ec9-111">[& İşleci](../../../../visual-basic/language-reference/operators/concatenation-operator.md) yalnızca için tanımlanan `String` işlenenler ve her zaman için işlenenleri widens `String`ne olursa olsun, ayarını `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="f0ec9-112">`&` İşleci, dize birleştirme için önerilir, çünkü özel olarak dizeleri için tanımlanır ve istenmeyen bir dönüştürme oluşturma, olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="f0ec9-113">Performans: Dize ve StringBuilder</span><span class="sxs-lookup"><span data-stu-id="f0ec9-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="f0ec9-114">Çok sayıda birleştirmeler, silme ve değişiklik, gibi bir dizesini işlemeleri yaparsanız performansınızı gelen kar <xref:System.Text.StringBuilder> sınıfını <xref:System.Text> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="f0ec9-115">Oluşturma ve başlatma için fazladan bir yönerge sürdüğünü bir <xref:System.Text.StringBuilder> nesnesi ve son değerine dönüştürmek için başka bir yönerge bir `String`, ancak bu kez kurtarmak <xref:System.Text.StringBuilder> daha hızlı gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ec9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0ec9-116">See Also</span></span>  
 [<span data-ttu-id="f0ec9-117">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="f0ec9-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="f0ec9-118">Visual Basic'de dize düzenleme yöntemlerinin türleri</span><span class="sxs-lookup"><span data-stu-id="f0ec9-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [<span data-ttu-id="f0ec9-119">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="f0ec9-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="f0ec9-120">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="f0ec9-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="f0ec9-121">Visual Basic'de mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="f0ec9-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
