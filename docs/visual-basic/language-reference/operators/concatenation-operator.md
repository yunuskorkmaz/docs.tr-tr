---
description: ': İşleci hakkında daha fazla bilgi edinin &amp; (Visual Basic)'
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
ms.openlocfilehash: ba7c94805e805c841d05241fef557ca972a19ae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774102"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="8b8ca-103">&amp; İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b8ca-103">&amp; Operator (Visual Basic)</span></span>

<span data-ttu-id="8b8ca-104">İki ifadenin dize birleştirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-104">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b8ca-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b8ca-105">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="8b8ca-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8b8ca-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="8b8ca-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-107">Required.</span></span> <span data-ttu-id="8b8ca-108">Herhangi bir `String` veya `Object` değişken.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-108">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="8b8ca-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-109">Required.</span></span> <span data-ttu-id="8b8ca-110">Widens tarafından kullanılan bir veri türüne sahip herhangi bir ifade `String` .</span><span class="sxs-lookup"><span data-stu-id="8b8ca-110">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="8b8ca-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-111">Required.</span></span> <span data-ttu-id="8b8ca-112">Widens tarafından kullanılan bir veri türüne sahip herhangi bir ifade `String` .</span><span class="sxs-lookup"><span data-stu-id="8b8ca-112">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b8ca-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b8ca-113">Remarks</span></span>  

 <span data-ttu-id="8b8ca-114">Veya veri türü `expression1` `expression2` değilse `String` , ancak widens ise `String` , öğesine dönüştürülür `String` .</span><span class="sxs-lookup"><span data-stu-id="8b8ca-114">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="8b8ca-115">Veri türlerinden biri olarak genişlemezse `String` , derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-115">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="8b8ca-116">Veri türü `result` `String` .</span><span class="sxs-lookup"><span data-stu-id="8b8ca-116">The data type of `result` is `String`.</span></span> <span data-ttu-id="8b8ca-117">Bir veya her iki ifade bir [Nothing](../nothing.md) olarak değerlendirilir veya bir değerine sahip olursa <xref:System.DBNull.Value?displayProperty=nameWithType> , "" değerine sahip bir dize olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-117">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b8ca-118">`&`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-118">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8b8ca-119">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8b8ca-120">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8b8ca-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b8ca-121">Ve (&) karakteri değişkenleri tür olarak tanımlamak için de kullanılabilir `Long` .</span><span class="sxs-lookup"><span data-stu-id="8b8ca-121">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="8b8ca-122">Daha fazla bilgi için bkz. [tür karakterleri](../../programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="8b8ca-122">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b8ca-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b8ca-123">Example</span></span>  

 <span data-ttu-id="8b8ca-124">Bu örnek, `&` dize birleştirmesini zorlamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-124">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="8b8ca-125">Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-125">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8b8ca-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b8ca-126">See also</span></span>

- [<span data-ttu-id="8b8ca-127">&= Işleci</span><span class="sxs-lookup"><span data-stu-id="8b8ca-127">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="8b8ca-128">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8b8ca-128">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="8b8ca-129">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="8b8ca-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="8b8ca-130">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="8b8ca-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="8b8ca-131">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8b8ca-131">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
