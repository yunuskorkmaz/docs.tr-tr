---
title: Yöntemler
description: F# yönteminin, nesnelerin ve türlerin işlevselliğini ve davranışını ortaya çıkarmak ve uygulamak için kullanılan bir türle ilişkili bir işlev olduğunu öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400213"
---
# <a name="methods"></a><span data-ttu-id="59a3a-103">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59a3a-103">Methods</span></span>

<span data-ttu-id="59a3a-104">*Yöntem,* bir türle ilişkili bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="59a3a-105">Nesne yönelimli programlamada, nesnelerin ve türlerin işlevselliğini ve davranışını ortaya çıkarmak ve uygulamak için yöntemler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59a3a-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="59a3a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59a3a-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="59a3a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59a3a-107">Remarks</span></span>

<span data-ttu-id="59a3a-108">Önceki sözdiziminde, yöntem bildirimlerinin ve tanımlarının çeşitli biçimlerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59a3a-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="59a3a-109">Uzun yöntem gövdelerinde, bir satır sonu eşit işareti (=) izler ve tüm yöntem gövdesi girintilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="59a3a-110">Öznitelikler herhangi bir yöntem bildirimine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="59a3a-111">Yöntem tanımı için sözdiziminden önce gelir ler ve genellikle ayrı bir satırda listelenirler.</span><span class="sxs-lookup"><span data-stu-id="59a3a-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="59a3a-112">Daha fazla bilgi için [Özniteliklere](../attributes.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="59a3a-113">Yöntemler işaretlenebilir. `inline`</span><span class="sxs-lookup"><span data-stu-id="59a3a-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="59a3a-114">Hakkında bilgi `inline`için Bkz. [Satır İçi Fonksiyonlar.](../functions/inline-functions.md)</span><span class="sxs-lookup"><span data-stu-id="59a3a-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="59a3a-115">Satır içi olmayan yöntemler, tür içinde özyinelemeli olarak kullanılabilir; anahtar kelimeyi `rec` açıkça kullanmaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="59a3a-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="59a3a-116">Örnek Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="59a3a-116">Instance Methods</span></span>

<span data-ttu-id="59a3a-117">Örnek yöntemleri `member` anahtar kelime ve *kendi kendini tanımlayıcı*ile bildirilir, ardından bir dönem (.) ve yöntem adı ve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="59a3a-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="59a3a-118">Bağlamalar için `let` olduğu gibi, *parametre listesi* bir desen olabilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="59a3a-119">Genellikle, yöntem parametrelerini parantez içinde bir tuple formuna alarsınız, bu da yöntemlerdiğer .NET Framework dillerinde oluşturulduklarında F#'da nasıl görünür?</span><span class="sxs-lookup"><span data-stu-id="59a3a-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="59a3a-120">Ancak, körili form (boşluklara göre ayrılmış parametreler) de yaygındır ve diğer desenler de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="59a3a-121">Aşağıdaki örnek, soyut olmayan bir örnek yönteminin tanımını ve kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="59a3a-122">Örnek yöntemleri içinde, let bağlamaları kullanılarak tanımlanan alanlara erişmek için öz tanımlayıcıyı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="59a3a-123">Diğer üyelere ve özelliklere erişirken kendi kendini tanımlayıcıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="59a3a-124">Statik Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59a3a-124">Static Methods</span></span>

<span data-ttu-id="59a3a-125">Anahtar kelime, `static` bir yöntemin bir örnek olmadan çağrılabileceğini ve bir nesne örneğiyle ilişkilendirilmediğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59a3a-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="59a3a-126">Aksi takdirde, yöntemler örnek yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="59a3a-127">Sonraki bölümde ki `let` örnekte, anahtar kelimeyle bildirilen alanlar, `member` anahtar kelimeyle bildirilen özellik `static` üyeleri ve anahtar kelimeyle birlikte bildirilen statik bir yöntem gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="59a3a-128">Aşağıdaki örnekte statik yöntemlerin tanımı ve kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="59a3a-129">Bu yöntem tanımlarının önceki `SomeType` bölümde sınıfta olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="59a3a-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="59a3a-130">Soyut ve Sanal Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59a3a-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="59a3a-131">Anahtar kelime, `abstract` bir yöntemin sanal bir gönderme yuvasına sahip olduğunu ve sınıfta bir tanımı nın olmayabilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="59a3a-132">*Sanal gönderme yuvası,* nesne yönelimli bir türde sanal işlev çağrılarını aramak için çalışma zamanında kullanılan dahili olarak korunan işlevler tablosundaki bir giriştir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="59a3a-133">Sanal gönderme mekanizması, nesne yönelimli programlamanın önemli bir özelliği olan *çok biçimliliği*uygulayan mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="59a3a-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="59a3a-134">Tanımı olmayan en az bir soyut metod olan bir sınıf soyut bir *sınıftır,* bu da o sınıftan hiçbir örnek oluşturulamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="59a3a-135">Soyut sınıflar hakkında daha fazla bilgi için [bkz.](../abstract-classes.md)</span><span class="sxs-lookup"><span data-stu-id="59a3a-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="59a3a-136">Soyut yöntem bildirimleri bir yöntem gövdesi içermez.</span><span class="sxs-lookup"><span data-stu-id="59a3a-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="59a3a-137">Bunun yerine, yöntemin adı bir iki nokta üst üste (:) ve yöntem için bir tür imza.</span><span class="sxs-lookup"><span data-stu-id="59a3a-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="59a3a-138">Bir yöntemin tür imzası, parametre adları dışında, Görsel Stüdyo Kodu Düzenleyicisi'ndeki bir yöntem adı üzerinde fare işaretçisini duraklattığınızda IntelliSense tarafından gösterilenle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="59a3a-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="59a3a-139">Tür imzaları da etkileşimli çalışırken, tercüman, fsi.exe tarafından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="59a3a-140">Bir yöntemin tür imzası, parametrelerin türlerinin listelenmesiyle oluşur ve ardından dönüş türü, uygun ayırıcı sembollerle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59a3a-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="59a3a-141">Curried parametreleri `->` ile ayrılır ve tuple parametreleri ile `*`ayrılır .</span><span class="sxs-lookup"><span data-stu-id="59a3a-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="59a3a-142">İade değeri her zaman bir `->` sembol le bağımsız değişkenlerden ayrılır.</span><span class="sxs-lookup"><span data-stu-id="59a3a-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="59a3a-143">Parantez, işlev türünün bir parametre olması gibi karmaşık parametreleri gruplandırmak veya bir tuple'ın iki parametre yerine tek bir parametre olarak ne zaman ele alındığını belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="59a3a-144">Ayrıca, bu konuda sözdizimi bloğunda gösterildiği gibi, `default` tanımı sınıfa ekleyerek ve anahtar sözcüğü kullanarak soyut yöntemler varsayılan tanımlar da verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59a3a-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="59a3a-145">Aynı sınıfta tanımı olan soyut bir yöntem, diğer .NET Framework dillerinde sanal yönteme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="59a3a-146">Bir tanım var olsun `abstract` veya olmasın, anahtar kelime sınıf için sanal işlev tablosunda yeni bir gönderme yuvası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59a3a-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="59a3a-147">Bir taban sınıfın soyut yöntemlerini uygulayıp uygulamadığına bakılmaksızın, türemiş sınıflar soyut yöntemlerin uygulamalarını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="59a3a-148">Türemiş bir sınıfta soyut bir yöntem uygulamak için, türemiş sınıfta, anahtar `override` sözcüğü kullanmak dışında aynı ada ve imzaya sahip bir yöntem tanımlayın `default` ve yöntem gövdesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="59a3a-149">Anahtar `override` kelimeler `default` ve tam olarak aynı şey anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="59a3a-150">Yeni `override` yöntem taban sınıf uygulamasını geçersiz kılıyorsa kullanın; özgün `default` özet bildirimle aynı sınıfta bir uygulama oluşturduğunuzda kullanın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="59a3a-151">Taban sınıfta `abstract` soyut olarak bildirilen yöntemi uygulayan yöntemde anahtar sözcüğü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="59a3a-152">Aşağıdaki örnekte, bir `Rotate` .NET Framework sanal yöntemieşdeğeri olan varsayılan bir uygulama olan soyut bir yöntem gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="59a3a-153">Aşağıdaki örnekte, taban sınıf yöntemini geçersiz kılan türetilmiş bir sınıf gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="59a3a-154">Bu durumda, geçersiz kılma, yöntemin hiçbir şey yapamaması için davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="59a3a-155">Aşırı Yüklenmiş Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59a3a-155">Overloaded Methods</span></span>

<span data-ttu-id="59a3a-156">Aşırı yüklenen yöntemler, belirli bir türde aynı adlara sahip ancak farklı bağımsız değişkenleri olan yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="59a3a-157">F#'da, genellikle aşırı yüklü yöntemler yerine isteğe bağlı bağımsız değişkenler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59a3a-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="59a3a-158">Ancak, aşırı yüklenen yöntemler, bağımsız değişkenler tuple şeklinde değil, curried şeklinde olması koşuluyla, dilde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="59a3a-159">İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="59a3a-159">Optional Arguments</span></span>

<span data-ttu-id="59a3a-160">F# 4.1 ile başlayarak, yöntemlerde varsayılan parametre değerine sahip isteğe bağlı bağımsız değişkenler de olabilir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="59a3a-161">Bu, C# kodu ile birlikte çalışma işlemini kolaylaştırmak içindir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="59a3a-162">Aşağıdaki örnek sözdizimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="59a3a-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="59a3a-163">Için `DefaultParameterValue` geçirilen değerin giriş türüyle eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="59a3a-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="59a3a-164">Yukarıdaki örnekte, bir `int`.</span><span class="sxs-lookup"><span data-stu-id="59a3a-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="59a3a-165">Tamsayı olmayan bir değeri derleme `DefaultParameterValue` hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="59a3a-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="59a3a-166">Örnek: Özellikler ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59a3a-166">Example: Properties and Methods</span></span>

<span data-ttu-id="59a3a-167">Aşağıdaki örnek, alanlar, özel işlevler, özellikler ve statik bir yöntem örnekleri içeren bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="59a3a-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="59a3a-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59a3a-168">See also</span></span>

- [<span data-ttu-id="59a3a-169">Üyeler</span><span class="sxs-lookup"><span data-stu-id="59a3a-169">Members</span></span>](index.md)
