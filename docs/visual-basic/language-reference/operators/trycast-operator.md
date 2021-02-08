---
description: ': TryCast Işleci (Visual Basic) hakkında daha fazla bilgi'
title: TryCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 5b941ec40c4ba0198fced64d0ef039605efad472
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795254"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="6a210-103">TryCast İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a210-103">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="6a210-104">Özel durum oluşturmayan bir tür dönüştürme işlemi sunar.</span><span class="sxs-lookup"><span data-stu-id="6a210-104">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a210-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a210-105">Remarks</span></span>  

 <span data-ttu-id="6a210-106">Denenen bir dönüştürme başarısız olursa `CType` ve `DirectCast` her ikisi de bir <xref:System.InvalidCastException> hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a210-106">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="6a210-107">Bu, uygulamanızın performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6a210-107">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="6a210-108">`TryCast`[hiçbir şey](../nothing.md)döndürmez, bu nedenle olası bir özel durumu işlemek zorunda kalmak yerine yalnızca döndürülen sonucu test etmeniz gerekir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="6a210-108">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="6a210-109">`TryCast`Anahtar sözcüğünü [CType Işlevini](../functions/ctype-function.md) ve [DirectCast İşleci](directcast-operator.md) anahtar sözcüğünü kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6a210-109">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="6a210-110">İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="6a210-110">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="6a210-111">`TryCast` Yalnızca sınıflar ve arabirimler gibi başvuru türlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="6a210-111">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="6a210-112">İki tür arasında devralma veya uygulama ilişkisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6a210-112">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="6a210-113">Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6a210-113">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="6a210-114">Hatalar ve hatalar</span><span class="sxs-lookup"><span data-stu-id="6a210-114">Errors and Failures</span></span>  

 <span data-ttu-id="6a210-115">`TryCast` devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a210-115">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="6a210-116">Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="6a210-116">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="6a210-117">İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a210-117">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="6a210-118">Bu durumda `TryCast` [hiçbir şey](../nothing.md)döndürmez.</span><span class="sxs-lookup"><span data-stu-id="6a210-118">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="6a210-119">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6a210-119">Conversion Keywords</span></span>  

 <span data-ttu-id="6a210-120">Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="6a210-120">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="6a210-121">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="6a210-121">Keyword</span></span>|<span data-ttu-id="6a210-122">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="6a210-122">Data types</span></span>|<span data-ttu-id="6a210-123">Bağımsız değişken ilişkisi</span><span class="sxs-lookup"><span data-stu-id="6a210-123">Argument relationship</span></span>|<span data-ttu-id="6a210-124">Çalışma zamanı hatası</span><span class="sxs-lookup"><span data-stu-id="6a210-124">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="6a210-125">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a210-125">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="6a210-126">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="6a210-126">Any data types</span></span>|<span data-ttu-id="6a210-127">İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır</span><span class="sxs-lookup"><span data-stu-id="6a210-127">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="6a210-128">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="6a210-128">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="6a210-129">DirectCast İşleci</span><span class="sxs-lookup"><span data-stu-id="6a210-129">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="6a210-130">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="6a210-130">Any data types</span></span>|<span data-ttu-id="6a210-131">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="6a210-131">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="6a210-132">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="6a210-132">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="6a210-133">Yalnızca başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="6a210-133">Reference types only</span></span>|<span data-ttu-id="6a210-134">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="6a210-134">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="6a210-135">[Hiçbir şey](../nothing.md) döndürmez</span><span class="sxs-lookup"><span data-stu-id="6a210-135">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a210-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a210-136">Example</span></span>  

 <span data-ttu-id="6a210-137">Aşağıdaki örnek nasıl kullanılacağını göstermektedir `TryCast` .</span><span class="sxs-lookup"><span data-stu-id="6a210-137">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6a210-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a210-138">See also</span></span>

- [<span data-ttu-id="6a210-139">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6a210-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="6a210-140">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="6a210-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
