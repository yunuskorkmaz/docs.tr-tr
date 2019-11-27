---
title: '&amp; İşleci'
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
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336052"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="0656a-102">&amp; Işleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0656a-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="0656a-103">İki ifadenin dize birleştirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0656a-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0656a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0656a-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0656a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0656a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0656a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0656a-106">Required.</span></span> <span data-ttu-id="0656a-107">Herhangi bir `String` veya `Object` değişken.</span><span class="sxs-lookup"><span data-stu-id="0656a-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="0656a-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0656a-108">Required.</span></span> <span data-ttu-id="0656a-109">`String`bir veri türüne sahip herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0656a-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0656a-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0656a-110">Required.</span></span> <span data-ttu-id="0656a-111">`String`bir veri türüne sahip herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0656a-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0656a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0656a-112">Remarks</span></span>  
 <span data-ttu-id="0656a-113">`expression1` veya `expression2` veri türü `String` değilse ancak `String`için ise, `String`dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="0656a-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="0656a-114">Veri türlerinden biri `String`olarak genişlemezse, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0656a-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="0656a-115">`result` veri türü `String`.</span><span class="sxs-lookup"><span data-stu-id="0656a-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="0656a-116">Bir veya her iki ifade bir [Nothing](../../../visual-basic/language-reference/nothing.md) olarak değerlendirilir veya <xref:System.DBNull.Value?displayProperty=nameWithType>bir değere sahip olursa, "" değerine sahip bir dize olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0656a-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0656a-117">`&` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0656a-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0656a-118">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0656a-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0656a-119">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0656a-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0656a-120">Ampersan (&) karakteri, değişkenleri tür `Long`olarak belirlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0656a-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="0656a-121">Daha fazla bilgi için bkz. [tür karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="0656a-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0656a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="0656a-122">Example</span></span>  
 <span data-ttu-id="0656a-123">Bu örnek, dize birleştirmesini zorlamak için `&` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0656a-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="0656a-124">Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="0656a-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0656a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0656a-125">See also</span></span>

- [<span data-ttu-id="0656a-126">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="0656a-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="0656a-127">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="0656a-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="0656a-128">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="0656a-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0656a-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="0656a-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0656a-130">Visual Basic birleştirme Işleçleri</span><span class="sxs-lookup"><span data-stu-id="0656a-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
