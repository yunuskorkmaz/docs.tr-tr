---
title: 'Öğretici: bir tür sağlayıcısı (F #) oluşturma'
description: 'Temel kavramları göstermek üzere birkaç basit tür sağlayıcısı inceleyerek kendi F # tür sağlayıcıları F # 3.0 içinde oluşturmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 3c998377b2c3a408d536ef416f3799bf7f04b6bd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44212327"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="2a023-103">Öğretici: bir tür sağlayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a023-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="2a023-104">F # tür sağlayıcısı mekanizması, kendi bilgi zengin programlama desteğinin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2a023-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="2a023-105">Bu öğretici, kendi tür sağlayıcıları tarafından temel kavramları göstermek üzere birkaç basit tür sağlayıcısı geliştirmeden walking oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a023-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="2a023-106">F # tür sağlayıcısı mekanizması hakkında daha fazla bilgi için bkz. [tür sağlayıcıları](index.md).</span><span class="sxs-lookup"><span data-stu-id="2a023-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="2a023-107">Bir dizi için yaygın olarak kullanılan Internet ve kurumsal veri hizmetlerinde tür sağlayıcıları F # ekosistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="2a023-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="2a023-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a023-108">For example:</span></span>

- <span data-ttu-id="2a023-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON, XML, CSV ve HTML biçimleri belge için tür sağlayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="2a023-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="2a023-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) bu veri kaynaklarına karşı sorgular bir nesne eşleme ve F # LINQ üzerinden SQL veritabanlarını kesin türü belirtilmiş erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="2a023-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sahip bir derleme zamanı için tür sağlayıcıları kümesini iade F # T-SQL ekleme.</span><span class="sxs-lookup"><span data-stu-id="2a023-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="2a023-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) kullanmak için tür sağlayıcıları SQL, Entity Framework, OData ve WSDL veri hizmetlerine erişmek için yalnızca .NET Framework programlama ile daha eski bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="2a023-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="2a023-113">Gerektiğinde, özel tür sağlayıcılarınızı oluşturabilir veya başkalarının oluşturulan tür sağlayıcılarına başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="2a023-114">Örneğin, kuruluşunuz bir büyük ve artan sayıda adlandırılmış veri kümeleri, her biri kendi kararlı veri şemasına sahip sağlayan bir veri hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="2a023-115">Şemaları okuyan ve geçerli veri kümelerini programcıya türü kesin belirlenmiş şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2a023-116">Başlamadan önce</span><span class="sxs-lookup"><span data-stu-id="2a023-116">Before You Start</span></span>

<span data-ttu-id="2a023-117">Tür sağlayıcısı mekanizması, öncelikli olarak kararlı veri ve hizmet bilgi uzaylarının F programlama deneyimi # ekleme için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2a023-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="2a023-118">Bu mekanizma, program mantığına uygun şekilde, programın yürütülmesi sırasında şema değişiklikleri bilgi alanları ekleme için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="2a023-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="2a023-119">Ayrıca, bu etki bazı geçerli kullanımlarını içerse mekanizması içi diller için meta programlama tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="2a023-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="2a023-120">Burada bir tür sağlayıcısı geliştirilmesini çok yüksek bir değer oluşturur ve bu mekanizma yalnızca gerekli olduğunda kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2a023-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="2a023-121">Burada bir şema kullanılamaz bir tür sağlayıcısı yazma kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="2a023-122">Benzer şekilde, bir tür sağlayıcısı sıradan (veya hatta var olduğunda) yazma kaçınmalısınız .NET kitaplığı yeterli.</span><span class="sxs-lookup"><span data-stu-id="2a023-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="2a023-123">Başlamadan önce aşağıdaki soruları sormaya:</span><span class="sxs-lookup"><span data-stu-id="2a023-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="2a023-124">Bilgi kaynağınız için bir şema var mı?</span><span class="sxs-lookup"><span data-stu-id="2a023-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="2a023-125">Bu durumda, F # ve .NET tür sistemi eşlemeye nedir?</span><span class="sxs-lookup"><span data-stu-id="2a023-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="2a023-126">Mevcut bir (dinamik olarak yazılan) API uygulamanız için başlangıç noktası olarak kullanabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="2a023-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="2a023-127">Sizin ve kuruluşunuzun yeterli yazmayı faydalı hale getirmek için tür sağlayıcısını kullanımları gerekir mi?</span><span class="sxs-lookup"><span data-stu-id="2a023-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="2a023-128">Normal bir .NET kitaplığı, ihtiyaçlarınızı karşılayacak?</span><span class="sxs-lookup"><span data-stu-id="2a023-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="2a023-129">Ne kadar şemanızı değişecek mi?</span><span class="sxs-lookup"><span data-stu-id="2a023-129">How much will your schema change?</span></span>

- <span data-ttu-id="2a023-130">Kodlama sırasında değişecek mi?</span><span class="sxs-lookup"><span data-stu-id="2a023-130">Will it change during coding?</span></span>

- <span data-ttu-id="2a023-131">Oturumlarının kodlama arasında değişir mi?</span><span class="sxs-lookup"><span data-stu-id="2a023-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="2a023-132">Bu program yürütme sırasında değişecek mi?</span><span class="sxs-lookup"><span data-stu-id="2a023-132">Will it change during program execution?</span></span>

<span data-ttu-id="2a023-133">Tür sağlayıcıları şema zamanında ve derlenmiş kod kullanım ömrü süresince kararlı olduğu durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="2a023-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="2a023-134">Bir basit tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2a023-134">A Simple Type Provider</span></span>

<span data-ttu-id="2a023-135">Bu örnek Samples.HelloWorldTypeProvider, örnekler, benzer olan `examples` dizininde [F # tür sağlayıcısı SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="2a023-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="2a023-136">Sağlayıcısı "F # imza sözdizimini kullanarak ve hariç tüm sayfalarında için ayrıntıları atlayarak aşağıdaki kodun gösterdiği olarak 100 silinen türlerini içeren bir tür alanı" kullanılabilmesini `Type1`.</span><span class="sxs-lookup"><span data-stu-id="2a023-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="2a023-137">Silinen türleri hakkında daha fazla bilgi için bkz. [ayrıntılar hakkında silinmesi sağlanan türleri](#details-about-erased-provided-types) bu konuda.</span><span class="sxs-lookup"><span data-stu-id="2a023-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

```fsharp
namespace Samples.HelloWorldTypeProvider

type Type1 =
    /// This is a static property.
    static member StaticProperty : string

    /// This constructor takes no arguments.
    new : unit -> Type1

    /// This constructor takes one argument.
    new : data:string -> Type1

    /// This is an instance property.
    member InstanceProperty : int

    /// This is an instance method.
    member InstanceMethod : x:int -> char

    nested type NestedType = 
        /// This is StaticProperty1 on NestedType.
        static member StaticProperty1 : string
        …
        /// This is StaticProperty100 on NestedType.
        static member StaticProperty100 : string

type Type2 =
…
…

type Type100 =
…
```

<span data-ttu-id="2a023-138">Dizi türleri ve üyeleri sağlanan statik olarak bilinen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2a023-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="2a023-139">Bu örnek, bir şemaya bağlı türleri sağlama yeteneği sağlayıcılarının yararlanarak değil.</span><span class="sxs-lookup"><span data-stu-id="2a023-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="2a023-140">Tür sağlayıcısı uygulaması aşağıdaki kodda gösterilmiştir ve Ayrıntılar, bu konunun sonraki bölümlerinde ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a023-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

>[!WARNING]
<span data-ttu-id="2a023-141">Bu kod ve çevrimiçi örnekleri arasındaki farklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-141">There may be differences between this code and the online samples.</span></span>

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open ProviderImplementation.ProvidedTypes
open FSharp.Core.CompilerServices
open FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces(config)

  let namespaceName = "Samples.HelloWorldTypeProvider"
  let thisAssembly = Assembly.GetExecutingAssembly()

  // Make one provided type, called TypeN.
  let makeOneProvidedType (n:int) = 
  …
  // Now generate 100 types
  let types = [ for i in 1 .. 100 -> makeOneProvidedType i ] 

  // And add them to the namespace
  do this.AddNamespace(namespaceName, types)

[<assembly:TypeProviderAssembly>] 
do()
```

<span data-ttu-id="2a023-142">Bu sağlayıcıyı kullanmak için Visual Studio ayrı bir örneğini açın, bir F # komut dosyası oluşturabilir ve ardından aşağıdaki kodun gösterdiği gibi #r kullanarak betiğinizi sağlayıcı için bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a023-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

```fsharp
#r @".\bin\Debug\Samples.HelloWorldTypeProvider.dll"

let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")

let obj2 = Samples.HelloWorldTypeProvider.Type1("some other data")

obj1.InstanceProperty
obj2.InstanceProperty

[ for index in 0 .. obj1.InstanceProperty-1 -> obj1.InstanceMethod(index) ]
[ for index in 0 .. obj2.InstanceProperty-1 -> obj2.InstanceMethod(index) ]

let data1 = Samples.HelloWorldTypeProvider.Type1.NestedType.StaticProperty35
```

<span data-ttu-id="2a023-143">Türleri altında bulun `Samples.HelloWorldTypeProvider` tür sağlayıcısını oluşturulan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2a023-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="2a023-144">Sağlayıcıyı yeniden derlemeden önce Visual Studio ve F # Etkileşimli'nın Sağlayıcı DLL kullanan tüm örneklerini kapalı emin olun.</span><span class="sxs-lookup"><span data-stu-id="2a023-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="2a023-145">Aksi takdirde, çıkış DLL kilitli olduğundan bir yapı hatası meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="2a023-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="2a023-146">Bu sağlayıcı yazdırma ifadeleri kullanarak hata ayıklamak için sağlayıcı ile ilgili bir sorun ortaya koyan bir betik olun ve ardından aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2a023-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="2a023-147">Bu sağlayıcı Visual Studio kullanarak hata ayıklama için yönetici kimlik bilgileriyle Visual Studio komut istemi açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2a023-147">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="2a023-148">Alternatif olarak, Visual Studio'yu açın, hata ayıklama menüsünü açın, `Debug/Attach to process…`ve başka bir ekleme `devenv` burada düzenlediğiniz komut dosyanızı işlem.</span><span class="sxs-lookup"><span data-stu-id="2a023-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="2a023-149">Bu yöntemi kullanarak, ikinci örneği (tam IntelliSense ve diğer özellikleri) içine etkileşimli olarak ifadeleri yazarak belirli bir tür sağlayıcısı mantığında daha kolay hedef alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="2a023-150">Oluşturulan kod hataları daha iyi tanımlamak için hata ayıklama Just My Code'u devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="2a023-151">Etkinleştirme veya bu özelliği devre dışı bırakma hakkında daha fazla bilgi için bkz. [hata ayıklayıcısı ile kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="2a023-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="2a023-152">Ayrıca, ayrıca ilk fırsat özel durum yakalama açarak ayarlayabilirsiniz `Debug` menüsüne ve ardından `Exceptions` açmak için Ctrl + Alt + E tuşlarını seçerek veya `Exceptions` iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="2a023-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="2a023-153">Bu iletişim kutusunda, altında `Common Language Runtime Exceptions`seçin `Thrown` onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="2a023-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="2a023-154">Tür sağlayıcısı uygulaması</span><span class="sxs-lookup"><span data-stu-id="2a023-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="2a023-155">Bu bölüm asıl tür sağlayıcısı uygulama bölümleri boyunca size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a023-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="2a023-156">İlk olarak, türü özel bir tür sağlayıcısı kendisi için tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="2a023-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="2a023-157">Bu tür genel olmalıdır ve kendisiyle işaretlemek [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) ayrı bir F # proje türü içeren derlemeye başvuruda bulunduğunda derleyicinin tür sağlayıcısını tanıyabilmesi için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2a023-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="2a023-158">*Config* parametresi isteğe bağlıdır ve, varsa, F # derleyicisi oluşturan tür sağlayıcısı örneği için bağlamsal yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2a023-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="2a023-159">Ardından, uygulamanız [Itypeprovider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2a023-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="2a023-160">Bu durumda, kullandığınız `TypeProviderForNamespaces` türünü `ProvidedTypes` temel tür olarak API.</span><span class="sxs-lookup"><span data-stu-id="2a023-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="2a023-161">Bu yardımcı türü her biri doğrudan sınırlı sayıda sabit içerir, ad alanları, türler eagerly sağlanan sağlanan sınırlı koleksiyonu eagerly sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="2a023-162">Bu bağlamda, sağlayıcı *eagerly* bile kullanılan gerekli veya olmayan türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a023-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="2a023-163">Ardından, sağlanan türler için ad alanı belirten yerel özel değerleri tanımlayın ve tür sağlayıcısı derlemenin kendisini bulun.</span><span class="sxs-lookup"><span data-stu-id="2a023-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="2a023-164">Bu derleme, daha sonra silinen türleri mantıksal üst türü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a023-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="2a023-165">Ardından, her tür Type1 sağlamak için bir işlev oluşturun... Type100.</span><span class="sxs-lookup"><span data-stu-id="2a023-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="2a023-166">Bu işlev, bu konunun ilerleyen bölümlerinde daha ayrıntılı açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2a023-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="2a023-167">Ardından, 100 sağlananlardan oluştur:</span><span class="sxs-lookup"><span data-stu-id="2a023-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="2a023-168">Ardından, belirtilen bir ad alanı türleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a023-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="2a023-169">Son olarak, bir tür sağlayıcısı DLL oluştururken bir bütünleştirilmiş kod özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a023-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="2a023-170">Bir tür ve üyeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="2a023-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="2a023-171">`makeOneProvidedType` İşlevi türlerinden birini sağlayarak gerçek iş yapar.</span><span class="sxs-lookup"><span data-stu-id="2a023-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="2a023-172">Bu adım, bu işlev uygulamasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2a023-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="2a023-173">İlk olarak sağlanan türü oluşturun (örneğin, Type1, n, = 1 veya Type57, 57 = n olduğunda).</span><span class="sxs-lookup"><span data-stu-id="2a023-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="2a023-174">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="2a023-174">You should note the following points:</span></span>

- <span data-ttu-id="2a023-175">Başka bir sağlanan türü silinir.</span><span class="sxs-lookup"><span data-stu-id="2a023-175">This provided type is erased.</span></span>  <span data-ttu-id="2a023-176">Temel tür olduğunu belirttiğinden `obj`, örnekleri, tür değerleri görünür [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) derlenmiş kodu.</span><span class="sxs-lookup"><span data-stu-id="2a023-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="2a023-177">Bir iç içe türü belirttiğinizde, derlemeyi ve ad alanını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="2a023-178">Silinen türleri için derleme, tür sağlayıcısı derlemenin kendisini olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="2a023-179">Ardından, XML belgeleri türüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a023-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="2a023-180">Bu belge, yani gecikir, konak derleyici gerekiyorsa isteğe bağlı hesaplanan.</span><span class="sxs-lookup"><span data-stu-id="2a023-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="2a023-181">Sonraki türüne sağlanan statik bir özellik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a023-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="2a023-182">Bu özellik alma "Hello!" dizesi her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="2a023-183">`GetterCode` Özelliği almak için konak derleyicinin ürettiği kodu temsil eden bir F # teklif özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="2a023-184">Teklifleri hakkında daha fazla bilgi için bkz: [kod tırnak işaretleri (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="2a023-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="2a023-185">XML belgelerinde özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a023-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="2a023-186">Artık sağlanan özelliği için sağlanan türü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a023-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="2a023-187">Belirtilen üye bir ve yalnızca bir türe eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="2a023-188">Aksi takdirde, üye hiç erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2a023-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="2a023-189">Parametre almayan sağlanan bir oluşturucu şimdi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a023-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="2a023-190">`InvokeCode` Oluşturucu çağrıldığında, konak Derleyicinin oluşturduğu kodu temsil eden bir F # teklif Oluşturucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a023-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="2a023-191">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="2a023-192">Belirtilen türün bir örneğini "Nesne verilerini" ile temel alınan verileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a023-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="2a023-193">Tırnak işaretli kod dönüştürmeyi içerir [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) silinmesini türü olduğundan (sağlanan türü olduğunda bildirdiğiniz belirttiğiniz gibi) bu türü sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a023-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="2a023-194">XML belgeleri oluşturucuyu ekleyin ve sağlanan türü için sağlanan oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2a023-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="2a023-195">Bir parametre alan ikinci bir sağlanan Oluşturucu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2a023-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="2a023-196">`InvokeCode` Oluşturucu tekrar ana derleyici yönteme bir çağrı için oluşturulan kodu temsil eden bir F # teklif döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a023-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="2a023-197">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="2a023-198">Belirtilen türün bir örneğini, temel alınan veriler "on" ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a023-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="2a023-199">Zaten fark etmiş `InvokeCode` tırnak işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a023-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="2a023-200">Bu işlev girişi ifadeleri, oluşturucu parametresi başına bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="2a023-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="2a023-201">Bu durumda, tek bir parametre değeri temsil eden bir ifade kullanılabilir `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="2a023-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="2a023-202">Dönüş değeri silinen türü için oluşturucu çağrısı için kod olacak şekilde zorlar `obj`.</span><span class="sxs-lookup"><span data-stu-id="2a023-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="2a023-203">İkinci sağlanan Oluşturucu türüne ekledikten sonra sağlanan örnek özellik oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2a023-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="2a023-204">Bu özellik alma gösterimi nesne dizenin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a023-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="2a023-205">`GetterCode` Özelliği özellik get yapılmaya konak derleyicinin ürettiği kodu belirten bir F # teklif döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a023-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="2a023-206">Gibi `InvokeCode`, `GetterCode` tırnak işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a023-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="2a023-207">Konak derleyici bağımsız değişken listesiyle birlikte bu işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="2a023-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="2a023-208">Bu durumda, bağımsız değişkenleri yalnızca kullanarak erişebileceğiniz bağlı alıcı çağrılmakta olan, örneği temsil eden tek ifade ekleyin `args.[0]`. Uygulamasını `GetterCode` sonra silinen yazın sonucu tırnak içine splices `obj`, ve bir atama türü bir nesne bir dize olduğunu denetlemek için derleyicinin mekanizması karşılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a023-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="2a023-209">Bir sonraki kısmına `makeOneProvidedType` bir parametre ile bir örnek yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-209">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

```fsharp
let instanceMeth = 
    ProvidedMethod(methodName = "InstanceMethod", 
                   parameters = [ProvidedParameter("x",typeof<int>)], 
                   returnType = typeof<char>, 
                   invokeCode = (fun args -> 
                       <@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

<span data-ttu-id="2a023-210">Son olarak, 100 iç içe özellikler içeren iç içe geçmiş bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a023-210">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="2a023-211">Bu oluşturma türü ve özelliklerini iç içe geçmiş, yani gecikir, isteğe bağlı olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-211">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () -> 
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () -> 
    let staticPropsInNestedType = 
      [ for i in 1 .. 100 do
          let valueOfTheProperty = "I am string "  + string i

          let p = 
            ProvidedProperty(propertyName = "StaticProperty" + string i, 
              propertyType = typeof<string>, 
              isStatic = true,
              getterCode= (fun args -> <@@ valueOfTheProperty @@>))

          p.AddXmlDocDelayed(fun () -> 
              sprintf "This is StaticProperty%d on NestedType" i)

          yield p ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="2a023-212">Silinen sağlanan türleri hakkında ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2a023-212">Details about Erased Provided Types</span></span>

<span data-ttu-id="2a023-213">Bu bölümdeki örnek yalnızca sağlar *sağlananlardan silinmesi*, aşağıdaki durumlarda özellikle yararlı olan:</span><span class="sxs-lookup"><span data-stu-id="2a023-213">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="2a023-214">Ne zaman yalnızca verilere ve yöntemlere içeren bir bilgi alanı için bir sağlayıcı yazıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2a023-214">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="2a023-215">Ne zaman doğru çalışma zamanı türü anlamları burada bilgi alanı pratik kullanım için kritik olmayan bir sağlayıcı yazıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2a023-215">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="2a023-216">Ne zaman büyük ve birbirine bilgi alanı gerçek .NET türleri üretmek için teknik olarak uygulanabilir olmayan bir bilgi alan için bir sağlayıcı yazıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2a023-216">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="2a023-217">Bu örnekte, her tür türüne silinir sağlanan `obj`, ve tüm kullanımları türü tür olarak görünür `obj` derlenmiş kodu.</span><span class="sxs-lookup"><span data-stu-id="2a023-217">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="2a023-218">Aslında, bu örneklerde temel nesneler dizelerdir, ancak türü olarak görünür `System.Object` derlenmiş .NET kodu.</span><span class="sxs-lookup"><span data-stu-id="2a023-218">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="2a023-219">Tür silme işlemini ile tüm kullanımları için açık kutulama kullanabileceğiniz gibi kutudan çıkarma ve atama bozmaya için türleri silinir.</span><span class="sxs-lookup"><span data-stu-id="2a023-219">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="2a023-220">Bu durumda, nesne kullanıldığında geçerli olmayan bir yayın özel durumu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-220">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="2a023-221">Bir sağlayıcı çalışma zamanı false ifadeleri karşı korumaya yardımcı olmak için kendi özel gösterimi türü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-221">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="2a023-222">F # dilinde kendisi silinmiş türleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2a023-222">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="2a023-223">Yalnızca sağlanan türler silinebilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-223">Only provided types may be erased.</span></span> <span data-ttu-id="2a023-224">Sonuçları, hem pratik anlamanız gerekir ve anlam kullanarak, silinen türleri, tür sağlayıcısı veya sağlayan bir sağlayıcı için türleri silinir.</span><span class="sxs-lookup"><span data-stu-id="2a023-224">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="2a023-225">Silinen bir türü gerçek .NET tür yok.</span><span class="sxs-lookup"><span data-stu-id="2a023-225">An erased type has no real .NET type.</span></span> <span data-ttu-id="2a023-226">Bu nedenle, türü üzerinden çevrenin yansımasını yapamayacağı ve çalışma zamanı yayınları ve çalışma zamanı türü semantiği kullanan diğer teknikleri kullanırsanız silinen türleri bozmaya.</span><span class="sxs-lookup"><span data-stu-id="2a023-226">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="2a023-227">Silinen türlerinin subversion çalışma zamanında tür özel durumlar sık sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-227">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="2a023-228">Türleri sağlanan gösterimleri silinmesi için seçme</span><span class="sxs-lookup"><span data-stu-id="2a023-228">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="2a023-229">Bazı silinen sağlananlardan kullanımlar için hiçbir gösterimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2a023-229">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="2a023-230">Örneğin, silinen tür yalnızca statik özellikleri ve üyeleri ve Oluşturucusu içerebilir ve yöntem ya da özellikleri türün bir örneğini döndürür sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-230">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="2a023-231">Silinen bir örneğini türü sağlanan erişebiliyorsa, aşağıdaki soruları göz önünde bulundurmalısınız:</span><span class="sxs-lookup"><span data-stu-id="2a023-231">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="2a023-232">**Belirtilen bir türün silinme nedir?**</span><span class="sxs-lookup"><span data-stu-id="2a023-232">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="2a023-233">Belirtilen bir türün silinme türü'nın derlenmiş .NET kodu nasıl göründüğü üzerinedir.</span><span class="sxs-lookup"><span data-stu-id="2a023-233">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="2a023-234">Sağlanan silinen sınıf türü silinme her zaman ilk silinebilir olmayan temel devralma zincirinde türü türüdür.</span><span class="sxs-lookup"><span data-stu-id="2a023-234">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="2a023-235">Her zaman silinme silinen sağlanan arabirim türü olduğundan `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="2a023-235">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="2a023-236">**Sağlanan türü temsillerini nelerdir?**</span><span class="sxs-lookup"><span data-stu-id="2a023-236">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="2a023-237">Bir silinen sağlanan türü için olası nesne kümesini kendi gösterimleri çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2a023-237">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="2a023-238">Bu belgedeki örnekte, tüm silinen sağlanan temsillerini türleri `Type1..Type100` dize nesneler her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-238">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="2a023-239">Sağlanan türü tüm temsillerini silinmesini sağlanan türü ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-239">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="2a023-240">(Aksi halde, F # derleyicisi, bir tür sağlayıcısı kullanım için bir hata verir veya geçerli olmayan doğrulanamayan .NET kodu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a023-240">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="2a023-241">Bir tür sağlayıcısı geçersiz bir temsili veren kodu döndürmesi durumunda geçerli değil.)</span><span class="sxs-lookup"><span data-stu-id="2a023-241">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="2a023-242">Sağlanan nesneler için bir gösterimi ikisi için de çok yaygın olarak, aşağıdaki yaklaşımlardan birini kullanarak birini seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-242">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="2a023-243">Üzerinde var olan bir .NET türü kesin olarak belirlenmiş bir sarmalayıcı yalnızca sağlıyorsanız, genellikle bu türe silmek, o türün örneklerinin gösterimleri veya her ikisi de olarak kullanın türünüz için mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="2a023-243">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="2a023-244">Bu türün varolan yöntemleri çoğunu yine de kesin türdeki sürümü kullanılırken anlamlı olduğunda bu yaklaşım uygundur.</span><span class="sxs-lookup"><span data-stu-id="2a023-244">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="2a023-245">Farklı bir API önemli ölçüde var olan bir .NET API'SİNDEN oluşturmak istiyorsanız, temsiller için sağlanan türler ve tür silme işlemini olacak çalışma zamanı türleri oluşturmak için mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="2a023-245">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="2a023-246">Bu belgede örnek sağlanan Nesne ifadeleri dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-246">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="2a023-247">Genellikle, diğer nesneleri temsiller için kullanılmak üzere uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-247">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="2a023-248">Örneğin, bir özellik paketi olarak bir sözlük kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-248">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="2a023-249">Alternatif olarak, türü Sağlayıcınızdaki çalışma zamanında bir veya daha fazla çalışma zamanı işlemlerinin yanı sıra bir gösterim oluşturmak için kullanılan bir tür tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-249">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="2a023-250">Belirtilen üye, ardından bu nesne türü örnekleri oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-250">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="2a023-251">Bu durumda, (isteğe bağlı) bu tür türü silinme bu türü olarak belirterek kullanabilirsiniz `baseType` oluştururken `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="2a023-251">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="2a023-252">Önemli dersler</span><span class="sxs-lookup"><span data-stu-id="2a023-252">Key Lessons</span></span>

<span data-ttu-id="2a023-253">Önceki bölümde çeşitli türler, özellikler ve yöntemler sağlayan basit bir silme tür sağlayıcısı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a023-253">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="2a023-254">Bu bölümde açıklanan bazı avantajları ve dezavantajları silinen türleri bir türü sağlayıcısından sağlayan dahil olmak üzere tür silme işlemini kavramını ve Silinen türleri temsillerini ele alınan.</span><span class="sxs-lookup"><span data-stu-id="2a023-254">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="2a023-255">Statik parametreler kullanan bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2a023-255">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="2a023-256">Tür sağlayıcıları tarafından statik veri Parametreleştirme olanağı bile sağlayıcısı herhangi bir yerel veya uzak veri erişimi gerekmez, durumlarda çok ilginç senaryolarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2a023-256">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="2a023-257">Bu bölümde, böyle bir sağlayıcı bir araya getirilmesi için bazı temel tekniklerini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-257">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="2a023-258">Regex sağlayıcısı türü işaretli</span><span class="sxs-lookup"><span data-stu-id="2a023-258">Type Checked Regex Provider</span></span>

<span data-ttu-id="2a023-259">.NET sarmalayan bir tür sağlayıcısı normal ifadeler için uygulamak istediğiniz Imagine <xref:System.Text.RegularExpressions.Regex> aşağıdaki derleme zamanı garanti sağlayan bir arabirimi kitaplıkları:</span><span class="sxs-lookup"><span data-stu-id="2a023-259">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="2a023-260">Bir normal ifade geçerli olup olmadığını doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="2a023-260">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="2a023-261">Normal ifadede herhangi bir grup adı temel alan eşleşme adlandırılmış özellikleri sunuyor.</span><span class="sxs-lookup"><span data-stu-id="2a023-261">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="2a023-262">Bu bölümde tür sağlayıcıları oluşturmak için nasıl kullanılacağını gösteren bir `RegexTyped` normal ifade deseni aşağıdaki yararları sağlamak üzere parametreleştiren yazın.</span><span class="sxs-lookup"><span data-stu-id="2a023-262">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="2a023-263">Derleyici, belirtilen desenle geçerli değil ve adlandırılmış eşleşmeleri Özellikler'i kullanarak erişebilmeleri tür sağlayıcısını grupları desenden ayıklayabilmeniz için bir hata rapor eder.</span><span class="sxs-lookup"><span data-stu-id="2a023-263">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="2a023-264">Bir tür sağlayıcısı tasarlarken, açık bir API nasıl görünmelidir dikkate almanız gereken son kullanıcılar ve bu tasarım .NET kodu için nasıl çevirir.</span><span class="sxs-lookup"><span data-stu-id="2a023-264">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="2a023-265">Aşağıdaki örnek, alan kodunu bileşenlerini almak için bu tür bir API kullanmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="2a023-265">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="2a023-266">Aşağıdaki örnek, ne tür sağlayıcısı bu çağrıları çeviren gösterir:</span><span class="sxs-lookup"><span data-stu-id="2a023-266">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="2a023-267">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="2a023-267">Note the following points:</span></span>

- <span data-ttu-id="2a023-268">Standart Regex tür parametreli temsil eden `RegexTyped` türü.</span><span class="sxs-lookup"><span data-stu-id="2a023-268">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="2a023-269">`RegexTyped` Deseni için statik tür bağımsız değişkeni olarak geçirerek Regex oluşturucusuna bir çağrı Oluşturucusu sonuçlanıyor.</span><span class="sxs-lookup"><span data-stu-id="2a023-269">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="2a023-270">Sonuçları `Match` yöntemi Standart tarafından temsil edilen <xref:System.Text.RegularExpressions.Match> türü.</span><span class="sxs-lookup"><span data-stu-id="2a023-270">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="2a023-271">Belirtilen bir özelliği her adlandırılmış Grup sonuçları gruplayan ve özellik erişen bir kullanımıyla sonuçlanıyor bir dizin oluşturucusunda bir eşleşme'nın `Groups` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2a023-271">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="2a023-272">Aşağıdaki kodu bir tür sağlayıcısı için uygulanacak bir mantıksal çekirdek olduğunu ve sağlanan türü için tüm üyeleri Ayrıca bu örnek atlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-272">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="2a023-273">Her üye eklendi hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde ilgili bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="2a023-273">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="2a023-274">Tam kod için içinden örneği karşıdan [F # 3.0 örnek paketi](https://fsharp3sample.codeplex.com) Codeplex Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="2a023-274">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams, 
        instantiationFunction=(fun typeName parameterValues ->

          match parameterValues with 
          | [| :? string as pattern|] -> 

            // Create an instance of the regular expression. 
            //
            // This will fail with System.ArgumentException if the regular expression is not valid. 
            // The exception will escape the type provider and be reported in client code.
            let r = System.Text.RegularExpressions.Regex(pattern)            

            // Declare the typed regex provided type.
            // The type erasure of this type is 'obj', even though the representation will always be a Regex
            // This, combined with hiding the object methods, makes the IntelliSense experience simpler.
            let ty = 
              ProvidedTypeDefinition(
                thisAssembly, 
                rootNamespace, 
                typeName, 
                baseType = Some baseTy)

            ...

            ty
          | _ -> failwith "unexpected parameter values")) 

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

<span data-ttu-id="2a023-275">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="2a023-275">Note the following points:</span></span>

- <span data-ttu-id="2a023-276">Tür sağlayıcısını iki statik parametreleri alır: `pattern`, zorunlu olan ve `options`, (varsayılan değer sağlandığı için) isteğe bağlı olduğu.</span><span class="sxs-lookup"><span data-stu-id="2a023-276">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="2a023-277">Statik bağımsız değişkenler sağlanan sonra normal ifade örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a023-277">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="2a023-278">Bu örnek, normal ifade hatalı biçimlendirilmiş ve kullanıcılara bu hata bildirilir bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a023-278">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="2a023-279">İçinde `DefineStaticParameters` geri bağımsız değişkenler sağlanan sonra döndürülecek tür tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2a023-279">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="2a023-280">Bu kod ayarlar `HideObjectMethods` IntelliSense deneyimi kolaylaştırılmış kalması true.</span><span class="sxs-lookup"><span data-stu-id="2a023-280">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="2a023-281">Bu öznitelik neden `Equals`, `GetHashCode`, `Finalize`, ve `GetType` atlanması üyelerinin sağlanan nesne için IntelliSense listelerden.</span><span class="sxs-lookup"><span data-stu-id="2a023-281">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="2a023-282">Kullandığınız `obj` yöntemi, ancak temel türünü kullanırsınız gibi bir `Regex` sonraki örnekte gösterildiği gibi bu tür, çalışma zamanı temsili olarak nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2a023-282">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="2a023-283">Çağrı `Regex` Oluşturucusu oluşturur bir <xref:System.ArgumentException> ne zaman bir normal ifade geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2a023-283">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="2a023-284">Derleyici, bu özel durumu yakalar ve derleme zamanında ya da Visual Studio düzenleyicisinde bir hata iletisi kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="2a023-284">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="2a023-285">Bu durum, bir uygulamayı çalıştırmadan doğrulanması için normal ifadeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-285">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="2a023-286">Yukarıda tanımlanan tür henüz herhangi bir anlamlı yöntemleri veya özellikleri içermediğinden kullanışlı değildir.</span><span class="sxs-lookup"><span data-stu-id="2a023-286">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="2a023-287">İlk olarak, bir statik ekleyin `IsMatch` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2a023-287">First, add a static `IsMatch` method:</span></span>

```fsharp
let isMatch = 
    ProvidedMethod(
        methodName = "IsMatch", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = typeof<bool>, 
        isStatic = true,
        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

<span data-ttu-id="2a023-288">Önceki kod, bir yöntem tanımlar `IsMatch`, giriş olarak bir dize alır ve döndürür bir `bool`.</span><span class="sxs-lookup"><span data-stu-id="2a023-288">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="2a023-289">Kullanımı yalnızca hassas parçasıdır `args` bağımsız değişkeni içinde `InvokeCode` tanımı.</span><span class="sxs-lookup"><span data-stu-id="2a023-289">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="2a023-290">Bu örnekte, `args` bu yönteme bağımsız değişkenleri temsil eden teklif listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a023-290">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="2a023-291">Yöntemi bir örnek yöntem ise, ilk bağımsız değişken temsil eden `this` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="2a023-291">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="2a023-292">Ancak, statik bir yöntem için yalnızca tüm açık bağımsız değişkenler yöntemi için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="2a023-292">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="2a023-293">Tırnak işaretli değerinin türü belirtilen dönüş türü eşleşmelidir Not (Bu durumda, `bool`).</span><span class="sxs-lookup"><span data-stu-id="2a023-293">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="2a023-294">Ayrıca bu kodu kullanan Not `AddXmlDoc` yöntemi sağlanan yöntem aynı zamanda IntelliSense sağladığınız kullanışlı belgeler olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2a023-294">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="2a023-295">Ardından, bir örneği Match yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a023-295">Next, add an instance Match method.</span></span> <span data-ttu-id="2a023-296">Ancak, bu yöntem bir sağlanan değerini döndürmelidir `Match` grupları türü kesin belirlenmiş bir biçimde erişilebilir olacak şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="2a023-296">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="2a023-297">Bu nedenle, öncelikle bildirin `Match` türü.</span><span class="sxs-lookup"><span data-stu-id="2a023-297">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="2a023-298">Bu tür bir statik bağımsız değişken olarak sağlanan deseni bağlı olduğundan bu tür parametreli tür tanımı içinde iç içe olmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="2a023-298">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="2a023-299">Her grup için eşleşme türü için bir özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2a023-299">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="2a023-300">Çalışma zamanında bir eşleşme olarak temsil edilen bir <xref:System.Text.RegularExpressions.Match> değeri özelliğini tanımlar tırnak kullanmalısınız <xref:System.Text.RegularExpressions.Match.Groups> ilgili grubun almak için özelliğin dizini.</span><span class="sxs-lookup"><span data-stu-id="2a023-300">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

```fsharp
for group in r.GetGroupNames() do
    // Ignore the group named 0, which represents all input.
    if group <> "0" then
    let prop = 
      ProvidedProperty(
        propertyName = group, 
        propertyType = typeof<Group>, 
        getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
    matchTy.AddMember prop
```

<span data-ttu-id="2a023-301">XML belgeleri için sağlanan özellik ekliyoruz yeniden unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2a023-301">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="2a023-302">Ayrıca, bir özelliği okunabilir Not bir `GetterCode` işlevi sağlanır ve özelliği, yazılabilir bir `SetterCode` işlevi sağlanır, sonuçta elde edilen özelliği salt okunur şekilde.</span><span class="sxs-lookup"><span data-stu-id="2a023-302">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="2a023-303">Bu değer döndüren bir örnek yöntemi oluşturabilirsiniz artık `Match` türü:</span><span class="sxs-lookup"><span data-stu-id="2a023-303">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod = 
    ProvidedMethod(
        methodName = "Match", 
        parameters = [ProvidedParameter("input", typeof<string>)], 
        returnType = matchTy, 
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

<span data-ttu-id="2a023-304">Bir örnek yöntemi oluşturduğunuzdan `args.[0]` temsil `RegexTyped` üzerinde yöntemi çağrılmakta olan, örnek ve `args.[1]` giriş bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="2a023-304">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="2a023-305">Son olarak, belirtilen türdeki örneklerin oluşturulan bir oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2a023-305">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="2a023-306">Oluşturucu yalnızca bir nesneye olduğundan yeniden paketlenmiş bir standart .NET normal ifade örneği oluşturulmasını siler `obj` sağlanan türü silinmesini olduğu.</span><span class="sxs-lookup"><span data-stu-id="2a023-306">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="2a023-307">Bu değişiklik, bu konuda daha önce belirtilen örnek API kullanımı beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="2a023-307">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="2a023-308">Aşağıdaki kod, tam ve son:</span><span class="sxs-lookup"><span data-stu-id="2a023-308">The following code is complete and final:</span></span>

```fsharp
namespace Samples.FSharp.RegexTypeProvider

open System.Reflection
open Microsoft.FSharp.Core.CompilerServices
open Samples.FSharp.ProvidedTypes
open System.Text.RegularExpressions

[<TypeProvider>]
type public CheckedRegexProvider() as this =
    inherit TypeProviderForNamespaces()

    // Get the assembly and namespace used to house the provided types.
    let thisAssembly = Assembly.GetExecutingAssembly()
    let rootNamespace = "Samples.FSharp.RegexTypeProvider"
    let baseTy = typeof<obj>
    let staticParams = [ProvidedStaticParameter("pattern", typeof<string>)]

    let regexTy = ProvidedTypeDefinition(thisAssembly, rootNamespace, "RegexTyped", Some baseTy)

    do regexTy.DefineStaticParameters(
        parameters=staticParams, 
        instantiationFunction=(fun typeName parameterValues ->

            match parameterValues with 
            | [| :? string as pattern|] -> 

                // Create an instance of the regular expression. 

                let r = System.Text.RegularExpressions.Regex(pattern)            

                // Declare the typed regex provided type.

                let ty = 
                    ProvidedTypeDefinition(
                        thisAssembly, 
                        rootNamespace, 
                        typeName, 
                        baseType = Some baseTy)

                ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

                // Provide strongly typed version of Regex.IsMatch static method.
                let isMatch = 
                    ProvidedMethod(
                        methodName = "IsMatch", 
                        parameters = [ProvidedParameter("input", typeof<string>)], 
                        returnType = typeof<bool>, 
                        isStatic = true,
                        invokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

                isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

                ty.AddMember isMatch

                // Provided type for matches
                // Again, erase to obj even though the representation will always be a Match
                let matchTy = 
                    ProvidedTypeDefinition(
                        "MatchType", 
                        baseType = Some baseTy, 
                        hideObjectMethods = true)

                // Nest the match type within parameterized Regex type.
                ty.AddMember matchTy

                // Add group properties to match type
                for group in r.GetGroupNames() do
                    // Ignore the group named 0, which represents all input.
                    if group <> "0" then
                        let prop = 
                          ProvidedProperty(
                            propertyName = group, 
                            propertyType = typeof<Group>, 
                            getterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
                        prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
                        matchTy.AddMember(prop)

                // Provide strongly typed version of Regex.Match instance method.
                let matchMeth = 
                  ProvidedMethod(
                    methodName = "Match", 
                    parameters = [ProvidedParameter("input", typeof<string>)], 
                    returnType = matchTy, 
                    invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

                ty.AddMember matchMeth

                // Declare a constructor.
                let ctor = 
                  ProvidedConstructor(
                    parameters = [], 
                    invokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

                // Add documentation to the constructor.
                ctor.AddXmlDoc "Initializes a regular expression instance"

                ty.AddMember ctor

                ty
            | _ -> failwith "unexpected parameter values")) 

    do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

### <a name="key-lessons"></a><span data-ttu-id="2a023-309">Önemli dersler</span><span class="sxs-lookup"><span data-stu-id="2a023-309">Key Lessons</span></span>

<span data-ttu-id="2a023-310">Bu bölümde, kendi statik parametrelerine göre işleyen bir tür sağlayıcısı oluşturma açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2a023-310">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="2a023-311">Sağlayıcı statik parametresinin denetler ve, değerini temel alarak işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-311">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="2a023-312">Yerel veri tarafından desteklenen bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2a023-312">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="2a023-313">Genellikle, yalnızca statik parametreler aynı zamanda bilgi yerel veya uzak sistemlerden dayalı API'leri sunmak için tür sağlayıcıları isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-313">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="2a023-314">Bu bölümde, yerel veri dosyaları gibi yerel verileri temel alan bir tür sağlayıcıları ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a023-314">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="2a023-315">Basit bir CSV dosya sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2a023-315">Simple CSV File Provider</span></span>

<span data-ttu-id="2a023-316">Basit bir örnek olarak, bir tür sağlayıcısı virgülle ayrılmış değer (CSV) biçimini bilimsel veri erişimi için göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2a023-316">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="2a023-317">Bu bölümde aşağıdaki tabloda gösterildiği gibi kayan nokta verisi tarafından izlenen bir üst bilgi satırı CSV dosyaları içerdiğini varsayar:</span><span class="sxs-lookup"><span data-stu-id="2a023-317">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="2a023-318">Uzaklık (ölçer)</span><span class="sxs-lookup"><span data-stu-id="2a023-318">Distance (meter)</span></span>|<span data-ttu-id="2a023-319">Süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="2a023-319">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="2a023-320">50.0</span><span class="sxs-lookup"><span data-stu-id="2a023-320">50.0</span></span>|<span data-ttu-id="2a023-321">3.7</span><span class="sxs-lookup"><span data-stu-id="2a023-321">3.7</span></span>|
|<span data-ttu-id="2a023-322">100.0</span><span class="sxs-lookup"><span data-stu-id="2a023-322">100.0</span></span>|<span data-ttu-id="2a023-323">5.2</span><span class="sxs-lookup"><span data-stu-id="2a023-323">5.2</span></span>|
|<span data-ttu-id="2a023-324">150.0</span><span class="sxs-lookup"><span data-stu-id="2a023-324">150.0</span></span>|<span data-ttu-id="2a023-325">6.4</span><span class="sxs-lookup"><span data-stu-id="2a023-325">6.4</span></span>|

<span data-ttu-id="2a023-326">Bu bölüm nasıl satırlarla almak için kullanabileceğiniz bir türü gösterir bir `Distance` türünün özelliği `float<meter>` ve `Time` türünün özelliği `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="2a023-326">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="2a023-327">Kolaylık olması için aşağıdaki varsayımların oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="2a023-327">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="2a023-328">Üst bilgi adları olan ya da birimi daha az veya "(birim) adı" sahiptir ve virgül içermeyen.</span><span class="sxs-lookup"><span data-stu-id="2a023-328">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="2a023-329">Birimlerin tüm Systeme uluslararası (sı) birimi olarak [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Modülü (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modülü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-329">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="2a023-330">Birimlerin tüm basit (örneğin, ölçüm) bileşik (örneğin, ölçüm/saniye) yerine.</span><span class="sxs-lookup"><span data-stu-id="2a023-330">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="2a023-331">Tüm sütunlar kayan nokta verisi içerir.</span><span class="sxs-lookup"><span data-stu-id="2a023-331">All columns contain floating point data.</span></span>

<span data-ttu-id="2a023-332">Daha eksiksiz bir sağlayıcı, bu kısıtlamalar çözmek.</span><span class="sxs-lookup"><span data-stu-id="2a023-332">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="2a023-333">Yeniden API'yi nasıl görünmelidir dikkate alınması gereken ilk adım olan.</span><span class="sxs-lookup"><span data-stu-id="2a023-333">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="2a023-334">Verilen bir `info.csv` dosyası (biçiminde virgülle ayrılmış) önceki tablosundan içeriğiyle sağlayıcısının kullanıcılar aşağıdaki örneğe benzeyen kod yazabiliyor olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="2a023-334">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="2a023-335">Bu durumda, derleyici aşağıdaki örnekte olduğu gibi bir şeyi bu çağrılar dönüştürmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="2a023-335">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="2a023-336">En uygun çeviri gerçek tanımlamak tür sağlayıcısını gerektirecek `CsvFile` derlemesindeki tür sağlayıcısının türü.</span><span class="sxs-lookup"><span data-stu-id="2a023-336">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="2a023-337">Tür sağlayıcıları, genellikle birkaç Yardımcısı türleri ve yöntemleri üzerinde önemli mantık sarmalamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-337">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="2a023-338">Çalışma zamanında ölçümleri silinmeden için kullanabileceğiniz bir `float[]` bir satır için silinen türü.</span><span class="sxs-lookup"><span data-stu-id="2a023-338">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="2a023-339">Derleyicinin farklı sütundan farklı ölçü türlerine sahip olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a023-339">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="2a023-340">Örneğin, Örneğimizdeki ilk sütunda türünde `float<meter>`, ve ikinci `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="2a023-340">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="2a023-341">Ancak, silinen gösterimi oldukça basit kalabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-341">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="2a023-342">Aşağıdaki kod, çekirdek uygulamasının gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a023-342">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data = 
        seq { for line in File.ReadAllLines(filename) |> Seq.skip 1 do
                 yield line.Split(',') |> Array.map float }
        |> Seq.cache
    member __.Data = data

[<TypeProvider>]
type public MiniCsvProvider(cfg:TypeProviderConfig) as this =
    inherit TypeProviderForNamespaces(cfg)

    // Get the assembly and namespace used to house the provided types.
    let asm = System.Reflection.Assembly.GetExecutingAssembly()
    let ns = "Samples.FSharp.MiniCsvProvider"

    // Create the main provided type.
    let csvTy = ProvidedTypeDefinition(asm, ns, "MiniCsv", Some(typeof<obj>))

    // Parameterize the type by the file to use as a template.
    let filename = ProvidedStaticParameter("filename", typeof<string>)
    do csvTy.DefineStaticParameters([filename], fun tyName [| :? string as filename |] ->
    
        // Resolve the filename relative to the resolution folder.
        let resolvedFilename = Path.Combine(cfg.ResolutionFolder, filename)

        // Get the first line from the file.
        let headerLine = File.ReadLines(resolvedFilename) |> Seq.head

        // Define a provided type for each row, erasing to a float[].
        let rowTy = ProvidedTypeDefinition("Row", Some(typeof<float[]>))

        // Extract header names from the file, splitting on commas.
        // use Regex matching to get the position in the row at which the field occurs
        let headers = Regex.Matches(headerLine, "[^,]+")

        // Add one property per CSV field.
        for i in 0 .. headers.Count - 1 do
            let headerText = headers.[i].Value

            // Try to decompose this header into a name and unit.
            let fieldName, fieldTy =
                let m = Regex.Match(headerText, @"(?<field>.+) \((?<unit>.+)\)")
                if m.Success then

                    let unitName = m.Groups.["unit"].Value
                    let units = ProvidedMeasureBuilder.Default.SI unitName
                    m.Groups.["field"].Value, ProvidedMeasureBuilder.Default.AnnotateType(typeof<float>,[units])

                else
                    // no units, just treat it as a normal float
                    headerText, typeof<float>

            let prop = 
                ProvidedProperty(fieldName, fieldTy, 
                    getterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

            // Add metadata that defines the property's location in the referenced file.
            prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
            rowTy.AddMember(prop) 

        // Define the provided type, erasing to CsvFile.
        let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

        // Add a parameterless constructor that loads the file that was used to define the schema.
        let ctor0 = 
            ProvidedConstructor([], 
                invokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
        ty.AddMember ctor0

        // Add a constructor that takes the file name to load.
        let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
            invokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
        ty.AddMember ctor1

        // Add a more strongly typed Data property, which uses the existing property at runtime.
        let prop = 
            ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
                getterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
        ty.AddMember prop

        // Add the row type as a nested type.
        ty.AddMember rowTy
        ty)

    // Add the type to the namespace.
    do this.AddNamespace(ns, [csvTy])
```

<span data-ttu-id="2a023-343">Uygulama hakkında aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="2a023-343">Note the following points about the implementation:</span></span>

- <span data-ttu-id="2a023-344">Özgün dosya veya okumak için bir aynı şemaya sahip bir aşırı yüklü oluşturucular sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-344">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="2a023-345">Bu düzen, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazma ve uzak veri için şablon olarak kullanılacak bir yerel dosya bu deseni tanır yaygındır.</span><span class="sxs-lookup"><span data-stu-id="2a023-345">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="2a023-346">Kullanabileceğiniz [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) göreli dosya adlarını çözümlemek için tür sağlayıcı oluşturucuya geçirilen değer.</span><span class="sxs-lookup"><span data-stu-id="2a023-346">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="2a023-347">Kullanabileceğiniz `AddDefinitionLocation` sağlanan özellikler konumunu tanımlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2a023-347">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="2a023-348">Bu nedenle, kullanırsanız `Go To Definition` sağlanan bir özellik, CSV dosyasını Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="2a023-348">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="2a023-349">Kullanabileceğiniz `ProvidedMeasureBuilder` türü sı birimler arayın ve ilgili oluşturmak üzere `float<_>` türleri.</span><span class="sxs-lookup"><span data-stu-id="2a023-349">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="2a023-350">Önemli dersler</span><span class="sxs-lookup"><span data-stu-id="2a023-350">Key Lessons</span></span>

<span data-ttu-id="2a023-351">Bu bölümde, veri kaynağında kendisini içeren basit bir şemaya sahip bir yerel veri kaynağı için bir tür sağlayıcısı oluşturma açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2a023-351">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="2a023-352">Daha fazla devam</span><span class="sxs-lookup"><span data-stu-id="2a023-352">Going Further</span></span>

<span data-ttu-id="2a023-353">Aşağıdaki bölümlerde daha fazla araştırma için öneriler içerir.</span><span class="sxs-lookup"><span data-stu-id="2a023-353">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="2a023-354">Silinen türleri için derlenmiş kod bakma</span><span class="sxs-lookup"><span data-stu-id="2a023-354">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="2a023-355">Ne tür sağlayıcısını kullanımını yayılan koduna karşılık gelen hakkında biraz fikir vermek için aşağıdaki işlevi kullanarak araması `HelloWorldTypeProvider` bu konunun önceki bölümlerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a023-355">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="2a023-356">Sonuç kodunu ildasm.exe kullanarak decompiled görüntüsü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2a023-356">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```
.class public abstract auto ansi sealed Module1
extends [mscorlib]System.Object
{
.custom instance void [FSharp.Core]Microsoft.FSharp.Core.CompilationMappingAtt
ribute::.ctor(valuetype [FSharp.Core]Microsoft.FSharp.Core.SourceConstructFlags)
= ( 01 00 07 00 00 00 00 00 )
.method public static int32  function1() cil managed
{
// Code size       24 (0x18)
.maxstack  3
.locals init ([0] object obj1)
IL_0000:  nop
IL_0001:  ldstr      "some data"
IL_0006:  unbox.any  [mscorlib]System.Object
IL_000b:  stloc.0
IL_000c:  ldloc.0
IL_000d:  call       !!0 [FSharp.Core_2]Microsoft.FSharp.Core.LanguagePrimit
ives/IntrinsicFunctions::UnboxGeneric<string>(object)
IL_0012:  callvirt   instance int32 [mscorlib_3]System.String::get_Length()
IL_0017:  ret
} // end of method Module1::function1

} // end of class Module1
```

<span data-ttu-id="2a023-357">Tüm bahsetmeleri türü örnekte gösterildiği gibi `Type1` ve `InstanceProperty` özelliği silinmesi, yalnızca çalışma zamanı türleri üzerinde işlemler dahil çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="2a023-357">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="2a023-358">Tasarım ve adlandırma kuralları için tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="2a023-358">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="2a023-359">Tür sağlayıcıları yazarken aşağıdaki kurallar gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="2a023-359">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="2a023-360">**Bağlantı protokoller için sağlayıcıları** genel olarak, veri ve hizmet bağlantısı gibi protokolleri OData veya SQL bağlantıları için çoğu sağlayıcısı DLL'leri adlarını bitmelidir `TypeProvider` veya `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="2a023-360">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="2a023-361">Örneğin, aşağıdaki dize şuna benzer bir DLL adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="2a023-361">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="2a023-362">Sağlanan türlerinizi karşılık gelen ad alanının üyeleri ve uygulanan bağlantı protokolü belirtmek emin olun:</span><span class="sxs-lookup"><span data-stu-id="2a023-362">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="2a023-363">**Genel olarak kodlamak için yardımcı program sağlayıcıları**.</span><span class="sxs-lookup"><span data-stu-id="2a023-363">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="2a023-364">Yardımcı programı için bir tür sağlayıcısı gibi normal ifadeler için tür sağlayıcısı aşağıdaki örnekte gösterildiği gibi bir temel kitaplığının bir parçası olabilir:</span><span class="sxs-lookup"><span data-stu-id="2a023-364">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="2a023-365">Bu durumda, sağlanan türü normal .NET Tasarım Kuralları göre uygun bir noktada görünür:</span><span class="sxs-lookup"><span data-stu-id="2a023-365">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="2a023-366">**Tekli veri kaynakları**.</span><span class="sxs-lookup"><span data-stu-id="2a023-366">**Singleton Data Sources**.</span></span> <span data-ttu-id="2a023-367">Bazı tür sağlayıcılarını tek bir adanmış veri kaynağına bağlanmak ve yalnızca veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-367">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="2a023-368">Bu durumda, düşmelidir `TypeProvider` sonek ve .NET normal kuralları kullanın:</span><span class="sxs-lookup"><span data-stu-id="2a023-368">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="2a023-369">Daha fazla bilgi için `GetConnection` tasarım bu konunun ilerleyen bölümlerinde açıklanan kuralı.</span><span class="sxs-lookup"><span data-stu-id="2a023-369">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="2a023-370">Tür sağlayıcıları için Tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="2a023-370">Design Patterns for Type Providers</span></span>

<span data-ttu-id="2a023-371">Aşağıdaki bölümlerde tasarım desenleri tür sağlayıcıları yazarken kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a023-371">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="2a023-372">GetConnection tasarım deseni</span><span class="sxs-lookup"><span data-stu-id="2a023-372">The GetConnection Design Pattern</span></span>

<span data-ttu-id="2a023-373">Çoğu tür sağlayıcıları kullanan yazılması gerektiğini `GetConnection` aşağıdaki örnekte gösterildiği gibi FSharp.Data.typeproviders.dll tür sağlayıcıları tarafından kullanılan Desen:</span><span class="sxs-lookup"><span data-stu-id="2a023-373">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="2a023-374">Uzak Veri ve hizmetler tarafından desteklenen tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="2a023-374">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="2a023-375">Uzak Veri ve hizmetler tarafından desteklenen bir tür sağlayıcısı oluşturmadan önce bir dizi bağlı programlamada belirlidir sorunları dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-375">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="2a023-376">Bu sorunları aşağıdaki önemli noktalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2a023-376">These issues include the following considerations:</span></span>

- <span data-ttu-id="2a023-377">Şema eşleme</span><span class="sxs-lookup"><span data-stu-id="2a023-377">schema mapping</span></span>

- <span data-ttu-id="2a023-378">canlılık ve şema değişikliği varlığında geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="2a023-378">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="2a023-379">Şema önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="2a023-379">schema caching</span></span>

- <span data-ttu-id="2a023-380">Veri erişim işlemleri zaman uyumsuz uygulamaları</span><span class="sxs-lookup"><span data-stu-id="2a023-380">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="2a023-381">LINQ sorguları da dahil olmak üzere, destekleyici sorguları</span><span class="sxs-lookup"><span data-stu-id="2a023-381">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="2a023-382">kimlik bilgileri ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2a023-382">credentials and authentication</span></span>

<span data-ttu-id="2a023-383">Bu konu bu sorunların daha fazla keşfedin değil.</span><span class="sxs-lookup"><span data-stu-id="2a023-383">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="2a023-384">Ek geliştirme teknikleri</span><span class="sxs-lookup"><span data-stu-id="2a023-384">Additional Authoring Techniques</span></span>

<span data-ttu-id="2a023-385">Kendi tür sağlayıcıları yazdığınızda, aşağıdaki ek teknikler kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-385">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="2a023-386">Türler ve üyeler üzerine oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a023-386">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="2a023-387">ProvidedType API sürümlerini AddMember Gecikmeli.</span><span class="sxs-lookup"><span data-stu-id="2a023-387">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="2a023-388">Bu sürümler, isteğe bağlı alanları türleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a023-388">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="2a023-389">Dizi türleri ve genel tür Örneklemeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="2a023-389">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="2a023-390">Belirtilen üye (dizi türleri ve byref türleriyle genel türlerin örneklemeleri dahil olan imzaları) normal kullanarak yaptığınız `MakeArrayType`, `MakePointerType`, ve `MakeGenericType` herhangi bir örneği üzerinde <xref:System.Type>de dahil olmak üzere `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="2a023-390">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="2a023-391">Bazı durumlarda yardımcı kullanmak zorunda kalabilirsiniz `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="2a023-391">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="2a023-392">Bkz: [tür sağlayıcısı SDK Belgeleri](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="2a023-392">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="2a023-393">Birim ölçü ek açıklamaları sağlama</span><span class="sxs-lookup"><span data-stu-id="2a023-393">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="2a023-394">ProvidedTypes API ölçü ek açıklamalar sağlayan Yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-394">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="2a023-395">Örneğin, türü sağlamak için `float<kg>`, aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2a023-395">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="2a023-396">Türü sağlamak `Nullable<decimal<kg/m^2>>`, aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2a023-396">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="2a023-397">Proje yerel veya komut dosyası yerel kaynaklara erişme</span><span class="sxs-lookup"><span data-stu-id="2a023-397">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="2a023-398">Her bir tür sağlayıcısı örneğini verilen bir `TypeProviderConfig` oluşturma sırasında değeri.</span><span class="sxs-lookup"><span data-stu-id="2a023-398">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="2a023-399">Bu değer, "Çözüm klasörü" sağlayıcısı (diğer bir deyişle, proje klasörü derleme veya bir komut dosyasını içeren dizin), başvurulan derlemelerin listesini ve diğer bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2a023-399">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="2a023-400">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="2a023-400">Invalidation</span></span>

<span data-ttu-id="2a023-401">Sağlayıcıları şema varsayımların değişmiş olan F # dil hizmeti bildirmek için geçersiz kılma sinyalleri yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-401">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="2a023-402">Geçersiz kılma meydana geldiğinde, sağlayıcı Visual Studio'da barındırılıyorsa bir typecheck alınabilir.</span><span class="sxs-lookup"><span data-stu-id="2a023-402">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="2a023-403">Bu sinyal sağlayıcısı F # Etkileşimli veya F # derleyici (fsc.exe) tarafından barındırıldığında yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="2a023-403">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="2a023-404">Şema bilgileri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="2a023-404">Caching Schema Information</span></span>

<span data-ttu-id="2a023-405">Sağlayıcıları, genellikle erişim için şema bilgileri önbelleğe gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-405">Providers must often cache access to schema information.</span></span> <span data-ttu-id="2a023-406">Kullanıcı verileri veya statik bir parametre olarak verilen dosya adı kullanarak önbelleğe alınmış verilerin depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-406">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="2a023-407">Şema önbelleğe alma, bir örnek verilmiştir `LocalSchemaFile` tür sağlayıcıları parametresinde `FSharp.Data.TypeProviders` derleme.</span><span class="sxs-lookup"><span data-stu-id="2a023-407">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="2a023-408">Uygulama bu sağlayıcıları, ağ üzerinden veri kaynağına erişim yerine yerel belirtilen dosyada şema bilgileri kullanmak için tür sağlayıcısını statik Bu parametre yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a023-408">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="2a023-409">Önbelleğe alınan şema bilgileri kullanmak için de statik parametresinin ayarlamalısınız `ForceUpdate` için `false`.</span><span class="sxs-lookup"><span data-stu-id="2a023-409">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="2a023-410">Benzer bir teknik, çevrimiçi ve çevrimdışı veri erişimi etkinleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-410">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="2a023-411">Derleme yedekleme</span><span class="sxs-lookup"><span data-stu-id="2a023-411">Backing Assembly</span></span>

<span data-ttu-id="2a023-412">Derleme yaparken bir `.dll` veya `.exe` dosyası, yedekleme .dll dosyası oluşturulan türleri statik olarak bağlanan elde edilen bütünleştirilmiş kod içine.</span><span class="sxs-lookup"><span data-stu-id="2a023-412">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="2a023-413">Bu bağlantı, son derlemeye yedekleme derlemeye Ara dil (IL) tür tanımları ve yönetilen kaynaklar kopyalayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a023-413">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="2a023-414">F # Etkileşimli kullandığınızda, yedekleme .dll dosyası kopyalanmıyor ve bunun yerine doğrudan F # Etkileşimli işlem yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2a023-414">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="2a023-415">Özel durumlar ve tür sağlayıcıları'ndan tanılama</span><span class="sxs-lookup"><span data-stu-id="2a023-415">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="2a023-416">Sağlanan türlerinden tüm üyeleri tüm kullanımları, özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="2a023-416">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="2a023-417">Bir tür sağlayıcısı bir özel durum oluşturursa tüm durumlarda, belirli bir tür sağlayıcısı için konak derleyici hata öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="2a023-417">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="2a023-418">Tür sağlayıcısı özel durumlar, hiçbir zaman içinde iç derleyici hatalarının neden olur.</span><span class="sxs-lookup"><span data-stu-id="2a023-418">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="2a023-419">Tür sağlayıcıları uyarıları bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-419">Type providers can't report warnings.</span></span>

- <span data-ttu-id="2a023-420">Bir tür Sağlayıcı F # derleyicisi, bir F # geliştirme ortamı veya F # Etkileşimli içinde barındırıldığında, tüm özel durumlar söz konusu sağlayıcısından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-420">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="2a023-421">İleti özelliği her zaman hata metnini ve yığın izlemesi yok görünür.</span><span class="sxs-lookup"><span data-stu-id="2a023-421">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="2a023-422">Bir özel durum oluşturmak için kullanacaksanız, aşağıdaki örneklerde oluşturabilecek: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="2a023-422">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="2a023-423">Oluşturulan türleri sağlama</span><span class="sxs-lookup"><span data-stu-id="2a023-423">Providing Generated Types</span></span>

<span data-ttu-id="2a023-424">Şu ana kadar bu belgede silinen türler sağlamak üzere nasıl açıklandığı.</span><span class="sxs-lookup"><span data-stu-id="2a023-424">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="2a023-425">Tür sağlayıcısı mekanizması F # gerçek .NET türü tanımları kullanıcıların programı olarak eklenen oluşturulan türler sağlamak üzere kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-425">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="2a023-426">Oluşturulan türleri bir tür tanımı kullanarak sağlanan başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-426">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="2a023-427">F # 3.0 yayının parçası ProvidedTypes 0.2 yardımcı kod, yalnızca oluşturulan türleri sağlamak için destek sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a023-427">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="2a023-428">Aşağıdaki deyimleri için oluşturulan tür tanımı true olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="2a023-428">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="2a023-429">`isErased` ayarlanmalıdır `false`.</span><span class="sxs-lookup"><span data-stu-id="2a023-429">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="2a023-430">Oluşturulan tür eklenmelidir için yeni oluşturulan `ProvidedAssembly()`, oluşturulan kod parçaları için bir kapsayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a023-430">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="2a023-431">Sağlayıcının bir gerçek destekleyen .NET .dll dosyası ile eşleşen bir .dll dosyası diskte sahip derlemeye olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a023-431">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="2a023-432">Kurallar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="2a023-432">Rules and Limitations</span></span>

<span data-ttu-id="2a023-433">Tür sağlayıcıları yazdığınızda, aşağıdaki kurallar ve sınırlamalar göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2a023-433">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="2a023-434">Sağlanan türler erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a023-434">Provided types must be reachable</span></span>

<span data-ttu-id="2a023-435">Tüm türler iç içe olmayan türlerinden erişilebilmeli sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2a023-435">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="2a023-436">İç içe türleri çağrısında verilen `TypeProviderForNamespaces` oluşturucu veya çağrı `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="2a023-436">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="2a023-437">Örneğin, bir tür sağlayıcısı sağlıyorsa `StaticClass.P : T`, T iç içe türü veya altında iç içe geçmiş bir tane olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2a023-437">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="2a023-438">Örneğin, bazı sağlayıcılar gibi statik bir sınıf sahip `DataTypes` bunlar içeren `T1, T2, T3, ...` türleri.</span><span class="sxs-lookup"><span data-stu-id="2a023-438">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="2a023-439">Aksi takdirde, derlemesi T türünde bir başvuru bulundu, ancak türü bu derlemede bulunamadı hatası diyor.</span><span class="sxs-lookup"><span data-stu-id="2a023-439">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="2a023-440">Bu hata yeniden görüntülenirse, tüm alt türleri sağlayıcı türlerinden erişilebildiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2a023-440">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="2a023-441">Not: Bu `T1, T2, T3...` türleri denir *üzerinde halindeyken* türleri.</span><span class="sxs-lookup"><span data-stu-id="2a023-441">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="2a023-442">Erişilebilir bir ad alanı veya üst türü koymayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2a023-442">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="2a023-443">Tür sağlayıcısı mekanizması sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="2a023-443">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="2a023-444">F # tür sağlayıcısı mekanizması aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2a023-444">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="2a023-445">Altyapının F # tür sağlayıcıları için genel türleri veya genel yöntemler sağlanan sağlanan desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="2a023-445">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="2a023-446">Mekanizması statik parametreler ile iç içe geçmiş türlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2a023-446">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="2a023-447">Geliştirme İpuçları</span><span class="sxs-lookup"><span data-stu-id="2a023-447">Development Tips</span></span>

<span data-ttu-id="2a023-448">Aşağıdaki ipuçları geliştirme sürecinde yararlı.</span><span class="sxs-lookup"><span data-stu-id="2a023-448">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="2a023-449">Visual Studio iki örneğini çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2a023-449">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="2a023-450">Tür sağlayıcısını bir örneğinde geliştirip test IDE yeniden oluşturulan tür sağlayıcısını engelleyen bir .dll dosyası üzerinde bir kilit etkinleştirilir çünkü sağlayıcı diğer test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-450">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="2a023-451">Bu nedenle, Visual Studio'nun ikinci örneğini ağdaki ilk örnek sağlayıcısı oluşturulur ve ardından sağlayıcısı oluşturulduktan sonra ikinci örneğini yeniden açmanız gerekir kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a023-451">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="2a023-452">Tür sağlayıcıları fsc.exe çağrıları kullanarak hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2a023-452">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="2a023-453">Tür sağlayıcıları aşağıdaki araçları kullanarak çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a023-453">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="2a023-454">fsc.exe (F # komut satırı derleyicisi)</span><span class="sxs-lookup"><span data-stu-id="2a023-454">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="2a023-455">fsi.exe (F # Etkileşimli derleyici)</span><span class="sxs-lookup"><span data-stu-id="2a023-455">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="2a023-456">Devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2a023-456">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="2a023-457">Tür sağlayıcıları test betiği (örneğin, script.fsx) üzerinde fsc.exe kullanarak, en kolay genellikle ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-457">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="2a023-458">Bir hata ayıklayıcı bir komut isteminden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-458">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="2a023-459">Yazdırma için stdout'u günlüğe kaydetme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a023-459">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a023-460">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a023-460">See also</span></span>

- [<span data-ttu-id="2a023-461">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="2a023-461">Type Providers</span></span>](index.md)
- [<span data-ttu-id="2a023-462">Tür sağlayıcısını SDK'sı</span><span class="sxs-lookup"><span data-stu-id="2a023-462">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
