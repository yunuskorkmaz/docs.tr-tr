---
title: 'Açık Alanlar: val Anahtar Sözcüğü (F#)'
description: "F # hakkında 'val' öğrenin anahtar sözcüğü bir değer türü başlatma olmadan bir sınıf veya yapı türü depolamak için bir konum bildirmek için kullanılır."
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262470"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="1f348-103">Açık Alanlar: val Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="1f348-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="1f348-104">`val` Anahtar sözcüğü, bir değer başlatma olmadan bir sınıf veya yapı türü depolamak için bir konum bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f348-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="1f348-105">Bu şekilde bildirilen depolama konumları çağrılır *açık alanlar*.</span><span class="sxs-lookup"><span data-stu-id="1f348-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="1f348-106">Başka bir kullanımını `val` anahtar sözcüğü, birlikte `member` otomatik uygulanan bir özellik bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1f348-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="1f348-107">Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="1f348-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="1f348-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f348-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="1f348-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f348-109">Remarks</span></span>

<span data-ttu-id="1f348-110">Bir sınıf veya yapı türü alanlarını tanımlamak için her zamanki şekilde kullanmaktır bir `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="1f348-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="1f348-111">Ancak, `let` bağlamaları her zaman mümkün, gerekli veya arzu değil, sınıf oluşturucusu bir parçası olarak başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f348-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="1f348-112">Kullanabileceğiniz `val` başlatılmamış bir alan istediğinizde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1f348-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="1f348-113">Açık alanlar, statik veya statik olmayan olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f348-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="1f348-114">*Erişim değiştiricisi* olabilir `public`, `private`, veya `internal`.</span><span class="sxs-lookup"><span data-stu-id="1f348-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="1f348-115">Varsayılan olarak açık alanlar ortaktır.</span><span class="sxs-lookup"><span data-stu-id="1f348-115">By default, explicit fields are public.</span></span> <span data-ttu-id="1f348-116">Bu farklıdır `let` her zaman özel sınıflar, bağlarında.</span><span class="sxs-lookup"><span data-stu-id="1f348-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="1f348-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil bir oluşturucuya sahip sınıf türleri açık alanları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f348-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="1f348-118">Bu öznitelik alanı sıfır olarak başlatılır belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f348-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="1f348-119">Sıfır başlatma alanın türünü desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f348-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="1f348-120">Aşağıdakilerden biri ise sıfır başlatma türü destekler:</span><span class="sxs-lookup"><span data-stu-id="1f348-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="1f348-121">Sıfır değerine sahip bir basit türü.</span><span class="sxs-lookup"><span data-stu-id="1f348-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="1f348-122">Normal bir değer olarak, olağan dışı bir değer olarak veya bir temsili bir değer olarak null değeri destekleyen bir türü.</span><span class="sxs-lookup"><span data-stu-id="1f348-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="1f348-123">Sınıflar, diziler, kayıtları, İşlevler, arabirimler, .NET başvuru türleri, bu içerir `unit` türü ve ayrılmış birleşim türleri.</span><span class="sxs-lookup"><span data-stu-id="1f348-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="1f348-124">Bir .NET değer türü.</span><span class="sxs-lookup"><span data-stu-id="1f348-124">A .NET value type.</span></span>

- <span data-ttu-id="1f348-125">Tüm alanları varsayılan bir sıfır değeri destekleyen bir yapısı.</span><span class="sxs-lookup"><span data-stu-id="1f348-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="1f348-126">Örneğin, sabit bir alan olarak adlandırılan `someField` . NET'te destek alanı gösterimi adı ile derlenmiş olan `someField@`, ve depolanan değeri adlı bir özellik kullanarak erişim `someField`.</span><span class="sxs-lookup"><span data-stu-id="1f348-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="1f348-127">Değişebilir bir alan için bir .NET alan derlenmiş .NET gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="1f348-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
<span data-ttu-id="1f348-128">`Note` .NET Framework ad alanı `System.ComponentModel` aynı ada sahip bir öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1f348-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="1f348-129">Bu özniteliği hakkında daha fazla bilgi için bkz: `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1f348-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="1f348-130">Açık alanlar ve karşılaştırma, kullanımı aşağıdaki kodda gösterildiği bir `let` birincil Oluşturucusu olan bir sınıf içinde bağlama.</span><span class="sxs-lookup"><span data-stu-id="1f348-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="1f348-131">Unutmayın `let`-ilişkili alan `myInt1` özeldir.</span><span class="sxs-lookup"><span data-stu-id="1f348-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="1f348-132">Zaman `let`-ilişkili alan `myInt1` bir üye yöntemi, kendi kendine tanımlayıcısı başvurulan `this` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1f348-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="1f348-133">Ancak, başvuruda açık alanlar `myInt2` ve `myString`, kendi kendine tanımlayıcısı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1f348-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="1f348-134">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1f348-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="1f348-135">Aşağıdaki kod, birincil bir oluşturucuya sahip değil bir sınıfta açık alanlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f348-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="1f348-136">Bu durumda, `DefaultValue` öznitelik gerekli değildir, ancak tüm alanları türü için tanımlanan Yapıcılardaki başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f348-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="1f348-137">Çıktı `35 22`.</span><span class="sxs-lookup"><span data-stu-id="1f348-137">The output is `35 22`.</span></span>

<span data-ttu-id="1f348-138">Aşağıdaki kod, bir yapıda açık alanlar kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f348-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="1f348-139">Bir yapı bir değer türü olduğundan, otomatik olarak, alanların değerlerini sıfır olarak ayarlayan bir varsayılan oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="1f348-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="1f348-140">Bu nedenle, `DefaultValue` öznitelik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1f348-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="1f348-141">Çıktı `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="1f348-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="1f348-142">Açık alanlar rutin kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="1f348-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="1f348-143">Genel olarak, mümkün olduğunda kullanmalısınız bir `let` açık bir alanı yerine bir sınıftaki bağlama.</span><span class="sxs-lookup"><span data-stu-id="1f348-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="1f348-144">Açık alanlar bazı birlikte çalışabilirlik senaryolarında yararlıdır, kullanılacak bir yapı tanımla gerektiğinde gibi bir platform çağırma çağrısı bir yerel API veya COM birlikte çalışma senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="1f348-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="1f348-145">Daha fazla bilgi için [dış işlevler](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1f348-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="1f348-146">Hangi birincil Oluşturucu olmadan sınıfları yayan bir F # kodu Oluşturucu ile çalışırken açık bir alan gerekli olabilir başka bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="1f348-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="1f348-147">Açık alanlar da iş parçacığı statik değişkenler veya benzer yapıları için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f348-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="1f348-148">Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="1f348-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="1f348-149">Zaman anahtar sözcükleri `member val` bir arada göründüğünü tür tanımında, otomatik olarak uygulanan bir özellik tanımı öyledir.</span><span class="sxs-lookup"><span data-stu-id="1f348-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="1f348-150">Daha fazla bilgi için [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="1f348-150">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f348-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f348-151">See also</span></span>

- [<span data-ttu-id="1f348-152">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1f348-152">Properties</span></span>](properties.md)
- [<span data-ttu-id="1f348-153">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1f348-153">Members</span></span>](index.md)
- [<span data-ttu-id="1f348-154">`let` Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1f348-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
