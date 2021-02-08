---
description: 'Hakkında daha fazla bilgi edinin:  >>= Işleci (Visual Basic)'
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
ms.openlocfilehash: 80f614042403ad9179de0025b289bd83c71008b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795319"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1998d-103">>>= Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1998d-103">>>= Operator (Visual Basic)</span></span>

<span data-ttu-id="1998d-104">Bir değişkenin veya özelliğin değerinde aritmetik sağa kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="1998d-104">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1998d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1998d-105">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1998d-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1998d-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="1998d-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1998d-107">Required.</span></span> <span data-ttu-id="1998d-108">İntegral türünün değişkeni veya özelliği ( `SByte` ,,, `Byte` `Short` `UShort` , `Integer` , `UInteger` , `Long` , veya `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="1998d-108">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1998d-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1998d-109">Required.</span></span> <span data-ttu-id="1998d-110">Widens tarafından kullanılan bir veri türünün sayısal ifadesi `Integer` .</span><span class="sxs-lookup"><span data-stu-id="1998d-110">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1998d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1998d-111">Remarks</span></span>  

 <span data-ttu-id="1998d-112">İşlecinin sol tarafındaki öğesi `>>=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1998d-112">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1998d-113">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="1998d-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1998d-114">`>>=`İşleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sağa kaydırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1998d-114">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="1998d-115">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="1998d-115">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="1998d-116">Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1998d-116">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1998d-117">Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki bit, sol taraftaki bit konumlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="1998d-117">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1998d-118">Yani `variableorproperty` negatif bir değer varsa, karıştırılmış konumlar bir olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1998d-118">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="1998d-119">`variableorproperty`Pozitif ise veya veri türü işaretsiz bir tür ise, karıştırılmış konumlar sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1998d-119">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1998d-120">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="1998d-120">Overloading</span></span>  

 <span data-ttu-id="1998d-121">[>> işleci](right-shift-operator.md) *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1998d-121">The [>> Operator](right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1998d-122">İşleci aşırı yüklemek `>>` işlecin davranışını etkiler `>>=` .</span><span class="sxs-lookup"><span data-stu-id="1998d-122">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="1998d-123">Kodunuzun `>>=` bir sınıf veya yapı üzerinde kullanması durumunda `>>` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1998d-123">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1998d-124">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1998d-124">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1998d-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="1998d-125">Example</span></span>  

 <span data-ttu-id="1998d-126">Aşağıdaki örnek, `>>=` bir değişkenin bit modelini `Integer` belirtilen miktarda sağa kaydırmak ve sonucu değişkenine atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1998d-126">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="1998d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1998d-127">See also</span></span>

- [<span data-ttu-id="1998d-128">>> Işleci</span><span class="sxs-lookup"><span data-stu-id="1998d-128">>> Operator</span></span>](right-shift-operator.md)
- [<span data-ttu-id="1998d-129">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="1998d-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="1998d-130">Bit Kaydırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="1998d-130">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="1998d-131">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="1998d-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1998d-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="1998d-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1998d-133">Deyimler</span><span class="sxs-lookup"><span data-stu-id="1998d-133">Statements</span></span>](../../programming-guide/language-features/statements.md)
