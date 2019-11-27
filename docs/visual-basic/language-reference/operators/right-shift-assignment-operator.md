---
title: '>>= İşleci'
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
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351989"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1649b-102">> > = Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1649b-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="1649b-103">Bir değişkenin veya özelliğin değerinde aritmetik sağa kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="1649b-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1649b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1649b-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1649b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1649b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1649b-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1649b-106">Required.</span></span> <span data-ttu-id="1649b-107">İntegral türünün değişkeni veya özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="1649b-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1649b-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1649b-108">Required.</span></span> <span data-ttu-id="1649b-109">`Integer`için widens bir veri türünün sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1649b-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1649b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1649b-110">Remarks</span></span>  
 <span data-ttu-id="1649b-111">`>>=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1649b-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1649b-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="1649b-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1649b-113">`>>=` işleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1649b-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="1649b-114">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="1649b-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="1649b-115">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1649b-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1649b-116">Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki bit, sol taraftaki bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="1649b-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1649b-117">Bu, `variableorproperty` negatif bir değer içeriyorsa, vakatılmış konumların bir olarak ayarlanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1649b-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="1649b-118">`variableorproperty` pozitifse veya veri türü işaretsiz bir tür ise, karıştırılmış konumlar sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1649b-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1649b-119">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="1649b-119">Overloading</span></span>  
 <span data-ttu-id="1649b-120">[> > işleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1649b-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1649b-121">`>>` işleci aşırı yükleme `>>=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="1649b-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="1649b-122">Kodunuz, `>>`aşırı yükleyen bir sınıf veya yapı üzerinde `>>=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1649b-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1649b-123">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1649b-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1649b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="1649b-124">Example</span></span>  
 <span data-ttu-id="1649b-125">Aşağıdaki örnek, bir `Integer` değişkeninin bit modelini belirtilen miktarda sağa kaydırmak ve sonucu değişkenine atamak için `>>=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1649b-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="1649b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1649b-126">See also</span></span>

- [<span data-ttu-id="1649b-127">>> İşleci</span><span class="sxs-lookup"><span data-stu-id="1649b-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="1649b-128">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1649b-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="1649b-129">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1649b-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="1649b-130">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="1649b-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1649b-131">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="1649b-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1649b-132">Deyimler</span><span class="sxs-lookup"><span data-stu-id="1649b-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
