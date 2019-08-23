---
title: '&amp;İşleç (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968350"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="c737a-102">&amp;İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c737a-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="c737a-103">İki ifadenin dize birleştirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c737a-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c737a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c737a-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c737a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c737a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="c737a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c737a-106">Required.</span></span> <span data-ttu-id="c737a-107">Herhangi `String` bir `Object` veya değişken.</span><span class="sxs-lookup"><span data-stu-id="c737a-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="c737a-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c737a-108">Required.</span></span> <span data-ttu-id="c737a-109">Widens tarafından kullanılan bir veri türüne sahip herhangi bir `String`ifade.</span><span class="sxs-lookup"><span data-stu-id="c737a-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="c737a-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c737a-110">Required.</span></span> <span data-ttu-id="c737a-111">Widens tarafından kullanılan bir veri türüne sahip herhangi bir `String`ifade.</span><span class="sxs-lookup"><span data-stu-id="c737a-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c737a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c737a-112">Remarks</span></span>  
 <span data-ttu-id="c737a-113">`expression1` `String` `String`Veya veri türü değilse`String` , ancak widens ise, öğesine dönüştürülür. `expression2`</span><span class="sxs-lookup"><span data-stu-id="c737a-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="c737a-114">Veri türlerinden biri olarak `String`genişlemezse, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c737a-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="c737a-115">Veri türü `result`. `String`</span><span class="sxs-lookup"><span data-stu-id="c737a-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="c737a-116">Bir veya her iki ifade bir [Nothing](../../../visual-basic/language-reference/nothing.md) olarak değerlendirilir veya bir değerine <xref:System.DBNull.Value?displayProperty=nameWithType>sahip olursa, "" değerine sahip bir dize olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c737a-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c737a-117">İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `&`</span><span class="sxs-lookup"><span data-stu-id="c737a-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c737a-118">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c737a-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c737a-119">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c737a-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c737a-120">Ve (&) karakteri değişkenleri tür `Long`olarak tanımlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c737a-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="c737a-121">Daha fazla bilgi için bkz. [tür karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="c737a-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c737a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c737a-122">Example</span></span>  
 <span data-ttu-id="c737a-123">Bu örnek, `&` dize birleştirmesini zorlamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c737a-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="c737a-124">Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="c737a-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c737a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c737a-125">See also</span></span>

- [<span data-ttu-id="c737a-126">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="c737a-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="c737a-127">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c737a-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="c737a-128">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="c737a-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c737a-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="c737a-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c737a-130">Visual Basic birleştirme Işleçleri</span><span class="sxs-lookup"><span data-stu-id="c737a-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
