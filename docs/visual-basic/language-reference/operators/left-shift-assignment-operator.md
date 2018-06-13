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
ms.openlocfilehash: 559624f7097f90d374ee83e3c0a9ac97d9f93444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600733"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="54a22-102">&lt;&lt;= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54a22-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="54a22-103">Bir değişkenin veya özelliğin değerini aritmetik sola kaydırma gerçekleştirir ve değişken veya özelliği için sonuç atar.</span><span class="sxs-lookup"><span data-stu-id="54a22-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54a22-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="54a22-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="54a22-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="54a22-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="54a22-106">Required.</span></span> <span data-ttu-id="54a22-107">Değişken ya da bir tam sayı türü özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="54a22-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="54a22-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="54a22-108">Required.</span></span> <span data-ttu-id="54a22-109">Sayısal ifade bir veri türündeki için widens `Integer`.</span><span class="sxs-lookup"><span data-stu-id="54a22-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54a22-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54a22-110">Remarks</span></span>  
 <span data-ttu-id="54a22-111">Öğe sol tarafındaki `<<=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="54a22-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="54a22-112">Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="54a22-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="54a22-113">`<<=` İşleci değişken veya özellik değeri üzerinde ilk aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="54a22-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="54a22-114">İşleci, daha sonra geri, değişken veya özellik için bu işlemin sonucu olarak atar.</span><span class="sxs-lookup"><span data-stu-id="54a22-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="54a22-115">Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil.</span><span class="sxs-lookup"><span data-stu-id="54a22-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="54a22-116">Aritmetik sola kaydırma, sonuç veri türü aralık dışında gölgeye BITS atılır ve sağ taraftaki vacated bit konumları sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="54a22-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="54a22-117">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="54a22-117">Overloading</span></span>  
 <span data-ttu-id="54a22-118">[<< İşleci](../../../visual-basic/language-reference/operators/left-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="54a22-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="54a22-119">Aşırı yükleme `<<` işleci davranışını etkileyen `<<=` işleci.</span><span class="sxs-lookup"><span data-stu-id="54a22-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="54a22-120">Kodunuzu kullanıyorsa `<<=` bir sınıf veya overloads yapısı `<<`, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="54a22-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="54a22-121">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="54a22-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54a22-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="54a22-122">Example</span></span>  
 <span data-ttu-id="54a22-123">Aşağıdaki örnek kullanır `<<=` bit desenini kaydırılacak işleci bir `Integer` değişkeni değişkenine sol atama sonucu ve belirtilen miktarı.</span><span class="sxs-lookup"><span data-stu-id="54a22-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="54a22-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54a22-124">See Also</span></span>  
 [<span data-ttu-id="54a22-125"><< İşleci</span><span class="sxs-lookup"><span data-stu-id="54a22-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [<span data-ttu-id="54a22-126">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="54a22-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="54a22-127">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="54a22-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="54a22-128">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="54a22-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="54a22-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="54a22-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="54a22-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="54a22-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
