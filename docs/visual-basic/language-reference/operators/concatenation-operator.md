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
ms.openlocfilehash: 20c2e2088691e68221872cc1dfc5486413515a4d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867151"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="f657c-102">&amp; İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f657c-102">&amp; Operator (Visual Basic)</span></span>

<span data-ttu-id="f657c-103">İki ifadenin dize birleştirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f657c-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f657c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f657c-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f657c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f657c-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="f657c-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f657c-106">Required.</span></span> <span data-ttu-id="f657c-107">Herhangi bir `String` veya `Object` değişken.</span><span class="sxs-lookup"><span data-stu-id="f657c-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f657c-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f657c-108">Required.</span></span> <span data-ttu-id="f657c-109">Widens tarafından kullanılan bir veri türüne sahip herhangi bir ifade `String` .</span><span class="sxs-lookup"><span data-stu-id="f657c-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f657c-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f657c-110">Required.</span></span> <span data-ttu-id="f657c-111">Widens tarafından kullanılan bir veri türüne sahip herhangi bir ifade `String` .</span><span class="sxs-lookup"><span data-stu-id="f657c-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f657c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f657c-112">Remarks</span></span>  

 <span data-ttu-id="f657c-113">Veya veri türü `expression1` `expression2` değilse `String` , ancak widens ise `String` , öğesine dönüştürülür `String` .</span><span class="sxs-lookup"><span data-stu-id="f657c-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="f657c-114">Veri türlerinden biri olarak genişlemezse `String` , derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f657c-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="f657c-115">Veri türü `result` `String` .</span><span class="sxs-lookup"><span data-stu-id="f657c-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="f657c-116">Bir veya her iki ifade bir [Nothing](../nothing.md) olarak değerlendirilir veya bir değerine sahip olursa <xref:System.DBNull.Value?displayProperty=nameWithType> , "" değerine sahip bir dize olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f657c-116">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f657c-117">`&`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f657c-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f657c-118">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f657c-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f657c-119">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f657c-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f657c-120">Ve (&) karakteri değişkenleri tür olarak tanımlamak için de kullanılabilir `Long` .</span><span class="sxs-lookup"><span data-stu-id="f657c-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="f657c-121">Daha fazla bilgi için bkz. [tür karakterleri](../../programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="f657c-121">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f657c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f657c-122">Example</span></span>  

 <span data-ttu-id="f657c-123">Bu örnek, `&` dize birleştirmesini zorlamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f657c-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="f657c-124">Sonuç iki dize işleneninin birleştirilmesiyle temsil eden bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="f657c-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f657c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f657c-125">See also</span></span>

- [<span data-ttu-id="f657c-126">&= Işleci</span><span class="sxs-lookup"><span data-stu-id="f657c-126">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="f657c-127">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f657c-127">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="f657c-128">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="f657c-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f657c-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="f657c-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f657c-130">Visual Basic'de Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f657c-130">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
