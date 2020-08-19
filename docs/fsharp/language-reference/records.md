---
title: Kayıtlar
description: 'F # kayıtlarının, isteğe bağlı olarak, adlandırılmış değerlerin basit toplamlarını nasıl temsil ettiğini öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 182b2e83c3940c866197052af102787a96e49c54
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559056"
---
# <a name="records"></a><span data-ttu-id="dafbe-103">Kayıtlar</span><span class="sxs-lookup"><span data-stu-id="dafbe-103">Records</span></span>

<span data-ttu-id="dafbe-104">Kayıtlar, isteğe bağlı olarak Üyeler ile adlandırılmış değerlerin basit toplamlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dafbe-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="dafbe-105">Bunlar, yapılar veya başvuru türleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="dafbe-106">Bunlar varsayılan olarak başvuru türlerdir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="dafbe-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="dafbe-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="dafbe-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dafbe-108">Remarks</span></span>

<span data-ttu-id="dafbe-109">Önceki sözdiziminde, *TypeName* kayıt türünün adı, *Label1* ve *Etiket 2* değerleri *Etiketler*olarak adlandırılır ve *Type1* ve *type2* bu değerlerin türleridir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="dafbe-110">*üye listesi* , türü için isteğe bağlı üyelerin listesidir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="dafbe-111">`[<Struct>]`Özniteliği, başvuru türü olan bir kayıt yerine bir struct kaydı oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="dafbe-112">Bazı örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-112">Following are some examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="dafbe-113">Her etiket ayrı bir satırda olduğunda, noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="dafbe-114">*Kayıt ifadeleri*olarak bilinen ifadelerde değerler belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="dafbe-115">Derleyici, kullanılan etiketlerden tür kullanır (Etiketler diğer kayıt türlerinden yeterince farklı olursa).</span><span class="sxs-lookup"><span data-stu-id="dafbe-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="dafbe-116">Küme ayraçları ({}) kayıt ifadesini kapsar.</span><span class="sxs-lookup"><span data-stu-id="dafbe-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="dafbe-117">Aşağıdaki kod, etiketleriyle üç float öğesi olan bir kaydı Başlatan bir kayıt ifadesi gösterir `x` `y` `z` .</span><span class="sxs-lookup"><span data-stu-id="dafbe-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="dafbe-118">Aynı etiketlere de sahip olan başka bir tür varsa, kısaltılmış biçimi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="dafbe-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="dafbe-119">En son tanımlanan türün etiketleri, önceden tanımlanmış olan türden önceliklidir, bu nedenle önceki örnekte olduğu gibi `mypoint3D` algılanır `Point3D` .</span><span class="sxs-lookup"><span data-stu-id="dafbe-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="dafbe-120">Kayıt türünü aşağıdaki kodda olduğu gibi açıkça belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="dafbe-121">Yöntemler, sınıf türleri için olduğu gibi kayıt türleri için tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="dafbe-122">Kayıt Ifadeleri kullanarak kayıt oluşturma</span><span class="sxs-lookup"><span data-stu-id="dafbe-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="dafbe-123">Kayıtları kayıtta tanımlanan etiketleri kullanarak başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="dafbe-124">Bunu yapan bir ifade, *kayıt ifadesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="dafbe-125">Kayıt ifadesini kapsamak ve noktalı virgülü sınırlayıcı olarak kullanmak için küme ayraçları kullanın.</span><span class="sxs-lookup"><span data-stu-id="dafbe-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="dafbe-126">Aşağıdaki örnek, bir kaydın nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="dafbe-127">Kayıt ifadesindeki son alandan sonra tür tanımında bulunan noktalı virgül, alanların tümünün tek bir satırda olup olmamasından bağımsız olarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="dafbe-128">Bir kayıt oluşturduğunuzda, her bir alan için değerler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="dafbe-129">Herhangi bir alan için başlatma ifadesindeki diğer alanların değerlerine başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="dafbe-130">Aşağıdaki kodda, türü `myRecord2` alanların adlarından algılanır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="dafbe-131">İsteğe bağlı olarak, tür adını açık şekilde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="dafbe-132">Başka bir kayıt oluşturma biçimi, var olan bir kaydı kopyalamanız gerektiğinde ve muhtemelen alan değerlerinden bazılarını değiştirebilmeniz yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="dafbe-133">Aşağıdaki kod satırı bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="dafbe-134">Kayıt ifadesinin bu formu, *Copy ve Update Record ifadesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="dafbe-135">Kayıtlar varsayılan olarak sabittir; Ancak, bir Kopyala ve Güncelleştir ifadesi kullanarak, değiştirilmiş kayıtları kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="dafbe-136">Ayrıca, açıkça kesilebilir bir alan belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="dafbe-137">DefaultValue özniteliğini kayıt alanları ile kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="dafbe-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="dafbe-138">Daha iyi bir yaklaşım, varsayılan değerlere başlatılan alanlara sahip kayıtların varsayılan örneklerini tanımlamak ve sonra varsayılan değerlerden farklı olan alanları ayarlamak için bir Kopyala ve Güncelleştir ifadesi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

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

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="dafbe-139">Birbirini dışlayan özyinelemeli kayıtlar oluşturma</span><span class="sxs-lookup"><span data-stu-id="dafbe-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="dafbe-140">Kayıt oluştururken, daha sonra tanımlamak istediğiniz başka bir türe bağlı olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="dafbe-141">Bu, karşılıklı özyinelemeli olacak kayıt türlerini tanımlamadığınız takdirde bir derleme hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="dafbe-142">Birbirini dışlayan özyinelemeli kayıtların tanımlanması `and` anahtar sözcükle yapılır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="dafbe-143">Bu, 2 veya daha fazla kayıt türünü birbirine bağlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dafbe-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="dafbe-144">Örneğin, aşağıdaki kod bir `Person` ve `Address` türünü birbirini dışlayan özyinelemeli olarak tanımlar:</span><span class="sxs-lookup"><span data-stu-id="dafbe-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

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
    PostCode: string
    Occupant: Person }
```

<span data-ttu-id="dafbe-145">Önceki örneği anahtar sözcüğü olmadan tanımlamanız durumunda `and` derlenmez.</span><span class="sxs-lookup"><span data-stu-id="dafbe-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="dafbe-146">`and`Anahtar sözcüğü, karşılıklı özyinelemeli tanımlar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="dafbe-147">Kayıtlarla eşleşen desenler</span><span class="sxs-lookup"><span data-stu-id="dafbe-147">Pattern Matching with Records</span></span>

<span data-ttu-id="dafbe-148">Kayıtlar, model eşleştirme ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="dafbe-149">Bazı alanları açık bir şekilde belirtebilir ve bir eşleşme gerçekleştiğinde atanacak diğer alanlar için değişken sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="dafbe-150">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="dafbe-151">Bu kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-151">The output of this code is as follows.</span></span>

```console
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="records-and-members"></a><span data-ttu-id="dafbe-152">Kayıtlar ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="dafbe-152">Records and members</span></span>

<span data-ttu-id="dafbe-153">Kayıtlar üzerinde, sınıflar ile yaptığınız gibi Üyeler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-153">You can specify members on records much like you can with classes.</span></span> <span data-ttu-id="dafbe-154">Alanlar için destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="dafbe-154">There is no support for fields.</span></span> <span data-ttu-id="dafbe-155">Yaygın bir yaklaşım, `Default` kolay kayıt oluşturma için statik bir üye tanımlamaktır:</span><span class="sxs-lookup"><span data-stu-id="dafbe-155">A common approach is to define a `Default` static member for easy record construction:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    static member Default =
        { Name = "Phillip"
          Age = 12
          Address = "123 happy fun street" }

let defaultPerson = Person.Default
```

<span data-ttu-id="dafbe-156">Kendi kendine tanımlayıcı kullanırsanız, bu tanımlayıcı, üyesini çağıran kaydın örneğine başvurur:</span><span class="sxs-lookup"><span data-stu-id="dafbe-156">If you use a self identifier, that identifier refers to the instance of the record whose member is called:</span></span>

```fsharp
type Person =
  { Name: string
    Age: int
    Address: string }

    member this.WeirdToString() =
        this.Name + this.Address + string this.Age

let p = { Name = "a"; Age = 12; Address = "abc123 }
let weirdString = p.WeirdToString()
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="dafbe-157">Kayıtlar ve sınıflar arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="dafbe-157">Differences Between Records and Classes</span></span>

<span data-ttu-id="dafbe-158">Kayıt alanları, otomatik olarak özellikler olarak sunuldukları sınıflardan farklıdır ve kayıtların oluşturulması ve kopyalanması halinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-158">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="dafbe-159">Kayıt oluşturma, sınıf yapılamadan da farklıdır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-159">Record construction also differs from class construction.</span></span> <span data-ttu-id="dafbe-160">Bir kayıt türünde, bir Oluşturucu tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dafbe-160">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="dafbe-161">Bunun yerine, bu konuda açıklanan yapım sözdizimi geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-161">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="dafbe-162">Sınıfların Oluşturucu parametreleri, alanları ve özellikleri arasında doğrudan bir ilişkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dafbe-162">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="dafbe-163">Birleşim ve yapı türleri gibi, kayıtların yapısal eşitlik semantiği vardır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-163">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="dafbe-164">Sınıflarda başvuru eşitlik semantiği vardır.</span><span class="sxs-lookup"><span data-stu-id="dafbe-164">Classes have reference equality semantics.</span></span> <span data-ttu-id="dafbe-165">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dafbe-165">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="dafbe-166">Bu kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dafbe-166">The output of this code is as follows:</span></span>

```console
The records are equal.
```

<span data-ttu-id="dafbe-167">Aynı kodu sınıflarla yazarsanız, iki değer yığında iki nesneyi temsil ettiğinden ve yalnızca adresler karşılaştırılacağından (sınıf türü yöntemi geçersiz kılmadığı takdirde), iki sınıf nesnesi eşit değildir `System.Object.Equals` .</span><span class="sxs-lookup"><span data-stu-id="dafbe-167">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="dafbe-168">Kayıtlar için başvuru eşitlik gerekiyorsa, `[<ReferenceEquality>]` kaydın üzerine özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dafbe-168">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="dafbe-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dafbe-169">See also</span></span>

- [<span data-ttu-id="dafbe-170">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="dafbe-170">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="dafbe-171">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="dafbe-171">Classes</span></span>](classes.md)
- [<span data-ttu-id="dafbe-172">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="dafbe-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="dafbe-173">Başvuru-eşitlik</span><span class="sxs-lookup"><span data-stu-id="dafbe-173">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="dafbe-174">Model eşleştirme</span><span class="sxs-lookup"><span data-stu-id="dafbe-174">Pattern Matching</span></span>](pattern-matching.md)
