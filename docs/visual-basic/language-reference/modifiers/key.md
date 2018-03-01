---
title: Anahtar (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a><span data-ttu-id="4a548-102">Anahtar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a548-102">Key (Visual Basic)</span></span>
<span data-ttu-id="4a548-103">`Key` Anahtar sözcüğü anonim türdeki özellikleri davranışını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a548-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="4a548-104">Anonim tür örneği veya karma kodu değerleri hesaplama arasında eşitlik testleri anahtar özellikleri katılan gibi yalnızca özellikleri, belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4a548-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="4a548-105">Anahtar özellikleri değerleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4a548-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="4a548-106">Anahtar sözcüğünü girerek bir anahtar özellik olarak belirttiğiniz anonim bir türün bir özellik `Key` bildiriminden başlatma listesinde önünde.</span><span class="sxs-lookup"><span data-stu-id="4a548-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="4a548-107">Aşağıdaki örnekte, `Airline` ve `FlightNo` anahtar özellikleri, ancak `Gate` değil.</span><span class="sxs-lookup"><span data-stu-id="4a548-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 <span data-ttu-id="4a548-108">Yeni bir anonim türü oluşturulduğunda, doğrudan öğesinden devralınan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="4a548-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="4a548-109">Derleyici üç devralınan üyeleri geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, ve <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a548-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="4a548-110">İçin üretilen geçersiz kılma kodu <xref:System.Object.Equals%2A> ve <xref:System.Object.GetHashCode%2A> anahtar özelliklerinde dayanır.</span><span class="sxs-lookup"><span data-stu-id="4a548-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="4a548-111">Tür, anahtar özellik varsa <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> değil geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="4a548-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="4a548-112">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="4a548-112">Equality</span></span>  
 <span data-ttu-id="4a548-113">İki anonim tür örnekleri aynı türde olup olmadığını ve anahtar özelliklerini değerleri aynıysa eşit örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="4a548-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="4a548-114">Aşağıdaki örneklerde, `flight2` eşittir `flight1` aynı anonim örneklerini olduklarından önceki örnekten türüne ve bunlar eşleşen anahtar özellikleri için değerleri sahip.</span><span class="sxs-lookup"><span data-stu-id="4a548-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="4a548-115">Ancak, `flight3` eşit değil `flight1` bir anahtar özellik için farklı bir değere sahip olduğundan `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="4a548-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="4a548-116">Örnek `flight4` aynı türde değil `flight1` çünkü bunlar farklı özellikleri anahtar özellik olarak belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4a548-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 <span data-ttu-id="4a548-117">Yalnızca anahtar olmayan özellikler, ad, tür, sipariş ve değer, aynı olan iki örneği bildirilen, iki örneği eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="4a548-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="4a548-118">Anahtar özellikleri olmayan bir örneği yalnızca kendisine eşittir.</span><span class="sxs-lookup"><span data-stu-id="4a548-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="4a548-119">İki anonim tür örnekleri altında aynı anonim türdeki örneklerin olan koşullar hakkında daha fazla bilgi için bkz: [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="4a548-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="4a548-120">Karma kod hesaplama</span><span class="sxs-lookup"><span data-stu-id="4a548-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="4a548-121">Gibi <xref:System.Object.Equals%2A>, tanımlanan karma işlevi <xref:System.Object.GetHashCode%2A> anonim bir tür türü anahtar özelliklerinde temel alınır.</span><span class="sxs-lookup"><span data-stu-id="4a548-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="4a548-122">Aşağıdaki örnekler anahtar özellikleri ve karma arasındaki etkileşim kod değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a548-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="4a548-123">Anahtar olmayan özellikler eşleşen değerleri olmasa bile, tüm anahtar özellikler için aynı değerlere sahip anonim bir tür örnekleri aynı karma kodu değere sahip.</span><span class="sxs-lookup"><span data-stu-id="4a548-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="4a548-124">Aşağıdaki deyim döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="4a548-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 <span data-ttu-id="4a548-125">Bir veya daha fazla anahtar özellikleri için farklı değerlere sahip anonim bir tür örnekleri farklı bir karma kod değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4a548-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="4a548-126">Aşağıdaki deyim döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="4a548-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 <span data-ttu-id="4a548-127">Farklı özellikleri anahtar özellikler örnekleri aynı türde olmadığından tanımladığınız anonim türler örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4a548-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="4a548-128">Adları ve değerleri tüm özelliklerin aynı olsa bile farklı bir karma kod değerleri sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="4a548-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="4a548-129">Aşağıdaki deyim döndürür `False`.</span><span class="sxs-lookup"><span data-stu-id="4a548-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a><span data-ttu-id="4a548-130">Salt okunur değerleri</span><span class="sxs-lookup"><span data-stu-id="4a548-130">Read-Only Values</span></span>  
 <span data-ttu-id="4a548-131">Anahtar özellikleri değerleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="4a548-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="4a548-132">Örneğin, `flight1` önceki örneklerde, `Airline` ve `FlightNo` alanları salt okunur, ancak `Gate` değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4a548-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a548-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a548-133">See Also</span></span>  
 [<span data-ttu-id="4a548-134">Anonim tür tanımı</span><span class="sxs-lookup"><span data-stu-id="4a548-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="4a548-135">Nasıl yapılır: özellik adları ve türlerini anonim türde bildirimlerden çıkarma</span><span class="sxs-lookup"><span data-stu-id="4a548-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="4a548-136">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="4a548-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
