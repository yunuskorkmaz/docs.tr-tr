---
title: 'Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295048"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="2cd50-102">Nasıl yapılır: İki nesnenin aynı (Visual Basic) olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="2cd50-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="2cd50-103">Visual Basic'te, her iki değişken için aynı sınıf örneği bellekte gelirseniz iki değişken başvuruları kendi işaretçileri aynıysa, diğer bir deyişle, aynı kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2cd50-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="2cd50-104">Örneğin, bir Windows Forms uygulamasında belirlemek için bir karşılaştırma yapmak isteyebileceğiniz olup olmadığını geçerli örneğini (`Me`) belirli bir örneği aynı olduğu gibi `Form2`.</span><span class="sxs-lookup"><span data-stu-id="2cd50-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="2cd50-105">Visual Basic işaretçileri karşılaştırmak için iki işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd50-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="2cd50-106">[İşleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) döndürür `True` nesneleri aynıysa ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) döndürür `True` yoksa.</span><span class="sxs-lookup"><span data-stu-id="2cd50-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="2cd50-107">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="2cd50-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="2cd50-108">İki nesnenin aynı olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="2cd50-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="2cd50-109">Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.</span><span class="sxs-lookup"><span data-stu-id="2cd50-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="2cd50-110">Test ifadesinde kullanmak `Is` işlenen olarak iki nesne işleci.</span><span class="sxs-lookup"><span data-stu-id="2cd50-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     `Is` <span data-ttu-id="2cd50-111">döndürür `True` için aynı sınıf örneği nesnelerini noktası.</span><span class="sxs-lookup"><span data-stu-id="2cd50-111">returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="2cd50-112">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="2cd50-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="2cd50-113">İki nesnenin aynı değildir ve birleştirmek garip olabilir bir eylem gerçekleştirmek istediğiniz bazen `Not` ve `Is`, örneğin `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="2cd50-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="2cd50-114">Böyle bir durumda kullanabileceğiniz `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="2cd50-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="2cd50-115">İki nesnenin aynı olup olmadığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="2cd50-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="2cd50-116">Ayarlanmış bir `Boolean` iki nesne test etmek için ifade.</span><span class="sxs-lookup"><span data-stu-id="2cd50-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="2cd50-117">Test ifadesinde kullanmak `IsNot` işlenen olarak iki nesne işleci.</span><span class="sxs-lookup"><span data-stu-id="2cd50-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     `IsNot` <span data-ttu-id="2cd50-118">döndürür `True` nesneleri aynı sınıf örneğine işaret etmiyorsa.</span><span class="sxs-lookup"><span data-stu-id="2cd50-118">returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cd50-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cd50-119">Example</span></span>  
 <span data-ttu-id="2cd50-120">Aşağıdaki örnek çiftlerini testleri `Object` aynı sınıf örneğine işaret görmek için değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="2cd50-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="2cd50-121">Yukarıdaki örnek aşağıdaki çıkışı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2cd50-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="2cd50-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd50-122">See also</span></span>

- [<span data-ttu-id="2cd50-123">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2cd50-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="2cd50-124">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="2cd50-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="2cd50-125">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="2cd50-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="2cd50-126">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="2cd50-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="2cd50-127">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="2cd50-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="2cd50-128">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="2cd50-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="2cd50-129">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="2cd50-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
