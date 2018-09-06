---
title: Yapılar (F#)
description: 'F # yapısı hakkında genellikle bir compact nesne türü bilgi türleri küçük miktarda veri ve basit davranışı için bir sınıf daha verimlidir.'
ms.date: 05/16/2016
ms.openlocfilehash: 889d493af3c9c388bdc7969c02bc7b021b82517d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799677"
---
# <a name="structures"></a><span data-ttu-id="fd726-103">Yapılar</span><span class="sxs-lookup"><span data-stu-id="fd726-103">Structures</span></span>

<span data-ttu-id="fd726-104">A *yapısı* küçük miktarda veri ve basit davranışı sahip türleri bir sınıf daha verimli olabilir compact nesne türüdür.</span><span class="sxs-lookup"><span data-stu-id="fd726-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd726-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd726-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="fd726-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd726-106">Remarks</span></span>

<span data-ttu-id="fd726-107">Yapıları, *değer türleri*, alanları doğrudan yığını veya olarak kullanılması durumunda depolanan anlamına gelir veya dizi öğeleri, satır içi üst yazın.</span><span class="sxs-lookup"><span data-stu-id="fd726-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="fd726-108">Sınıfları ve kayıtları aksine, yapıları geçişi değerli semantiklere sahip.</span><span class="sxs-lookup"><span data-stu-id="fd726-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="fd726-109">Bu, öncelikle küçük toplamları erişilen ve sık kopyalanan verileri için yararlı oldukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fd726-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="fd726-110">Önceki sözdiziminde, iki formları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd726-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="fd726-111">İlk basit söz dizimi değil, ancak yine de sık kullandığınız zaman için kullanılır `struct` ve `end` anahtar çıkarabilirsiniz `StructAttribute` ikinci formda görünen özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd726-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="fd726-112">Kısaltabilirsiniz `StructAttribute` yalnızca `Struct`.</span><span class="sxs-lookup"><span data-stu-id="fd726-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="fd726-113">*Tür-definition-öğeleri-ve-üyeleri* üye bildirimleri ve tanımları önceki sözdiziminde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd726-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="fd726-114">Yapıları oluşturucular ve alanlar değişebilir ve sabit sahip olabilir ve üyeleri ve arabirim uygulamalarına bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd726-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="fd726-115">Daha fazla bilgi için [üyeleri](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="fd726-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="fd726-116">Yapıları Devralmada alamaz, içeremez `let` veya `do` bağlamaları ve yinelemeli olarak (kendi türüne başvuru hücreleri içerebilse) kendi türünde alanlar içeremez.</span><span class="sxs-lookup"><span data-stu-id="fd726-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="fd726-117">Yapıları izin vermez çünkü `let` bağlamaları kullanarak yapılardaki alanlar bildirmeniz gerekir `val` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fd726-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="fd726-118">`val` Anahtar sözcüğü bir alan ve türünü tanımlar ancak başlatma izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="fd726-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="fd726-119">Bunun yerine, `val` bildirimlerdir sıfıra başlatılmış veya null.</span><span class="sxs-lookup"><span data-stu-id="fd726-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="fd726-120">Bu nedenle, bir örtük Oluşturucu (diğer bir deyişle, hemen sonra bildiriminde yapısı adı verilen parametreleri) sahip yapıları gerektiren `val` bildirimleri ek açıklama ile `DefaultValue` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd726-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="fd726-121">Tanımlı bir oluşturucuya sahip yapıları sıfır başlatma yine de destekler.</span><span class="sxs-lookup"><span data-stu-id="fd726-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="fd726-122">Bu nedenle, `DefaultValue` özniteliği, bu tür bir sıfır değeri alan için geçerli bir bildirim.</span><span class="sxs-lookup"><span data-stu-id="fd726-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="fd726-123">Yapıları için örtük Oluşturucu olduğundan herhangi bir eylem gerçekleştirmeyin `let` ve `do` bağlamaları türüne izin verilmiyor, ancak geçirilen örtük Oluşturucu parametre değerlerini özel alanları olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd726-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="fd726-124">Alan değerlerinin başlatma açık oluşturucuları gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="fd726-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="fd726-125">Açık bir oluşturucu içeren bir yapıya sahip olduğunda sıfır başlatma yine de destekler. kullanmaz ancak `DefaultValue` özniteliği `val` bildirimleri içeren açık Oluşturucu çakıştığı için.</span><span class="sxs-lookup"><span data-stu-id="fd726-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="fd726-126">Hakkında daha fazla bilgi için `val` bildirimleri için bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="fd726-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="fd726-127">Öznitelikler ve erişilebilirlik değiştiricileri yapıları izin verilir ve diğer türleri için aynı kuralları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fd726-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="fd726-128">Daha fazla bilgi için [öznitelikleri](attributes.md) ve [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="fd726-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="fd726-129">Aşağıdaki kod örnekleri, yapı tanımları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fd726-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="fd726-130">Yapı kayıtları ve ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="fd726-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="fd726-131">F # 4.1 ile başlayarak, gösterebilir [kayıtları](records.md) ve [ayırt edici birleşimler](discriminated-unions.md) yapılar ile olarak `[<Struct>]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd726-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="fd726-132">Daha fazla bilgi için her bir makaleye göz atın.</span><span class="sxs-lookup"><span data-stu-id="fd726-132">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd726-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd726-133">See also</span></span>

- [<span data-ttu-id="fd726-134">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fd726-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="fd726-135">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="fd726-135">Classes</span></span>](classes.md)
- [<span data-ttu-id="fd726-136">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="fd726-136">Records</span></span>](records.md)
- [<span data-ttu-id="fd726-137">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fd726-137">Members</span></span>](members/index.md)
