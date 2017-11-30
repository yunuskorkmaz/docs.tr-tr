---
title: "Yöntemler (F#)"
description: "Nasıl bir F # yöntemi işlevsellik ve nesneler ve türlerle davranışını uygular ve kullanıma sunmak için kullanılan bir türle ilişkilendirilmiş bir işlevi olduğunu öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a><span data-ttu-id="50bfd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50bfd-104">Methods</span></span>

<span data-ttu-id="50bfd-105">A *yöntemi* türü ile ilişkilendirilmiş bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-105">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="50bfd-106">Nesne odaklı programlama içinde yöntemleri işlevsellik ve nesneler ve türlerle davranışını uygular ve kullanıma sunmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50bfd-106">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="50bfd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50bfd-107">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="50bfd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50bfd-108">Remarks</span></span>
<span data-ttu-id="50bfd-109">Önceki sözdiziminde yöntemi bildirimler ve tanımlar çeşitli biçimlerde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50bfd-109">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="50bfd-110">Uzun yöntem gövdeleri eşittir (=) satır sonu izler ve tüm yöntem gövdesi girintili.</span><span class="sxs-lookup"><span data-stu-id="50bfd-110">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="50bfd-111">Öznitelikler için herhangi bir yöntem bildirimi uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-111">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="50bfd-112">Bunlar, bir yöntemin tanımı sözdizimi koyun ve genellikle ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-112">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="50bfd-113">Daha fazla bilgi için bkz: [öznitelikleri](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="50bfd-113">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="50bfd-114">Yöntemleri işaretlenir `inline`.</span><span class="sxs-lookup"><span data-stu-id="50bfd-114">Methods can be marked `inline`.</span></span> <span data-ttu-id="50bfd-115">Hakkında bilgi için `inline`, bkz: [satır içi işlevler](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="50bfd-115">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="50bfd-116">Satır içi olmayan yöntemleri türü içinde kullanılan yinelemeli olabilir; açıkça kullanmaya gerek yoktur `rec` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="50bfd-116">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="50bfd-117">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="50bfd-117">Instance Methods</span></span>
<span data-ttu-id="50bfd-118">Örnek yöntemleri ile bildirildiğinde `member` anahtar sözcüğü ve *kendi kendine tanımlayıcı*takip eden bir nokta (.) ve yöntem adı ve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="50bfd-118">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="50bfd-119">İçin olduğu gibi `let` bağlamaları *parametre listesi* bir desen olabilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-119">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="50bfd-120">Diğer .NET Framework dillerde oluşturduğunuzda genellikle, Parametreler şekilde yöntemleri bir tanımlama grubu formunda parantez içinde görüntülenir yöntemi F # alın.</span><span class="sxs-lookup"><span data-stu-id="50bfd-120">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="50bfd-121">Ancak, curried formun (parametrelerini boşluklarla ayırarak) de yaygındır ve diğer desenleri de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-121">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="50bfd-122">Aşağıdaki örnek, bir Özet olmayan örnek yöntemin kullanılması ve tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-122">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="50bfd-123">Örnek yöntemleri içinde kendi kendine tanımlayıcı let bağlamaları kullanarak tanımlanan erişim alanları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="50bfd-123">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="50bfd-124">Kendi kendine tanımlayıcı diğer üyeleri ve özellikleri erişirken kullanın.</span><span class="sxs-lookup"><span data-stu-id="50bfd-124">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="50bfd-125">Statik yöntemler</span><span class="sxs-lookup"><span data-stu-id="50bfd-125">Static Methods</span></span>
<span data-ttu-id="50bfd-126">Anahtar sözcüğü `static` bir yöntem örneği çağrılabilir belirtmek için kullanılır ve bir nesne örneği ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="50bfd-126">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="50bfd-127">Aksi takdirde, örnek yöntemleri yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-127">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="50bfd-128">Sonraki bölümdeki örnek ile bildirilen alanlarını gösterir `let` özelliği üyelerini anahtar sözcüğü, bildirilen ile `member` anahtar sözcüğü ve bir statik yöntem ile bildirilen `static` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="50bfd-128">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="50bfd-129">Aşağıdaki örnek, tanım ve statik yöntemler kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-129">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="50bfd-130">Bu yöntem tanımlarını olduğunu varsayın `SomeType` önceki bölümdeki sınıfı.</span><span class="sxs-lookup"><span data-stu-id="50bfd-130">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="50bfd-131">Soyut ve sanal yöntemleri</span><span class="sxs-lookup"><span data-stu-id="50bfd-131">Abstract and Virtual Methods</span></span>
<span data-ttu-id="50bfd-132">Anahtar sözcüğü `abstract` bir yöntem bir sanal dağıtım yuvasına sahip ve bir tanımı sınıfında olmayabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-132">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="50bfd-133">A *sanal dağıtım yuvası* çalışma zamanında sanal işlevini aramak için kullanılan içte oluşturulmuş tabloya işlevlerin bir girişe çağıran bir nesne yönelimli türü değil.</span><span class="sxs-lookup"><span data-stu-id="50bfd-133">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="50bfd-134">Sanal dağıtım mekanizması uygulayan mekanizmasıdır *çok biçimlilik*, nesne odaklı programlama önemli bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-134">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="50bfd-135">Bir tanımı olmadan en az bir soyut yöntemi olan bir sınıfı olan bir *soyut sınıf*, yani bu sınıfının hiçbir örneği oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-135">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="50bfd-136">Soyut sınıflar hakkında daha fazla bilgi için bkz: [soyut sınıflar](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="50bfd-136">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="50bfd-137">Özet yöntem bildirimleri bir yöntem gövdesi dahil etmeyin.</span><span class="sxs-lookup"><span data-stu-id="50bfd-137">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="50bfd-138">Bunun yerine, iki nokta üst üste (:) ve bir tür imzası yöntemi için yöntem adını izler.</span><span class="sxs-lookup"><span data-stu-id="50bfd-138">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="50bfd-139">Bir yöntemin tür imzası fare işaretçisi bir yöntem adı Visual Studio Kod Düzenleyicisi'nde, üzerinden dışında parametre adları duraklattığınızda IntelliSense tarafından gösterilen aynıdır.</span><span class="sxs-lookup"><span data-stu-id="50bfd-139">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="50bfd-140">Etkileşimli olarak çalışırken türü imzaları fsi.exe yorumlayıcısı tarafından da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-140">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="50bfd-141">Bir yöntemin tür imzası uygun ayırıcı simgelerle dönüş türü ve ardından bu parametreleri türlerini listeleme tarafından oluşturulmuş.</span><span class="sxs-lookup"><span data-stu-id="50bfd-141">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="50bfd-142">Curried parametreleri ayrılır `->` ve tanımlama grubu parametreleri ayrılır `*`.</span><span class="sxs-lookup"><span data-stu-id="50bfd-142">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="50bfd-143">Dönüş değeri her zaman değişkenleriyle gelen ayrılmış bir `->` simgesi.</span><span class="sxs-lookup"><span data-stu-id="50bfd-143">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="50bfd-144">Parantez işlevi türü bir parametre olduğunda gibi karmaşık parametreleri, Grup veya tek bir parametre olarak yerine iki parametre olarak bir tanımlama grubu ne zaman işleneceğini belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-144">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="50bfd-145">Ayrıca soyut yöntemler varsayılan tanımları tanımı sınıfına ekleme ve kullanarak verebilirsiniz `default` anahtar sözcüğü, bu konudaki sözdizimi bloğunda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="50bfd-145">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="50bfd-146">Aynı sınıfta bir tanımı sahip bir soyut yöntemi, sanal bir yöntem diğer .NET Framework dillerde eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-146">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="50bfd-147">Olsun veya olmasın bir tanım var, `abstract` anahtar sözcüğü sınıfı için sanal işlev tablosunda yeni bir dağıtım yuvası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50bfd-147">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="50bfd-148">Türetilen sınıflar temel sınıf soyut yöntemler olup uygulayan bağımsız olarak, soyut yöntemler uygulamaları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-148">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="50bfd-149">Türetilen bir sınıfta soyut bir yöntem uygulamak için kullanımı dışında türetilmiş sınıfında imza ve aynı ada sahip bir yöntemi tanımlamak `override` veya `default` anahtar sözcüğü ve yöntem gövdesi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="50bfd-149">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="50bfd-150">Anahtar sözcükler `override` ve `default` tam olarak aynı anlama gelir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-150">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="50bfd-151">Kullanmak `override` bir temel sınıf uygulamasını; yeni yöntemini geçersiz kılar kullanırsanız `default` özgün soyut bildirimi ile aynı sınıfta bir uygulama oluşturduğunuzda.</span><span class="sxs-lookup"><span data-stu-id="50bfd-151">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="50bfd-152">Kullanmayın `abstract` anahtar sözcüğü taban sınıf içinde soyut bildirildi yöntemi uygulayan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50bfd-152">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="50bfd-153">Aşağıdaki örnekte, soyut bir yöntem gösterilmektedir `Rotate` varsayılan uygulama, .NET Framework sanal bir yöntem denk sahip.</span><span class="sxs-lookup"><span data-stu-id="50bfd-153">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="50bfd-154">Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılar türetilmiş bir sınıf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-154">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="50bfd-155">Bu durumda, geçersiz kılma yöntemi, hiçbir şey yapmıyor şekilde davranışını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-155">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="50bfd-156">Aşırı yüklenmiş yöntemler</span><span class="sxs-lookup"><span data-stu-id="50bfd-156">Overloaded Methods</span></span>
<span data-ttu-id="50bfd-157">Aşırı yüklenmiş yöntemler, belirli bir türde aynı adlara sahip ancak farklı bağımsız değişkenleri sahip yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-157">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="50bfd-158">F #'ta isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50bfd-158">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="50bfd-159">Ancak, bağımsız değişken değil curried form, tanımlama grubu form olması koşuluyla aşırı yüklenmiş yöntemler dilde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-159">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="50bfd-160">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="50bfd-160">Optional Arguments</span></span>

<span data-ttu-id="50bfd-161">F # 4.1 ile başlayarak, yöntemleri varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenler de sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-161">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="50bfd-162">C# kod ile birlikte çalışma kolaylaştırmaya yardımcı olması için budur.</span><span class="sxs-lookup"><span data-stu-id="50bfd-162">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="50bfd-163">Aşağıdaki örnek sözdizimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="50bfd-163">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="50bfd-164">Değer geçirilen için Not `DefaultParameterValue` giriş türüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-164">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="50bfd-165">Yukarıdaki örnekte olduğu bir `int`.</span><span class="sxs-lookup"><span data-stu-id="50bfd-165">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="50bfd-166">Tamsayı olmayan değerler uygulamasına geçirmek çalışırken `DefaultParameterValue` bir derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="50bfd-166">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="50bfd-167">Örnek: Özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="50bfd-167">Example: Properties and Methods</span></span>
<span data-ttu-id="50bfd-168">Aşağıdaki örnek, alanları, özel işlevler, özellikleri ve bir statik yöntem örnekleri olan bir türü içerir.</span><span class="sxs-lookup"><span data-stu-id="50bfd-168">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="50bfd-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50bfd-169">See Also</span></span>
[<span data-ttu-id="50bfd-170">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="50bfd-170">Members</span></span>](index.md)
