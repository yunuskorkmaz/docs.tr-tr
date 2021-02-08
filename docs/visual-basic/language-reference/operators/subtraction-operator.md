---
description: Daha fazla bilgi edinin:-Işleci (Visual Basic)
title: '- Operatör'
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
ms.openlocfilehash: 858e887fa7c5c0cc6129996c98bddb78bc53045c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795267"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="913c6-103">- İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="913c6-103">- Operator (Visual Basic)</span></span>

<span data-ttu-id="913c6-104">İki sayısal ifade arasındaki farkı ya da sayısal bir ifadenin negatif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="913c6-104">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="913c6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="913c6-105">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="913c6-106">veya</span><span class="sxs-lookup"><span data-stu-id="913c6-106">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="913c6-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="913c6-107">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="913c6-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="913c6-108">Required.</span></span> <span data-ttu-id="913c6-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="913c6-109">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="913c6-110">`–`İşleç negatif bir değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="913c6-110">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="913c6-111">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="913c6-111">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="913c6-112">Sonuç</span><span class="sxs-lookup"><span data-stu-id="913c6-112">Result</span></span>  

 <span data-ttu-id="913c6-113">Sonuç, `expression1` ile veya arasında bir değer arasındaki farktır `expression2` `expression1` .</span><span class="sxs-lookup"><span data-stu-id="913c6-113">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="913c6-114">Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="913c6-114">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="913c6-115">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="913c6-115">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="913c6-116">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="913c6-116">Supported Types</span></span>  

 <span data-ttu-id="913c6-117">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="913c6-117">All numeric types.</span></span> <span data-ttu-id="913c6-118">Bu, imzasız ve kayan nokta türlerini içerir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="913c6-118">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="913c6-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="913c6-119">Remarks</span></span>  

 <span data-ttu-id="913c6-120">Daha önce gösterilen sözdiziminde gösterilen ilk kullanımlarda `–` işleç, iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçidir.</span><span class="sxs-lookup"><span data-stu-id="913c6-120">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="913c6-121">Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımda `–` işleci, bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir.</span><span class="sxs-lookup"><span data-stu-id="913c6-121">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="913c6-122">Bu anlamda olumsuzlama, negatif ise sonucun pozitif olması için işaretini tersine döndürdükten oluşur `expression1` `expression1` .</span><span class="sxs-lookup"><span data-stu-id="913c6-122">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="913c6-123">Her iki ifade de [Nothing](../nothing.md)olarak değerlendirilirse, `–` işleç onu sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="913c6-123">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="913c6-124">`–`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="913c6-124">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="913c6-125">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="913c6-125">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="913c6-126">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="913c6-126">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="913c6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="913c6-127">Example</span></span>  

 <span data-ttu-id="913c6-128">Aşağıdaki örnek, `–` iki sayı arasındaki farkı hesaplamak ve döndürmek için işlecini ve sonra bir sayıyı bir sayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="913c6-128">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="913c6-129">Bu deyimlerin yürütülmesi sonrasında `binaryResult` 124,45 ve `unaryResult` içerir – 334,90 içerir.</span><span class="sxs-lookup"><span data-stu-id="913c6-129">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913c6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="913c6-130">See also</span></span>

- [<span data-ttu-id="913c6-131">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="913c6-131">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="913c6-132">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="913c6-132">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="913c6-133">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="913c6-133">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="913c6-134">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="913c6-134">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="913c6-135">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="913c6-135">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
