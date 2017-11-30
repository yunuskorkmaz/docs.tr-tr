---
title: "TryCast İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords: TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6be11b49eb3b9d98e3bf147e9b1026d4ffc860c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="f8ded-102">TryCast İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8ded-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="f8ded-103">Bir özel durum olmayan bir tür dönüştürme işleminin tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f8ded-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8ded-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8ded-104">Remarks</span></span>  
 <span data-ttu-id="f8ded-105">Denenen bir dönüştürme başarısız olursa, `CType` ve `DirectCast` her ikisi de throw bir <xref:System.InvalidCastException> hata.</span><span class="sxs-lookup"><span data-stu-id="f8ded-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="f8ded-106">Bu, uygulamanızın performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="f8ded-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="f8ded-107">`TryCast`döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md), olası bir özel durum işleme gerek kalmadan yerine yalnızca döndürülen sonuç karşı test böylece `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f8ded-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="f8ded-108">Kullandığınız `TryCast` anahtar sözcüğü kullandığınız aynı şekilde [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f8ded-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="f8ded-109">Bir ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak dönüştürmek için bir türü olarak sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f8ded-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="f8ded-110">`TryCast`yalnızca başvuru türleri, sınıflar ve arabirimler gibi üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f8ded-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="f8ded-111">İki tür arasında bir devralma ya da uygulanmasını ilişkisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8ded-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="f8ded-112">Bu tür öğesinden devralmalı ya da diğer uygulamak, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f8ded-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="f8ded-113">Hataları</span><span class="sxs-lookup"><span data-stu-id="f8ded-113">Errors and Failures</span></span>  
 <span data-ttu-id="f8ded-114">`TryCast`Devralma veya uygulama hiçbir ilişki var olduğunu algılarsa derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8ded-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="f8ded-115">Ancak derleyici hatası eksikliği başarılı dönüştürme garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="f8ded-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="f8ded-116">İstenen dönüştürme daraltma değilse, çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8ded-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="f8ded-117">Bu durumda, `TryCast` döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="f8ded-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="f8ded-118">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f8ded-118">Conversion Keywords</span></span>  
 <span data-ttu-id="f8ded-119">Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f8ded-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="f8ded-120">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f8ded-120">Keyword</span></span>|<span data-ttu-id="f8ded-121">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="f8ded-121">Data types</span></span>|<span data-ttu-id="f8ded-122">Bağımsız değişken ilişkisi</span><span class="sxs-lookup"><span data-stu-id="f8ded-122">Argument relationship</span></span>|<span data-ttu-id="f8ded-123">Çalışma zamanı hatası</span><span class="sxs-lookup"><span data-stu-id="f8ded-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="f8ded-124">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="f8ded-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="f8ded-125">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="f8ded-125">Any data types</span></span>|<span data-ttu-id="f8ded-126">Genişletme veya daraltma dönüştürme iki veri türleri arasında tanımlanmalıdır</span><span class="sxs-lookup"><span data-stu-id="f8ded-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="f8ded-127">Oluşturur<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="f8ded-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="f8ded-128">DirectCast işleci</span><span class="sxs-lookup"><span data-stu-id="f8ded-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="f8ded-129">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="f8ded-129">Any data types</span></span>|<span data-ttu-id="f8ded-130">Bir tür öğesinden devralmalı ya da başka tür</span><span class="sxs-lookup"><span data-stu-id="f8ded-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="f8ded-131">Oluşturur<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="f8ded-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="f8ded-132">Yalnızca başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="f8ded-132">Reference types only</span></span>|<span data-ttu-id="f8ded-133">Bir tür öğesinden devralmalı ya da başka tür</span><span class="sxs-lookup"><span data-stu-id="f8ded-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="f8ded-134">Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="f8ded-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8ded-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8ded-135">Example</span></span>  
 <span data-ttu-id="f8ded-136">Aşağıdaki örnekte nasıl kullanılacağını gösterir `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="f8ded-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f8ded-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8ded-137">See Also</span></span>  
 [<span data-ttu-id="f8ded-138">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="f8ded-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="f8ded-139">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="f8ded-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
