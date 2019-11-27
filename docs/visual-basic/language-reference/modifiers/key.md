---
title: Anahtar
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92c8809779d6cab524f67ee47f355b72ab152403
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351512"
---
# <a name="key-visual-basic"></a><span data-ttu-id="f7319-102">Anahtar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7319-102">Key (Visual Basic)</span></span>
<span data-ttu-id="f7319-103">`Key` anahtar sözcüğü anonim türlerin özellikleri için davranış belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7319-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="f7319-104">Yalnızca anahtar özellikleri olarak belirleyeceğiniz özellikler, anonim tür örnekleri arasındaki eşitlik testlerine veya karma kodu değerlerinin hesaplanmasına katılır.</span><span class="sxs-lookup"><span data-stu-id="f7319-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="f7319-105">Anahtar özelliklerinin değerleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f7319-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="f7319-106">Anahtar sözcüğü `Key` bir özellik olarak bir özelliği, başlangıç listesindeki bildiriminin önüne yazarak anahtar özelliği olarak belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="f7319-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="f7319-107">Aşağıdaki örnekte, `Airline` ve `FlightNo` anahtar özelliklerdir, ancak `Gate` değildir.</span><span class="sxs-lookup"><span data-stu-id="f7319-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="f7319-108">Yeni bir anonim tür oluşturulduğunda, doğrudan <xref:System.Object>devralır.</span><span class="sxs-lookup"><span data-stu-id="f7319-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="f7319-109">Derleyici, devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>ve <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7319-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="f7319-110"><xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> için üretilen geçersiz kılma kodu, anahtar özelliklerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="f7319-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="f7319-111">Türde hiç anahtar özelliği yoksa, <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="f7319-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="f7319-112">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="f7319-112">Equality</span></span>  
 <span data-ttu-id="f7319-113">İki anonim tür örneği aynı türde örneklerse ve anahtar özelliklerinin değerleri eşitse eşittir.</span><span class="sxs-lookup"><span data-stu-id="f7319-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="f7319-114">Aşağıdaki örneklerde `flight2`, aynı anonim türdeki örnekler olduklarından ve bunların anahtar özellikleri için eşleşen değerleri olduğundan, önceki örnekteki `flight1` eşittir.</span><span class="sxs-lookup"><span data-stu-id="f7319-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="f7319-115">Ancak, bir anahtar özelliği için farklı bir değere sahip olduğundan, `flight3` `flight1` eşit değildir `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="f7319-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="f7319-116">Örnek `flight4`, anahtar özellikler olarak farklı özellikleri tasardıklarından `flight1` aynı türde değil.</span><span class="sxs-lookup"><span data-stu-id="f7319-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="f7319-117">İki örnek yalnızca anahtar olmayan özelliklerle, ad, tür, düzen ve değer ile bildirilirse, iki örnek eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="f7319-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="f7319-118">Anahtar özellikleri olmayan bir örnek yalnızca kendi kendine eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="f7319-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="f7319-119">İki anonim tür örneğinin aynı anonim türdeki örnekleri olduğu koşullar hakkında daha fazla bilgi için bkz. [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f7319-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="f7319-120">Karma kod hesaplama</span><span class="sxs-lookup"><span data-stu-id="f7319-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="f7319-121"><xref:System.Object.Equals%2A>gibi, anonim bir tür için <xref:System.Object.GetHashCode%2A> tanımlanan karma işlevi, türün anahtar özelliklerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7319-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="f7319-122">Aşağıdaki örneklerde, anahtar özellikleri ve karma kod değerleri arasındaki etkileşim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7319-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="f7319-123">Anahtar olmayan özelliklerde eşleşen değerler olmasa bile, tüm anahtar özellikleri için aynı değere sahip anonim bir türün örnekleri aynı karma kod değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7319-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="f7319-124">Aşağıdaki ifade `True`döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7319-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="f7319-125">Bir veya daha fazla anahtar özelliği için farklı değerlere sahip anonim bir türün örnekleri, farklı karma kodu değerlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7319-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="f7319-126">Aşağıdaki ifade `False`döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7319-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="f7319-127">Anahtar özellikler olarak farklı özellikleri belirten anonim türlerin örnekleri aynı türde örnekler değildir.</span><span class="sxs-lookup"><span data-stu-id="f7319-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="f7319-128">Tüm özelliklerin adları ve değerleri aynı olduğunda bile, farklı karma kodu değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f7319-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="f7319-129">Aşağıdaki ifade `False`döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7319-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="f7319-130">Salt okunurdur değerler</span><span class="sxs-lookup"><span data-stu-id="f7319-130">Read-Only Values</span></span>  
 <span data-ttu-id="f7319-131">Anahtar özelliklerinin değerleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f7319-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="f7319-132">Örneğin, önceki örneklerde `flight1`, `Airline` ve `FlightNo` alanları salt okunurdur, ancak `Gate` değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f7319-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="f7319-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7319-133">See also</span></span>

- [<span data-ttu-id="f7319-134">Anonim Tip Tanımı</span><span class="sxs-lookup"><span data-stu-id="f7319-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="f7319-135">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="f7319-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="f7319-136">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="f7319-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
