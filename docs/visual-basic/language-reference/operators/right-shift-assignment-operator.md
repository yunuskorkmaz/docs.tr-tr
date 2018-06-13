---
title: '&gt;&gt;= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604113"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="5c2cf-102">&gt;&gt;= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c2cf-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="5c2cf-103">Bir değişkenin veya özelliğin değerini aritmetik sağa kaydırma gerçekleştirir ve değişken veya özelliği için sonuç atar.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c2cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c2cf-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="5c2cf-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5c2cf-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="5c2cf-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-106">Required.</span></span> <span data-ttu-id="5c2cf-107">Değişken ya da bir tam sayı türü özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="5c2cf-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="5c2cf-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-108">Required.</span></span> <span data-ttu-id="5c2cf-109">Sayısal ifade bir veri türündeki için widens `Integer`.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c2cf-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c2cf-110">Remarks</span></span>  
 <span data-ttu-id="5c2cf-111">Öğe sol tarafındaki `>>=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="5c2cf-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="5c2cf-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="5c2cf-113">`>>=` İşleci değişken veya özellik değeri üzerinde ilk aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="5c2cf-114">İşleci, daha sonra değişken veya özellik için bu işlemin sonucu olarak atar.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="5c2cf-115">Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="5c2cf-116">Aritmetik sağa kaydırma, en sağdaki bit konumu gölgeye BITS atılır ve soldaki bit solda vacated bit konumları içine yayılır.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="5c2cf-117">Bu olması durumunda gelir `variableorproperty` negatif bir değere sahip vacated konumlar için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="5c2cf-118">Varsa `variableorproperty` pozitifse veya kendi veri türü imzasız bir tür ise, vacated konumlar sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5c2cf-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="5c2cf-119">Overloading</span></span>  
 <span data-ttu-id="5c2cf-120">[>> İşleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5c2cf-121">Aşırı yükleme `>>` işleci davranışını etkileyen `>>=` işleci.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="5c2cf-122">Kodunuzu kullanıyorsa `>>=` bir sınıf veya overloads yapısı `>>`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5c2cf-123">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5c2cf-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c2cf-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c2cf-124">Example</span></span>  
 <span data-ttu-id="5c2cf-125">Aşağıdaki örnek kullanır `>>=` bit desenini kaydırılacak işleci bir `Integer` değişken sağ tarafından belirtilen tutar ve ata değişkene sonucu.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5c2cf-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-126">See Also</span></span>  
 [<span data-ttu-id="5c2cf-127">>> İşleci</span><span class="sxs-lookup"><span data-stu-id="5c2cf-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="5c2cf-128">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5c2cf-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="5c2cf-129">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="5c2cf-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="5c2cf-130">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="5c2cf-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="5c2cf-131">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="5c2cf-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="5c2cf-132">Deyimler</span><span class="sxs-lookup"><span data-stu-id="5c2cf-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
