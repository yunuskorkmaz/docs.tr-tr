---
title: Yapılar
description: Küçük miktarda veri ve basit davranış içeren türler için bir sınıftan genellikle daha verimli olan kompakt bir nesne türü olan F# yapısı hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400283"
---
# <a name="structures"></a><span data-ttu-id="4b916-103">Yapılar</span><span class="sxs-lookup"><span data-stu-id="4b916-103">Structures</span></span>

<span data-ttu-id="4b916-104">*Yapı,* az miktarda veri ve basit davranış alabilen türler için bir sınıftan daha verimli olabilecek kompakt bir nesne türüdür.</span><span class="sxs-lookup"><span data-stu-id="4b916-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b916-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b916-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="4b916-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b916-106">Remarks</span></span>

<span data-ttu-id="4b916-107">Yapılar *değer türleridir,* bu da doğrudan yığında veya üst türde satır veya dizi öğesi olarak kullanıldıklarında depolandıkları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4b916-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="4b916-108">Sınıfların ve kayıtların aksine, yapıların pass-by-value semantik vardır.</span><span class="sxs-lookup"><span data-stu-id="4b916-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="4b916-109">Bu, bunların öncelikle erişilen ve sık sık kopyalanan küçük veri toplamları için yararlı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4b916-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="4b916-110">Önceki sözdiziminde iki form gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4b916-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="4b916-111">Birincisi hafif sözdizimi değildir, ancak yine de sık sık kullanılır, `struct` çünkü `end` anahtar kelimeleri ve anahtar `StructAttribute` kelimeleri kullandığınızda, ikinci formda görünen özniteliği atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b916-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="4b916-112">Sadece `StructAttribute` `Struct`kısaltma kullanabilirsiniz .</span><span class="sxs-lookup"><span data-stu-id="4b916-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="4b916-113">Önceki sözdiziminde *tür tanım-tanım-elemanlar ve üyeler* üye bildirimlerini ve tanımlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4b916-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="4b916-114">Yapıların oluşturucuları, mutable ve değişmez alanları olabilir ve üyeleri ve arayüz uygulamalarını bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="4b916-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="4b916-115">Daha fazla bilgi için [Üyeler'e](./members/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4b916-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="4b916-116">Yapılar kalıtıma katılamaz, `let` `do` ciltleme veya içeremez ve kendi türünden alanları özyinelemeli olarak içeremez (ancak kendi türüne başvuran referans hücreleri içerebilirler).</span><span class="sxs-lookup"><span data-stu-id="4b916-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="4b916-117">Yapılar bağlamaya `let` izin vermeygerektiğinden, `val` anahtar sözcüğü kullanarak yapılardaki alanları bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b916-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="4b916-118">`val` Anahtar kelime bir alanı ve türünü tanımlar, ancak başlatmaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="4b916-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="4b916-119">Bunun `val` yerine, bildirimler sıfır veya null olarak başharfe alınır.</span><span class="sxs-lookup"><span data-stu-id="4b916-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="4b916-120">Bu nedenle, örtük bir oluşturucuya sahip yapılar (yani bildirimdeki yapı adından hemen `val` sonra verilen parametreler) bildirimlerin öznitelik ile `DefaultValue` açıklamalı olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4b916-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="4b916-121">Tanımlı bir oluşturucuya sahip yapılar hala sıfır başlatmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="4b916-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="4b916-122">Bu nedenle, `DefaultValue` öznitelik böyle bir sıfır değeri alan için geçerli olduğunu bir bildirimdir.</span><span class="sxs-lookup"><span data-stu-id="4b916-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="4b916-123">Yapıların örtük oluşturucuları herhangi bir `let` `do` eylem gerçekleştirmez, çünkü türde bağlamalara izin verilmez, ancak geçirilen örtük yapıcı parametre değerleri özel alanlar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b916-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="4b916-124">Açık oluşturucular alan değerlerinin başlatılmasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4b916-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="4b916-125">Açık bir oluşturucuya sahip bir yapınız varsa, yine de sıfır başlatmayı destekler; ancak, açık oluşturucuile çakıştığı için `DefaultValue` `val` bildirimlerdeki özniteliği kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4b916-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="4b916-126">Bildirimler hakkında `val` daha fazla bilgi için Bkz. [Açık Alanlar: `val` Anahtar Kelime](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4b916-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="4b916-127">Özniteliklere ve erişilebilirlik değiştiricilerine yapılarda izin verilir ve diğer türler için aynı kurallara uyar.</span><span class="sxs-lookup"><span data-stu-id="4b916-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="4b916-128">Daha fazla bilgi için [Bkz. Öznitelikler](attributes.md) ve [Erişim Denetimi.](access-control.md)</span><span class="sxs-lookup"><span data-stu-id="4b916-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="4b916-129">Aşağıdaki kod örnekleri yapı tanımlarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4b916-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="4b916-130">ByRefLike structs</span><span class="sxs-lookup"><span data-stu-id="4b916-130">ByRefLike structs</span></span>

<span data-ttu-id="4b916-131">Semantik gibi kendi yapılarınızı tanımlayabilirsiniz: `byref`daha fazla bilgi için [Byrefs'a](byrefs.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="4b916-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="4b916-132">Bu öznitelik <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ile yapılır:</span><span class="sxs-lookup"><span data-stu-id="4b916-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="4b916-133">`IsByRefLike`anlamına `Struct`gelmez.</span><span class="sxs-lookup"><span data-stu-id="4b916-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="4b916-134">Her ikisi de türünde mevcut olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b916-134">Both must be present on the type.</span></span>

<span data-ttu-id="4b916-135">F#'daki "-like"`byref`struct, yığına bağlı bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="4b916-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="4b916-136">Yönetilen yığına hiçbir zaman ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="4b916-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="4b916-137">Bir `byref`-benzeri yapı, yaşam boyu ve yakalamama ile ilgili güçlü denetimler kümesiyle uygulandığından, yüksek performanslı programlama için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4b916-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="4b916-138">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4b916-138">The rules are:</span></span>

- <span data-ttu-id="4b916-139">İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem döndürürler olarak kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="4b916-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
- <span data-ttu-id="4b916-140">Bunlar statik veya bir sınıfın veya normal yapının örnek üyeleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="4b916-140">They cannot be static or instance members of a class or normal struct.</span></span>
- <span data-ttu-id="4b916-141">Herhangi bir kapatma yapısı (yöntemler`async` veya lambda ifadeleri) tarafından ele geçirilemezler.</span><span class="sxs-lookup"><span data-stu-id="4b916-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
- <span data-ttu-id="4b916-142">Genel bir parametre olarak kullanılamazlar.</span><span class="sxs-lookup"><span data-stu-id="4b916-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="4b916-143">Bu kurallar kullanımı çok güçlü bir şekilde kısıtlasa da, bunu yüksek performanslı bilgi işlem sözünü güvenli bir şekilde yerine getirmek için yapar.</span><span class="sxs-lookup"><span data-stu-id="4b916-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="4b916-144">ReadOnly structs</span><span class="sxs-lookup"><span data-stu-id="4b916-144">ReadOnly structs</span></span>

<span data-ttu-id="4b916-145">Yapılarını öznitelikile <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b916-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="4b916-146">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4b916-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="4b916-147">`IsReadOnly`anlamına `Struct`gelmez.</span><span class="sxs-lookup"><span data-stu-id="4b916-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="4b916-148">Bir `IsReadOnly` yapı ya da yapı için ikisini de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b916-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="4b916-149">Bu özniteliğin kullanımı, meta verileri, F# ve C#'ın sırasıyla `inref<'T>` ve `in ref`sırasıyla</span><span class="sxs-lookup"><span data-stu-id="4b916-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="4b916-150">Okunan bir yapının içinde değişken bir değer tanımlamak bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="4b916-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="4b916-151">Yapı Kayıtları ve Ayrımcı Birlikler</span><span class="sxs-lookup"><span data-stu-id="4b916-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="4b916-152">[Kayıtlar](records.md) ve [Ayrımcı Birleþmeler'](discriminated-unions.md) i `[<Struct>]` öznitelikile yapý cuzk olarak temsil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b916-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="4b916-153">Daha fazla bilgi edinmek için her makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="4b916-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b916-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b916-154">See also</span></span>

- [<span data-ttu-id="4b916-155">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="4b916-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4b916-156">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="4b916-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="4b916-157">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="4b916-157">Records</span></span>](records.md)
- [<span data-ttu-id="4b916-158">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4b916-158">Members</span></span>](./members/index.md)
