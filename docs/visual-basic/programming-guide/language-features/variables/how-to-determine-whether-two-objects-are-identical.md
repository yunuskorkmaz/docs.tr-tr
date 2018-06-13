---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: bbcac2fc51e57427b125ec2f5e68f017a60186d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650104"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="f6978-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6978-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="f6978-103">Visual Basic'te aynı sınıfı örneğini bellekte her iki değişken noktası iki değişken başvuruları kendi işaretçileri, diğer bir deyişle, aynıysa aynı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f6978-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="f6978-104">Örneğin, bir Windows Forms uygulamasında, belirlemek için bir karşılaştırma yapmak isteyebilirsiniz olup olmadığını geçerli örneğini (`Me`) belirli bir örneği ile aynı olduğu gibi `Form2`.</span><span class="sxs-lookup"><span data-stu-id="f6978-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="f6978-105">Visual Basic iki işleç işaretçilerini karşılaştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6978-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="f6978-106">[Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) döndürür `True` nesneleri özdeş ise ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) döndürür `True` değillerse.</span><span class="sxs-lookup"><span data-stu-id="f6978-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="f6978-107">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="f6978-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="f6978-108">İki nesnenin aynı olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="f6978-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="f6978-109">Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.</span><span class="sxs-lookup"><span data-stu-id="f6978-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="f6978-110">Sınama İfadenizde kullanmak `Is` işlenen olarak iki nesnenin işleç.</span><span class="sxs-lookup"><span data-stu-id="f6978-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="f6978-111">`Is` döndürür `True` nesneleri aynı sınıf örneğine noktası.</span><span class="sxs-lookup"><span data-stu-id="f6978-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="f6978-112">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="f6978-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="f6978-113">İki nesnenin aynı değilseniz ve birleştirmek garip olabilir bir eylem gerçekleştirmek istediğiniz bazen `Not` ve `Is`, örneğin `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="f6978-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="f6978-114">Böyle bir durumda kullandığınız `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="f6978-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="f6978-115">İki nesnenin aynı olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="f6978-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="f6978-116">Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.</span><span class="sxs-lookup"><span data-stu-id="f6978-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="f6978-117">Sınama İfadenizde kullanmak `IsNot` işlenen olarak iki nesnenin işleç.</span><span class="sxs-lookup"><span data-stu-id="f6978-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="f6978-118">`IsNot` döndürür `True` nesneleri aynı sınıfı örneğini işaret etmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="f6978-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6978-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6978-119">Example</span></span>  
 <span data-ttu-id="f6978-120">Aşağıdaki örnek çiftlerini testleri `Object` aynı sınıf örneğine noktası görmek için değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="f6978-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="f6978-121">Önceki örnekte, aşağıdaki çıkış görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f6978-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="f6978-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6978-122">See Also</span></span>  
 [<span data-ttu-id="f6978-123">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f6978-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="f6978-124">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f6978-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="f6978-125">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="f6978-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="f6978-126">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="f6978-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="f6978-127">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="f6978-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="f6978-128">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f6978-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="f6978-129">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="f6978-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
