---
title: << = işleci (Visual Basic)
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
ms.openlocfilehash: da2b5ca0b7538d77c3c8d8bc7d45712d656ce63a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829154"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="32f26-102">\<\<= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32f26-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="32f26-103">Bir değişken veya özellik değerini temel aritmetik sola kaydırma gerçekleştirir ve sonucu değişken veya özellik için atar.</span><span class="sxs-lookup"><span data-stu-id="32f26-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32f26-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="32f26-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="32f26-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="32f26-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32f26-106">Required.</span></span> <span data-ttu-id="32f26-107">Değişken veya özellik bir tamsayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="32f26-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="32f26-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="32f26-108">Required.</span></span> <span data-ttu-id="32f26-109">Sayısal ifade bir veri türünün için widens `Integer`.</span><span class="sxs-lookup"><span data-stu-id="32f26-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32f26-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32f26-110">Remarks</span></span>  
 <span data-ttu-id="32f26-111">Öğe sol tarafındaki `<<=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="32f26-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="32f26-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="32f26-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="32f26-113">`<<=` İşleci ilk değişken veya özellik değerini temel aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="32f26-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="32f26-114">İşleci, bu işlemin sonucunu daha sonra değişken veya özellik geri atar.</span><span class="sxs-lookup"><span data-stu-id="32f26-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="32f26-115">Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir.</span><span class="sxs-lookup"><span data-stu-id="32f26-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="32f26-116">Aritmetik sola kaydırma, sonuç veri türü aralığının dışında kaydırılacak bitlerin atılır ve sağ tarafta işleci boşaltılmış bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="32f26-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="32f26-117">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="32f26-117">Overloading</span></span>  
 <span data-ttu-id="32f26-118">[<< İşleci](../../../visual-basic/language-reference/operators/left-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32f26-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="32f26-119">Aşırı yükleme `<<` işleci davranışını etkileyen `<<=` işleci.</span><span class="sxs-lookup"><span data-stu-id="32f26-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="32f26-120">Kodunuzu kullanıyorsa `<<=` bir sınıf veya aşırı yapısı `<<`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="32f26-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="32f26-121">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="32f26-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f26-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="32f26-122">Example</span></span>  
 <span data-ttu-id="32f26-123">Aşağıdaki örnekte `<<=` bit desenini kaydırılacak işleci bir `Integer` değişkeni değişkene atama sonucu ve belirtilen süre kaldı.</span><span class="sxs-lookup"><span data-stu-id="32f26-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="32f26-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32f26-124">See also</span></span>

- [<span data-ttu-id="32f26-125"><< İşleci</span><span class="sxs-lookup"><span data-stu-id="32f26-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="32f26-126">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="32f26-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="32f26-127">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="32f26-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="32f26-128">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="32f26-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="32f26-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="32f26-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="32f26-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="32f26-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
