---
title: '&lt;&lt;= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 9d4f367506c847ddf2478dd1ea07e28332cc62a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677777"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="94d6f-102">&lt;&lt;= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94d6f-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="94d6f-103">Bir değişken veya özellik değerini temel aritmetik sola kaydırma gerçekleştirir ve sonucu değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="94d6f-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94d6f-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="94d6f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="94d6f-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="94d6f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="94d6f-106">Required.</span></span> <span data-ttu-id="94d6f-107">Değişken veya özellik bir tamsayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="94d6f-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="94d6f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="94d6f-108">Required.</span></span> <span data-ttu-id="94d6f-109">Sayısal ifade bir veri türünün için widens `Integer`.</span><span class="sxs-lookup"><span data-stu-id="94d6f-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94d6f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94d6f-110">Remarks</span></span>  
 <span data-ttu-id="94d6f-111">Öğe sol tarafındaki `<<=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="94d6f-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="94d6f-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="94d6f-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="94d6f-113">`<<=` İşleci ilk değişken veya özellik değerini temel aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="94d6f-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="94d6f-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik geri atar.</span><span class="sxs-lookup"><span data-stu-id="94d6f-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="94d6f-115">Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir.</span><span class="sxs-lookup"><span data-stu-id="94d6f-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="94d6f-116">Aritmetik sola kaydırma, sonuç veri türü aralığının dışında kaydırılacak bitlerin atılır ve sağ tarafta işleci boşaltılmış bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="94d6f-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="94d6f-117">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="94d6f-117">Overloading</span></span>  
 <span data-ttu-id="94d6f-118">[<< İşleci](../../../visual-basic/language-reference/operators/left-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="94d6f-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="94d6f-119">Aşırı yükleme `<<` işleci davranışını etkileyen `<<=` işleci.</span><span class="sxs-lookup"><span data-stu-id="94d6f-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="94d6f-120">Kodunuzu kullanıyorsa `<<=` bir sınıf veya aşırı yapısı `<<`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="94d6f-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="94d6f-121">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="94d6f-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d6f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="94d6f-122">Example</span></span>  
 <span data-ttu-id="94d6f-123">Aşağıdaki örnekte `<<=` bit desenini kaydırılacak işleci bir `Integer` değişkeni değişkene atama sonucu ve belirtilen süre kaldı.</span><span class="sxs-lookup"><span data-stu-id="94d6f-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="94d6f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94d6f-124">See also</span></span>
- [<span data-ttu-id="94d6f-125"><< İşleci</span><span class="sxs-lookup"><span data-stu-id="94d6f-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="94d6f-126">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="94d6f-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="94d6f-127">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="94d6f-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="94d6f-128">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="94d6f-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="94d6f-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="94d6f-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="94d6f-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="94d6f-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
