---
title: "Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02083a93e63fe799f529776f777ca877d2d138b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="47a82-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47a82-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="47a82-103">İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], her iki değişken aynı sınıfı örneğini bellekte noktası iki değişken başvuruları kendi işaretçileri, diğer bir deyişle, aynıysa aynı değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="47a82-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="47a82-104">Örneğin, bir Windows Forms uygulamasında, belirlemek için bir karşılaştırma yapmak isteyebilirsiniz olup olmadığını geçerli örneğini (`Me`) belirli bir örneği ile aynı olduğu gibi `Form2`.</span><span class="sxs-lookup"><span data-stu-id="47a82-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="47a82-105">iki işleç işaretçilerini karşılaştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="47a82-105"> provides two operators to compare pointers.</span></span> <span data-ttu-id="47a82-106">[Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) döndürür `True` nesneleri özdeş ise ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) döndürür `True` değillerse.</span><span class="sxs-lookup"><span data-stu-id="47a82-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="47a82-107">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="47a82-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="47a82-108">İki nesnenin aynı olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="47a82-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="47a82-109">Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.</span><span class="sxs-lookup"><span data-stu-id="47a82-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="47a82-110">Sınama İfadenizde kullanmak `Is` işlenen olarak iki nesnenin işleç.</span><span class="sxs-lookup"><span data-stu-id="47a82-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="47a82-111">`Is`döndürür `True` nesneleri aynı sınıf örneğine noktası.</span><span class="sxs-lookup"><span data-stu-id="47a82-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="47a82-112">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="47a82-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="47a82-113">İki nesnenin aynı değilseniz ve birleştirmek garip olabilir bir eylem gerçekleştirmek istediğiniz bazen `Not` ve `Is`, örneğin `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="47a82-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="47a82-114">Böyle bir durumda kullandığınız `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="47a82-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="47a82-115">İki nesnenin aynı olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="47a82-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="47a82-116">Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.</span><span class="sxs-lookup"><span data-stu-id="47a82-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="47a82-117">Sınama İfadenizde kullanmak `IsNot` işlenen olarak iki nesnenin işleç.</span><span class="sxs-lookup"><span data-stu-id="47a82-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="47a82-118">`IsNot`döndürür `True` nesneleri aynı sınıfı örneğini işaret etmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="47a82-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47a82-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="47a82-119">Example</span></span>  
 <span data-ttu-id="47a82-120">Aşağıdaki örnek çiftlerini testleri `Object` aynı sınıf örneğine noktası görmek için değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="47a82-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="47a82-121">Önceki örnekte, aşağıdaki çıkış görüntüler.</span><span class="sxs-lookup"><span data-stu-id="47a82-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="47a82-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47a82-122">See Also</span></span>  
 [<span data-ttu-id="47a82-123">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="47a82-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="47a82-124">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="47a82-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="47a82-125">Nesne değişkeni değerleri</span><span class="sxs-lookup"><span data-stu-id="47a82-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="47a82-126">Is işleci</span><span class="sxs-lookup"><span data-stu-id="47a82-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="47a82-127">IsNot işleci</span><span class="sxs-lookup"><span data-stu-id="47a82-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="47a82-128">Nasıl yapılır: iki nesnenin ilgili olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="47a82-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="47a82-129">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="47a82-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
