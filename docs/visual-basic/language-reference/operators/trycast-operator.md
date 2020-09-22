---
title: TryCast İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875316"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="043ee-102">TryCast İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="043ee-102">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="043ee-103">Özel durum oluşturmayan bir tür dönüştürme işlemi sunar.</span><span class="sxs-lookup"><span data-stu-id="043ee-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="043ee-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="043ee-104">Remarks</span></span>  

 <span data-ttu-id="043ee-105">Denenen bir dönüştürme başarısız olursa `CType` ve `DirectCast` her ikisi de bir <xref:System.InvalidCastException> hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="043ee-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="043ee-106">Bu, uygulamanızın performansını olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="043ee-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="043ee-107">`TryCast`[hiçbir şey](../nothing.md)döndürmez, bu nedenle olası bir özel durumu işlemek zorunda kalmak yerine yalnızca döndürülen sonucu test etmeniz gerekir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="043ee-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="043ee-108">`TryCast`Anahtar sözcüğünü [CType Işlevini](../functions/ctype-function.md) ve [DirectCast İşleci](directcast-operator.md) anahtar sözcüğünü kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="043ee-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="043ee-109">İlk bağımsız değişken olarak bir ifade ve ikinci bağımsız değişken olarak dönüştürülecek bir tür sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="043ee-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="043ee-110">`TryCast` Yalnızca sınıflar ve arabirimler gibi başvuru türlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="043ee-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="043ee-111">İki tür arasında devralma veya uygulama ilişkisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="043ee-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="043ee-112">Bu, bir türün diğerini devralması ya da uygulamanız gereken anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="043ee-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="043ee-113">Hatalar ve hatalar</span><span class="sxs-lookup"><span data-stu-id="043ee-113">Errors and Failures</span></span>  

 <span data-ttu-id="043ee-114">`TryCast` devralma veya uygulama ilişkisi olmadığını algılarsa bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="043ee-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="043ee-115">Ancak bir derleyici hatasının olmaması, başarılı bir dönüştürmeyi garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="043ee-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="043ee-116">İstenen dönüştürme daraltılamaz, çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="043ee-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="043ee-117">Bu durumda `TryCast` [hiçbir şey](../nothing.md)döndürmez.</span><span class="sxs-lookup"><span data-stu-id="043ee-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="043ee-118">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="043ee-118">Conversion Keywords</span></span>  

 <span data-ttu-id="043ee-119">Tür dönüştürme anahtar sözcüklerini karşılaştırma aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="043ee-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="043ee-120">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="043ee-120">Keyword</span></span>|<span data-ttu-id="043ee-121">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="043ee-121">Data types</span></span>|<span data-ttu-id="043ee-122">Bağımsız değişken ilişkisi</span><span class="sxs-lookup"><span data-stu-id="043ee-122">Argument relationship</span></span>|<span data-ttu-id="043ee-123">Çalışma zamanı hatası</span><span class="sxs-lookup"><span data-stu-id="043ee-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="043ee-124">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="043ee-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="043ee-125">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="043ee-125">Any data types</span></span>|<span data-ttu-id="043ee-126">İki veri türü arasında genişletme veya daraltma dönüştürmesi tanımlanmalıdır</span><span class="sxs-lookup"><span data-stu-id="043ee-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="043ee-127">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="043ee-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="043ee-128">DirectCast İşleci</span><span class="sxs-lookup"><span data-stu-id="043ee-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="043ee-129">Tüm veri türleri</span><span class="sxs-lookup"><span data-stu-id="043ee-129">Any data types</span></span>|<span data-ttu-id="043ee-130">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="043ee-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="043ee-131">Oluşturur <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="043ee-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="043ee-132">Yalnızca başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="043ee-132">Reference types only</span></span>|<span data-ttu-id="043ee-133">Bir tür, diğer türden devralması veya uygulamamalıdır</span><span class="sxs-lookup"><span data-stu-id="043ee-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="043ee-134">[Hiçbir şey](../nothing.md) döndürmez</span><span class="sxs-lookup"><span data-stu-id="043ee-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="043ee-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="043ee-135">Example</span></span>  

 <span data-ttu-id="043ee-136">Aşağıdaki örnek nasıl kullanılacağını göstermektedir `TryCast` .</span><span class="sxs-lookup"><span data-stu-id="043ee-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="043ee-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="043ee-137">See also</span></span>

- [<span data-ttu-id="043ee-138">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="043ee-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="043ee-139">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="043ee-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
