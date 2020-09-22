---
title: DirectCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 7b070b8eba240440821f7984a9336c2ecaf61706
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867093"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="b3931-102">DirectCast İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3931-102">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="b3931-103">Devralma veya uygulamaya göre bir tür dönüştürme işlemi sunar.</span><span class="sxs-lookup"><span data-stu-id="b3931-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3931-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3931-104">Remarks</span></span>  

 <span data-ttu-id="b3931-105">`DirectCast` dönüştürme için Visual Basic çalışma zamanı yardımcı yordamlarını kullanmaz, bu nedenle `CType` veri türüne dönüştürme işleminden daha iyi bir performans sağlayabilir `Object` .</span><span class="sxs-lookup"><span data-stu-id="b3931-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="b3931-106">`DirectCast` [CType Işlevini](../functions/ctype-function.md) ve [TryCast İşleci](trycast-operator.md) anahtar sözcüğünü kullanma yöntemine benzer şekilde anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b3931-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="b3931-107">İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b3931-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="b3931-108">`DirectCast` iki bağımsız değişkenin veri türleri arasında devralma veya uygulama ilişkisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b3931-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="b3931-109">Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b3931-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="b3931-110">Hatalar ve hatalar</span><span class="sxs-lookup"><span data-stu-id="b3931-110">Errors and Failures</span></span>  

 <span data-ttu-id="b3931-111">`DirectCast` devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3931-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="b3931-112">Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="b3931-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="b3931-113">İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3931-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="b3931-114">Bu durumda, çalışma zamanı bir hata oluşturur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="b3931-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="b3931-115">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b3931-115">Conversion Keywords</span></span>  

 <span data-ttu-id="b3931-116">Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="b3931-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="b3931-117">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="b3931-117">Keyword</span></span>|<span data-ttu-id="b3931-118">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b3931-118">Data types</span></span>|<span data-ttu-id="b3931-119">Bağımsız değişken ilişkisi</span><span class="sxs-lookup"><span data-stu-id="b3931-119">Argument relationship</span></span>|<span data-ttu-id="b3931-120">Çalışma zamanı hatası</span><span class="sxs-lookup"><span data-stu-id="b3931-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="b3931-121">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="b3931-121">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="b3931-122">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="b3931-122">Any data types</span></span>|<span data-ttu-id="b3931-123">İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır</span><span class="sxs-lookup"><span data-stu-id="b3931-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="b3931-124">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b3931-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="b3931-125">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="b3931-125">Any data types</span></span>|<span data-ttu-id="b3931-126">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="b3931-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b3931-127">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="b3931-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="b3931-128">TryCast İşleci</span><span class="sxs-lookup"><span data-stu-id="b3931-128">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="b3931-129">Yalnızca başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="b3931-129">Reference types only</span></span>|<span data-ttu-id="b3931-130">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="b3931-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="b3931-131">[Hiçbir şey](../nothing.md) döndürmez</span><span class="sxs-lookup"><span data-stu-id="b3931-131">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b3931-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3931-132">Example</span></span>  

 <span data-ttu-id="b3931-133">Aşağıdaki örnek `DirectCast` , çalışma zamanında başarısız olan diğeri ve başarılı olan iki kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3931-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="b3931-134">Önceki örnekte, çalışma zamanı türü ' `q` dir `Double` .</span><span class="sxs-lookup"><span data-stu-id="b3931-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="b3931-135">`CType` ' `Double` e dönüştürülebileceğinden başarılı oldu `Integer` .</span><span class="sxs-lookup"><span data-stu-id="b3931-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="b3931-136">Ancak, `DirectCast` `Double` `Integer` bir dönüştürme var olsa da, çalışma zamanı türünün ile devralma ilişkisi olmadığından, ilki çalışma zamanında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b3931-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="b3931-137">İkinciden `DirectCast` <xref:System.Windows.Forms.Form> Devralındığı için, türünden türüne dönüştürdüğü için ikinci başarılı olur <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="b3931-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3931-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3931-138">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b3931-139">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b3931-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="b3931-140">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b3931-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
