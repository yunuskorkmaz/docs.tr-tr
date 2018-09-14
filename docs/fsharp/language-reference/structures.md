---
title: Yapılar (F#)
description: 'F # yapısı hakkında genellikle bir compact nesne türü bilgi türleri küçük miktarda veri ve basit davranışı için bir sınıf daha verimlidir.'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508456"
---
# <a name="structures"></a><span data-ttu-id="50d6f-103">Yapılar</span><span class="sxs-lookup"><span data-stu-id="50d6f-103">Structures</span></span>

<span data-ttu-id="50d6f-104">A *yapısı* küçük miktarda veri ve basit davranışı sahip türleri bir sınıf daha verimli olabilir compact nesne türüdür.</span><span class="sxs-lookup"><span data-stu-id="50d6f-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="50d6f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50d6f-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="50d6f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50d6f-106">Remarks</span></span>

<span data-ttu-id="50d6f-107">Yapıları, *değer türleri*, alanları doğrudan yığını veya olarak kullanılması durumunda depolanan anlamına gelir veya dizi öğeleri, satır içi üst yazın.</span><span class="sxs-lookup"><span data-stu-id="50d6f-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="50d6f-108">Sınıfları ve kayıtları aksine, yapıları geçişi değerli semantiklere sahip.</span><span class="sxs-lookup"><span data-stu-id="50d6f-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="50d6f-109">Bu, öncelikle küçük toplamları erişilen ve sık kopyalanan verileri için yararlı oldukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="50d6f-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="50d6f-110">Önceki sözdiziminde, iki formları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50d6f-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="50d6f-111">İlk basit söz dizimi değil, ancak yine de sık kullandığınız zaman için kullanılır `struct` ve `end` anahtar çıkarabilirsiniz `StructAttribute` ikinci formda görünen özniteliği.</span><span class="sxs-lookup"><span data-stu-id="50d6f-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="50d6f-112">Kısaltabilirsiniz `StructAttribute` yalnızca `Struct`.</span><span class="sxs-lookup"><span data-stu-id="50d6f-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="50d6f-113">*Tür-definition-öğeleri-ve-üyeleri* üye bildirimleri ve tanımları önceki sözdiziminde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50d6f-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="50d6f-114">Yapıları oluşturucular ve alanlar değişebilir ve sabit sahip olabilir ve üyeleri ve arabirim uygulamalarına bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50d6f-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="50d6f-115">Daha fazla bilgi için [üyeleri](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="50d6f-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="50d6f-116">Yapıları Devralmada alamaz, içeremez `let` veya `do` bağlamaları ve yinelemeli olarak (kendi türüne başvuru hücreleri içerebilse) kendi türünde alanlar içeremez.</span><span class="sxs-lookup"><span data-stu-id="50d6f-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="50d6f-117">Yapıları izin vermez çünkü `let` bağlamaları kullanarak yapılardaki alanlar bildirmeniz gerekir `val` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="50d6f-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="50d6f-118">`val` Anahtar sözcüğü bir alan ve türünü tanımlar ancak başlatma izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="50d6f-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="50d6f-119">Bunun yerine, `val` bildirimlerdir sıfıra başlatılmış veya null.</span><span class="sxs-lookup"><span data-stu-id="50d6f-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="50d6f-120">Bu nedenle, bir örtük Oluşturucu (diğer bir deyişle, hemen sonra bildiriminde yapısı adı verilen parametreleri) sahip yapıları gerektiren `val` bildirimleri ek açıklama ile `DefaultValue` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="50d6f-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="50d6f-121">Tanımlı bir oluşturucuya sahip yapıları sıfır başlatma yine de destekler.</span><span class="sxs-lookup"><span data-stu-id="50d6f-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="50d6f-122">Bu nedenle, `DefaultValue` özniteliği, bu tür bir sıfır değeri alan için geçerli bir bildirim.</span><span class="sxs-lookup"><span data-stu-id="50d6f-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="50d6f-123">Yapıları için örtük Oluşturucu olduğundan herhangi bir eylem gerçekleştirmeyin `let` ve `do` bağlamaları türüne izin verilmiyor, ancak geçirilen örtük Oluşturucu parametre değerlerini özel alanları olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50d6f-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="50d6f-124">Alan değerlerinin başlatma açık oluşturucuları gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="50d6f-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="50d6f-125">Açık bir oluşturucu içeren bir yapıya sahip olduğunda sıfır başlatma yine de destekler. kullanmaz ancak `DefaultValue` özniteliği `val` bildirimleri içeren açık Oluşturucu çakıştığı için.</span><span class="sxs-lookup"><span data-stu-id="50d6f-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="50d6f-126">Hakkında daha fazla bilgi için `val` bildirimleri için bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="50d6f-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="50d6f-127">Öznitelikler ve erişilebilirlik değiştiricileri yapıları izin verilir ve diğer türleri için aynı kuralları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50d6f-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="50d6f-128">Daha fazla bilgi için [öznitelikleri](attributes.md) ve [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="50d6f-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="50d6f-129">Aşağıdaki kod örnekleri, yapı tanımları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="50d6f-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="50d6f-130">ByRefLike yapılar</span><span class="sxs-lookup"><span data-stu-id="50d6f-130">ByRefLike structs</span></span>

<span data-ttu-id="50d6f-131">Uyması için kendi yapılar tanımlayabilirsiniz `byref`-ister semantiği: bkz [Zkratka](byrefs.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="50d6f-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="50d6f-132">Bunun <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliği:</span><span class="sxs-lookup"><span data-stu-id="50d6f-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="50d6f-133">`IsByRefLike` değil gelmez `Struct`.</span><span class="sxs-lookup"><span data-stu-id="50d6f-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="50d6f-134">Her ikisi de türünde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50d6f-134">Both must be present on the type.</span></span>

<span data-ttu-id="50d6f-135">Bir "`byref`-gibi" yapı F # içinde bir yığın bağlı değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="50d6f-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="50d6f-136">Bu, hiçbir zaman yönetilen yığında ayrılır.</span><span class="sxs-lookup"><span data-stu-id="50d6f-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="50d6f-137">A `byref`-gibi yaşam süresi ve yakalama olmayan hakkında güçlü denetimleri kümesiyle zorlanmış olarak yapı yüksek performanslı programlama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="50d6f-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="50d6f-138">Kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="50d6f-138">The rules are:</span></span>

* <span data-ttu-id="50d6f-139">İşlev parametrelerini, yöntem parametreleri, yerel değişkenler döner kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="50d6f-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="50d6f-140">Statik olamaz veya bir sınıf ya da normal yapı üyelerinin örneği.</span><span class="sxs-lookup"><span data-stu-id="50d6f-140">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="50d6f-141">Herhangi bir kapanış yapısı tarafından yakalanamıyor (`async` yöntemlerde veya lambda ifadelerinde).</span><span class="sxs-lookup"><span data-stu-id="50d6f-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="50d6f-142">Genel parametre olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="50d6f-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="50d6f-143">Bu kurallar çok kesin kullanımını kısıtlıyor olsa da, bunlar promise yüksek performanslı bilgi işlem güvenli bir şekilde karşılamak için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="50d6f-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="50d6f-144">Salt okunur yapılar</span><span class="sxs-lookup"><span data-stu-id="50d6f-144">ReadOnly structs</span></span>

<span data-ttu-id="50d6f-145">Yapılar ile açıklama ekleyebilirsiniz <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="50d6f-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="50d6f-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="50d6f-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="50d6f-147">`IsReadOnly` değil gelmez `Struct`.</span><span class="sxs-lookup"><span data-stu-id="50d6f-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="50d6f-148">Her ikisi de sahip olarak eklemelisiniz bir `IsReadOnly` yapısı.</span><span class="sxs-lookup"><span data-stu-id="50d6f-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="50d6f-149">Bu özniteliğin kullanımı yayan F # ile C# işleme biçimi için bilmeniz izin vererek meta verileri `inref<'T>` ve `in ref`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="50d6f-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="50d6f-150">Salt okunur yapı içinde değiştirilebilir bir değer tanımlayan bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50d6f-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="50d6f-151">Yapı kayıtları ve ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="50d6f-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="50d6f-152">Temsil ettiğiniz [kayıtları](records.md) ve [ayırt edici birleşimler](discriminated-unions.md) yapılar ile olarak `[<Struct>]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="50d6f-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="50d6f-153">Daha fazla bilgi için her bir makaleye göz atın.</span><span class="sxs-lookup"><span data-stu-id="50d6f-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="50d6f-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50d6f-154">See also</span></span>

- [<span data-ttu-id="50d6f-155">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="50d6f-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="50d6f-156">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="50d6f-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="50d6f-157">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="50d6f-157">Records</span></span>](records.md)
- [<span data-ttu-id="50d6f-158">Üyeler</span><span class="sxs-lookup"><span data-stu-id="50d6f-158">Members</span></span>](members/index.md)
