---
title: '>>= İşleci (Visual Basic)'
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
ms.openlocfilehash: 0ea1e03168da12564f148f525af977f29a43bec8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265291"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0c899-102">>>= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c899-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="0c899-103">Bir değişken veya özellik değerini temel aritmetik sağa kaydırma gerçekleştirir ve sonucu değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="0c899-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c899-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c899-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="0c899-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0c899-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="0c899-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0c899-106">Required.</span></span> <span data-ttu-id="0c899-107">Değişken veya özellik bir tamsayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="0c899-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="0c899-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0c899-108">Required.</span></span> <span data-ttu-id="0c899-109">Sayısal ifade bir veri türünün için widens `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0c899-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c899-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c899-110">Remarks</span></span>  
 <span data-ttu-id="0c899-111">Öğe sol tarafındaki `>>=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c899-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0c899-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0c899-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0c899-113">`>>=` İşleci ilk değişken veya özellik değerini temel aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0c899-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="0c899-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="0c899-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="0c899-115">Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir.</span><span class="sxs-lookup"><span data-stu-id="0c899-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="0c899-116">Aritmetik sağa kaydırma, en sağdaki bit ötesindeki kaydırılacak bitlerin atılır ve soldaki bit içine solda işleci boşaltılmış bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="0c899-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="0c899-117">Olması durumunda başka bir deyişle `variableorproperty` negatif bir değere sahip boşaltılmış konumları birine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0c899-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="0c899-118">Varsa `variableorproperty` pozitif ise veya veri türünü işaretsiz bir türü ise, boşaltılmış konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0c899-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0c899-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="0c899-119">Overloading</span></span>  
 <span data-ttu-id="0c899-120">[>> İşleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0c899-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0c899-121">Aşırı yükleme `>>` işleci davranışını etkileyen `>>=` işleci.</span><span class="sxs-lookup"><span data-stu-id="0c899-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="0c899-122">Kodunuzu kullanıyorsa `>>=` bir sınıf veya aşırı yapısı `>>`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0c899-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0c899-123">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0c899-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c899-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c899-124">Example</span></span>  
 <span data-ttu-id="0c899-125">Aşağıdaki örnekte `>>=` bit desenini kaydırılacak işleci bir `Integer` değişken sağ tarafından belirtilen tutar ve sonucu bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="0c899-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0c899-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c899-126">See also</span></span>
- [<span data-ttu-id="0c899-127">>> İşleci</span><span class="sxs-lookup"><span data-stu-id="0c899-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="0c899-128">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0c899-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="0c899-129">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0c899-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="0c899-130">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="0c899-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0c899-131">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="0c899-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0c899-132">Deyimler</span><span class="sxs-lookup"><span data-stu-id="0c899-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
