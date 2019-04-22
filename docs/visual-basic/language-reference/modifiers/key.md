---
title: Anahtar (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842310"
---
# <a name="key-visual-basic"></a><span data-ttu-id="8af0d-102">Anahtar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8af0d-102">Key (Visual Basic)</span></span>
<span data-ttu-id="8af0d-103">`Key` Anahtar sözcüğü anonim türler, özellikler için davranışını belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="8af0d-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="8af0d-104">Anonim tür örnekleri veya bir karma kod değerleri hesaplama arasındaki testlerinde anahtar özellikleri arttıkça, yalnızca özellikleri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8af0d-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="8af0d-105">Anahtar özelliklerin değerlerini değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8af0d-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="8af0d-106">Anahtar sözcüğünü koyarak bir anahtar özellik olarak belirlediğiniz anonim bir türün bir özellik `Key` başlatma listesi bildiriminde önünde.</span><span class="sxs-lookup"><span data-stu-id="8af0d-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="8af0d-107">Aşağıdaki örnekte, `Airline` ve `FlightNo` anahtar özellikleri, ancak `Gate` değil.</span><span class="sxs-lookup"><span data-stu-id="8af0d-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="8af0d-108">Yeni bir anonim tür oluşturulduğunda, doğrudan devralan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8af0d-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="8af0d-109">Derleyici, üç devralınan üyeleri geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="8af0d-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="8af0d-110">İçin üretilen geçersiz kılma kod <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtar özelliklerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8af0d-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="8af0d-111">Tür, anahtar özellik varsa <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> geçersiz kılınmadığını.</span><span class="sxs-lookup"><span data-stu-id="8af0d-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="8af0d-112">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="8af0d-112">Equality</span></span>  
 <span data-ttu-id="8af0d-113">Aynı türdeki örneklerin olmaları durumunda ve bunların anahtar özelliklerinin değerler eşitse, iki anonim tür örnekleri eşit olur.</span><span class="sxs-lookup"><span data-stu-id="8af0d-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="8af0d-114">Aşağıdaki örneklerde, `flight2` eşittir `flight1` aynı anonim örneklerini olduklarından önceki örnekteki tür değerleri kendi anahtar özellikleri için eşleşen sahip olur.</span><span class="sxs-lookup"><span data-stu-id="8af0d-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="8af0d-115">Ancak, `flight3` eşit değildir `flight1` , bir anahtar özellik için farklı bir değer içerdiğinden `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="8af0d-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="8af0d-116">Örnek `flight4` aynı türde değil `flight1` çünkü bunlar farklı özellikleri anahtar özellik olarak belirleyin.</span><span class="sxs-lookup"><span data-stu-id="8af0d-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="8af0d-117">Yalnızca anahtar olmayan özellikleri olan adı, türü, sırası ve değeri, aynı iki örneği bildirilmişse iki örnek eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="8af0d-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="8af0d-118">Örneği anahtar özellikleri olmadan yalnızca kendisine eşittir.</span><span class="sxs-lookup"><span data-stu-id="8af0d-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="8af0d-119">İki anonim tür örnekleri altında aynı anonim tür örnekleri olan koşullar hakkında daha fazla bilgi için bkz. [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="8af0d-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="8af0d-120">Karma kod hesaplama</span><span class="sxs-lookup"><span data-stu-id="8af0d-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="8af0d-121">Gibi <xref:System.Object.Equals%2A>, tanımlanan karma işlevi <xref:System.Object.GetHashCode%2A> türü anahtar özellikleri anonim bir tür temel alınır.</span><span class="sxs-lookup"><span data-stu-id="8af0d-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="8af0d-122">Aşağıdaki örnekler arasındaki etkileşimler anahtar özellikleri ve karma kod değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8af0d-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="8af0d-123">Anahtar olmayan özellikler eşleşen değerler olmasa bile, tüm anahtar özellikleri için aynı değerlere sahip anonim bir türün örneklerinin aynı karma kodu değeri var.</span><span class="sxs-lookup"><span data-stu-id="8af0d-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="8af0d-124">Aşağıdaki ifade döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="8af0d-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="8af0d-125">Bir veya daha fazla anahtar özelliği için farklı değerlere sahip anonim bir türün örneklerinin farklı bir karma kod değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="8af0d-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="8af0d-126">Aşağıdaki ifade döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="8af0d-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="8af0d-127">Farklı özellikleri anahtar özellik olarak belirlediğiniz anonim türlerin örneklerini örnekleri aynı türde değil.</span><span class="sxs-lookup"><span data-stu-id="8af0d-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="8af0d-128">Adları ve değerleri tüm özelliklerin aynı olsa bile farklı bir karma kod değerlere sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="8af0d-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="8af0d-129">Aşağıdaki ifade döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="8af0d-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="8af0d-130">Salt okunur değerleri</span><span class="sxs-lookup"><span data-stu-id="8af0d-130">Read-Only Values</span></span>  
 <span data-ttu-id="8af0d-131">Anahtar özelliklerin değerlerini değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8af0d-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="8af0d-132">Örneğin, `flight1` önceki örneklerde, `Airline` ve `FlightNo` alanları salt okunur ancak `Gate` değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8af0d-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="8af0d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8af0d-133">See also</span></span>

- [<span data-ttu-id="8af0d-134">Anonim Tip Tanımı</span><span class="sxs-lookup"><span data-stu-id="8af0d-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="8af0d-135">Nasıl yapılır: Özellik adları ve türleri anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="8af0d-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="8af0d-136">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="8af0d-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
