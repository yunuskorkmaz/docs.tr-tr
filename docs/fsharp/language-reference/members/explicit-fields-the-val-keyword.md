---
title: 'Açık Alanlar: Val anahtar sözcüğü'
description: Türü başlatmadan bir F# sınıf veya yapı türünde bir değeri depolamak için bir konum bildirmek üzere kullanılan ' Val ' anahtar sözcüğü hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 13e0ba2875e8accfd1c0da0e1c6fef4973309f9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627537"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="a7f32-103">Açık Alanlar: Val anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a7f32-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="a7f32-104">`val` Anahtar sözcüğü, bir değeri, bir sınıf veya yapı türünde depolayacak bir konum bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="a7f32-105">Bu şekilde belirtilen depolama konumlarına *açık alanlar*denir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="a7f32-106">`val` Anahtar sözcüğünün başka bir kullanımı, otomatik olarak uygulanan bir `member` özelliği bildirmek için anahtar kelimesiyle birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="a7f32-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="a7f32-107">Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz. [Özellikler](properties.md).</span><span class="sxs-lookup"><span data-stu-id="a7f32-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="a7f32-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7f32-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="a7f32-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7f32-109">Remarks</span></span>

<span data-ttu-id="a7f32-110">Bir sınıf veya yapı türündeki alanları tanımlamanın olağan yolu bir `let` bağlama kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="a7f32-111">`let` Ancak bağlamalar, sınıf oluşturucusunun bir parçası olarak başlatılmalıdır, bu her zaman mümkün, gerekli veya istenmez.</span><span class="sxs-lookup"><span data-stu-id="a7f32-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="a7f32-112">Başlatılmamış bir alanı istediğiniz `val` zaman anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7f32-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="a7f32-113">Açık Alanlar statik veya statik olmayan bir şekilde olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="a7f32-114">*Erişim-değiştirici* , `public` `private`veya `internal`olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="a7f32-115">Varsayılan olarak açık alanlar geneldir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-115">By default, explicit fields are public.</span></span> <span data-ttu-id="a7f32-116">Bu, her `let` zaman özel olan sınıflardaki bağlamalardan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="a7f32-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil Oluşturucusu olan sınıf türlerindeki açık alanlar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="a7f32-118">Bu öznitelik, alanın sıfıra başlatıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="a7f32-119">Alanın türü sıfır başlatmayı desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="a7f32-120">Bir tür, aşağıdakilerden biri ise sıfır başlatmayı destekler:</span><span class="sxs-lookup"><span data-stu-id="a7f32-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="a7f32-121">Sıfır değeri olan temel bir tür.</span><span class="sxs-lookup"><span data-stu-id="a7f32-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="a7f32-122">Normal değer olarak, olağan dışı bir değer olarak veya bir değerin temsili olarak null değeri destekleyen bir tür.</span><span class="sxs-lookup"><span data-stu-id="a7f32-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="a7f32-123">Bu sınıflar, tanımlama grupları, kayıtlar, işlevler, arabirimler, .net başvuru türleri, `unit` türü ve ayırt edici birleşim türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="a7f32-124">.NET değer türü.</span><span class="sxs-lookup"><span data-stu-id="a7f32-124">A .NET value type.</span></span>

- <span data-ttu-id="a7f32-125">Alanlarının tümü varsayılan sıfır değerini destekleyen bir yapı.</span><span class="sxs-lookup"><span data-stu-id="a7f32-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="a7f32-126">Örneğin, adlı `someField` bir sabit alan, .NET derlenmiş temsilinin adına `someField@`sahip bir yedekleme alanına sahiptir ve depolanan değere adlı `someField`bir özellik kullanarak erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7f32-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="a7f32-127">Kesilebilir bir alan için, .NET derlenmiş gösterimi .NET alanıdır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
><span data-ttu-id="a7f32-128">.NET Framework ad alanı `System.ComponentModel` aynı ada sahip bir özniteliği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a7f32-128">The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="a7f32-129">Bu öznitelik hakkında daha fazla bilgi için `System.ComponentModel.DefaultValueAttribute`bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f32-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="a7f32-130">Aşağıdaki kod açık alanların kullanımını ve karşılaştırma `let` için, birincil Oluşturucusu olan bir sınıftaki bağlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="a7f32-131">-Bağlanacak alanın `myInt1` özel olduğunu unutmayın. `let`</span><span class="sxs-lookup"><span data-stu-id="a7f32-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="a7f32-132">Bir üye yönteminden bağlantılı alana `myInt1` başvuruluyorsa, kendi tanımlayıcısı `this` gerekli değildir. `let`</span><span class="sxs-lookup"><span data-stu-id="a7f32-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="a7f32-133">Ancak açık alanlara `myInt2` `myString`başvururken, kendi tanımlayıcısı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="a7f32-134">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="a7f32-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="a7f32-135">Aşağıdaki kod, birincil Oluşturucusu olmayan bir sınıfta açık alanların kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="a7f32-136">Bu durumda `DefaultValue` , öznitelik gerekli değildir, ancak tüm alanların tür için tanımlanan oluşturucularda başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="a7f32-137">Çıktı `35 22`.</span><span class="sxs-lookup"><span data-stu-id="a7f32-137">The output is `35 22`.</span></span>

<span data-ttu-id="a7f32-138">Aşağıdaki kod, bir yapıda açık alanların kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="a7f32-139">Bir yapı bir değer türü olduğundan, kendi alanlarının değerlerini sıfıra ayarlayan bir varsayılan oluşturucuya otomatik olarak sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="a7f32-140">Bu nedenle, `DefaultValue` öznitelik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="a7f32-141">Çıktı `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="a7f32-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="a7f32-142">**Dikkat**edin, yapınızı `mutable` anahtar sözcük içermeyen `mutable` alanlarla başlatacaksanız, atamalarınız, atamadan sonra atılacak yapının bir kopyası üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-142">**Beware**, if you are going to initialize your structure with `mutable` fields without `mutable` keyword, your assignments will work on a copy of the structure which will be discarded right after assignment.</span></span> <span data-ttu-id="a7f32-143">Bu nedenle, yapınız değişmeyecek.</span><span class="sxs-lookup"><span data-stu-id="a7f32-143">Therefore your structure won't change.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

<span data-ttu-id="a7f32-144">Açık alanlar, rutin kullanım için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-144">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="a7f32-145">Genel olarak, mümkün olduğunda açık bir alan yerine `let` sınıfında bir bağlama kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7f32-145">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="a7f32-146">Açık alanlar, yerel API 'ye yönelik platform çağırma çağrısında veya COM birlikte çalışma senaryolarında kullanılacak bir yapı tanımlamanız gerektiğinde olduğu gibi, belirli birlikte çalışabilirlik senaryolarında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-146">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="a7f32-147">Daha fazla bilgi için bkz. [dış işlevler](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a7f32-147">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="a7f32-148">Bir açık alanın gerekli olabileceği başka bir durum ise, sınıfları birincil Oluşturucu olmadan yayar bir F# kod Oluşturucu ile çalışmaktır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-148">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="a7f32-149">Açık alanlar, iş parçacığı statik değişkenleri veya benzer yapılar için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-149">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="a7f32-150">Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="a7f32-150">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="a7f32-151">Anahtar sözcükler `member val` bir tür tanımında birlikte görüntülendiğinde, otomatik olarak uygulanan bir özelliğin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="a7f32-151">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="a7f32-152">Daha fazla bilgi için bkz. [Özellikler](properties.md).</span><span class="sxs-lookup"><span data-stu-id="a7f32-152">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7f32-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f32-153">See also</span></span>

- [<span data-ttu-id="a7f32-154">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a7f32-154">Properties</span></span>](properties.md)
- [<span data-ttu-id="a7f32-155">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a7f32-155">Members</span></span>](index.md)
- [<span data-ttu-id="a7f32-156">`let`Sınıflarda bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a7f32-156">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
