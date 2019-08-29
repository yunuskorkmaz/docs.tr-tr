---
title: Yapılar
description: Küçük bir veri F# miktarı ve basit davranışları olan türler için bir sınıftan daha verimli bir kompakt nesne türü yapı hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106820"
---
# <a name="structures"></a><span data-ttu-id="b01e7-103">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b01e7-103">Structures</span></span>

<span data-ttu-id="b01e7-104">*Yapı* , az miktarda veri ve basit davranışa sahip olan türler için bir sınıftan daha verimli olabilecek bir Compact nesne türüdür.</span><span class="sxs-lookup"><span data-stu-id="b01e7-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="b01e7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b01e7-105">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a><span data-ttu-id="b01e7-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b01e7-106">Remarks</span></span>

<span data-ttu-id="b01e7-107">Yapılar *değer türlerdir*, bu, doğrudan yığında depolandıkları veya alan veya dizi öğeleri olarak kullanıldıkları zaman, üst tür içinde satır içi olarak kullanıldıkları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="b01e7-108">Sınıfların ve kayıtlardan farklı olarak, yapıların değer geçişi semantiği vardır.</span><span class="sxs-lookup"><span data-stu-id="b01e7-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="b01e7-109">Bu, öncelikli olarak sık erişilen ve kopyalandığı verilerin küçük toplamalar için yararlı oldukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="b01e7-110">Önceki sözdiziminde iki form gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="b01e7-111">İlki basit sözdizimi değildir, ancak, `struct` ve `end` anahtar sözcüklerini kullandığınızda, ikinci formda görünen `StructAttribute` özniteliği atlayabilirsiniz, ancak.</span><span class="sxs-lookup"><span data-stu-id="b01e7-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="b01e7-112">`StructAttribute` Yalnızca`Struct`' i kısaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="b01e7-113">Önceki sözdiziminde bulunan *tür tanımı-öğeler-ve-Üyeler* üye bildirimlerini ve tanımlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b01e7-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="b01e7-114">Yapılar, oluşturucular ve değişebilir ve sabit alanlara sahip olabilir ve üyeleri ve arabirim uygulamalarını bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="b01e7-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="b01e7-115">Daha fazla bilgi için bkz. [Üyeler](./members/index.md).</span><span class="sxs-lookup"><span data-stu-id="b01e7-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="b01e7-116">Yapılar devralmaya katılamaz, `let` veya `do` bağlama içeremez ve kendi türündeki alanları özyinelemeli olarak içeremez (ancak kendi türlerine başvuran başvuru hücreleri içerebilse de).</span><span class="sxs-lookup"><span data-stu-id="b01e7-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="b01e7-117">Yapılar bağlamalara izin `let` vermediğinden, `val` anahtar sözcüğünü kullanarak yapıların alanlarını bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="b01e7-118">Anahtar `val` sözcüğü bir alanı ve türünü tanımlar, ancak başlatmaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="b01e7-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="b01e7-119">Bunun yerine `val` , bildirimler sıfır veya null olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b01e7-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="b01e7-120">Bu nedenle, örtük Oluşturucusu olan yapılar (diğer bir deyişle, bildirimdeki yapı adından hemen sonra verilen Parametreler), `val` bildirimlerin `DefaultValue` özniteliğiyle açıklanabilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="b01e7-121">Tanımlı bir oluşturucuya sahip olan yapılar sıfır başlatmayı desteklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="b01e7-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="b01e7-122">Bu nedenle öznitelik, bu tür sıfır değeri alan için geçerli olan bir bildirimidir. `DefaultValue`</span><span class="sxs-lookup"><span data-stu-id="b01e7-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="b01e7-123">Tür üzerinde `do` bağlamalara izin verilmediğinden, yapılar için örtük `let` oluşturucular hiçbir eylem gerçekleştirmez, ancak geçirilen örtük Oluşturucu parametre değerleri özel alanlar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="b01e7-124">Açık oluşturucular alan değerlerinin başlatılmasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="b01e7-125">Açık Oluşturucusu olan bir yapınız varsa, yine de sıfır başlatmayı destekler; Ancak, açık Oluşturucu ile çakıştığından, `DefaultValue` bu özniteliği `val` bildirimlerinde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b01e7-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="b01e7-126">Bildirimler hakkında `val` daha fazla bilgi için bkz [. açık alanlar: `val` Anahtar sözcüğü](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="b01e7-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="b01e7-127">Yapılar üzerinde özniteliklere ve erişilebilirlik değiştiricilerine izin verilir ve diğer türlerle aynı kuralları izler.</span><span class="sxs-lookup"><span data-stu-id="b01e7-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="b01e7-128">Daha fazla bilgi için bkz. [öznitelikler](attributes.md) ve [Access Control](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="b01e7-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="b01e7-129">Aşağıdaki kod örnekleri yapı tanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="b01e7-130">ByRefLike yapıları</span><span class="sxs-lookup"><span data-stu-id="b01e7-130">ByRefLike structs</span></span>

<span data-ttu-id="b01e7-131">Benzer anlambilimi olan `byref`kendi yapı birimlerinizi tanımlayabilirsiniz: daha fazla bilgi için bkz. [byrefs](byrefs.md) .</span><span class="sxs-lookup"><span data-stu-id="b01e7-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="b01e7-132">Bu, <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliğiyle yapılır:</span><span class="sxs-lookup"><span data-stu-id="b01e7-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="b01e7-133">`IsByRefLike`göstermez `Struct`.</span><span class="sxs-lookup"><span data-stu-id="b01e7-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="b01e7-134">Her ikisi de türünde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b01e7-134">Both must be present on the type.</span></span>

<span data-ttu-id="b01e7-135">İçindeki F# "`byref`-LIKE" yapısı, yığın bağlantılı bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="b01e7-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="b01e7-136">Yönetilen yığında hiçbir şekilde ayrılmadı.</span><span class="sxs-lookup"><span data-stu-id="b01e7-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="b01e7-137">Bir `byref`-LIKE yapısı, yoğun ömür ve yakalama olmayan bir güçlü denetim kümesiyle zorlandığından, yüksek performanslı programlama için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b01e7-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="b01e7-138">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b01e7-138">The rules are:</span></span>

- <span data-ttu-id="b01e7-139">İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem geri dönüş olarak kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="b01e7-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
- <span data-ttu-id="b01e7-140">Bunlar statik veya bir sınıfın ya da normal yapının örnek üyeleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-140">They cannot be static or instance members of a class or normal struct.</span></span>
- <span data-ttu-id="b01e7-141">Bunlar herhangi bir kapanış yapısı (`async` Yöntemler veya lambda ifadeleri) tarafından yakalanamaz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
- <span data-ttu-id="b01e7-142">Genel parametre olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="b01e7-143">Bu kurallar kullanımı çok kuvvetli olsa da, yüksek performanslı bilgi işlem taahhüdünü güvenli bir şekilde yerine getirmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b01e7-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="b01e7-144">ReadOnly yapılar</span><span class="sxs-lookup"><span data-stu-id="b01e7-144">ReadOnly structs</span></span>

<span data-ttu-id="b01e7-145"><xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> Özniteliği olan yapılara not ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="b01e7-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b01e7-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="b01e7-147">`IsReadOnly`göstermez `Struct`.</span><span class="sxs-lookup"><span data-stu-id="b01e7-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="b01e7-148">`IsReadOnly` Yapısına sahip olmak için her ikisini de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b01e7-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="b01e7-149">Bu özniteliğin kullanılması, verileri sırasıyla ve F# `in ref`olarak C# `inref<'T>` değerlendirmek için meta verileri yayar.</span><span class="sxs-lookup"><span data-stu-id="b01e7-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="b01e7-150">Salt okunur bir yapının içinde kesilebilir değer tanımlamak bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b01e7-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="b01e7-151">Struct kayıtları ve ayırt edici birleşimler</span><span class="sxs-lookup"><span data-stu-id="b01e7-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="b01e7-152">Özniteliği`[<Struct>]` ile yapılar olarak [kayıtları](records.md) ve [ayırt edici birleşimleri](discriminated-unions.md) temsil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="b01e7-153">Daha fazla bilgi için her makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="b01e7-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="b01e7-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b01e7-154">See also</span></span>

- [<span data-ttu-id="b01e7-155">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b01e7-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b01e7-156">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b01e7-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="b01e7-157">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="b01e7-157">Records</span></span>](records.md)
- [<span data-ttu-id="b01e7-158">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b01e7-158">Members</span></span>](./members/index.md)
