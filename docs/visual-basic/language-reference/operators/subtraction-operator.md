---
title: '- İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 8526f632b7e54c03bd16c3af70375179cd7cf277
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724479"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="46608-102">- İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46608-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="46608-103">İki sayısal ifadeye veya sayısal bir ifadenin negatif değerini arasındaki farkı döndürür.</span><span class="sxs-lookup"><span data-stu-id="46608-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46608-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46608-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="46608-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="46608-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="46608-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46608-106">Required.</span></span> <span data-ttu-id="46608-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="46608-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="46608-108">Sürece gerekli `–` işleci, negatif bir değer hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="46608-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="46608-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="46608-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="46608-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="46608-110">Result</span></span>  
 <span data-ttu-id="46608-111">Sonuç arasındaki farktır `expression1` ve `expression2`, ya da eksi değeri kadar çevrilerek `expression1`.</span><span class="sxs-lookup"><span data-stu-id="46608-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="46608-112">Sonuç veri türü olan veri türleri için uygun bir sayısal tür `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="46608-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="46608-113">"Tamsayı aritmetik" tablolarında bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="46608-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="46608-114">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="46608-114">Supported Types</span></span>  
 <span data-ttu-id="46608-115">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="46608-115">All numeric types.</span></span> <span data-ttu-id="46608-116">Bu imzalanmamış ve kayan nokta türlerini içerir ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="46608-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46608-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46608-117">Remarks</span></span>  
 <span data-ttu-id="46608-118">Daha önce gösterilen sözdiziminde gösterilen ilk kullanımında `–` işleci *ikili* aritmetik çıkarma işleci iki sayısal ifade arasındaki farkı.</span><span class="sxs-lookup"><span data-stu-id="46608-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="46608-119">Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımı `–` işleci *birli* değilleme işleci bir ifadenin negatif değerini için.</span><span class="sxs-lookup"><span data-stu-id="46608-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="46608-120">Bu anlamda işareti ters olan olumsuzlama oluşur `expression1` sonuç pozitif olur böylece varsa `expression1` negatiftir.</span><span class="sxs-lookup"><span data-stu-id="46608-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="46608-121">Her iki ifade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), `–` işleci, sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="46608-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46608-122">`–` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46608-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="46608-123">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="46608-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="46608-124">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="46608-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46608-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="46608-125">Example</span></span>  
 <span data-ttu-id="46608-126">Aşağıdaki örnekte `–` hesaplamak ve iki sayı arasındaki farkı döndürmek için işleç ve bir sayı negatif yapılacak.</span><span class="sxs-lookup"><span data-stu-id="46608-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="46608-127">Bu deyimler yürütülmesinin `binaryResult` 124.45 içerir ve `unaryResult` –334.90 içerir.</span><span class="sxs-lookup"><span data-stu-id="46608-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46608-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46608-128">See also</span></span>
- [<span data-ttu-id="46608-129">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46608-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="46608-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="46608-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="46608-131">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="46608-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="46608-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="46608-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="46608-133">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="46608-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
