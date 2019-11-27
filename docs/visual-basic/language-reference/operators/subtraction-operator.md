---
title: '- İşleç'
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
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348219"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="516be-102">- İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="516be-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="516be-103">İki sayısal ifade arasındaki farkı ya da sayısal bir ifadenin negatif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="516be-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="516be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="516be-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="516be-105">veya</span><span class="sxs-lookup"><span data-stu-id="516be-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="516be-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="516be-106">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="516be-107">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="516be-107">Required.</span></span> <span data-ttu-id="516be-108">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="516be-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="516be-109">`–` işleci negatif bir değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="516be-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="516be-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="516be-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="516be-111">Sonuç</span><span class="sxs-lookup"><span data-stu-id="516be-111">Result</span></span>  
 <span data-ttu-id="516be-112">Sonuç, `expression1` ve `expression2`ya da `expression1`'in nelenmiş değeri arasındaki farktır.</span><span class="sxs-lookup"><span data-stu-id="516be-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="516be-113">Sonuç veri türü, `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür.</span><span class="sxs-lookup"><span data-stu-id="516be-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="516be-114">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="516be-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="516be-115">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="516be-115">Supported Types</span></span>  
 <span data-ttu-id="516be-116">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="516be-116">All numeric types.</span></span> <span data-ttu-id="516be-117">Bu, işaretsiz ve kayan nokta türlerini ve `Decimal`içerir.</span><span class="sxs-lookup"><span data-stu-id="516be-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="516be-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="516be-118">Remarks</span></span>  
 <span data-ttu-id="516be-119">Daha önce gösterilen sözdiziminde gösterilen ilk kullanımlarda, `–` işleci iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçidir.</span><span class="sxs-lookup"><span data-stu-id="516be-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="516be-120">Daha önce gösterilen sözdiziminde gösterilen ikinci kullanım için `–` işleci, bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir.</span><span class="sxs-lookup"><span data-stu-id="516be-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="516be-121">Bu anlamda olumsuzlama, `expression1` negatifse, sonucun pozitif olması için `expression1` işaretini ters çevirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="516be-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="516be-122">Her iki ifade de [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, `–` işleci onu sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="516be-122">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="516be-123">`–` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="516be-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="516be-124">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="516be-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="516be-125">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="516be-125">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="516be-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="516be-126">Example</span></span>  
 <span data-ttu-id="516be-127">Aşağıdaki örnek iki sayı arasındaki farkı hesaplamak ve döndürmek için `–` işlecini, sonra da bir sayıyı bir sayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="516be-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="516be-128">Bu deyimlerin yürütülmesini izleyerek `binaryResult` 124,45 ve `unaryResult` içerir – 334,90.</span><span class="sxs-lookup"><span data-stu-id="516be-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516be-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="516be-129">See also</span></span>

- [<span data-ttu-id="516be-130">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="516be-130">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="516be-131">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="516be-131">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="516be-132">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="516be-132">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="516be-133">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="516be-133">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="516be-134">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="516be-134">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
