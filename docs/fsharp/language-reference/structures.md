---
title: Yapılar (F#)
description: 'F # yapısı hakkında genellikle bir compact nesne türü öğrenin küçük miktarda veri ve basit davranışı türleriyle için bir sınıf daha verimlidir.'
ms.date: 05/16/2016
ms.openlocfilehash: 57c4148aec1d6a19237d74aa99824ef475c3632e
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172470"
---
# <a name="structures"></a><span data-ttu-id="58dec-103">Yapılar</span><span class="sxs-lookup"><span data-stu-id="58dec-103">Structures</span></span>

<span data-ttu-id="58dec-104">A *yapısı* küçük miktarda veri ve basit davranışı türleri için bir sınıf daha etkili olabilir compact nesne türüdür.</span><span class="sxs-lookup"><span data-stu-id="58dec-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="58dec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58dec-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="58dec-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58dec-106">Remarks</span></span>
<span data-ttu-id="58dec-107">Yapıları olan *değer türleri*, doğrudan yığında veya olarak kullanıldığında depolanan anlamına alanları veya dizi öğeleri, satır içi üst yazın.</span><span class="sxs-lookup"><span data-stu-id="58dec-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="58dec-108">Sınıfları ve kayıtları aksine, yapıları geçişi değerli semantiklerine sahip.</span><span class="sxs-lookup"><span data-stu-id="58dec-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="58dec-109">Bu, öncelikle erişilen ve sık kopyalanan verilerin küçük Toplamalar için yararlı oldukları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="58dec-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="58dec-110">Önceki sözdiziminde iki form gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58dec-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="58dec-111">İlk basit sözdizimi değil, ancak yine de sık kullandığınızda, çünkü kullanılır `struct` ve `end` anahtar sözcüklerini atlayın `StructAttribute` ikinci biçiminde görünür öznitelik.</span><span class="sxs-lookup"><span data-stu-id="58dec-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="58dec-112">Kısaltma `StructAttribute` henüz için `Struct`.</span><span class="sxs-lookup"><span data-stu-id="58dec-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="58dec-113">*Tür-tanımı-öğeleri-ve-üyeleri* üye bildirimler ve tanımlar önceki sözdiziminde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58dec-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="58dec-114">Yapıları oluşturucular ve kesilebilir ve değişmez alanları olabilir ve bunlar üyeleri ve arabirim uygulamaları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58dec-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="58dec-115">Daha fazla bilgi için bkz: [üyeleri](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="58dec-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="58dec-116">Yapıları devralma katılamaz, içeremez `let` veya `do` bağlamalar ve yinelemeli olarak (kendi türü başvuru başvuru hücreleri içerebilse) kendi türünde alanlar içeremez.</span><span class="sxs-lookup"><span data-stu-id="58dec-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="58dec-117">Yapıları izin verme çünkü `let` bağlamaları kullanarak yapıları alanlarında bildirmelidir `val` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="58dec-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="58dec-118">`val` Anahtar sözcüğü bir alan ve türünü tanımlar ancak başlatma izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="58dec-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="58dec-119">Bunun yerine, `val` bildirimleri sıfır başlatılmış veya null.</span><span class="sxs-lookup"><span data-stu-id="58dec-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="58dec-120">Bu nedenle, gerektiren bir örtük Oluşturucu (diğer bir deyişle, hemen sonra bildiriminde yapısı adı verilen parametreleri) sahip yapıları, `val` bildirimleri açıklama ile `DefaultValue` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="58dec-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="58dec-121">Tanımlanan bir oluşturucuya sahip yapıları hala sıfır başlatma destekler.</span><span class="sxs-lookup"><span data-stu-id="58dec-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="58dec-122">Bu nedenle, `DefaultValue` böyle sıfır değerini alan için geçerli bir bildirimi bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="58dec-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="58dec-123">Örtük oluşturucuları yapıları için kullanılmayacak herhangi bir eylem olduğundan `let` ve `do` bağlamaları türüne izin verilmiyor, ancak geçirilen örtük Oluşturucu parametre değerlerini özel alanlar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="58dec-124">Açıkça oluşturucular alan değerlerinin başlatma gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="58dec-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="58dec-125">Açık bir oluşturucuya sahip bir yapıya sahip olduğunda hala sıfır başlatma destekler; Ancak, kullanmaz `DefaultValue` özniteliği `val` bildirimleri açık Oluşturucu ile çakıştığı için.</span><span class="sxs-lookup"><span data-stu-id="58dec-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="58dec-126">Hakkında daha fazla bilgi için `val` bildirimleri, bkz: [açık alanlar: `val` anahtar sözcüğü](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="58dec-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="58dec-127">Öznitelikler ve erişilebilirlik değiştiricileri yapıları izin verilir ve bu diğer türleri olarak aynı kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="58dec-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="58dec-128">Daha fazla bilgi için bkz: [öznitelikleri](attributes.md) ve [erişim denetimi](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="58dec-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="58dec-129">Aşağıdaki kod örnekleri yapısı tanımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58dec-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="58dec-130">Yapı kaydeder ve ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="58dec-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="58dec-131">F # 4.1 ile başlayarak, size gösterebilir [kayıtları](records.md) ve [ayrılmış birleşimler](discriminated-unions.md) ile yapılar olarak `[<Struct>]` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="58dec-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="58dec-132">Daha fazla bilgi için her makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="58dec-132">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="58dec-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58dec-133">See Also</span></span>
[<span data-ttu-id="58dec-134">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="58dec-134">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="58dec-135">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="58dec-135">Classes</span></span>](classes.md)

[<span data-ttu-id="58dec-136">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="58dec-136">Records</span></span>](records.md)

[<span data-ttu-id="58dec-137">Üyeler</span><span class="sxs-lookup"><span data-stu-id="58dec-137">Members</span></span>](members/index.md)
