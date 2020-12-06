---
title: Özellikler
description: 'Bir nesneyle ilişkili değerleri temsil eden Üyeler olan F # özellikleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740204"
---
# <a name="properties"></a><span data-ttu-id="a3a9e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a3a9e-103">Properties</span></span>

<span data-ttu-id="a3a9e-104">*Özellikler* , bir nesneyle ilişkili değerleri temsil eden üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3a9e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3a9e-105">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="a3a9e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3a9e-106">Remarks</span></span>

<span data-ttu-id="a3a9e-107">Özellikler, nesne odaklı programlamada, nesne örnekleriyle ilişkili verileri temsil eden veya statik özellikler için, türü ile birlikte "" a "ilişkisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="a3a9e-108">Özelliği için temel alınan değeri (yedekleme deposu olarak da bilinir) açıkça belirtmek isteyip istemediğinize veya derleyicinin sizin için otomatik olarak yedekleme deposunu oluşturmasına izin vermek istiyorsanız, özellikleri iki şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="a3a9e-109">Genellikle, özelliğin önemsiz olmayan bir uygulamasına sahip olması ve özelliğin bir değer ya da değişken için yalnızca basit bir sarmalayıcı olması durumunda, otomatik olarak daha açık bir yöntem kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="a3a9e-110">Bir özelliği açıkça bildirmek için `member` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="a3a9e-111">Bu bildirim temelli söz dizimi, `get` sonra `set` da *erişimcileri* adlı ve yöntemlerini belirten sözdizimi tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="a3a9e-112">Sözdizimi bölümünde gösterilen açık sözdiziminin çeşitli biçimleri, okuma/yazma, salt okunurdur ve salt yazılır özellikler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="a3a9e-113">Salt okuma özellikleri için yalnızca bir yöntemi tanımlarsınız; salt `get` yazılır özellikler için yalnızca bir `set` yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="a3a9e-114">Bir özellik hem hem de erişimcileri olduğunda `get` `set` , alternatif sözdizimi, aşağıdaki kodda gösterildiği gibi her erişimci için farklı öznitelikler ve erişilebilirlik değiştiricileri belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="a3a9e-115">Hem hem de yöntemine sahip olan okuma/yazma özellikleri `get` için `set` , sırası `get` ve `set` ters alınabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="a3a9e-116">Alternatif olarak, yalnızca için gösterilen söz dizimini `get` ve yalnızca için gösterilen sözdizimini `set` birleştirilmiş sözdizimini kullanmak yerine sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="a3a9e-117">Bunu yapmak `get` `set` , tek yapmanız gereken bir şey ise, her şeyi veya yöntemi açıklamayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="a3a9e-118">Birleşik söz dizimini kullanmanın bu alternatifi aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="a3a9e-119">Özellikler için verileri tutan özel değerler *Mağaza yedekleme* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="a3a9e-120">Derleyicinin yedekleme deposunu otomatik olarak oluşturmasını sağlamak için, anahtar sözcüklerini kullanın `member val` , kendi kendine tanımlayıcıyı atlayın ve sonra özelliği başlatmak için bir ifade sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="a3a9e-121">Özelliği değiştirilebilir ise, dahil edin `with get, set` .</span><span class="sxs-lookup"><span data-stu-id="a3a9e-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="a3a9e-122">Örneğin, aşağıdaki sınıf türü otomatik olarak uygulanan iki özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="a3a9e-123">`Property1` salt okunurdur ve birincil oluşturucuya sunulan bağımsız değişkene başlatılır ve `Property2` boş bir dizeye başlatılan ayarlanabilir bir özelliktir:</span><span class="sxs-lookup"><span data-stu-id="a3a9e-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="a3a9e-124">Otomatik uygulanan özellikler bir tür başlatmanın bir parçasıdır. bu nedenle, `let` bir tür tanımındaki bağlamalar ve bağlamalar gibi diğer üye tanımlarından önce dahil olmaları gerekir `do` .</span><span class="sxs-lookup"><span data-stu-id="a3a9e-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="a3a9e-125">Otomatik olarak uygulanan bir özelliği Başlatan ifadenin, her özelliğe erişildiğinde değil, yalnızca başlatma sonrasında değerlendirildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="a3a9e-126">Bu davranış, açıkça uygulanan bir özelliğin davranışının aksine.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="a3a9e-127">Bunun ne kadar etkili olduğu, bu özellikleri başlatacak kodun bir sınıfın oluşturucusuna eklendiği şeydir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="a3a9e-128">Bu farkı gösteren aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a3a9e-128">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

<span data-ttu-id="a3a9e-129">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="a3a9e-129">**Output**</span></span>

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="a3a9e-130">Önceki kodun çıktısı, tekrar tekrar çağrıldığında,, her çağrıldığında açıkça IProperty değiştiği zaman, tekrar tekrar çağrıldığında, tekrar özelliğinin değerinin değiştirilmemiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="a3a9e-131">Bu, açık özelliğin alıcı yöntemi olduğu gibi, otomatik olarak uygulanan bir özelliğin ifadesinin her seferinde değerlendirilmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
><span data-ttu-id="a3a9e-132">`System.Data.Entity`Otomatik olarak uygulanan özelliklerin başlatılmasına göre iyi çalışmayan temel sınıf oluşturucuları içinde özel işlemler gerçekleştiren Entity Framework () gibi bazı kitaplıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="a3a9e-133">Bu durumlarda, açık özellikleri kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="a3a9e-134">Özellikler sınıfların, yapıların, ayrılmış birleşimlerin, kayıtların, arabirimlerin ve tür uzantılarının üyeleri olabilir ve ayrıca nesne ifadelerinde de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="a3a9e-135">Öznitelikler, özelliklere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="a3a9e-136">Bir özelliğe öznitelik uygulamak için, özelliğinden önce özniteliği ayrı bir satıra yazın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="a3a9e-137">Daha fazla bilgi için bkz. [öznitelikler](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a3a9e-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="a3a9e-138">Varsayılan olarak, Özellikler geneldir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-138">By default, properties are public.</span></span> <span data-ttu-id="a3a9e-139">Erişilebilirlik değiştiricileri de özelliklere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="a3a9e-140">Bir erişilebilirlik değiştiricisi uygulamak için, hem hem de yöntemlerine uygulanacaksa özelliğin adından hemen önce ekleyin `get` `set` ; `get` `set` her erişimci için farklı erişilebilirlik gerekliyse, ve anahtar sözcüklerden önce ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="a3a9e-141">*Erişilebilirlik-değiştirici* aşağıdakilerden biri olabilir: `public` , `private` , `internal` .</span><span class="sxs-lookup"><span data-stu-id="a3a9e-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="a3a9e-142">Daha fazla bilgi için bkz. [Erişim Denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="a3a9e-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="a3a9e-143">Özellik uygulamaları her bir özelliğe erişildiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="a3a9e-144">Statik ve örnek özellikleri</span><span class="sxs-lookup"><span data-stu-id="a3a9e-144">Static and Instance Properties</span></span>

<span data-ttu-id="a3a9e-145">Özellikler statik veya örnek özellikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="a3a9e-146">Statik özellikler bir örnek olmadan çağrılabilir ve ayrı nesneler ile değil, türle ilişkili değerler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="a3a9e-147">Statik özellikler için, kendi kendine tanımlayıcıyı atlayın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="a3a9e-148">Örnek özellikleri için kendi kendine tanımlayıcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="a3a9e-149">Aşağıdaki statik özellik tanımı, `myStaticValue` özelliği için yedekleme deposu olan bir statik alana sahip olduğunuz bir senaryoyu temel alır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="a3a9e-150">Özellikler ayrıca dizi benzeri olabilir, bu durumda *dizinlenmiş özellikler* olarak adlandırılırlar.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="a3a9e-151">Daha fazla bilgi için bkz. [dizinli Özellikler](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a3a9e-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="a3a9e-152">Özellikler için tür ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="a3a9e-152">Type Annotation for Properties</span></span>

<span data-ttu-id="a3a9e-153">Çoğu durumda, derleyicinin bir özelliğin türünü, yedekleme deposunun türünden çıkarması için yeterli bilgi vardır, ancak tür ek açıklaması ekleyerek türü açıkça ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="a3a9e-154">Özellik kümesi erişimcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="a3a9e-154">Using Property set Accessors</span></span>

<span data-ttu-id="a3a9e-155">İşlecini kullanarak erişimciler sağlayan özellikleri ayarlayabilirsiniz `set` `<-` .</span><span class="sxs-lookup"><span data-stu-id="a3a9e-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="a3a9e-156">Çıktı **20**' dir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="a3a9e-157">Soyut Özellikler</span><span class="sxs-lookup"><span data-stu-id="a3a9e-157">Abstract Properties</span></span>

<span data-ttu-id="a3a9e-158">Özellikler soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-158">Properties can be abstract.</span></span> <span data-ttu-id="a3a9e-159">Metotlarda olduğu gibi, `abstract` özelliği ile ilişkili bir sanal dağıtım olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="a3a9e-160">Soyut Özellikler gerçekten soyut olabilir, diğer bir deyişle, aynı sınıfta bir tanım olmadan.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="a3a9e-161">Böyle bir özelliği içeren sınıf bu nedenle soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="a3a9e-162">Alternatif olarak, soyut bir özelliğin sanal olduğu anlamına gelir ve bu durumda bir tanım aynı sınıfta bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="a3a9e-163">Soyut özelliklerin özel olmaması gerektiğini ve bir erişimcinin soyut olduğunu, diğerinin de soyut olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="a3a9e-164">Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut sınıflar](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a3a9e-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="a3a9e-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3a9e-165">See also</span></span>

- [<span data-ttu-id="a3a9e-166">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a3a9e-166">Members</span></span>](index.md)
- [<span data-ttu-id="a3a9e-167">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a3a9e-167">Methods</span></span>](methods.md)
