---
title: "Özellikler (F#)"
description: "Bir nesneyle ilişkilendirilmiş değerlerini temsil eden üyeleri olan F # özellikleri hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a><span data-ttu-id="a73b7-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a73b7-104">Properties</span></span>

<span data-ttu-id="a73b7-105">*Özellikler* bir nesneyle ilişkilendirilmiş değerlerini temsil eden üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-105">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="a73b7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a73b7-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="a73b7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a73b7-107">Remarks</span></span>
<span data-ttu-id="a73b7-108">Özelliklerini temsil eder "sahip bir" nesne örnekleri ile veya türüyle statik özellikler için ilişkili verileri temsil eden nesne odaklı programlama ilişkisinde.</span><span class="sxs-lookup"><span data-stu-id="a73b7-108">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="a73b7-109">Özellikler (yedekleme deposu olarak da adlandırılır) temel alınan değer özelliği için açıkça belirtmek istediğiniz veya yedekleme deposu sizin için otomatik olarak oluşturmak derleyici izin vermek istediğiniz bağlı olarak iki yolla bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a73b7-109">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="a73b7-110">Genellikle, özelliği yalnızca bir değer veya değişken için basit bir sarmalayıcı olduğunda daha açık şekilde Önemsiz olmayan bir uygulama özelliğine sahipse ve otomatik şekilde kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-110">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="a73b7-111">Bir özellik açıkça bildirmek için kullanın `member` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a73b7-111">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="a73b7-112">Bu tanımlayıcı sözdizimi belirten sözdizimi tarafından izlenir `get` ve `set` olarak da adlandırılan yöntemleri *erişimciler*.</span><span class="sxs-lookup"><span data-stu-id="a73b7-112">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="a73b7-113">Çeşitli tür sözdizimi bölümünde gösterilen açık sözdizimi okuma/yazma, salt okunur ve salt yazılır özellikler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a73b7-113">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="a73b7-114">Salt okunur özellikler yalnızca tanımladığınız bir `get` yöntemi; salt yazılır özellikler yalnızca tanımlayan bir `set` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a73b7-114">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="a73b7-115">Hem bir özelliğe sahip olduğunda unutmayın `get` ve `set` erişimciler, alternatif bir sözdizimi öznitelikleri ve aşağıdaki kodda gösterildiği gibi her erişimci için farklı erişilebilirlik değiştiricileri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a73b7-115">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="a73b7-116">Hem de okuma/yazma özellikleri için bir `get` ve `set` yöntemi, sırasını `get` ve `set` ters çevrilebilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-116">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="a73b7-117">Alternatif olarak, gösterilen sözdizimi sağlayabilir `get` yalnızca ve için sözdizimini `set` birleşik sözdizimi yerine yalnızca.</span><span class="sxs-lookup"><span data-stu-id="a73b7-117">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="a73b7-118">Bunun yapılması kolaylaştırır açıklamaya tek tek çıkışı `get` veya `set` yöntemi ise, bir şey yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-118">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="a73b7-119">Bu alternatif birleşik sözdizimini kullanarak aşağıdaki kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-119">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="a73b7-120">Özel özellikler için verileri çağrılır ayrı tutmayı değerleri *depolarını yedekleme*.</span><span class="sxs-lookup"><span data-stu-id="a73b7-120">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="a73b7-121">Derleyicinin yedekleme deposu otomatik olarak oluşturmak için anahtar sözcüklerini kullanın `member val`, kendi kendine tanımlayıcı çıkarın ve ardından özelliği başlatmak için bir ifade girin.</span><span class="sxs-lookup"><span data-stu-id="a73b7-121">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="a73b7-122">Özelliği değişebilir olması gerekiyorsa dahil `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="a73b7-122">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="a73b7-123">Örneğin, aşağıdaki sınıf türü iki otomatik olarak uygulanan özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-123">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="a73b7-124">`Property1`salt okunur ve birincil oluşturucuya sağlanan değişkeni başlatılır ve `Property2` boş bir dize olarak başlatılan bir özelliğidir ayarlanabilir:</span><span class="sxs-lookup"><span data-stu-id="a73b7-124">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="a73b7-125">Otomatik uygulanan özellikler bunlar diğer üye tanımları önce tıpkı dahil edilmesi için bir tür başlatma parçası olan `let` bağlamalar ve `do` tür tanımında bağlar.</span><span class="sxs-lookup"><span data-stu-id="a73b7-125">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="a73b7-126">Otomatik olarak uygulanan bir özellik başlatır ifade başlatma sırasında ve değil özelliği her erişildiğinde yalnızca değerlendirilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a73b7-126">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="a73b7-127">Açıkça gerçekleştirilen özellik aksine bu davranış davranıştır.</span><span class="sxs-lookup"><span data-stu-id="a73b7-127">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="a73b7-128">Ne bu etkili bir şekilde, bu özellikleri başlatmak için kod olduğu anlamına gelir, bir sınıfın oluşturucuya eklenir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-128">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="a73b7-129">Bu farklılık gösteren aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a73b7-129">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="a73b7-130">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="a73b7-130">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="a73b7-131">Önceki kod çıkışı ExplicitProperty her çağrıldığında değişir ancak AutoProperty değerini tekrar tekrar çağrıldığında değiştirilmemiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-131">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="a73b7-132">Açık özellik alıcısı yöntemi olarak ifade otomatik olarak uygulanan bir özellik için her zaman değerlendirilmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-132">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="a73b7-133">Entity Framework gibi bazı kitaplığı (`System.Data.Entity`), özel işlemi gerçekleştirir temel sınıf Yapıcılardaki de otomatik olarak uygulanan özellikler başlatma ile çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="a73b7-133">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="a73b7-134">Bu durumlarda, açık özelliklerini kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="a73b7-134">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="a73b7-135">Özellikler, sınıflar, yapılar, ayrılmış birleşimler, kayıtları, arabirimler ve tür uzantıları üyesi olabilir ve nesne ifadelerde de tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-135">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="a73b7-136">Öznitelikleri özelliklerine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-136">Attributes can be applied to properties.</span></span> <span data-ttu-id="a73b7-137">Öznitelik bir özelliğe uygulamak için ayrı bir satırda özelliği önce öznitelik yazma.</span><span class="sxs-lookup"><span data-stu-id="a73b7-137">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="a73b7-138">Daha fazla bilgi için bkz: [öznitelikleri](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a73b7-138">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="a73b7-139">Varsayılan olarak, ortak özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-139">By default, properties are public.</span></span> <span data-ttu-id="a73b7-140">Erişilebilirlik değiştiricileri özelliklerine de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-140">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="a73b7-141">Her ikisini de uygulamak için istediyseniz erişim değiştiricisi uygulamak için bu özelliğin adı hemen önce ekleyin `get` ve `set` yöntemleri; önce eklemek `get` ve `set` farklı erişilebilirlik ise anahtar sözcükler her erişimci için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-141">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="a73b7-142">*Erişim değiştiricisi* şunlardan biri olabilir: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="a73b7-142">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="a73b7-143">Daha fazla bilgi için bkz: [erişim denetimi](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="a73b7-143">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="a73b7-144">Özellik uygulamaları bir özelliği her erişildiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a73b7-144">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="a73b7-145">Statik ve örnek özellikleri</span><span class="sxs-lookup"><span data-stu-id="a73b7-145">Static and Instance Properties</span></span>
<span data-ttu-id="a73b7-146">Özellikler, statik ya da Özellikler örneği.</span><span class="sxs-lookup"><span data-stu-id="a73b7-146">Properties can be static or instance properties.</span></span> <span data-ttu-id="a73b7-147">Statik özellikler örneği çağrılabilir ve türü değil ayrı ayrı nesneleri ile ilişkili değerleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a73b7-147">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="a73b7-148">Statik özellikler için kendi kendine tanımlayıcısı yok sayın.</span><span class="sxs-lookup"><span data-stu-id="a73b7-148">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="a73b7-149">Kendi kendine tanımlayıcısı örneği özellikleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-149">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="a73b7-150">Aşağıdaki statik özellik tanımını statik bir alana sahip bir senaryo tabanlı `myStaticValue` özelliği için diğer bir deyişle yedekleme deposu.</span><span class="sxs-lookup"><span data-stu-id="a73b7-150">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="a73b7-151">Özellikler de olabilir dizi benzeri; bu durumda adlı *özellikleri dizine*.</span><span class="sxs-lookup"><span data-stu-id="a73b7-151">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="a73b7-152">Daha fazla bilgi için bkz: [Dizinli Özellikler](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a73b7-152">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="a73b7-153">Özellikleri için tür ek açıklaması</span><span class="sxs-lookup"><span data-stu-id="a73b7-153">Type Annotation for Properties</span></span>
<span data-ttu-id="a73b7-154">Çoğu durumda, derleyici tür yedekleme deposu özelliğinden türünü anlamak için yeterli bilgiye sahip, ancak türü ek açıklama ekleyerek türü açıkça ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a73b7-154">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="a73b7-155">Özelliğini kullanarak set erişimcileri</span><span class="sxs-lookup"><span data-stu-id="a73b7-155">Using Property set Accessors</span></span>
<span data-ttu-id="a73b7-156">Sağlayan özellikleri ayarlayabilirsiniz `set` kullanarak erişimciler `<-` işleci.</span><span class="sxs-lookup"><span data-stu-id="a73b7-156">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="a73b7-157">Çıktı **20**.</span><span class="sxs-lookup"><span data-stu-id="a73b7-157">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="a73b7-158">Soyut Özellikler</span><span class="sxs-lookup"><span data-stu-id="a73b7-158">Abstract Properties</span></span>
<span data-ttu-id="a73b7-159">Özellikler soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-159">Properties can be abstract.</span></span> <span data-ttu-id="a73b7-160">Yöntemleriyle olduğu gibi `abstract` yeni özellik ile ilişkilendirilmiş sanal bir gönderme olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-160">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="a73b7-161">Diğer bir deyişle, soyut özellikleri aynı sınıf tanımında olmadan gerçekten soyut olabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-161">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="a73b7-162">Böyle bir özellik içeren bu nedenle bir Özet sınıf sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a73b7-162">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="a73b7-163">Alternatif olarak, Özet yalnızca bir sanal bir özelliktir ve bu durumda, bir tanım aynı sınıfta bulunmalıdır anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-163">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="a73b7-164">Soyut özellikler özel olmamalı ve bir erişimci soyut ise, diğer ayrıca soyut olmalıdır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a73b7-164">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="a73b7-165">Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a73b7-165">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="a73b7-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a73b7-166">See Also</span></span>
[<span data-ttu-id="a73b7-167">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="a73b7-167">Members</span></span>](index.md)

[<span data-ttu-id="a73b7-168">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a73b7-168">Methods</span></span>](methods.md)
