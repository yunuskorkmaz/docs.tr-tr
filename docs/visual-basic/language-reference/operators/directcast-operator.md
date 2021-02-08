---
description: 'Daha fazla bilgi edinin: DirectCast Işleci (Visual Basic)'
title: DirectCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: be1eb4885940571788769bae968b1a094e256c79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773907"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="8d740-103">DirectCast İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d740-103">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="8d740-104">Devralma veya uygulamaya göre bir tür dönüştürme işlemi sunar.</span><span class="sxs-lookup"><span data-stu-id="8d740-104">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d740-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d740-105">Remarks</span></span>  

 <span data-ttu-id="8d740-106">`DirectCast` dönüştürme için Visual Basic çalışma zamanı yardımcı yordamlarını kullanmaz, bu nedenle `CType` veri türüne dönüştürme işleminden daha iyi bir performans sağlayabilir `Object` .</span><span class="sxs-lookup"><span data-stu-id="8d740-106">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="8d740-107">`DirectCast` [CType Işlevini](../functions/ctype-function.md) ve [TryCast İşleci](trycast-operator.md) anahtar sözcüğünü kullanma yöntemine benzer şekilde anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8d740-107">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="8d740-108">İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8d740-108">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="8d740-109">`DirectCast` iki bağımsız değişkenin veri türleri arasında devralma veya uygulama ilişkisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d740-109">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="8d740-110">Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8d740-110">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="8d740-111">Hatalar ve hatalar</span><span class="sxs-lookup"><span data-stu-id="8d740-111">Errors and Failures</span></span>  

 <span data-ttu-id="8d740-112">`DirectCast` devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d740-112">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="8d740-113">Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="8d740-113">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="8d740-114">İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d740-114">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="8d740-115">Bu durumda, çalışma zamanı bir hata oluşturur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="8d740-115">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="8d740-116">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8d740-116">Conversion Keywords</span></span>  

 <span data-ttu-id="8d740-117">Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="8d740-117">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="8d740-118">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="8d740-118">Keyword</span></span>|<span data-ttu-id="8d740-119">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="8d740-119">Data types</span></span>|<span data-ttu-id="8d740-120">Bağımsız değişken ilişkisi</span><span class="sxs-lookup"><span data-stu-id="8d740-120">Argument relationship</span></span>|<span data-ttu-id="8d740-121">Çalışma zamanı hatası</span><span class="sxs-lookup"><span data-stu-id="8d740-121">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="8d740-122">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="8d740-122">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="8d740-123">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="8d740-123">Any data types</span></span>|<span data-ttu-id="8d740-124">İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır</span><span class="sxs-lookup"><span data-stu-id="8d740-124">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="8d740-125">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="8d740-125">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="8d740-126">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="8d740-126">Any data types</span></span>|<span data-ttu-id="8d740-127">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="8d740-127">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="8d740-128">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="8d740-128">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="8d740-129">TryCast İşleci</span><span class="sxs-lookup"><span data-stu-id="8d740-129">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="8d740-130">Yalnızca başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="8d740-130">Reference types only</span></span>|<span data-ttu-id="8d740-131">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="8d740-131">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="8d740-132">[Hiçbir şey](../nothing.md) döndürmez</span><span class="sxs-lookup"><span data-stu-id="8d740-132">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d740-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d740-133">Example</span></span>  

 <span data-ttu-id="8d740-134">Aşağıdaki örnek `DirectCast` , çalışma zamanında başarısız olan diğeri ve başarılı olan iki kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d740-134">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="8d740-135">Önceki örnekte, çalışma zamanı türü ' `q` dir `Double` .</span><span class="sxs-lookup"><span data-stu-id="8d740-135">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="8d740-136">`CType` ' `Double` e dönüştürülebileceğinden başarılı oldu `Integer` .</span><span class="sxs-lookup"><span data-stu-id="8d740-136">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="8d740-137">Ancak, `DirectCast` `Double` `Integer` bir dönüştürme var olsa da, çalışma zamanı türünün ile devralma ilişkisi olmadığından, ilki çalışma zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8d740-137">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="8d740-138">İkinciden `DirectCast` <xref:System.Windows.Forms.Form> Devralındığı için, türünden türüne dönüştürdüğü için ikinci başarılı olur <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="8d740-138">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d740-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d740-139">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8d740-140">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="8d740-140">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="8d740-141">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="8d740-141">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
