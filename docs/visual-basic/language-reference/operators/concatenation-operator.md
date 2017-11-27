---
title: "&amp;İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="3d73b-102">&amp;İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d73b-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="3d73b-103">İki ifadenin dize birleştirmesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d73b-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d73b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d73b-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="3d73b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3d73b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="3d73b-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3d73b-106">Required.</span></span> <span data-ttu-id="3d73b-107">Tüm `String` veya `Object` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="3d73b-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="3d73b-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3d73b-108">Required.</span></span> <span data-ttu-id="3d73b-109">İçin widens bir veri türüne sahip herhangi bir ifade `String`.</span><span class="sxs-lookup"><span data-stu-id="3d73b-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="3d73b-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3d73b-110">Required.</span></span> <span data-ttu-id="3d73b-111">İçin widens bir veri türüne sahip herhangi bir ifade `String`.</span><span class="sxs-lookup"><span data-stu-id="3d73b-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d73b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d73b-112">Remarks</span></span>  
 <span data-ttu-id="3d73b-113">Veri türü `expression1` veya `expression2` değil `String` ancak için widens `String`, dönüştürülmeden `String`.</span><span class="sxs-lookup"><span data-stu-id="3d73b-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="3d73b-114">Veri türlerinden birini değil genişletmek için `String`, derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3d73b-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="3d73b-115">Veri türü `result` olan `String`.</span><span class="sxs-lookup"><span data-stu-id="3d73b-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="3d73b-116">İçin bir veya iki ifade değerlendirin varsa [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya değerine sahip <xref:System.DBNull.Value?displayProperty=nameWithType>, değerini bir dize olarak kabul edilir "".</span><span class="sxs-lookup"><span data-stu-id="3d73b-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d73b-117">`&` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3d73b-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3d73b-118">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3d73b-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3d73b-119">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3d73b-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d73b-120">(&) Karakteri de değişkenleri türü olarak tanımlamak için kullanılabilir `Long`.</span><span class="sxs-lookup"><span data-stu-id="3d73b-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="3d73b-121">Daha fazla bilgi için bkz: [türü karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="3d73b-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d73b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d73b-122">Example</span></span>  
 <span data-ttu-id="3d73b-123">Bu örnekte `&` dize birleştirme zorlamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="3d73b-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="3d73b-124">Sonuç, iki dize işlenenleri birleşimini temsil eden bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="3d73b-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3d73b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d73b-125">See Also</span></span>  
 [<span data-ttu-id="3d73b-126">& = işleci</span><span class="sxs-lookup"><span data-stu-id="3d73b-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="3d73b-127">Birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="3d73b-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="3d73b-128">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="3d73b-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="3d73b-129">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="3d73b-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="3d73b-130">Visual Basic'de birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="3d73b-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
