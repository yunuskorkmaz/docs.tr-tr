---
title: Yöntemler (F#)
description: 'Bir F # yöntemi kullanıma sunar ve davranışı nesnelerin ve türleri ve işlevleri uygulamak için kullanılan bir türü ile ilişkili bir işlevin nasıl olduğunu öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 02d5a7d22d1ce79a06e15462637c373b33623f61
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253214"
---
# <a name="methods"></a><span data-ttu-id="fa071-103">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa071-103">Methods</span></span>

<span data-ttu-id="fa071-104">A *yöntemi* türü ile ilişkilendirilmiş bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="fa071-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="fa071-105">Nesne yönelimli programlama, yöntemleri, kullanıma ve davranışı nesnelerin ve türleri ve işlevleri uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa071-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa071-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa071-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="fa071-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa071-107">Remarks</span></span>

<span data-ttu-id="fa071-108">Önceki sözdiziminde, çeşitli forms yöntemi bildirimlerinin ve tanımlarının görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa071-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="fa071-109">Uzun metot gövdeleri eşittir (=) satır sonu izler ve tüm yöntem gövdesini girintili hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="fa071-110">Öznitelikler için herhangi bir yöntem bildiriminde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="fa071-111">Bunlar, bir yöntem tanımını sözdizimi koyun ve genellikle ayrı bir satıra listelenir.</span><span class="sxs-lookup"><span data-stu-id="fa071-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="fa071-112">Daha fazla bilgi için [öznitelikleri](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fa071-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="fa071-113">Yöntemleri işaretlenebilir `inline`.</span><span class="sxs-lookup"><span data-stu-id="fa071-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="fa071-114">Hakkında bilgi için `inline`, bkz: [satır içi işlevleri](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="fa071-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="fa071-115">Satır içi yöntemler türü içinde kullanılan yinelemeli olarak olabilir. açıkça kullanmaya gerek yoktur `rec` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fa071-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="fa071-116">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="fa071-116">Instance Methods</span></span>

<span data-ttu-id="fa071-117">Örnek yöntemleri ile bildirilmiş `member` anahtar sözcüğü ve *kendi kendine tanımlayıcısı*ve ardından bir nokta (.) ve yöntem adı ve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="fa071-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="fa071-118">İçin olduğu gibi `let` bağlamaları *parametre-listesi* desen olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="fa071-119">Diğer .NET Framework dillerinde oluştururken genellikle, yöntem parametreleri yöntemlerin bir kayıt düzeni formunda parantez içinde görünmesi F # alın.</span><span class="sxs-lookup"><span data-stu-id="fa071-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="fa071-120">Ancak, curried (parametrelerini boşluklarla ayırarak) Ayrıca yaygın biçimidir ve diğer desenleri de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa071-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="fa071-121">Aşağıdaki örnekte, soyut olmayan örnek yöntemi kullanımını ve tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa071-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="fa071-122">Örnek yöntemler let bağlamaları kullanılarak tanımlanmış erişim alanlarına erişmek için kendi kendine tanımlayıcısı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="fa071-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="fa071-123">Diğer üyeleri ve özelliklerine erişirken kendini tanımlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa071-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="fa071-124">Statik yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa071-124">Static Methods</span></span>

<span data-ttu-id="fa071-125">Anahtar sözcüğü `static` örneği olmadan bir yöntem çağrılabilir belirtmek için kullanılır ve bir nesne örneği ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="fa071-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="fa071-126">Aksi takdirde, örnek yöntemler yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="fa071-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="fa071-127">Sonraki bölümde örnek alanları ile bildirilen gösterir `let` özelliği üyelerini anahtar sözcüğü ile bildirilmiş `member` anahtar sözcüğü ve ile bildirilen bir statik yöntem `static` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fa071-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="fa071-128">Aşağıdaki örnek, statik yöntemler kullanımını ve tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa071-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="fa071-129">Bu yöntem tanımlarını olduğunu varsayın `SomeType` önceki bölümde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fa071-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="fa071-130">Soyut ve sanal yöntemleri</span><span class="sxs-lookup"><span data-stu-id="fa071-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="fa071-131">Anahtar sözcüğü `abstract` bir yöntem bir sanal dağıtım yuvasına sahiptir ve bir tanımı sınıfında olmayabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa071-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="fa071-132">A *sanal dağıtım yuvası* olduğundan çalışma zamanında sanal işlevini aramak için kullanılan dahili olarak tutulan bir tabloda işlevlerin bir giriş bir nesne yönelimli türünün çağırır.</span><span class="sxs-lookup"><span data-stu-id="fa071-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="fa071-133">Sanal dağıtım mekanizması uygular mekanizmadır *çok biçimlilik*, nesne yönelimli programlama önemli bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="fa071-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="fa071-134">Bir tanımı olmadan en az bir soyut yöntemi olan bir sınıfı, bir *soyut sınıf*, yani bu sınıfının hiçbir örneği oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="fa071-135">Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="fa071-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="fa071-136">Soyut yöntem bildirimleri bir yöntem gövdesi içermez.</span><span class="sxs-lookup"><span data-stu-id="fa071-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="fa071-137">Bunun yerine, yöntemin adı iki nokta üst üste (:) ve bir tür imzası yöntemi tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="fa071-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="fa071-138">Bir yöntem tür imzası, fare işaretçisini bir yöntem adı Visual Studio Kod Düzenleyicisi'nde, üzerinde dışında parametre adları duraklattığınızda IntelliSense tarafından gösterilen aynıdır.</span><span class="sxs-lookup"><span data-stu-id="fa071-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="fa071-139">Etkileşimli olarak çalışırken türü imzalarını fsi.exe yorumlayıcısı tarafından da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fa071-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="fa071-140">Tür imzası bir yöntemin kullanıma uygun ayırıcı semboller dönüş türüyle ardından, parametre türleri listesi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa071-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="fa071-141">Curried parametreleri ayrılır `->` ve demet parametre ayrılır `*`.</span><span class="sxs-lookup"><span data-stu-id="fa071-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="fa071-142">Bağımsız değişken tarafından gelen dönüş değeri her zaman ayrılmış bir `->` sembol.</span><span class="sxs-lookup"><span data-stu-id="fa071-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="fa071-143">Parantezler, bir işlev türü bir parametre olduğunda gibi karmaşık parametreler, Grup veya tek bir parametre yerine iki parametre olarak bir tanımlama grubu ne zaman işlendiğini belirten kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="fa071-144">De soyut yöntemler varsayılan tanımları tanımı sınıfa ekleme ve kullanma tanıyabilirsiniz `default` anahtar sözcüğü, bu konudaki sözdizimi bloğunda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fa071-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="fa071-145">Aynı sınıf içinde bir tanıma sahip soyut bir yöntemi, diğer .NET Framework dillerinde sanal bir yöntem eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="fa071-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="fa071-146">Bir tanımı var olup olmadığını `abstract` anahtar sözcüğü, sınıfın sanal işlev tablosuna yeni bir dağıtım yuvası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fa071-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="fa071-147">Bir taban sınıfı soyut yöntemlerini mi uygulayan bağımsız olarak, türetilmiş sınıflar uygulamaları soyut yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa071-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="fa071-148">Türetilen bir sınıfta bir soyut yönteminden uygulamak için kullanımı dışında türetilmiş sınıf içinde aynı ada ve imzaya sahip bir yöntemi tanımlamak `override` veya `default` anahtar sözcüğü ve yöntem gövdesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="fa071-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="fa071-149">Anahtar sözcükler `override` ve `default` tam olarak aynı anlama gelir.</span><span class="sxs-lookup"><span data-stu-id="fa071-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="fa071-150">Kullanma `override` yeni bir temel sınıf uygulaması; kılma kullanırsanız `default` özgün soyut bildirimiyle aynı sınıftaki bir uygulama oluşturduğunuzda.</span><span class="sxs-lookup"><span data-stu-id="fa071-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="fa071-151">Kullanmayın `abstract` anahtar sözcüğü, soyut temel sınıfta bildirilen yöntemini uygulayan bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="fa071-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="fa071-152">Aşağıdaki örnekte bir soyut yönteminden `Rotate` bir varsayılan uygulama, .NET Framework sanal bir yöntem denk olan.</span><span class="sxs-lookup"><span data-stu-id="fa071-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="fa071-153">Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılan türetilmiş bir sınıf göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fa071-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="fa071-154">Bu durumda geçersiz kılma davranışı değiştirir, böylece yöntemi hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="fa071-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="fa071-155">Aşırı yüklenmiş yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa071-155">Overloaded Methods</span></span>

<span data-ttu-id="fa071-156">Belirli bir türde aynı ada sahip olan ancak farklı bağımsız değişkenleri olan yöntemleri aşırı yüklenmiş yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="fa071-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="fa071-157">F # programında, isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa071-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="fa071-158">Bununla birlikte, bağımsız değişken değil curried form, tanımlama grubu form olması koşuluyla aşırı yüklenmiş yöntemler dilde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="fa071-159">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="fa071-159">Optional Arguments</span></span>

<span data-ttu-id="fa071-160">F # 4.1 ile başlayarak, varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenlere yöntemleri de olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa071-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="fa071-161">C# kod ile birlikte çalışma kolaylaştırmaya yardımcı olması için budur.</span><span class="sxs-lookup"><span data-stu-id="fa071-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="fa071-162">Aşağıdaki örnek, sözdizimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="fa071-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="fa071-163">İçinde geçirilen değer için Not `DefaultParameterValue` giriş türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa071-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="fa071-164">Yukarıdaki örnekte olduğu bir `int`.</span><span class="sxs-lookup"><span data-stu-id="fa071-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="fa071-165">Bir tamsayı olmayan değerde geçirmeye çalışırken `DefaultParameterValue` bir derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fa071-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="fa071-166">Örnek: Özellikler ve yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa071-166">Example: Properties and Methods</span></span>

<span data-ttu-id="fa071-167">Aşağıdaki örnek, alanları, özel işlevler, özellikler ve bir statik yöntem örnekleri olan bir türü içerir.</span><span class="sxs-lookup"><span data-stu-id="fa071-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="fa071-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa071-168">See also</span></span>

- [<span data-ttu-id="fa071-169">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa071-169">Members</span></span>](index.md)
