---
title: "Yapılar (F#)"
description: "F # yapısı hakkında genellikle bir compact nesne türü öğrenin küçük miktarda veri ve basit davranışı türleriyle için bir sınıf daha verimlidir."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a><span data-ttu-id="e109f-104">Yapılar</span><span class="sxs-lookup"><span data-stu-id="e109f-104">Structures</span></span>

<span data-ttu-id="e109f-105">A *yapısı* küçük miktarda veri ve basit davranışı türleri için bir sınıf daha etkili olabilir compact nesne türüdür.</span><span class="sxs-lookup"><span data-stu-id="e109f-105">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="e109f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e109f-106">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a><span data-ttu-id="e109f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e109f-107">Remarks</span></span>
<span data-ttu-id="e109f-108">Yapıları olan *değer türleri*, doğrudan yığında veya olarak kullanıldığında depolanan anlamına alanları veya dizi öğeleri, satır içi üst yazın.</span><span class="sxs-lookup"><span data-stu-id="e109f-108">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="e109f-109">Sınıfları ve kayıtları aksine, yapıları geçişi değerli semantiklerine sahip.</span><span class="sxs-lookup"><span data-stu-id="e109f-109">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="e109f-110">Bu, öncelikle erişilen ve sık kopyalanan verilerin küçük Toplamalar için yararlı oldukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e109f-110">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="e109f-111">Önceki sözdiziminde iki form gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e109f-111">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="e109f-112">İlk basit sözdizimi değil, ancak yine de sık kullandığınızda, çünkü kullanılır `struct` ve `end` anahtar sözcüklerini atlayın `StructAttribute` ikinci biçiminde görünür öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e109f-112">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="e109f-113">Kısaltma `StructAttribute` henüz için `Struct`.</span><span class="sxs-lookup"><span data-stu-id="e109f-113">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="e109f-114">*Tür tanımı öğeleri* önceki sözdiziminde üye bildirimler ve tanımlar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e109f-114">The *type-definition-elements* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="e109f-115">Yapıları oluşturucular ve kesilebilir ve değişmez alanları olabilir ve bunlar üyeleri ve arabirim uygulamaları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e109f-115">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="e109f-116">Daha fazla bilgi için bkz: [üyeleri](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="e109f-116">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="e109f-117">Yapıları devralma katılamaz, içeremez `let` veya `do` bağlamalar ve yinelemeli olarak (kendi türü başvuru başvuru hücreleri içerebilse) kendi türünde alanlar içeremez.</span><span class="sxs-lookup"><span data-stu-id="e109f-117">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="e109f-118">Yapıları izin verme çünkü `let` bağlamaları kullanarak yapıları alanlarında bildirmelidir `val` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e109f-118">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="e109f-119">`val` Anahtar sözcüğü bir alan ve türünü tanımlar ancak başlatma izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="e109f-119">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="e109f-120">Bunun yerine, `val` bildirimleri sıfır başlatılmış veya null.</span><span class="sxs-lookup"><span data-stu-id="e109f-120">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="e109f-121">Bu nedenle, gerektiren bir örtük Oluşturucu (diğer bir deyişle, hemen sonra bildiriminde yapısı adı verilen parametreleri) sahip yapıları, `val` bildirimleri açıklama ile `DefaultValue` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e109f-121">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="e109f-122">Tanımlanan bir oluşturucuya sahip yapıları hala sıfır başlatma destekler.</span><span class="sxs-lookup"><span data-stu-id="e109f-122">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="e109f-123">Bu nedenle, `DefaultValue` böyle sıfır değerini alan için geçerli bir bildirimi bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="e109f-123">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="e109f-124">Örtük oluşturucuları yapıları için kullanılmayacak herhangi bir eylem olduğundan `let` ve `do` bağlamaları türüne izin verilmiyor, ancak geçirilen örtük Oluşturucu parametre değerlerini özel alanlar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e109f-124">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="e109f-125">Açıkça oluşturucular alan değerlerinin başlatma gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e109f-125">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="e109f-126">Açık bir oluşturucuya sahip bir yapıya sahip olduğunda hala sıfır başlatma destekler; Ancak, kullanmaz `DefaultValue` özniteliği `val` bildirimleri açık Oluşturucu ile çakıştığı için.</span><span class="sxs-lookup"><span data-stu-id="e109f-126">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="e109f-127">Hakkında daha fazla bilgi için `val` bildirimleri, bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="e109f-127">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="e109f-128">Öznitelikler ve erişilebilirlik değiştiricileri yapıları izin verilir ve bu diğer türleri olarak aynı kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e109f-128">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="e109f-129">Daha fazla bilgi için bkz: [öznitelikleri](attributes.md) ve [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="e109f-129">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="e109f-130">Aşağıdaki kod örnekleri yapısı tanımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e109f-130">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="e109f-131">Yapı kaydeder ve ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="e109f-131">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="e109f-132">F # 4.1 ile başlayarak, size gösterebilir [kayıtları](records.md) ve [ayrılmış birleşimler](discriminated-unions.md) ile yapılar olarak `[<Struct>]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e109f-132">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="e109f-133">Daha fazla bilgi için her makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="e109f-133">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e109f-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e109f-134">See Also</span></span>
[<span data-ttu-id="e109f-135">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="e109f-135">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e109f-136">Sınıfları</span><span class="sxs-lookup"><span data-stu-id="e109f-136">Classes</span></span>](classes.md)

[<span data-ttu-id="e109f-137">Kayıtları</span><span class="sxs-lookup"><span data-stu-id="e109f-137">Records</span></span>](records.md)

[<span data-ttu-id="e109f-138">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="e109f-138">Members</span></span>](members/index.md)
