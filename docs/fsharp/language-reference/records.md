---
title: "Kayıtlar (F#)"
description: "F # kayıtları üyeleri isteğe bağlı olarak adlandırılmış değerler basit toplamalar nasıl temsil öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: 478ab74ad32cc6e53daffd1bd6229729149d2a1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="records"></a><span data-ttu-id="ec263-104">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="ec263-104">Records</span></span>

<span data-ttu-id="ec263-105">Kayıtları üyeleri isteğe bağlı olarak adlandırılmış değerler basit toplamalar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ec263-105">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="ec263-106">F # 4.1 ile başlayarak, bunlar yapılar veya reference türü ya da olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec263-106">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="ec263-107">Başvuru türleri varsayılan olarak oldukları.</span><span class="sxs-lookup"><span data-stu-id="ec263-107">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec263-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec263-108">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="ec263-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec263-109">Remarks</span></span>
<span data-ttu-id="ec263-110">Önceki sözdiziminde *typename* kayıt türünün adı *label1* ve *label2* adları olarak adlandırılan değerlerin *etiketleri*, ve *type1* ve *type2* bu değerleri türleridir.</span><span class="sxs-lookup"><span data-stu-id="ec263-110">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="ec263-111">*üye listesi* üye türü için isteğe bağlı bir listedir.</span><span class="sxs-lookup"><span data-stu-id="ec263-111">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="ec263-112">Kullanabileceğiniz `[<Struct>]` bir başvuru türü olan bir kaydı yerine bir yapı kaydı oluşturmak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ec263-112">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="ec263-113">Bazı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ec263-113">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="ec263-114">Her etiket ayrı bir satırda, noktalı virgülü isteğe bağlı olur.</span><span class="sxs-lookup"><span data-stu-id="ec263-114">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="ec263-115">Değerleri olarak bilinen ifadelerde belirleyebileceğiniz *kayıt ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="ec263-115">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="ec263-116">Derleyici (etiketleri yeterince farklı diğer kayıt türleri olanlardan varsa) kullanılan etiketler türünden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec263-116">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="ec263-117">Kaşlı ayraçlar kayıt deyimi alın.</span><span class="sxs-lookup"><span data-stu-id="ec263-117">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="ec263-118">Aşağıdaki kod etiketlerle üç float öğeleri içeren bir kayıt başlatır kayıt ifade gösterir `x`, `y` ve `z`.</span><span class="sxs-lookup"><span data-stu-id="ec263-118">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="ec263-119">Olabilir, ayrıca aynı etikete sahip başka bir tür kısaltılmış şekilde kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ec263-119">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="ec263-120">En son bildirilen etiketleri olanlar daha önce bildirilen bir türe önceliklidir önceki örnekte, bunu `mypoint3D` olmasını olayla `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="ec263-120">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="ec263-121">Aşağıdaki kod olduğu gibi kayıt türü açık olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec263-121">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="ec263-122">Yöntemleri, yalnızca sınıf türleri için kayıt türleri için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ec263-122">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="ec263-123">Kayıt ifadeler kullanarak kayıtları oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec263-123">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="ec263-124">Kayıtları kayıtta tanımlı etiketleri kullanarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec263-124">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="ec263-125">Bu bir ifade olarak adlandırılır bir *kayıt ifade*.</span><span class="sxs-lookup"><span data-stu-id="ec263-125">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="ec263-126">Kayıt deyimi alın ve noktalı virgül ayırıcı olarak kullanmak için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec263-126">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="ec263-127">Aşağıdaki örnek, bir kayıt oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ec263-127">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="ec263-128">Kayıt ifadesinde ve tür tanımı son alanından sonra noktalı alanların tümünü tek bir satırı içinde olup bağımsız olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ec263-128">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="ec263-129">Bir kayıt oluşturduğunuzda, her bir alan için değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec263-129">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="ec263-130">Herhangi bir alan için başlatma ifadedeki diğer alanların değerlerini başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="ec263-130">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="ec263-131">Aşağıdaki kodda, türü `myRecord2` alanları adlarından algılanır.</span><span class="sxs-lookup"><span data-stu-id="ec263-131">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="ec263-132">İsteğe bağlı olarak, tür adı açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec263-132">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="ec263-133">Varolan bir kaydı kopyalayın ve büyük olasılıkla bazı alan değerleri değiştirmek zorunda kayıt yapım başka bir formu kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec263-133">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="ec263-134">Aşağıdaki kod satırını bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ec263-134">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="ec263-135">Bu form kayıt ifadesinin adlı *kopyalama ve güncelleştirme kayıt ifade*.</span><span class="sxs-lookup"><span data-stu-id="ec263-135">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="ec263-136">Varsayılan olarak değişmez kayıtlarıdır; Ancak, kopyalama ve güncelleştirme ifade kullanarak değiştirilen kayıtları kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec263-136">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="ec263-137">Aynı zamanda açıkça değişebilir bir alan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec263-137">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="ec263-138">DefaultValue özniteliği kaydı alanlarla kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ec263-138">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="ec263-139">Daha iyi bir kayıt başlatılmış alanları ile varsayılan örnekleri için varsayılan değerleri tanımlayın ve ardından bir kopyasını kullanın ve varsayılan değerlerinden farklı alanları ayarlamak için kayıt ifade güncelleştirmek için yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="ec263-139">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="ec263-140">Desen eşleştirme kayıtlarıyla</span><span class="sxs-lookup"><span data-stu-id="ec263-140">Pattern Matching with Records</span></span>
<span data-ttu-id="ec263-141">Kayıtları desen eşleştirme ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec263-141">Records can be used with pattern matching.</span></span> <span data-ttu-id="ec263-142">Bazı alanlar açıkça belirtmek ve bir eşleşme oluştuğunda atanacak diğer alanlar için değişkenleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ec263-142">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="ec263-143">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec263-143">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="ec263-144">Bu kod çıkışı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="ec263-144">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="ec263-145">Kayıtlar ve sınıflar arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="ec263-145">Differences Between Records and Classes</span></span>
<span data-ttu-id="ec263-146">Kayıt alanları otomatik olarak bir özellik olarak sunulan ve oluşturmada kullanılan ve kayıtların kopyalama sınıflardan farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec263-146">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="ec263-147">Kayıt oluşturma da sınıfı yapım farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ec263-147">Record construction also differs from class construction.</span></span> <span data-ttu-id="ec263-148">Bir kayıt türü bir oluşturucu tanımlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="ec263-148">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="ec263-149">Bunun yerine, bu konuda açıklanan yapım sözdizimi geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ec263-149">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="ec263-150">Sınıfları Oluşturucusu parametreleri, alanları ve özellikleri arasında doğrudan hiçbir ilişki sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ec263-150">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="ec263-151">Birleşim ve yapı türleri gibi kayıtları yapısal eşitlik semantiklerine sahip.</span><span class="sxs-lookup"><span data-stu-id="ec263-151">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="ec263-152">Sınıfları sahip referans eşitlik semantiği.</span><span class="sxs-lookup"><span data-stu-id="ec263-152">Classes have reference equality semantics.</span></span> <span data-ttu-id="ec263-153">Aşağıdaki kod örneğinde bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec263-153">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="ec263-154">Sınıfları içeren aynı kodu yazarsanız, iki sınıf nesnelerine çünkü iki değer yığında iki nesneleri temsil eder ve yalnızca adresleri karşılaştırıldığında eşit olacaktır (sınıf türü geçersiz kılmadıkça `System.Object.Equals` yöntemi).</span><span class="sxs-lookup"><span data-stu-id="ec263-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="ec263-155">Eşitlik kayıtları için referans olursa öznitelik Ekle `[<ReferenceEquality>]` kaydı üstünde.</span><span class="sxs-lookup"><span data-stu-id="ec263-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec263-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec263-156">See Also</span></span>
[<span data-ttu-id="ec263-157">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="ec263-157">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="ec263-158">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="ec263-158">Classes</span></span>](classes.md)

[<span data-ttu-id="ec263-159">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ec263-159">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="ec263-160">Başvuru eşitliği</span><span class="sxs-lookup"><span data-stu-id="ec263-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="ec263-161">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="ec263-161">Pattern Matching</span></span>](pattern-matching.md)
