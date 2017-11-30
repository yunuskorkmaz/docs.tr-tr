---
title: "DirectCast İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords: DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="1ddaa-102">DirectCast İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ddaa-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="1ddaa-103">Devralma veya uygulama temel türü dönüştürme işlemi sunar.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ddaa-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ddaa-104">Remarks</span></span>  
 <span data-ttu-id="1ddaa-105">`DirectCast`Visual Basic çalışma zamanı yardımcı yordamları biraz sağlayabilmesi için dönüştürme için daha iyi performans daha kullanmaz `CType` için ve veri türüne dönüştürülürken `Object`.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="1ddaa-106">Kullandığınız `DirectCast` anahtar sözcüğü benzer kullandığınız şekilde [CType işlevi](../../../visual-basic/language-reference/functions/ctype-function.md) ve [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword.</span></span> <span data-ttu-id="1ddaa-107">Bir ifade ilk bağımsız değişken ve ikinci bağımsız değişken olarak dönüştürmek için bir türü olarak sağlayın.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="1ddaa-108">`DirectCast`iki bağımsız değişkenlerinin veri türleri arasında bir devralma ya da uygulanmasını ilişkisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="1ddaa-109">Bu tür öğesinden devralmalı ya da diğer uygulamak, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="1ddaa-110">Hataları</span><span class="sxs-lookup"><span data-stu-id="1ddaa-110">Errors and Failures</span></span>  
 <span data-ttu-id="1ddaa-111">`DirectCast`Devralma veya uygulama hiçbir ilişki var olduğunu algılarsa derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="1ddaa-112">Ancak derleyici hatası eksikliği başarılı dönüştürme garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="1ddaa-113">İstenen dönüştürme daraltma değilse, çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="1ddaa-114">Bu durumda, çalışma zamanı oluşturur bir <xref:System.InvalidCastException> hata.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="1ddaa-115">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1ddaa-115">Conversion Keywords</span></span>  
 <span data-ttu-id="1ddaa-116">Tür Dönüşüm anahtar sözcükleri karşılaştırması aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="1ddaa-117">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="1ddaa-117">Keyword</span></span>|<span data-ttu-id="1ddaa-118">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="1ddaa-118">Data types</span></span>|<span data-ttu-id="1ddaa-119">Bağımsız değişken ilişkisi</span><span class="sxs-lookup"><span data-stu-id="1ddaa-119">Argument relationship</span></span>|<span data-ttu-id="1ddaa-120">Çalışma zamanı hatası</span><span class="sxs-lookup"><span data-stu-id="1ddaa-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="1ddaa-121">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="1ddaa-121">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="1ddaa-122">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="1ddaa-122">Any data types</span></span>|<span data-ttu-id="1ddaa-123">Genişletme veya daraltma dönüştürme iki veri türleri arasında tanımlanmalıdır</span><span class="sxs-lookup"><span data-stu-id="1ddaa-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="1ddaa-124">Oluşturur<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="1ddaa-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="1ddaa-125">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="1ddaa-125">Any data types</span></span>|<span data-ttu-id="1ddaa-126">Bir tür öğesinden devralmalı ya da başka tür</span><span class="sxs-lookup"><span data-stu-id="1ddaa-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="1ddaa-127">Oluşturur<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="1ddaa-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="1ddaa-128">TryCast işleci</span><span class="sxs-lookup"><span data-stu-id="1ddaa-128">TryCast Operator</span></span>](../../../visual-basic/language-reference/operators/trycast-operator.md)|<span data-ttu-id="1ddaa-129">Yalnızca başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="1ddaa-129">Reference types only</span></span>|<span data-ttu-id="1ddaa-130">Bir tür öğesinden devralmalı ya da başka tür</span><span class="sxs-lookup"><span data-stu-id="1ddaa-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="1ddaa-131">Döndürür [hiçbir şey](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="1ddaa-131">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1ddaa-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ddaa-132">Example</span></span>  
 <span data-ttu-id="1ddaa-133">Aşağıdaki örnek, iki kullanımını gösterir `DirectCast`, bir çalışma zamanı ve biri başarısız başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 <span data-ttu-id="1ddaa-134">Önceki örnekte, çalışma zamanı türü `q` olan `Double`.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="1ddaa-135">`CType`çünkü başarılı `Double` dönüştürülebilir `Integer`.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="1ddaa-136">Ancak, ilk `DirectCast` çalışma zamanı türü olduğundan çalışma zamanında başarısız `Double` ile herhangi bir devralma ilişkisi yoktur `Integer`rağmen bir dönüştürme yok.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="1ddaa-137">İkinci `DirectCast` çünkü türünden dönüştürür başarılı <xref:System.Windows.Forms.Form> yazmak için <xref:System.Windows.Forms.Control>, içinden <xref:System.Windows.Forms.Form> devralır.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ddaa-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ddaa-138">See Also</span></span>  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1ddaa-139">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="1ddaa-139">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="1ddaa-140">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="1ddaa-140">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
