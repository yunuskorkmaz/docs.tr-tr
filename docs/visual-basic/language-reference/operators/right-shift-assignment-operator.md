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
ms.openlocfilehash: 1076ce62077391f2c88ebdd621d1dbd6fb40d647
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982390"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="cff7c-102">>> = işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cff7c-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="cff7c-103">Bir değişken veya özellik değerini temel aritmetik sağa kaydırma gerçekleştirir ve sonucu değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="cff7c-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cff7c-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="cff7c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cff7c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="cff7c-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cff7c-106">Required.</span></span> <span data-ttu-id="cff7c-107">Değişken veya özellik bir tamsayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="cff7c-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="cff7c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="cff7c-108">Required.</span></span> <span data-ttu-id="cff7c-109">Sayısal ifade bir veri türünün için widens `Integer`.</span><span class="sxs-lookup"><span data-stu-id="cff7c-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff7c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cff7c-110">Remarks</span></span>  
 <span data-ttu-id="cff7c-111">Öğe sol tarafındaki `>>=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cff7c-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="cff7c-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="cff7c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="cff7c-113">`>>=` İşleci ilk değişken veya özellik değerini temel aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cff7c-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="cff7c-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="cff7c-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="cff7c-115">Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir.</span><span class="sxs-lookup"><span data-stu-id="cff7c-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="cff7c-116">Aritmetik sağa kaydırma, en sağdaki bit ötesindeki kaydırılacak bitlerin atılır ve soldaki bit içine solda işleci boşaltılmış bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="cff7c-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="cff7c-117">Olması durumunda başka bir deyişle `variableorproperty` negatif bir değere sahip boşaltılmış konumları birine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cff7c-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="cff7c-118">Varsa `variableorproperty` pozitif ise veya veri türünü işaretsiz bir türü ise, boşaltılmış konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cff7c-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cff7c-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="cff7c-119">Overloading</span></span>  
 <span data-ttu-id="cff7c-120">[>> İşleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cff7c-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cff7c-121">Aşırı yükleme `>>` işleci davranışını etkileyen `>>=` işleci.</span><span class="sxs-lookup"><span data-stu-id="cff7c-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="cff7c-122">Kodunuzu kullanıyorsa `>>=` bir sınıf veya aşırı yapısı `>>`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cff7c-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cff7c-123">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cff7c-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cff7c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="cff7c-124">Example</span></span>  
 <span data-ttu-id="cff7c-125">Aşağıdaki örnekte `>>=` bit desenini kaydırılacak işleci bir `Integer` değişken sağ tarafından belirtilen tutar ve sonucu bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="cff7c-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="cff7c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cff7c-126">See also</span></span>

- [<span data-ttu-id="cff7c-127">>> İşleci</span><span class="sxs-lookup"><span data-stu-id="cff7c-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="cff7c-128">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="cff7c-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="cff7c-129">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="cff7c-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="cff7c-130">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="cff7c-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="cff7c-131">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="cff7c-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cff7c-132">Deyimler</span><span class="sxs-lookup"><span data-stu-id="cff7c-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
