---
title: "- İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ffb7c96fe95e73dc857a15608df94ed8468f9df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="4db21-102">- İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4db21-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="4db21-103">İki sayısal ifadeye veya sayısal bir ifadenin negatif değerini arasındaki farkı döndürür.</span><span class="sxs-lookup"><span data-stu-id="4db21-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4db21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4db21-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="4db21-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4db21-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="4db21-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4db21-106">Required.</span></span> <span data-ttu-id="4db21-107">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="4db21-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="4db21-108">Sürece gerekli `–` işleci negatif bir değer hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="4db21-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="4db21-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="4db21-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="4db21-110">Sonuç</span><span class="sxs-lookup"><span data-stu-id="4db21-110">Result</span></span>  
 <span data-ttu-id="4db21-111">Sonuç arasındaki farktır `expression1` ve `expression2`, veya eksi değeri kadar çevrilerek `expression1`.</span><span class="sxs-lookup"><span data-stu-id="4db21-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="4db21-112">Sonuç veri türü sayısal bir tür veri türleri için uygun değil `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="4db21-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="4db21-113">"Tamsayı aritmetiğini" tablolarda bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="4db21-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="4db21-114">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="4db21-114">Supported Types</span></span>  
 <span data-ttu-id="4db21-115">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="4db21-115">All numeric types.</span></span> <span data-ttu-id="4db21-116">Bu imzasız ve kayan nokta türleri içerir ve `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4db21-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4db21-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4db21-117">Remarks</span></span>  
 <span data-ttu-id="4db21-118">Daha önce gösterilen sözdiziminde gösterilen ilk kullanımında `–` işlecidir *ikili* iki sayısal ifadeye arasındaki farkı aritmetik çıkarma işleci.</span><span class="sxs-lookup"><span data-stu-id="4db21-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="4db21-119">Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımı `–` işlecidir *birli* bir ifadenin negatif değerini değilleme işleci.</span><span class="sxs-lookup"><span data-stu-id="4db21-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="4db21-120">Bu anlamda işaretini ters değilleme oluşur `expression1` sonucu pozitif olmasını sağlamak, `expression1` negatiftir.</span><span class="sxs-lookup"><span data-stu-id="4db21-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="4db21-121">Ya da ifade değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), `–` işleci, sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4db21-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4db21-122">`–` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4db21-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4db21-123">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4db21-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="4db21-124">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4db21-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4db21-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="4db21-125">Example</span></span>  
 <span data-ttu-id="4db21-126">Aşağıdaki örnek kullanır `–` hesaplamak ve iki sayı arasındaki farkı dönmek için işleci ve ardından bir sayı negate.</span><span class="sxs-lookup"><span data-stu-id="4db21-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="4db21-127">Bu deyimler yürütülmesinin `binaryResult` 124.45 içerir ve `unaryResult` –334.90 içerir.</span><span class="sxs-lookup"><span data-stu-id="4db21-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db21-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4db21-128">See Also</span></span>  
 <span data-ttu-id="4db21-129">[-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="4db21-129">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span></span>  
 [<span data-ttu-id="4db21-130">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="4db21-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="4db21-131">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="4db21-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="4db21-132">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="4db21-132">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
