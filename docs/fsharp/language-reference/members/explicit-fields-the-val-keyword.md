---
title: "Açık Alanlar: val Anahtar Sözcüğü (F#)"
description: "F # hakkında 'val' öğrenme anahtar sözcük türü başlatmadan bir sınıf veya yapı türünde bir değer depolamak için bir konum bildirmek için kullanılır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="522fb-104">Açık Alanlar: val Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="522fb-104">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="522fb-105">`val` Anahtar sözcüğü başlatma olmadan bir sınıf veya yapı tür, bir değeri depolamak için bir konum bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="522fb-105">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="522fb-106">Bu şekilde bildirilen depolama konumları çağrılır *açık alanlar*.</span><span class="sxs-lookup"><span data-stu-id="522fb-106">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="522fb-107">Başka bir kullanımını `val` sözcüktür birlikte `member` otomatik uygulanan özellikler bildirmenize anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="522fb-107">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="522fb-108">Otomatik uygulanan özellikler hakkında daha fazla bilgi için bkz: [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="522fb-108">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="522fb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="522fb-109">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="522fb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="522fb-110">Remarks</span></span>
<span data-ttu-id="522fb-111">Bir sınıf veya yapı türü alanlarını tanımlamak için her zamanki gibi kullanmaktır bir `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="522fb-111">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="522fb-112">Ancak, `let` bağlamaları her zaman mümkün, gerekli veya istenmediğinde değil sınıfı oluşturucusu bir parçası olarak başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="522fb-112">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="522fb-113">Kullanabileceğiniz `val` başlatılmamış olan bir alan istediğinizde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="522fb-113">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="522fb-114">Açık alanlar, statik ya da statik olmayan olabilir.</span><span class="sxs-lookup"><span data-stu-id="522fb-114">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="522fb-115">*Erişim değiştiricisi* olabilir `public`, `private`, veya `internal`.</span><span class="sxs-lookup"><span data-stu-id="522fb-115">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="522fb-116">Varsayılan olarak açık ortak alanlardır.</span><span class="sxs-lookup"><span data-stu-id="522fb-116">By default, explicit fields are public.</span></span> <span data-ttu-id="522fb-117">Bu farklıdır `let` her zaman özel sınıflar bağlama.</span><span class="sxs-lookup"><span data-stu-id="522fb-117">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="522fb-118">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) özniteliği, birincil bir oluşturucuya sahip sınıf türleri, açık alanlar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="522fb-118">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="522fb-119">Bu öznitelik alanı sıfır olarak başlatıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="522fb-119">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="522fb-120">Alanın türü sıfır başlatma desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="522fb-120">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="522fb-121">Aşağıdakilerden biri olması durumunda bir türü sıfır başlatma destekler:</span><span class="sxs-lookup"><span data-stu-id="522fb-121">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="522fb-122">Sıfır değerine sahip bir basit türü.</span><span class="sxs-lookup"><span data-stu-id="522fb-122">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="522fb-123">Normal bir değer olarak, normal olmayan bir değer olarak ya da bir gösterimini bir değer olarak null değer destekleyen bir türü.</span><span class="sxs-lookup"><span data-stu-id="522fb-123">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="522fb-124">Sınıfları, tanımlama grupları, kayıtları, İşlevler, arabirimler, .NET başvuru türleri, bu içerir `unit` türü ve ayrılmış birleşim türü.</span><span class="sxs-lookup"><span data-stu-id="522fb-124">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="522fb-125">Bir .NET değer türü.</span><span class="sxs-lookup"><span data-stu-id="522fb-125">A .NET value type.</span></span>

- <span data-ttu-id="522fb-126">Tüm alanları varsayılan sıfır değeri destekleyen bir yapısı.</span><span class="sxs-lookup"><span data-stu-id="522fb-126">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="522fb-127">Örneğin, sabit bir alan adlı `someField` .NET yedekleme alanında adıyla gösterimi hazırladığı `someField@`, ve adlı bir özellik kullanarak depolanan değer erişim `someField`.</span><span class="sxs-lookup"><span data-stu-id="522fb-127">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="522fb-128">Değişebilir bir alan için derlenmiş .NET temsili bir .NET alandır.</span><span class="sxs-lookup"><span data-stu-id="522fb-128">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="522fb-129">`Note`.NET Framework ad `System.ComponentModel` aynı ada sahip bir öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="522fb-129">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="522fb-130">Bu öznitelik hakkında daha fazla bilgi için bkz: `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="522fb-130">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="522fb-131">Açık alanlar ve karşılaştırma, kullanımı aşağıdaki kod gösterir bir `let` birincil bir oluşturucuya sahip bir sınıfta bağlama.</span><span class="sxs-lookup"><span data-stu-id="522fb-131">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="522fb-132">Unutmayın `let`-ilişkili alan `myInt1` özeldir.</span><span class="sxs-lookup"><span data-stu-id="522fb-132">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="522fb-133">Zaman `let`-ilişkili alan `myInt1` bir üye yöntemi, kendi kendine tanımlayıcı başvurulan `this` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="522fb-133">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="522fb-134">Ancak zaman başvuruda açık alanlar `myInt2` ve `myString`, kendi kendine tanımlayıcısı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="522fb-134">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="522fb-135">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="522fb-135">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="522fb-136">Aşağıdaki kod, birincil bir oluşturucu yok bir sınıfta açık alanlar kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="522fb-136">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="522fb-137">Bu durumda, `DefaultValue` özniteliği gerekli değildir, ancak tüm alanları türü için tanımlı oluşturucular başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="522fb-137">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="522fb-138">Çıktı `35 22`.</span><span class="sxs-lookup"><span data-stu-id="522fb-138">The output is `35 22`.</span></span>

<span data-ttu-id="522fb-139">Aşağıdaki kod bir yapısında açık alanlar kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="522fb-139">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="522fb-140">Bir yapı bir değer türü olduğundan, otomatik olarak kendi alanların değerlerini sıfıra ayarlar varsayılan bir oluşturucu yoktur.</span><span class="sxs-lookup"><span data-stu-id="522fb-140">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="522fb-141">Bu nedenle, `DefaultValue` özniteliği gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="522fb-141">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="522fb-142">Çıktı `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="522fb-142">The output is `11 xyz`.</span></span>

<span data-ttu-id="522fb-143">Açık alanlar rutin kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="522fb-143">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="522fb-144">Genel olarak, mümkün olduğunda, kullanması gereken bir `let` açık bir alanı yerine bir sınıftaki bağlama.</span><span class="sxs-lookup"><span data-stu-id="522fb-144">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="522fb-145">Açık alanlar belirli birlikte çalışabilirlik senaryolarda yararlı olan, kullanılacak bir yapı tanımlamak gerektiğinde gibi bir platform çağırma çağrısı bir yerel API veya COM birlikte çalışma senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="522fb-145">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="522fb-146">Daha fazla bilgi için bkz: [dış işlevler](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="522fb-146">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="522fb-147">Hangi birincil Oluşturucusu olmadan sınıflarını yayar bir F # kod Oluşturucu ile çalışırken açık bir alanı gerekebilir başka bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="522fb-147">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="522fb-148">Açık alanlar, ayrıca iş parçacığı statik değişkenler veya benzer yapıları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="522fb-148">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="522fb-149">Daha fazla bilgi için bkz. `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="522fb-149">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="522fb-150">Zaman anahtar sözcükleri `member val` görünür birlikte bir tür tanımında otomatik olarak uygulanan bir özellik tanımını öyledir.</span><span class="sxs-lookup"><span data-stu-id="522fb-150">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="522fb-151">Daha fazla bilgi için bkz: [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="522fb-151">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="522fb-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="522fb-152">See Also</span></span>
[<span data-ttu-id="522fb-153">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="522fb-153">Properties</span></span>](properties.md)

[<span data-ttu-id="522fb-154">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="522fb-154">Members</span></span>](index.md)

[<span data-ttu-id="522fb-155">`let`Sınıflardaki bağlamaları</span><span class="sxs-lookup"><span data-stu-id="522fb-155">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
