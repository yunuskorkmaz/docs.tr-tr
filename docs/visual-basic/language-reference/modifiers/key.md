---
description: 'Daha fazla bilgi edinin: anahtar (Visual Basic)'
title: Anahtar
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 5ec918da661144053824ca2a734cdec11873b0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640803"
---
# <a name="key-visual-basic"></a><span data-ttu-id="271e7-103">Anahtar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="271e7-103">Key (Visual Basic)</span></span>

<span data-ttu-id="271e7-104">`Key`Anahtar sözcüğü anonim türlerin özellikleri için davranış belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="271e7-104">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="271e7-105">Yalnızca anahtar özellikleri olarak belirleyeceğiniz özellikler, anonim tür örnekleri arasındaki eşitlik testlerine veya karma kodu değerlerinin hesaplanmasına katılır.</span><span class="sxs-lookup"><span data-stu-id="271e7-105">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="271e7-106">Anahtar özelliklerinin değerleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="271e7-106">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="271e7-107">Anahtar sözcüğünü `Key` başlatma listesindeki bildiriminin önüne yerleştirerek, anonim türdeki bir özelliği anahtar özelliği olarak belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="271e7-107">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="271e7-108">Aşağıdaki örnekte `Airline` ve `FlightNo` temel özelliklerdir, ancak `Gate` değildir.</span><span class="sxs-lookup"><span data-stu-id="271e7-108">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="271e7-109">Yeni bir anonim tür oluşturulduğunda, doğrudan öğesinden devralır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="271e7-109">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="271e7-110">Derleyici, devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> , ve <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="271e7-110">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="271e7-111">Ve için üretilen geçersiz kılma kodu, <xref:System.Object.Equals%2A> <xref:System.Object.GetHashCode%2A> anahtar özelliklerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="271e7-111">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="271e7-112">Türde hiç anahtar özellik yoksa <xref:System.Object.GetHashCode%2A> ve <xref:System.Object.Equals%2A> geçersiz kılınmamışsa.</span><span class="sxs-lookup"><span data-stu-id="271e7-112">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="271e7-113">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="271e7-113">Equality</span></span>  

 <span data-ttu-id="271e7-114">İki anonim tür örneği aynı türde örneklerse ve anahtar özelliklerinin değerleri eşitse eşittir.</span><span class="sxs-lookup"><span data-stu-id="271e7-114">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="271e7-115">Aşağıdaki örneklerde, `flight2` `flight1` aynı anonim türün örnekleri olduklarından ve bunların anahtar özellikleri için eşleşen değerleri bulunduğundan, önceki örnekteki öğesine eşittir.</span><span class="sxs-lookup"><span data-stu-id="271e7-115">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="271e7-116">Ancak, `flight3` `flight1` bir anahtar özelliği için farklı bir değere sahip olduğundan, öğesine eşit değildir `FlightNo` .</span><span class="sxs-lookup"><span data-stu-id="271e7-116">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="271e7-117">Örnek `flight4` , `flight1` anahtar özellikler olarak farklı özellikleri belirlemediklerinden aynı türde değildir.</span><span class="sxs-lookup"><span data-stu-id="271e7-117">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="271e7-118">İki örnek yalnızca anahtar olmayan özelliklerle, ad, tür, düzen ve değer ile bildirilirse, iki örnek eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="271e7-118">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="271e7-119">Anahtar özellikleri olmayan bir örnek yalnızca kendi kendine eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="271e7-119">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="271e7-120">İki anonim tür örneğinin aynı anonim türdeki örnekleri olduğu koşullar hakkında daha fazla bilgi için bkz. [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="271e7-120">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="271e7-121">Karma kod hesaplama</span><span class="sxs-lookup"><span data-stu-id="271e7-121">Hash Code Calculation</span></span>  

 <span data-ttu-id="271e7-122">Benzer şekilde <xref:System.Object.Equals%2A> , anonim bir tür için ' de tanımlanan karma işlevi, <xref:System.Object.GetHashCode%2A> türün anahtar özelliklerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="271e7-122">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="271e7-123">Aşağıdaki örneklerde, anahtar özellikleri ve karma kod değerleri arasındaki etkileşim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="271e7-123">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="271e7-124">Anahtar olmayan özelliklerde eşleşen değerler olmasa bile, tüm anahtar özellikleri için aynı değere sahip anonim bir türün örnekleri aynı karma kod değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="271e7-124">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="271e7-125">Aşağıdaki ifade döndürür `True` .</span><span class="sxs-lookup"><span data-stu-id="271e7-125">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="271e7-126">Bir veya daha fazla anahtar özelliği için farklı değerlere sahip anonim bir türün örnekleri, farklı karma kodu değerlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="271e7-126">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="271e7-127">Aşağıdaki ifade döndürür `False` .</span><span class="sxs-lookup"><span data-stu-id="271e7-127">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="271e7-128">Anahtar özellikler olarak farklı özellikleri belirten anonim türlerin örnekleri aynı türde örnekler değildir.</span><span class="sxs-lookup"><span data-stu-id="271e7-128">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="271e7-129">Tüm özelliklerin adları ve değerleri aynı olduğunda bile, farklı karma kodu değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="271e7-129">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="271e7-130">Aşağıdaki ifade döndürür `False` .</span><span class="sxs-lookup"><span data-stu-id="271e7-130">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="271e7-131">Read-Only değerleri</span><span class="sxs-lookup"><span data-stu-id="271e7-131">Read-Only Values</span></span>  

 <span data-ttu-id="271e7-132">Anahtar özelliklerinin değerleri değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="271e7-132">The values of key properties cannot be changed.</span></span> <span data-ttu-id="271e7-133">Örneğin, `flight1` Önceki örneklerde, `Airline` ve `FlightNo` alanları salt okunurdur, ancak `Gate` değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="271e7-133">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="271e7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="271e7-134">See also</span></span>

- [<span data-ttu-id="271e7-135">Anonim Tip Tanımı</span><span class="sxs-lookup"><span data-stu-id="271e7-135">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="271e7-136">Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma</span><span class="sxs-lookup"><span data-stu-id="271e7-136">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="271e7-137">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="271e7-137">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
