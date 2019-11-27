---
title: <<= İşleci
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
ms.openlocfilehash: cc89e0dadc7148b21e695a53a2e746a00ed66441
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350951"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2434a-102">\<\<= Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2434a-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="2434a-103">Bir değişkenin veya özelliğin değerinde aritmetik sola kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="2434a-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2434a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2434a-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="2434a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2434a-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2434a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2434a-106">Required.</span></span> <span data-ttu-id="2434a-107">İntegral türünün değişkeni veya özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`).</span><span class="sxs-lookup"><span data-stu-id="2434a-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="2434a-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2434a-108">Required.</span></span> <span data-ttu-id="2434a-109">`Integer`için widens bir veri türünün sayısal ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2434a-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2434a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2434a-110">Remarks</span></span>  
 <span data-ttu-id="2434a-111">`<<=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="2434a-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2434a-112">Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="2434a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="2434a-113">`<<=` işleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sola kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2434a-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="2434a-114">İşleci daha sonra bu işlemin sonucunu bu değişkene veya özelliğe yeniden atar.</span><span class="sxs-lookup"><span data-stu-id="2434a-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="2434a-115">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2434a-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="2434a-116">Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2434a-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2434a-117">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="2434a-117">Overloading</span></span>  
 <span data-ttu-id="2434a-118">[< < işleci](../../../visual-basic/language-reference/operators/left-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2434a-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2434a-119">`<<` işleci aşırı yükleme `<<=` işlecinin davranışını etkiler.</span><span class="sxs-lookup"><span data-stu-id="2434a-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="2434a-120">Kodunuz, `<<`aşırı yükleyen bir sınıf veya yapı üzerinde `<<=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2434a-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2434a-121">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2434a-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2434a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="2434a-122">Example</span></span>  
 <span data-ttu-id="2434a-123">Aşağıdaki örnek, bir `Integer` değişkeninin bit modelini belirtilen miktarda sola kaydırmak ve sonucu değişkenine atamak için `<<=` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2434a-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="2434a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2434a-124">See also</span></span>

- [<span data-ttu-id="2434a-125"><< İşleci</span><span class="sxs-lookup"><span data-stu-id="2434a-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="2434a-126">Atama İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2434a-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="2434a-127">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2434a-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="2434a-128">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="2434a-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2434a-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="2434a-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2434a-130">Deyimler</span><span class="sxs-lookup"><span data-stu-id="2434a-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
