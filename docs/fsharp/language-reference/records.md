---
title: Kayıtlar
description: Bilgi nasıl F# kayıtları basit toplamalarla üyeleri ile isteğe bağlı olarak adlandırılan değerleri temsil eder.
ms.date: 06/09/2019
ms.openlocfilehash: cfb8de8272b479571119ae4cf91ea1d6fd5db73c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816195"
---
# <a name="records"></a><span data-ttu-id="67f45-103">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="67f45-103">Records</span></span>

<span data-ttu-id="67f45-104">Kayıtları basit toplamalarla üyeleri ile isteğe bağlı olarak adlandırılan değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="67f45-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="67f45-105">Bunlar, yapılar veya başvuru türleri ya da olabilir.</span><span class="sxs-lookup"><span data-stu-id="67f45-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="67f45-106">Bunlar, başvuru türleri varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="67f45-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="67f45-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67f45-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="67f45-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67f45-108">Remarks</span></span>

<span data-ttu-id="67f45-109">Önceki sözdiziminde, *typename* adı kayıt türü *label1* ve *etiket 2* adları olarak adlandırılan değerleri *etiketleri*, ve *type1* ve *type2* bu değerleri türleridir.</span><span class="sxs-lookup"><span data-stu-id="67f45-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="67f45-110">*üye listesi* üye türü için isteğe bağlı bir listedir.</span><span class="sxs-lookup"><span data-stu-id="67f45-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="67f45-111">Kullanabileceğiniz `[<Struct>]` olan bir başvuru türüdür a kaydı yerine bir yapı kaydı oluşturmak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="67f45-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="67f45-112">Bazı örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67f45-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="67f45-113">Her etiket ayrı bir satırda, noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67f45-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="67f45-114">Bilinen ifadelerde değerlerini ayarlayabilirsiniz *kayıt ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="67f45-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="67f45-115">Derleyici (etiketler yeterince diğer kayıt türleri olanlardan farklıdır) kullanılıyorsa etiketleri türünden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="67f45-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="67f45-116">Küme ayraçları ({}) kaydı ifadesi içine alın.</span><span class="sxs-lookup"><span data-stu-id="67f45-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="67f45-117">Aşağıdaki kod etiketlerle üç float öğeleri içeren bir kayıt başlatan bir kayıt ifadesi gösterir `x`, `y` ve `z`.</span><span class="sxs-lookup"><span data-stu-id="67f45-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="67f45-118">Ayrıca aynı etikete sahip başka bir tür olabilir, kısaltılmış kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="67f45-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="67f45-119">Etiketler en kısa süre önce bildirilen türü, bunlar daha önce bildirilen tür önceliklidir önceki örnekte, bu nedenle `mypoint3D` olmasını çıkarılan `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="67f45-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="67f45-120">Kayıt türü, aşağıdaki kodda gösterildiği gibi açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f45-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="67f45-121">Yöntem, sınıf türleri olduğu gibi kayıt türleri için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="67f45-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="67f45-122">Kayıt ifadelerini kullanarak kayıtları oluşturma</span><span class="sxs-lookup"><span data-stu-id="67f45-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="67f45-123">Kayıt içinde tanımlanan etiketleri kullanarak kayıtları başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f45-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="67f45-124">Bunu yapan bir ifade olarak belirtilen bir *kayıt ifade*.</span><span class="sxs-lookup"><span data-stu-id="67f45-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="67f45-125">Kayıt ifadesi içine alın ve noktalı virgül sınırlayıcı olarak kullanmak için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="67f45-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="67f45-126">Aşağıdaki örnek, bir kayıt oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67f45-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="67f45-127">Noktalı virgüller sonra kaydı ifadesinde ve tür tanımında son alan, alanların tümünü tek bir satırda olduğundan bağımsız olarak, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67f45-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="67f45-128">Bir kayıt oluşturduğunuzda, her bir alan için değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="67f45-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="67f45-129">Herhangi bir alan için başlatma ifadesini diğer alanların değerlerine başvuruda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="67f45-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="67f45-130">Aşağıdaki kodda, türü `myRecord2` alanlarının adları algılanır.</span><span class="sxs-lookup"><span data-stu-id="67f45-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="67f45-131">İsteğe bağlı olarak, tür adı açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f45-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="67f45-132">Kayıtlardan kopyalayabilir ve büyük olasılıkla bazı alan değerleri değiştirmek olduğunda, başka bir form kayıt oluşturma yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="67f45-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="67f45-133">Aşağıdaki kod satırını bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="67f45-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="67f45-134">Bu formu kayıt ifadenin adlı *kopyalama ve güncelleştirme kayıt ifade*.</span><span class="sxs-lookup"><span data-stu-id="67f45-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="67f45-135">Varsayılan olarak kayıtları sabittir; Ancak, kopyalama ve güncelleştirme ifade kullanarak değiştirilmiş kayıtlar kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f45-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="67f45-136">Değişebilir bir alan da açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f45-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="67f45-137">DefaultValue özniteliği kayıt alanlarla kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="67f45-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="67f45-138">Daha iyi bir yaklaşım, kayıt başlatılır alanları ile varsayılan örnekleri için varsayılan değerleri tanımlama ve ardından bir kopyayı kullanın ve varsayılan değerlerden farklı herhangi bir alan ayarlamak için kayıt ifadeyi güncelleştirin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="67f45-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="67f45-139">Karşılıklı özyinelemeli kayıtlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="67f45-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="67f45-140">Süre bir kayıt oluştururken, daha sonra tanımlamak için istediğiniz başka bir türüne bağlıdır isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67f45-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="67f45-141">Karşılıklı özyinelemeli olarak kayıt türlerinin tanımlamadığınız sürece bir derleme hatası budur.</span><span class="sxs-lookup"><span data-stu-id="67f45-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="67f45-142">Karşılıklı özyinelemeli kayıtları tanımlama ile yapılır `and` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="67f45-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="67f45-143">Bu, 2 veya daha fazla kayıt türü birlikte bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="67f45-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="67f45-144">Örneğin, aşağıdaki kodu tanımlayan bir `Person` ve `Address` karşılıklı özyinelemeli olarak türü:</span><span class="sxs-lookup"><span data-stu-id="67f45-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

<span data-ttu-id="67f45-145">Önceki örnekte olmadan tanımlamak için olsaydı `and` anahtar sözcüğü ve ardından derleme.</span><span class="sxs-lookup"><span data-stu-id="67f45-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="67f45-146">`and` Karşılıklı özyinelemeli tanımları için anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="67f45-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="67f45-147">Desen eşleştirme ile kayıtları</span><span class="sxs-lookup"><span data-stu-id="67f45-147">Pattern Matching with Records</span></span>

<span data-ttu-id="67f45-148">Kayıtları desen eşleştirme ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67f45-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="67f45-149">Bazı alanlar açıkça belirtin ve bir eşleşme olduğunda, atanacak diğer alanlar için değişkenleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="67f45-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="67f45-150">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="67f45-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="67f45-151">Bu kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="67f45-151">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="67f45-152">Kayıt ve sınıfları arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="67f45-152">Differences Between Records and Classes</span></span>

<span data-ttu-id="67f45-153">Kayıt alanları otomatik olarak bir özellik olarak kullanıma ve kullanılan oluşturma ve kopyalama kayıtların sınıflardan farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="67f45-153">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="67f45-154">Kayıt oluşturma da sınıfı oluşturma farklıdır.</span><span class="sxs-lookup"><span data-stu-id="67f45-154">Record construction also differs from class construction.</span></span> <span data-ttu-id="67f45-155">Bir kayıt türü bir oluşturucu tanımlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="67f45-155">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="67f45-156">Bunun yerine, bu konuda açıklanan yapım söz dizimi geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="67f45-156">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="67f45-157">Oluşturucu parametresi, alanlar ve özellikler arasında hiçbir doğrudan ilişki sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="67f45-157">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="67f45-158">Birleşim ve yapı türleri gibi kayıtları yapısal eşitlik semantiklere sahip.</span><span class="sxs-lookup"><span data-stu-id="67f45-158">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="67f45-159">Başvuru sınıfları sahip eşitlik semantiği.</span><span class="sxs-lookup"><span data-stu-id="67f45-159">Classes have reference equality semantics.</span></span> <span data-ttu-id="67f45-160">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="67f45-160">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="67f45-161">Bu kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="67f45-161">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="67f45-162">Sınıflarla aynı kod yazın, iki sınıf nesnelerine çünkü iki değer iki nesne yığını üzerindeki temsil eder ve yalnızca adreslerine kıyasla eşit olacaktır (sınıf türü geçersiz kılmadıkça `System.Object.Equals` yöntemi).</span><span class="sxs-lookup"><span data-stu-id="67f45-162">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="67f45-163">Kayıtlar için eşitlik başvuruyorsa öznitelik Ekle `[<ReferenceEquality>]` yukarıda kaydı.</span><span class="sxs-lookup"><span data-stu-id="67f45-163">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="67f45-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67f45-164">See also</span></span>

- [<span data-ttu-id="67f45-165">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="67f45-165">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="67f45-166">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="67f45-166">Classes</span></span>](classes.md)
- [<span data-ttu-id="67f45-167">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="67f45-167">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="67f45-168">Başvuru eşitliği</span><span class="sxs-lookup"><span data-stu-id="67f45-168">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="67f45-169">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="67f45-169">Pattern Matching</span></span>](pattern-matching.md)
