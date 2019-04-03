---
title: '&amp; İşleci (Visual Basic)'
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
ms.openlocfilehash: dd85363447e9b405241d608550d9484b4760a739
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817285"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="be58f-102">&amp; İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be58f-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="be58f-103">İki ifadenin dize birleştirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be58f-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be58f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be58f-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="be58f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="be58f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="be58f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="be58f-106">Required.</span></span> <span data-ttu-id="be58f-107">Tüm `String` veya `Object` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="be58f-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="be58f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="be58f-108">Required.</span></span> <span data-ttu-id="be58f-109">Herhangi bir ifade bir veri türüyle için widens `String`.</span><span class="sxs-lookup"><span data-stu-id="be58f-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="be58f-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="be58f-110">Required.</span></span> <span data-ttu-id="be58f-111">Herhangi bir ifade bir veri türüyle için widens `String`.</span><span class="sxs-lookup"><span data-stu-id="be58f-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be58f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be58f-112">Remarks</span></span>  
 <span data-ttu-id="be58f-113">Veri türü `expression1` veya `expression2` değil `String` ancak için widens `String`, dönüştürülür `String`.</span><span class="sxs-lookup"><span data-stu-id="be58f-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="be58f-114">Veri türlerinden birini değil genişletmek için `String`, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be58f-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="be58f-115">Veri türü `result` olduğu `String`.</span><span class="sxs-lookup"><span data-stu-id="be58f-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="be58f-116">Bir veya iki ifadeleri sonucunu verirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya bir değere sahip <xref:System.DBNull.Value?displayProperty=nameWithType>, değerini içeren bir dize olarak kabul edilir "".</span><span class="sxs-lookup"><span data-stu-id="be58f-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be58f-117">`&` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="be58f-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="be58f-118">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="be58f-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="be58f-119">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="be58f-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be58f-120">(&) Karakteri de değişken türü olarak tanımlamak için kullanılabilir `Long`.</span><span class="sxs-lookup"><span data-stu-id="be58f-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="be58f-121">Daha fazla bilgi için [tür karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="be58f-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be58f-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="be58f-122">Example</span></span>  
 <span data-ttu-id="be58f-123">Bu örnekte `&` dize birleştirme zorlamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="be58f-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="be58f-124">Sonucu, iki dizeyi işlenenlere birleşimi temsil eden bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="be58f-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="be58f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be58f-125">See also</span></span>

- [<span data-ttu-id="be58f-126">&= İşleci</span><span class="sxs-lookup"><span data-stu-id="be58f-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="be58f-127">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="be58f-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="be58f-128">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="be58f-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="be58f-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="be58f-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="be58f-130">Visual Basic'de birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="be58f-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
