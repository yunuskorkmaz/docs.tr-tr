---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 67c3af8b7bdac3ad1c7e4908f1ac2684df7a87aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410483"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="19cf5-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19cf5-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="19cf5-103">Visual Basic, işaretçilerin aynısı varsa, iki değişken başvurusu özdeş kabul edilir, yani her iki değişken de bellekteki aynı sınıf örneğini işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="19cf5-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="19cf5-104">Örneğin, Windows Forms bir uygulamada, geçerli örneğin ( `Me` ) belirli bir örnekle aynı olup olmadığını (gibi) belirlemede bir karşılaştırma yapmak isteyebilirsiniz `Form2` .</span><span class="sxs-lookup"><span data-stu-id="19cf5-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="19cf5-105">Visual Basic işaretçileri karşılaştırmak için iki işleç sağlar.</span><span class="sxs-lookup"><span data-stu-id="19cf5-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="19cf5-106">[,](../../../language-reference/operators/is-operator.md) `True` Nesneleri özdeş Ise ve [ınot işleci](../../../language-reference/operators/isnot-operator.md) değilse, işleç döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="19cf5-106">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="19cf5-107">Iki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="19cf5-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="19cf5-108">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="19cf5-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="19cf5-109">`Boolean`İki nesneyi test etmek için bir ifade ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="19cf5-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="19cf5-110">Test ifadesiyse `Is` işleci iki nesne ile işlenen olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="19cf5-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="19cf5-111">`Is``True`nesneler aynı sınıf örneğine işaret ettikten sonra döndürür.</span><span class="sxs-lookup"><span data-stu-id="19cf5-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="19cf5-112">Iki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="19cf5-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="19cf5-113">Bazen iki nesne özdeş değilse bir eylem gerçekleştirmek istersiniz ve bu, örneğin, birleştirmek için de olabilir `Not` `Is` `If Not obj1 Is obj2` .</span><span class="sxs-lookup"><span data-stu-id="19cf5-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="19cf5-114">Böyle bir durumda, `IsNot` işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19cf5-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="19cf5-115">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="19cf5-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="19cf5-116">`Boolean`İki nesneyi test etmek için bir ifade ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="19cf5-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="19cf5-117">Test ifadesiyse `IsNot` işleci iki nesne ile işlenen olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="19cf5-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="19cf5-118">`IsNot``True`nesnelerin aynı sınıf örneğini işaret edip etmez döndürür.</span><span class="sxs-lookup"><span data-stu-id="19cf5-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19cf5-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="19cf5-119">Example</span></span>  
 <span data-ttu-id="19cf5-120">Aşağıdaki örnek, `Object` aynı sınıf örneğine işaret edip ettikleri anlamak için değişken çiftlerini sınar.</span><span class="sxs-lookup"><span data-stu-id="19cf5-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="19cf5-121">Yukarıdaki örnek aşağıdaki çıktıyı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19cf5-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="19cf5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19cf5-122">See also</span></span>

- [<span data-ttu-id="19cf5-123">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="19cf5-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="19cf5-124">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="19cf5-124">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="19cf5-125">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="19cf5-125">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="19cf5-126">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="19cf5-126">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="19cf5-127">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="19cf5-127">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="19cf5-128">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="19cf5-128">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="19cf5-129">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="19cf5-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
