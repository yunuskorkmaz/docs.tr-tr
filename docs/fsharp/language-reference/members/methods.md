---
title: Yöntemler
description: Bir F# yöntemin, nesnelerin ve türlerin işlevlerini ve davranışlarını göstermek ve uygulamak için kullanılan bir türle ilişkili bir işlev olduğunu öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 13503690a59ace13dacba93b6fce9ea3240c5cc2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627444"
---
# <a name="methods"></a><span data-ttu-id="fa7b2-103">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-103">Methods</span></span>

<span data-ttu-id="fa7b2-104">Bir *Yöntem* , bir türle ilişkili bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="fa7b2-105">Nesne odaklı programlamada Yöntemler, nesnelerin ve türlerin işlevlerini ve davranışını göstermek ve uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa7b2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa7b2-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="fa7b2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa7b2-107">Remarks</span></span>

<span data-ttu-id="fa7b2-108">Önceki sözdiziminde, yöntem bildirimlerinin ve tanımlarının çeşitli biçimlerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="fa7b2-109">Daha uzun Yöntem gövdelerinde, bir satır sonu eşittir işareti (=) ve tüm Yöntem gövdesi girintilenir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="fa7b2-110">Öznitelikler, herhangi bir yöntem bildirimine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="fa7b2-111">Bir yöntem tanımı için sözdiziminin önüne ve genellikle ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="fa7b2-112">Daha fazla bilgi için bkz. [öznitelikler](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fa7b2-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="fa7b2-113">Yöntemler işaretlenebilir `inline`.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="fa7b2-114">Hakkında `inline`bilgi için bkz. [satır içi işlevler](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="fa7b2-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="fa7b2-115">Satır içi olmayan yöntemler, türü içinde yinelemeli olarak kullanılabilir; `rec` anahtar sözcüğünü açıkça kullanmaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="fa7b2-116">Örnek yöntemleri</span><span class="sxs-lookup"><span data-stu-id="fa7b2-116">Instance Methods</span></span>

<span data-ttu-id="fa7b2-117">Örnek yöntemleri, `member` anahtar sözcüğü ve bir *kendinden tanımlayıcı*ile, ardından bir nokta (.) ve Yöntem adı ve parametreleri ile birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="fa7b2-118">Bağlamalarda olduğu gibi, *parametre listesi* bir kalıp olabilir. `let`</span><span class="sxs-lookup"><span data-stu-id="fa7b2-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="fa7b2-119">Genellikle, yöntem parametrelerini parantez içinde, yöntemlerin diğer .NET Framework dillerde F# oluşturulduklarında görünme yöntemi olan bir demet formunda çevreleolursunuz.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="fa7b2-120">Ancak, curried formu (boşluklarla ayrılmış parametreler) de ortaktır ve diğer desenler de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="fa7b2-121">Aşağıdaki örnek Özet olmayan bir örnek yönteminin tanımını ve kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="fa7b2-122">Örnek yöntemleri içinde, Let bağlamaları kullanılarak tanımlanan alanlara erişmek için kendi kendine tanımlayıcıyı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="fa7b2-123">Diğer üyelere ve özelliklere erişirken kendi kendine tanımlayıcıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="fa7b2-124">Statik yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-124">Static Methods</span></span>

<span data-ttu-id="fa7b2-125">Anahtar sözcüğü `static` , bir yöntemin bir örnek olmadan çağrılabilecek olduğunu ve bir nesne örneğiyle ilişkilendirilmediği belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="fa7b2-126">Aksi halde Yöntemler örnek yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="fa7b2-127">Sonraki bölümde yer alan örnek, anahtar sözcükle belirtilen özellik üyeleri `let` `member` ve anahtar sözcüğüyle belirtilen `static` statik bir yöntem ile tanımlanan alanları gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="fa7b2-128">Aşağıdaki örnek, statik yöntemlerin tanımını ve kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="fa7b2-129">Bu yöntem tanımlarının `SomeType` önceki bölümdeki sınıfında olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="fa7b2-130">Soyut ve sanal yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="fa7b2-131">Anahtar sözcüğü `abstract` , bir yöntemin sanal bir dağıtım yuvasına sahip olduğunu ve sınıfta tanımına sahip olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="fa7b2-132">*Sanal dağıtım yuvası* , bir nesne odaklı türdeki sanal işlev çağrılarını aramak için çalışma zamanında kullanılan, dahili olarak tutulan işlevlerin bir girişi olan bir giriştir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="fa7b2-133">Sanal dağıtım mekanizması, nesne odaklı bir Programlamanın önemli bir özelliği olan çok *biçimlilik*uygulayan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="fa7b2-134">Tanımı olmayan en az bir soyut metoda sahip bir sınıf *soyut bir sınıftır*ve bu sınıfın hiçbir örneği oluşturulamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="fa7b2-135">Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut sınıflar](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="fa7b2-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="fa7b2-136">Soyut yöntem bildirimleri bir yöntem gövdesi içermez.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="fa7b2-137">Bunun yerine, yöntemin adı iki nokta üst üste gelir (:) ve yöntemi için bir tür imzası.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="fa7b2-138">Bir yöntemin tür imzası, fare işaretçisini parametre adları hariç Visual Studio Code düzenleyicisinde bir yöntem adı üzerinde duraklatdığınızda IntelliSense tarafından gösterilenle aynı olur.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="fa7b2-139">Etkileşimli olarak çalışırken tür imzaları, fsi. exe yorumlayıcı tarafından da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="fa7b2-140">Bir yöntemin tür imzası, parametre türleri ve ardından dönüş türü, uygun ayırıcı sembolleri ile eklenerek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="fa7b2-141">Curried parametreleri ile ayrılır `->` ve demet parametreleri ile `*`ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="fa7b2-142">Dönüş değeri her zaman bağımsız değişkenlerden bir `->` sembol ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="fa7b2-143">Parantezler, bir işlev türü parametre olduğunda ya da bir kayıt düzeninin iki parametre yerine tek bir parametre olarak ele alındığı zaman göstermek için, karmaşık parametreleri gruplandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="fa7b2-144">Ayrıca, bu konudaki Sözdizimi bloğunda gösterildiği gibi, tanımı sınıfa ekleyerek ve `default` anahtar sözcüğünü kullanarak soyut yöntemlere varsayılan tanımlamalar da verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="fa7b2-145">Aynı sınıfta bir tanımı olan soyut bir yöntem, diğer .NET Framework dillerdeki sanal bir yönteme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="fa7b2-146">Bir tanım olup olmadığı, `abstract` anahtar sözcüğü sınıfı için sanal işlev tablosunda yeni bir dağıtım yuvası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="fa7b2-147">Bir temel sınıfın soyut yöntemlerini uygulayıp uygulamamasından bağımsız olarak, türetilmiş sınıflar soyut yöntemler için uygulamalar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="fa7b2-148">Türetilmiş bir sınıfta soyut bir yöntem uygulamak için, türetilmiş sınıfta aynı ada ve imzaya sahip bir yöntemi tanımlayın, `override` or `default` anahtar sözcüğünü kullanın ve Yöntem gövdesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="fa7b2-149">Anahtar sözcükler `override` ve `default` tam olarak aynı şey anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="fa7b2-150">Yeni `override` Yöntem bir temel sınıf uygulamasını geçersiz kıldığında kullanın; özgün `default` soyut bildirimle aynı sınıfta bir uygulama oluşturduğunuzda kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="fa7b2-151">Temel sınıfta soyut olarak `abstract` tanımlanan yöntemi uygulayan yöntemde anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="fa7b2-152">Aşağıdaki örnek, bir .NET Framework sanal yönteminin `Rotate` eşdeğeri olan varsayılan bir uygulamaya sahip olan soyut bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="fa7b2-153">Aşağıdaki örnek, bir temel sınıf yöntemini geçersiz kılan türetilmiş bir sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="fa7b2-154">Bu durumda, geçersiz kılma yöntemi, yöntemin hiçbir şey yapabilmesi için davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="fa7b2-155">Aşırı yüklenmiş yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-155">Overloaded Methods</span></span>

<span data-ttu-id="fa7b2-156">Aşırı yüklenmiş yöntemler, belirli bir tür içinde özdeş adlara sahip ancak farklı bağımsız değişkenleri olan yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="fa7b2-157">F#' Da, isteğe bağlı bağımsız değişkenler genellikle aşırı yüklenmiş yöntemler yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="fa7b2-158">Ancak, bağımsız değişkenlerin bir curried form değil, tanımlama grubu biçiminde olması şartıyla, dilde aşırı yüklenmiş yöntemlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="fa7b2-159">İsteğe bağlı bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-159">Optional Arguments</span></span>

<span data-ttu-id="fa7b2-160">4,1 ile F# başlayarak, metotlarda varsayılan parametre değeri ile isteğe bağlı bağımsız değişkenlere de sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="fa7b2-161">Bu, C# kodla birlikte çalışabilirliği kolaylaştırmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="fa7b2-162">Aşağıdaki örnek söz dizimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="fa7b2-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="fa7b2-163">İçin `DefaultParameterValue` geçirilen değerin giriş türüyle eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="fa7b2-164">Yukarıdaki örnekte, bir `int`.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="fa7b2-165">Tamsayı olmayan bir değeri `DefaultParameterValue` ' a geçirmeye çalışmak, derleme hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="fa7b2-166">Örnek: Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-166">Example: Properties and Methods</span></span>

<span data-ttu-id="fa7b2-167">Aşağıdaki örnek, alan, özel işlevler, Özellikler ve statik bir yöntem örnekleri içeren bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="fa7b2-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa7b2-168">See also</span></span>

- [<span data-ttu-id="fa7b2-169">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fa7b2-169">Members</span></span>](index.md)
