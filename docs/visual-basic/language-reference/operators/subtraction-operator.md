---
title: '- İşleç (Visual Basic)'
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
ms.openlocfilehash: eb34b34986613f36b624c43c04f98390ffba4fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965860"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="721d6-102">- İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="721d6-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="721d6-103">İki sayısal ifade arasındaki farkı ya da sayısal bir ifadenin negatif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="721d6-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="721d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="721d6-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="721d6-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="721d6-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="721d6-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="721d6-106">Required.</span></span> <span data-ttu-id="721d6-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="721d6-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="721d6-108">İşleç negatif bir `–` değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="721d6-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="721d6-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="721d6-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="721d6-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="721d6-110">Result</span></span>  
 <span data-ttu-id="721d6-111">Sonuç, ile `expression2`veya arasında bir `expression1` `expression1`değer arasındaki farktır.</span><span class="sxs-lookup"><span data-stu-id="721d6-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="721d6-112">Sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür.</span><span class="sxs-lookup"><span data-stu-id="721d6-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="721d6-113">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="721d6-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="721d6-114">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="721d6-114">Supported Types</span></span>  
 <span data-ttu-id="721d6-115">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="721d6-115">All numeric types.</span></span> <span data-ttu-id="721d6-116">Bu, imzasız ve kayan nokta türlerini `Decimal`içerir.</span><span class="sxs-lookup"><span data-stu-id="721d6-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="721d6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="721d6-117">Remarks</span></span>  
 <span data-ttu-id="721d6-118">Daha önce `–` Gösterilen sözdiziminde gösterilen ilk kullanımlarda işleç, iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçidir.</span><span class="sxs-lookup"><span data-stu-id="721d6-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="721d6-119">Daha önce `–` Gösterilen sözdiziminde gösterilen ikinci kullanımda işleci, bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir.</span><span class="sxs-lookup"><span data-stu-id="721d6-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="721d6-120">Bu anlamda olumsuzlama, negatif ise sonucun `expression1` `expression1` pozitif olması için işaretini tersine döndürdükten oluşur.</span><span class="sxs-lookup"><span data-stu-id="721d6-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="721d6-121">Her iki ifade de [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilirse, `–` işleç onu sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="721d6-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="721d6-122">İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `–`</span><span class="sxs-lookup"><span data-stu-id="721d6-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="721d6-123">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="721d6-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="721d6-124">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="721d6-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="721d6-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="721d6-125">Example</span></span>  
 <span data-ttu-id="721d6-126">Aşağıdaki örnek `–` , iki sayı arasındaki farkı hesaplamak ve döndürmek için işlecini ve sonra bir sayıyı bir sayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="721d6-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="721d6-127">Bu deyimlerin `binaryResult` yürütülmesi sonrasında 124,45 ve `unaryResult` içerir – 334,90 içerir.</span><span class="sxs-lookup"><span data-stu-id="721d6-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="721d6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="721d6-128">See also</span></span>

- [<span data-ttu-id="721d6-129">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="721d6-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="721d6-130">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="721d6-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="721d6-131">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="721d6-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="721d6-132">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="721d6-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="721d6-133">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="721d6-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
