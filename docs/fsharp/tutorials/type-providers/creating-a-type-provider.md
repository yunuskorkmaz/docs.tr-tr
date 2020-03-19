---
title: 'Öğretici: Tür Sağlayıcısı Oluşturma'
description: Temel kavramları göstermek için birkaç basit tür sağlayıcısını inceleyerek F# 3.0'da kendi F# türü sağlayıcılarınızı nasıl oluştururuz öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 3b8145d4c2d8bf96b6dcf66de02e9f2d83927d74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186120"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="8b661-103">Öğretici: Tür Sağlayıcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b661-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="8b661-104">F#'daki tür sağlayıcı mekanizması, bilgi açısından zengin programlama ya da destek desteğinin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="8b661-105">Bu öğretici, temel kavramları göstermek için birkaç basit tür sağlayıcıların geliştirilmesi ile size yol göstererek kendi türü sağlayıcıları oluşturmak için nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b661-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="8b661-106">F#'daki tür sağlayıcı mekanizması hakkında daha fazla bilgi için [Bkz.](index.md)</span><span class="sxs-lookup"><span data-stu-id="8b661-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="8b661-107">F# ekosistemi, yaygın olarak kullanılan Internet ve kurumsal veri hizmetleri için çeşitli tür sağlayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="8b661-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b661-108">For example:</span></span>

- <span data-ttu-id="8b661-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON, XML, CSV ve HTML belge biçimleri için tür sağlayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="8b661-110">[SQLProvider,](https://fsprojects.github.io/SQLProvider/) nesne eşleme ve f# LINQ sorguları aracılığıyla bu veri kaynaklarına karşı güçlü bir şekilde daktio erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="8b661-111">[FSharp.Data.SqlClient,](https://fsprojects.github.io/FSharp.Data.SqlClient/) T-SQL'in F#'da zaman kontrol edilmiş gömmesini derlemek için bir dizi tür sağlayıcısına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b661-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="8b661-112">[FSharp.Data.TypeProviders,](https://fsprojects.github.io/FSharp.Data.TypeProviders/) SQL, Entity Framework, OData ve WSDL veri hizmetlerine erişmek için yalnızca .NET Framework programlama ile kullanılmak üzere eski bir tür sağlayıcıları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="8b661-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="8b661-113">Gerektiğinde, özel tür sağlayıcıları oluşturabilir veya başkalarının oluşturduğu tür sağlayıcılarına başvuruda bulunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="8b661-114">Örneğin, kuruluşunuzun her biri kendi kararlı veri şeması olan çok sayıda adlandırılmış veri kümesi sağlayan bir veri hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="8b661-115">Şemaları okuyan ve geçerli veri kümelerini programcıya güçlü bir şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8b661-116">Başlamadan Önce</span><span class="sxs-lookup"><span data-stu-id="8b661-116">Before You Start</span></span>

<span data-ttu-id="8b661-117">Tür sağlayıcı mekanizması öncelikle F# programlama deneyimine kararlı veri ve hizmet bilgi alanları enjekte etmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="8b661-118">Bu mekanizma, program yürütme sırasında şema ları program mantığıyla ilgili şekillerde değişen bilgi alanlarını enjekte etmek için tasarlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="8b661-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="8b661-119">Ayrıca, bu etki alanı bazı geçerli kullanımlar içerse bile, mekanizma dil içi meta programlama için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="8b661-120">Bu mekanizmayı yalnızca gerektiğinde ve bir tür sağlayıcısının geliştirilmesinin çok yüksek değer elde ettiği durumlarda kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="8b661-121">Şema nın kullanılamadığı bir tür sağlayıcısı yazmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="8b661-122">Aynı şekilde, sıradan (hatta varolan) .NET kitaplığı yeterli olacağını bir tür sağlayıcı yazmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="8b661-123">Başlamadan önce aşağıdaki soruları sorabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="8b661-124">Bilgi kaynağınız için bir şema nız var mı?</span><span class="sxs-lookup"><span data-stu-id="8b661-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="8b661-125">Eğer öyleyse, F# ve .NET tip sistemine haritalama nedir?</span><span class="sxs-lookup"><span data-stu-id="8b661-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="8b661-126">Uygulamanız için başlangıç noktası olarak varolan (dinamik olarak daktive) API'yi kullanabilir misiniz?</span><span class="sxs-lookup"><span data-stu-id="8b661-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="8b661-127">Siz ve kuruluşunuz, yazıyazmaya değer kılmak için tür sağlayıcının yeterli kullanımına sahip olacak mı?</span><span class="sxs-lookup"><span data-stu-id="8b661-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="8b661-128">Normal bir .NET kitaplığı ihtiyaçlarınızı karşılar mı?</span><span class="sxs-lookup"><span data-stu-id="8b661-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="8b661-129">Şemane ne kadar değişecek?</span><span class="sxs-lookup"><span data-stu-id="8b661-129">How much will your schema change?</span></span>

- <span data-ttu-id="8b661-130">Kodlama sırasında değişecek mi?</span><span class="sxs-lookup"><span data-stu-id="8b661-130">Will it change during coding?</span></span>

- <span data-ttu-id="8b661-131">Kodlama oturumları arasında değişecek mi?</span><span class="sxs-lookup"><span data-stu-id="8b661-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="8b661-132">Program yürütme sırasında değişecek mi?</span><span class="sxs-lookup"><span data-stu-id="8b661-132">Will it change during program execution?</span></span>

<span data-ttu-id="8b661-133">Tür sağlayıcıları, şemanın çalışma zamanında ve derlenmiş kodun ömrü boyunca kararlı olduğu durumlar için en uygun olandır.</span><span class="sxs-lookup"><span data-stu-id="8b661-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="8b661-134">Basit Bir Tür Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="8b661-134">A Simple Type Provider</span></span>

<span data-ttu-id="8b661-135">Bu örnek Samples.HelloWorldTypeProvider, `examples` [F# Türü Sağlayıcı SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)dizini örneklerine benzer.</span><span class="sxs-lookup"><span data-stu-id="8b661-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="8b661-136">Sağlayıcı, f# imza sözdizimini kullanarak ve hariç tüm ayrıntıları atlayarak aşağıdaki kodun gösterdiği gibi, 100 `Type1`silinmiş türü içeren bir "tür alanı" sunar.</span><span class="sxs-lookup"><span data-stu-id="8b661-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="8b661-137">Silinen türler hakkında daha fazla bilgi için, bu konunun ilerleyen saatlerinde [Silinen Sağlanan Türler Hakkında Ayrıntılar'a](#details-about-erased-provided-types) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="8b661-138">Sağlanan tür ve üye kümesinin statik olarak bilindiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="8b661-139">Bu örnek, sağlayıcıların şemaya bağlı türleri sağlama yeteneğinden yararlanmaz.</span><span class="sxs-lookup"><span data-stu-id="8b661-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="8b661-140">Tür sağlayıcısının uygulanması aşağıdaki kodda özetlenmiştir ve ayrıntılar bu konunun sonraki bölümlerinde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="8b661-141">Bu kod ve çevrimiçi örnekler arasında farklılıklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="8b661-142">Bu sağlayıcıyı kullanmak için Visual Studio'nun ayrı bir örneğini açın, bir F# komut dosyası oluşturun ve ardından aşağıdaki kodun gösterdiği gibi #r kullanarak komut dosyanızdan sağlayıcıya bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b661-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="8b661-143">Ardından, tür sağlayıcısının `Samples.HelloWorldTypeProvider` oluşturduğu ad alanı altındaki türleri arayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="8b661-144">Sağlayıcıyı yeniden derlemeden önce, sağlayıcı DLL'yi kullanan Visual Studio ve F# Interactive'in tüm örneklerini kapattığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8b661-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="8b661-145">Aksi takdirde, çıkış DLL kilitli olacak, çünkü bir yapı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b661-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="8b661-146">Yazdırma deyimleri kullanarak bu sağlayıcının hata sını ayıklamak için, sağlayıcıyla ilgili bir sorunu ortaya çıkaran bir komut dosyası yapın ve ardından aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b661-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="8b661-147">Visual Studio'yu kullanarak bu sağlayıcının hatasını ayıklamak için, Visual Studio için Geliştirici Komut Komut Ustem'ini yönetim kimlik bilgileriyle açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8b661-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="8b661-148">Alternatif olarak Visual Studio'yu açın, Hata `Debug/Attach to process…`Ayıklama menüsünü `devenv` açın, komut dosyanızı düzenlediğiniz başka bir işleme seçin ve diğer bir işleme takın.</span><span class="sxs-lookup"><span data-stu-id="8b661-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="8b661-149">Bu yöntemi kullanarak, ikinci örnekiçine ifadeleri etkileşimli olarak yazarak (tam IntelliSense ve diğer özelliklerle) tür sağlayıcısındaki belirli mantığı daha kolay hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="8b661-150">Oluşturulan koddaki hataları daha iyi tanımlamak için Just My Code hata ayıklamadevre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="8b661-151">Bu özelliği etkinleştirme veya devre dışı etme hakkında bilgi için [hata ayıklayıcıyla Kod da Gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="8b661-152">Ayrıca, menüyü `Debug` açıp iletişim kutusunu açmak `Exceptions` `Exceptions` için Ctrl+Alt+E tuşlarını seçerek veya seçerek ilk şans özel durum yakalamayı da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="8b661-153">Bu iletişim kutusunda, `Common Language Runtime Exceptions`altında , `Thrown` onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="8b661-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="8b661-154">Tip Sağlayıcının Uygulanması</span><span class="sxs-lookup"><span data-stu-id="8b661-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="8b661-155">Bu bölüm, tür sağlayıcı uygulamasının temel bölümleri boyunca size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b661-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="8b661-156">İlk olarak, özel tür sağlayıcısıkendisi için türü tanımlarsınız:</span><span class="sxs-lookup"><span data-stu-id="8b661-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="8b661-157">Bu tür ortak olmalıdır ve derleyici türü içeren derleme derleme başvurur tür sağlayıcısı tanıyacak şekilde [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) özniteliği ile işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="8b661-158">*Config* parametresi isteğe bağlıdır ve varsa, F# derleyicisinin oluşturduğu tür sağlayıcı örneği için bağlamsal yapılandırma bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="8b661-159">Ardından, [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) arabirimini uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="8b661-160">Bu durumda, `TypeProviderForNamespaces` `ProvidedTypes` API'deki türü temel türü olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="8b661-161">Bu yardımcı türü, her biri doğrudan sınırlı sayıda sabit, hevesle sağlanan türleri içeren hevesle sağlanan ad alanlarının sınırlı bir koleksiyon sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="8b661-162">Bu bağlamda, *sağlayıcı* gerekli olmasa veya kullanılmasa bile hevesle türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b661-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="8b661-163">Ardından, sağlanan türler için ad alanını belirten yerel özel değerleri tanımlayın ve tür sağlayıcı derlemesinin kendisini bulun.</span><span class="sxs-lookup"><span data-stu-id="8b661-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="8b661-164">Bu derleme daha sonra sağlanan silinmiş türlerin mantıksal üst türü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="8b661-165">Ardından, Type1 türlerinin her birini sağlamak için bir işlev oluşturun... Tip100.</span><span class="sxs-lookup"><span data-stu-id="8b661-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="8b661-166">Bu işlev daha sonra bu konuda daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="8b661-167">Ardından, sağlanan 100 türü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8b661-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="8b661-168">Ardından, sağlanan ad alanı olarak türleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b661-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="8b661-169">Son olarak, bir tür sağlayıcısı DLL oluşturduğunuzu gösteren bir derleme özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b661-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="8b661-170">Tek Tip Ve Üyeleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="8b661-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="8b661-171">İşlev, `makeOneProvidedType` türlerden birini sağlama nın gerçek işini yapar.</span><span class="sxs-lookup"><span data-stu-id="8b661-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="8b661-172">Bu adım, bu işlevin uygulanmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b661-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="8b661-173">İlk olarak, sağlanan türü oluşturun (örneğin, Type1, ne zaman n = 1, veya Type57, ne zaman n = 57).</span><span class="sxs-lookup"><span data-stu-id="8b661-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="8b661-174">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8b661-174">You should note the following points:</span></span>

- <span data-ttu-id="8b661-175">Bu sağlanan tür silinir.</span><span class="sxs-lookup"><span data-stu-id="8b661-175">This provided type is erased.</span></span>  <span data-ttu-id="8b661-176">Temel türünün , `obj`örneklerin derlenmiş koddaki [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) türü değerleri olarak görüneceğini belirttiğiiçin.</span><span class="sxs-lookup"><span data-stu-id="8b661-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="8b661-177">İç içe olmayan bir tür belirttiğiniz zaman, derlemeve ad alanını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="8b661-178">Silinen türler için, derleme türü sağlayıcı derlemenin kendisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="8b661-179">Ardından, türüne XML belgeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b661-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="8b661-180">Bu dokümantasyon geciktirilir, diğer bir şekilde, ana bilgisayar derleyicisinin ihtiyacı varsa isteğe bağlı olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="8b661-181">Sonra türüne sağlanan statik özellik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b661-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="8b661-182">Bu özelliği almak her zaman dize "Merhaba!" olarak değerlendirecektir.</span><span class="sxs-lookup"><span data-stu-id="8b661-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="8b661-183">`GetterCode` Özellik için, ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu temsil eden bir F# alıntısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="8b661-184">Teklifler hakkında daha fazla bilgi için [Kod Alıntıları (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="8b661-185">Tesise XML belgeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b661-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="8b661-186">Şimdi sağlanan özelliği sağlanan türe takın.</span><span class="sxs-lookup"><span data-stu-id="8b661-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="8b661-187">Sağlanan bir üyeyi bir ve yalnızca bir türe eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="8b661-188">Aksi takdirde, üyeye hiçbir zaman erişilemez.</span><span class="sxs-lookup"><span data-stu-id="8b661-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="8b661-189">Şimdi hiçbir parametre gerektiren sağlanan bir oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b661-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="8b661-190">Oluşturucu `InvokeCode` için, oluşturucu çağrıldığında ev sahibiderleyicinin oluşturduğu kodu temsil eden bir F# teklifi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b661-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="8b661-191">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="8b661-192">Sağlanan tür bir örnek altta yatan veri "nesne verileri" ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8b661-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="8b661-193">Teklif edilen kod, bu tür bu sağlanan türün silinmesi olduğundan (sağlanan türü beyan ettiğinizde belirttiğiniz gibi) [obj'ye](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) dönüştürme içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="8b661-194">Oluşturucuya XML belgeleri ekleyin ve sağlanan oluşturucuyu sağlanan türe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b661-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="8b661-195">Bir parametre alan ikinci bir sağlanan oluşturucu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8b661-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="8b661-196">Oluşturucu `InvokeCode` için yine, ana bilgisayar derleyicisinin yönteme çağrı için oluşturduğu kodu temsil eden bir F# teklifi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b661-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="8b661-197">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="8b661-198">Sağlanan tür bir örnek altta yatan veri "on" ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8b661-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="8b661-199">İşlevin `InvokeCode` bir teklif döndürür önceden fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="8b661-200">Bu işleve giriş, yapılayıcı parametresi başına bir ifade listesidir.</span><span class="sxs-lookup"><span data-stu-id="8b661-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="8b661-201">Bu durumda, tek parametre değerini temsil eden `args.[0]`bir ifade .</span><span class="sxs-lookup"><span data-stu-id="8b661-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="8b661-202">Oluşturucuya yapılan bir çağrının kodu, silinen türe `obj`iade değerini zorlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="8b661-203">İkinci sağlanan oluşturucuyu türe ekledikten sonra, sağlanan bir örnek özelliği oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="8b661-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="8b661-204">Bu özelliği almak, temsil nesnesi olan dize uzunluğunu döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="8b661-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="8b661-205">Özellik, `GetterCode` ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu belirten bir F# teklifi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b661-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="8b661-206">Gibi `InvokeCode`, `GetterCode` işlev bir teklif döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b661-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="8b661-207">Ana bilgisayar derleyicisi bu işlevi bağımsız değişkenlerin listesiyle çağırır.</span><span class="sxs-lookup"><span data-stu-id="8b661-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="8b661-208">Bu durumda, bağımsız değişkenler, gönderenin çağrıldığı örneği temsil eden ve kullanarak `args.[0]`erişebileceğiniz tek bir ifadeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="8b661-209">Daha `GetterCode` sonra silinen türde `obj`sonuç teklif içine splices uygulanması ve bir döküm nesnebir dize olduğunu türleri denetlemek için derleyici mekanizmasını karşılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="8b661-210">Bir sonraki `makeOneProvidedType` bölümü bir parametre ile bir örnek yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="8b661-211">Son olarak, 100 iç içe özellikleri içeren iç içe bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b661-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="8b661-212">Bu iç içe tür ve özellikleri, yani isteğe bağlı olarak hesaplanan, gecikti.</span><span class="sxs-lookup"><span data-stu-id="8b661-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

```fsharp
t.AddMembersDelayed(fun () ->
  let nestedType = ProvidedTypeDefinition("NestedType", Some typeof<obj>)

  nestedType.AddMembersDelayed (fun () ->
    let staticPropsInNestedType =
      [
          for i in 1 .. 100 ->
              let valueOfTheProperty = "I am string "  + string i

              let p =
                ProvidedProperty(propertyName = "StaticProperty" + string i,
                  propertyType = typeof<string>,
                  isStatic = true,
                  getterCode= (fun args -> <@@ valueOfTheProperty @@>))

              p.AddXmlDocDelayed(fun () ->
                  sprintf "This is StaticProperty%d on NestedType" i)

              p
      ]

    staticPropsInNestedType)

  [nestedType])
```

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="8b661-213">Silinen Sağlanan Türler Hakkında Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8b661-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="8b661-214">Bu bölümdeki örnek, özellikle aşağıdaki durumlarda yararlı olan yalnızca *silinmiş sağlanan türleri*sağlar:</span><span class="sxs-lookup"><span data-stu-id="8b661-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="8b661-215">Yalnızca veri ve yöntem içeren bir bilgi alanı için bir sağlayıcı yazarken.</span><span class="sxs-lookup"><span data-stu-id="8b661-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="8b661-216">Doğru çalışma zamanı türü semantik bilgi alanının pratik kullanımı için kritik olmayan bir sağlayıcı yazarken.</span><span class="sxs-lookup"><span data-stu-id="8b661-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="8b661-217">Bir bilgi alanı için bir sağlayıcı yazarken, bilgi alanı için gerçek .NET türleri oluşturmak teknik olarak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="8b661-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="8b661-218">Bu örnekte, sağlanan her tür `obj`türü türüne silinir ve türün tüm kullanımları derlenmiş kodda tür olarak `obj` görünür.</span><span class="sxs-lookup"><span data-stu-id="8b661-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="8b661-219">Aslında, bu örneklerde altta yatan nesneler dizeleri, ancak `System.Object` türü .NET derlenmiş kod olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="8b661-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="8b661-220">Türü silme tüm kullanımları olduğu gibi, silinmiş türleri yıkmak için açık kutulama, unboxing ve döküm kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="8b661-221">Bu durumda, nesne kullanıldığında geçerli olmayan bir döküm özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="8b661-222">Sağlayıcı çalışma süresi, yanlış temsillere karşı korunmaya yardımcı olmak için kendi özel gösterim türünü tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="8b661-223">F# kendinde silinmiş türleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="8b661-224">Yalnızca sağlanan türler silinebilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-224">Only provided types may be erased.</span></span> <span data-ttu-id="8b661-225">Hem pratik hem de anlamsal olarak, türü sağlayıcınız veya silinmiş türleri sağlayan bir sağlayıcı için silinmiş türleri kullanmanın sonuçlarını anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="8b661-226">Silinmiş bir türün gerçek .NET türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b661-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="8b661-227">Bu nedenle, türü üzerinde doğru yansıma yapamaz ve tam çalışma zamanı türü semantiği dayanan çalışma zamanı dökümleri ve diğer teknikleri kullanırsanız silinmiş türleri yıkmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="8b661-228">Silinen türlerin alt alt alt sürümü sık sık çalışma zamanında tür döküm özel durumları ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="8b661-229">Silinen Sağlanan Türler için Temsiller Seçme</span><span class="sxs-lookup"><span data-stu-id="8b661-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="8b661-230">Silinen sağlanan türlerin bazı kullanımları için, hiçbir gösterim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8b661-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="8b661-231">Örneğin, silinen sağlanan tür yalnızca statik özellikler ve üyeler ve hiçbir oluşturucu içerebilir ve hiçbir yöntem veya özellik türün bir örneğini döndüremez.</span><span class="sxs-lookup"><span data-stu-id="8b661-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="8b661-232">Silinmiş sağlanan tür örneklerine ulaşabiliyorsanız, aşağıdaki soruları göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8b661-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="8b661-233">**Sağlanan bir türün silinmesi nedir?**</span><span class="sxs-lookup"><span data-stu-id="8b661-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="8b661-234">Sağlanan bir türün silinmesi, derlenmiş .NET kodunda türün nasıl göründüğüdür.</span><span class="sxs-lookup"><span data-stu-id="8b661-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="8b661-235">Sağlanan silinmiş sınıf türünün silinmesi, her zaman türün kalıtım zincirindeki ilk silinmeyen taban türüdür.</span><span class="sxs-lookup"><span data-stu-id="8b661-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="8b661-236">Sağlanan silinmiş arabirim türünün silinmesi her zaman `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="8b661-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="8b661-237">**Sağlanan bir türün temsilleri nelerdir?**</span><span class="sxs-lookup"><span data-stu-id="8b661-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="8b661-238">Silinmiş sağlanan bir tür için olası nesnelerin kümesi, gösterimleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="8b661-239">Bu belgedeki örnekte, silinen tüm sağlanan türlerin `Type1..Type100` gösterimleri her zaman dize nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="8b661-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="8b661-240">Sağlanan türün tüm gösterimleri, sağlanan türün silinmesi ile uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="8b661-241">(Aksi takdirde, F# derleyicisi tür sağlayıcısının kullanımı için bir hata verir veya geçerli olmayan doğrulanamayan .NET kodu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8b661-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="8b661-242">Bir tür sağlayıcısı, geçerli olmayan bir gösterim veren kodu döndürürse geçerli değildir.)</span><span class="sxs-lookup"><span data-stu-id="8b661-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="8b661-243">Her ikisi de çok yaygın olan aşağıdaki yaklaşımlardan birini kullanarak sağlanan nesneler için bir gösterim seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="8b661-244">Yalnızca varolan bir .NET türü üzerinde güçlü bir şekilde yazılan bir sarıcı sağlıyorsanız, türünüzün bu türe silinmesi genellikle mantıklı dır, bu türdeki örnekleri temsil olarak veya her ikisi de kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b661-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="8b661-245">Bu türdeki varolan yöntemlerin çoğu güçlü bir şekilde yazılan sürümü kullanırken hala mantıklı olduğunda bu yaklaşım uygundur.</span><span class="sxs-lookup"><span data-stu-id="8b661-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="8b661-246">Varolan .NET API'den önemli ölçüde farklı bir API oluşturmak istiyorsanız, sağlanan türler için tür silme ve gösterimleri olacak çalışma zamanı türleri oluşturmak mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="8b661-247">Bu belgedeki örnek, dizeleri sağlanan nesnelerin gösterimi olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="8b661-248">Sık sık, gösterimleri için diğer nesneleri kullanmak uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="8b661-249">Örneğin, bir sözlük özelliği çantası olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="8b661-250">Alternatif olarak, tür sağlayıcınızda gösterimi oluşturmak için çalışma zamanında kullanılacak bir tür ve bir veya daha fazla çalışma zamanı işlemi tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="8b661-251">Sağlanan üyeler daha sonra bu nesne türüörnekleri oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="8b661-252">Bu durumda, (isteğe bağlı olarak) bu türü, aşağıdakileri yaparken bu `baseType` tür olarak `ProvidedTypeDefinition`belirterek tür silme olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="8b661-253">Temel Dersler</span><span class="sxs-lookup"><span data-stu-id="8b661-253">Key Lessons</span></span>

<span data-ttu-id="8b661-254">Önceki bölümde, çeşitli türler, özellikler ve yöntemler sağlayan basit bir sileme türü sağlayıcısının nasıl oluşturulacak olduğu açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="8b661-255">Bu bölümde ayrıca, bir tür sağlayıcısından silinmiş türleri sağlamanın bazı avantajları ve dezavantajları da dahil olmak üzere, tür silme kavramı açıklanmış ve silinmiş türlerin gösterimleri tartışılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="8b661-256">Statik parametreler kullanan bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8b661-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="8b661-257">Tür sağlayıcılarını statik verilerle parametreleme yeteneği, sağlayıcının herhangi bir yerel veya uzak veriye erişmesi gerekmediği durumlarda bile birçok ilginç senaryoya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="8b661-258">Bu bölümde, böyle bir sağlayıcı bir araya getirmek için bazı temel teknikler öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="8b661-259">Tip İşaretli Regex Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8b661-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="8b661-260">.NET <xref:System.Text.RegularExpressions.Regex> kitaplıklarını aşağıdaki derleme zamanı garantileri sağlayan bir arabirimde saran normal ifadeler için bir tür sağlayıcısı uygulamak istediğinizi düşünün:</span><span class="sxs-lookup"><span data-stu-id="8b661-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="8b661-261">Normal bir ifadenin geçerli olup olmadığını doğrulama.</span><span class="sxs-lookup"><span data-stu-id="8b661-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="8b661-262">Normal ifadedeki tüm grup adlarını temel alan eşleşmelerde adlandırılmış özellikler sağlama.</span><span class="sxs-lookup"><span data-stu-id="8b661-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="8b661-263">Bu bölümde, normal ifade deseni `RegexTyped` bu yararları sağlamak için parametreize bir tür oluşturmak için tür sağlayıcıları nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b661-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="8b661-264">Derleyici, sağlanan desen geçerli değilse bir hata bildirir ve tür sağlayıcısı, eşleşmeler üzerinde adlandırılmış özellikleri kullanarak bunlara erişebilmeniz için grupları desenden ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="8b661-265">Bir tür sağlayıcısı tasarlarken, açıkta kalan API'sinin son kullanıcılara nasıl görünmesi gerektiğini ve bu tasarımın .NET koduna nasıl çevrileceğini düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="8b661-266">Aşağıdaki örnek, alan kodunun bileşenlerini almak için böyle bir API'nin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="8b661-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="8b661-267">Aşağıdaki örnek, tür sağlayıcısının bu çağrıları nasıl çevirdiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8b661-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="8b661-268">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8b661-268">Note the following points:</span></span>

- <span data-ttu-id="8b661-269">Standart Regex türü parametreli `RegexTyped` türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8b661-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="8b661-270">Oluşturucu, `RegexTyped` Regex oluşturucuya çağrı yla sonuçlanır ve desen için statik tür bağımsız değişkenini geçer.</span><span class="sxs-lookup"><span data-stu-id="8b661-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="8b661-271">Yöntemin `Match` sonuçları standart <xref:System.Text.RegularExpressions.Match> türe göre temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="8b661-272">Adlandırılmış her grup, sağlanan bir özellik ile sonuçlanır ve özellik erişim, eşleşmenin `Groups` koleksiyonunda bir dizinleyici nin kullanılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="8b661-273">Aşağıdaki kod, böyle bir sağlayıcıyı uygulama mantığının özüdür ve bu örnek, tüm üyelerin sağlanan türe eklenmesini atlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="8b661-274">Eklenen her üye hakkında bilgi için, daha sonra bu konuyla ilgili ilgili bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="8b661-275">Tam kod için, örneği CodePlex web sitesindeki [F# 3.0 Örnek Paketi'nden](https://archive.codeplex.com/?p=fsharp3sample) indirin.</span><span class="sxs-lookup"><span data-stu-id="8b661-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="8b661-276">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8b661-276">Note the following points:</span></span>

- <span data-ttu-id="8b661-277">Tür sağlayıcı iki statik parametre alır: zorunlu `pattern` `options`olan , ve isteğe bağlı olan (varsayılan değer sağlandığı için).</span><span class="sxs-lookup"><span data-stu-id="8b661-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="8b661-278">Statik bağımsız değişkenler sağlandıktan sonra, normal ifadenin bir örneğini oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="8b661-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="8b661-279">Regex yanlış biçimlendirilmişse bu örnek bir özel durum oluşturur ve bu hata kullanıcılara bildirilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="8b661-280">Geri `DefineStaticParameters` arama da, bağımsız değişkenler sağlandıktan sonra döndürülecek türü tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="8b661-281">Bu `HideObjectMethods` kod, IntelliSense deneyiminin düzenli kalması için gerçeğe ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="8b661-282">Bu `Equals`öznitelik, `GetHashCode` `Finalize` `GetType` sağlanan bir nesne için IntelliSense listelerinden bastırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8b661-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="8b661-283">Yöntemin `obj` temel türü olarak kullanırsınız, ancak bir `Regex` sonraki örnekte görüldüğü gibi, bu türün çalışma zamanı gösterimi olarak bir nesne kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="8b661-284">Düzenli bir `Regex` ifade geçerli olmadığında, oluşturucuya yapılan çağrı bir <xref:System.ArgumentException> hata atar.</span><span class="sxs-lookup"><span data-stu-id="8b661-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="8b661-285">Derleyici bu özel durumu yakalar ve derleme zamanında veya Visual Studio düzenleyicisinde kullanıcıya bir hata iletisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="8b661-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="8b661-286">Bu özel durum, normal ifadelerin bir uygulama çalıştırılmadan doğrulanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="8b661-287">Anlamlı yöntemler veya özellikler içermediğinden, yukarıda tanımlanan tür henüz yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8b661-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="8b661-288">İlk olarak, `IsMatch` statik bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b661-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="8b661-289">Önceki kod, bir `IsMatch`dize girişi olarak alır ve `bool`bir . döndürür bir yöntem tanımlar</span><span class="sxs-lookup"><span data-stu-id="8b661-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="8b661-290">Tek zor kısmı `args` `InvokeCode` tanım içinde argüman kullanımıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="8b661-291">Bu örnekte, `args` bu yönteme bağımsız değişkenleri temsil eden tırnak listesi dir.</span><span class="sxs-lookup"><span data-stu-id="8b661-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="8b661-292">Yöntem bir örnek yöntemi ise, ilk `this` bağımsız değişken bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8b661-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="8b661-293">Ancak, statik bir yöntem için, bağımsız değişkenlerin tümü yönteme açık bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="8b661-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="8b661-294">Teklif edilen değerin türünün belirtilen iade türüyle eşleşmesi `bool`gerektiğini unutmayın (bu durumda).</span><span class="sxs-lookup"><span data-stu-id="8b661-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="8b661-295">Ayrıca, bu kodun, sağlanan yöntemin IntelliSense aracılığıyla sağlayabileceğiniz yararlı belgelere sahip olduğundan emin olmak için `AddXmlDoc` bu yöntemi kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="8b661-296">Ardından, örnek Eşler yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b661-296">Next, add an instance Match method.</span></span> <span data-ttu-id="8b661-297">Ancak, bu yöntem, gruplara `Match` güçlü bir şekilde yazılması için sağlanan bir tür değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b661-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="8b661-298">Böylece, ilk `Match` türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="8b661-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="8b661-299">Bu tür statik bağımsız değişken olarak sağlanan desenbağlıdır, bu tür parametreli tür tanımı içinde iç içe gerekir:</span><span class="sxs-lookup"><span data-stu-id="8b661-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="8b661-300">Daha sonra her grup için Eşler türüne bir özellik eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="8b661-301">Çalışma zamanında, bir eşleşme bir <xref:System.Text.RegularExpressions.Match> değer olarak temsil edilir, bu nedenle özelliği <xref:System.Text.RegularExpressions.Match.Groups> tanımlayan teklif ilgili grubu almak için dizine sahip özelliği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="8b661-302">Yine, sağlanan özelliğe XML belgeleri eklediğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="8b661-303">Ayrıca, bir `GetterCode` işlev sağlanmışsa bir özelliğin okunabileceğini ve `SetterCode` bir işlev sağlanırsa özelliğin yazılabilir olduğunu, böylece ortaya çıkan özelliğin yalnızca okunduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="8b661-304">Şimdi bu `Match` tür bir değer döndüren bir örnek yöntemi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

```fsharp
let matchMethod =
    ProvidedMethod(
        methodName = "Match",
        parameters = [ProvidedParameter("input", typeof<string>)],
        returnType = matchTy,
        invokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)

matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

ty.AddMember matchMeth
```

<span data-ttu-id="8b661-305">Bir örnek yöntemi `args.[0]` oluşturduğunuziçin, `RegexTyped` yöntemin çağrıldığı örneği temsil `args.[1]` eder ve giriş bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="8b661-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="8b661-306">Son olarak, sağlanan tür örnekleri oluşturulabilir, böylece bir oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="8b661-307">Oluşturucu yalnızca standart bir .NET Regex örneğinin oluşturulmasını siler, bu `obj` da sağlanan türün silinmesi olduğundan yine bir nesneye kutulanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="8b661-308">Bu değişiklikle, konunun daha önce belirtilen örnek API kullanımı beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="8b661-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="8b661-309">Aşağıdaki kod tamamlandı ve son oldu:</span><span class="sxs-lookup"><span data-stu-id="8b661-309">The following code is complete and final:</span></span>

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
                matchMeth.AddXmlDoc "Searches the specified input string for the first occurrence of this regular expression"

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

### <a name="key-lessons"></a><span data-ttu-id="8b661-310">Temel Dersler</span><span class="sxs-lookup"><span data-stu-id="8b661-310">Key Lessons</span></span>

<span data-ttu-id="8b661-311">Bu bölümde, statik parametreleri üzerinde çalışan bir tür sağlayıcısının nasıl oluşturulacak olduğu açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="8b661-312">Sağlayıcı statik parametreyi denetler ve değerine göre işlem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="8b661-313">Yerel Verilerle Desteklenen Bir Tür Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8b661-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="8b661-314">Sık sık tür sağlayıcılarının yalnızca statik parametrelere değil, yerel veya uzak sistemlerden gelen bilgilere de dayalı OLARAK API'ler sunmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="8b661-315">Bu bölümde, yerel veri dosyaları gibi yerel verileri temel alan tür sağlayıcıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="8b661-316">Basit CSV Dosya Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8b661-316">Simple CSV File Provider</span></span>

<span data-ttu-id="8b661-317">Basit bir örnek olarak, Virgülle Ayrılmış Değer (CSV) biçiminde bilimsel verilere erişmek için bir tür sağlayıcısı düşünün.</span><span class="sxs-lookup"><span data-stu-id="8b661-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="8b661-318">Bu bölümde, Aşağıdaki tabloda gösterildiği gibi, CSV dosyalarının bir üstbilgi satırı ve ardından kayan nokta verileri içerdiğini varsayar:</span><span class="sxs-lookup"><span data-stu-id="8b661-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="8b661-319">Mesafe (metre)</span><span class="sxs-lookup"><span data-stu-id="8b661-319">Distance (meter)</span></span>|<span data-ttu-id="8b661-320">Zaman (ikinci)</span><span class="sxs-lookup"><span data-stu-id="8b661-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="8b661-321">50.0</span><span class="sxs-lookup"><span data-stu-id="8b661-321">50.0</span></span>|<span data-ttu-id="8b661-322">3.7</span><span class="sxs-lookup"><span data-stu-id="8b661-322">3.7</span></span>|
|<span data-ttu-id="8b661-323">100.0</span><span class="sxs-lookup"><span data-stu-id="8b661-323">100.0</span></span>|<span data-ttu-id="8b661-324">5.2</span><span class="sxs-lookup"><span data-stu-id="8b661-324">5.2</span></span>|
|<span data-ttu-id="8b661-325">150.0</span><span class="sxs-lookup"><span data-stu-id="8b661-325">150.0</span></span>|<span data-ttu-id="8b661-326">6.4</span><span class="sxs-lookup"><span data-stu-id="8b661-326">6.4</span></span>|

<span data-ttu-id="8b661-327">Bu bölümde, tür özelliği `Distance` ve türü `float<meter>` `Time` `float<second>`özelliği olan satırları almak için kullanabileceğiniz bir tür nasıl sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b661-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="8b661-328">Basitlik için aşağıdaki varsayımlar yapılır:</span><span class="sxs-lookup"><span data-stu-id="8b661-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="8b661-329">Üstbilgi adları birimden azdır veya "Ad (birim)" formuna sahiptir ve virgül içermez.</span><span class="sxs-lookup"><span data-stu-id="8b661-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="8b661-330">Birimler, [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Modülü (F#) modülü](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) olarak tanımladığı tüm System International (SI) birimleridir.</span><span class="sxs-lookup"><span data-stu-id="8b661-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="8b661-331">Birimler bileşik yerine (örneğin, metre/saniye) basittir.</span><span class="sxs-lookup"><span data-stu-id="8b661-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="8b661-332">Tüm sütunlar kayan nokta verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-332">All columns contain floating point data.</span></span>

<span data-ttu-id="8b661-333">Daha eksiksiz bir sağlayıcı bu kısıtlamaları gevşetecektir.</span><span class="sxs-lookup"><span data-stu-id="8b661-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="8b661-334">Yine ilk adım, API'nin nasıl görünmesi gerektiğini göz önünde bulundurmaktır.</span><span class="sxs-lookup"><span data-stu-id="8b661-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="8b661-335">Önceki `info.csv` tablodaki içerikleri içeren bir dosya (virgülle ayrılmış biçimde) verildiğinde, sağlayıcının kullanıcıları aşağıdaki örneğe benzeyen kod yazabilmelidir:</span><span class="sxs-lookup"><span data-stu-id="8b661-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="8b661-336">Bu durumda, derleyici bu çağrıları aşağıdaki örnek gibi bir şeye dönüştürmelidir:</span><span class="sxs-lookup"><span data-stu-id="8b661-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="8b661-337">En uygun çeviri, tür sağlayıcısının `CsvFile` montajında gerçek bir türü tanımlamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b661-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="8b661-338">Tür sağlayıcıları genellikle önemli mantığı sarmak için birkaç yardımcı türüne ve yöntemine güvenir.</span><span class="sxs-lookup"><span data-stu-id="8b661-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="8b661-339">Ölçüler çalışma zamanında silindiği için, `float[]` bir satır için silinmiş tür olarak bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="8b661-340">Derleyici farklı sütunları farklı ölçü türlerine sahip olarak ele alacaktır.</span><span class="sxs-lookup"><span data-stu-id="8b661-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="8b661-341">Örneğin, örneğimizdeki ilk sütuntürü `float<meter>`vardır ve `float<second>`ikinci .</span><span class="sxs-lookup"><span data-stu-id="8b661-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="8b661-342">Ancak, silinen gösterim oldukça basit kalabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="8b661-343">Aşağıdaki kod, uygulamanın çekirdeğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b661-343">The following code shows the core of the implementation.</span></span>

```fsharp
// Simple type wrapping CSV data
type CsvFile(filename) =
    // Cache the sequence of all data lines (all lines but the first)
    let data =
        seq {
            for line in File.ReadAllLines(filename) |> Seq.skip 1 ->
                line.Split(',') |> Array.map float
        }
        |> Seq.cache
    member _.Data = data

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

<span data-ttu-id="8b661-344">Uygulama yla ilgili aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8b661-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="8b661-345">Aşırı yüklü oluşturucular, özgün dosyanın veya aynı şemaya sahip olanın okunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="8b661-346">Bu desen, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazdığınızda yaygındır ve bu desen, uzak veri şablonu olarak yerel bir dosyanın kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8b661-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="8b661-347">Göreli dosya adlarını çözümlemek için tür sağlayıcı oluşturucuya geçirilen [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) değerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="8b661-348">Sağlanan özelliklerin `AddDefinitionLocation` konumunu tanımlamak için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="8b661-349">Bu nedenle, `Go To Definition` sağlanan bir özellik üzerinde kullanırsanız, CSV dosyası Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="8b661-350">`ProvidedMeasureBuilder` Türü, SI birimlerini aramak ve ilgili `float<_>` türleri oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="8b661-351">Temel Dersler</span><span class="sxs-lookup"><span data-stu-id="8b661-351">Key Lessons</span></span>

<span data-ttu-id="8b661-352">Bu bölümde, veri kaynağının kendisinde bulunan basit bir şemaya sahip yerel bir veri kaynağı için bir tür sağlayıcısının nasıl oluşturulacak olduğu açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="8b661-353">Daha Ileri Gitmek</span><span class="sxs-lookup"><span data-stu-id="8b661-353">Going Further</span></span>

<span data-ttu-id="8b661-354">Aşağıdaki bölümlerde daha fazla çalışma için öneriler yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b661-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="8b661-355">Silinen Türler İçin Derlenmiş Koda Bir Bakış</span><span class="sxs-lookup"><span data-stu-id="8b661-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="8b661-356">Tür sağlayıcısının kullanımının yayılan koda nasıl karşılık geldiği hakkında size bir fikir vermek için, bu `HelloWorldTypeProvider` konuda daha önce kullanılan işlevi kullanarak aşağıdaki işleve bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="8b661-357">Burada ildasm.exe kullanılarak derlenen ortaya çıkan kodun bir görüntüsü:</span><span class="sxs-lookup"><span data-stu-id="8b661-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

```il
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

<span data-ttu-id="8b661-358">Örnekte de görüldüğü gibi, tür `Type1` ve `InstanceProperty` özellik ile ilgili tüm sözler silinmiş, yalnızca çalışma zamanı türlerinde işlemler söz konusu.</span><span class="sxs-lookup"><span data-stu-id="8b661-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="8b661-359">Tip Sağlayıcılar için Tasarım ve Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="8b661-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="8b661-360">Tür sağlayıcılar yazarken aşağıdaki kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="8b661-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="8b661-361">**Bağlantı Protokolleri Sağlayıcıları** Genel olarak, Veri ve Hizmet bağlantı protokolleri için çoğu sağlayıcı DLs adları (OData `TypeProvider` veya `TypeProviders`SQL bağlantıları gibi) veya .</span><span class="sxs-lookup"><span data-stu-id="8b661-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="8b661-362">Örneğin, aşağıdaki dize benzer bir DLL adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b661-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="8b661-363">Sağlanan türlerinizin ilgili ad alanının üyeleri olduğundan emin olun ve uyguladığınız bağlantı iletişimini belirtin:</span><span class="sxs-lookup"><span data-stu-id="8b661-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="8b661-364">**Genel Kodlama için Yardımcı Sağlayıcılar.**</span><span class="sxs-lookup"><span data-stu-id="8b661-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="8b661-365">Normal ifadeler gibi bir yardımcı program türü sağlayıcısı için, tür sağlayıcısı aşağıdaki örnekte görüldüğü gibi, temel kitaplığın bir parçası olabilir:</span><span class="sxs-lookup"><span data-stu-id="8b661-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="8b661-366">Bu durumda, sağlanan tür normal .NET tasarım kurallarına göre uygun bir noktada görünür:</span><span class="sxs-lookup"><span data-stu-id="8b661-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="8b661-367">**Singleton Veri Kaynakları**.</span><span class="sxs-lookup"><span data-stu-id="8b661-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="8b661-368">Bazı tür sağlayıcıları tek bir özel veri kaynağına bağlanır ve yalnızca veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="8b661-369">Bu durumda, `TypeProvider` sonek bırakmalı ve .NET adlandırma için normal kuralları kullanmalısınız:</span><span class="sxs-lookup"><span data-stu-id="8b661-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="8b661-370">Daha fazla bilgi `GetConnection` için, bu konuda daha sonra açıklanan tasarım kuralına bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="8b661-371">Tip Sağlayıcılar için Tasarım Desenleri</span><span class="sxs-lookup"><span data-stu-id="8b661-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="8b661-372">Aşağıdaki bölümlerde, tür sağlayıcılarını yazarken kullanabileceğiniz tasarım desenleri açıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="8b661-373">GetConnection Tasarım Deseni</span><span class="sxs-lookup"><span data-stu-id="8b661-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="8b661-374">Çoğu tür sağlayıcı, aşağıdaki `GetConnection` örnekte görüldüğü gibi, FSharp.Data.TypeProviders.dll'deki tür sağlayıcıları tarafından kullanılan deseni kullanmak için yazılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8b661-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="8b661-375">Uzaktan Veri ve Hizmetlerle Desteklenen Tip Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="8b661-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="8b661-376">Uzak veri ve hizmetlertarafından desteklenen bir tür sağlayıcısı oluşturmadan önce, bağlı programlamanın doğasında olan bir dizi sorunu göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="8b661-377">Bu konular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b661-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="8b661-378">şema haritalama</span><span class="sxs-lookup"><span data-stu-id="8b661-378">schema mapping</span></span>

- <span data-ttu-id="8b661-379">şema değişimi varlığında canlılık ve geçersizlik</span><span class="sxs-lookup"><span data-stu-id="8b661-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="8b661-380">şema önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="8b661-380">schema caching</span></span>

- <span data-ttu-id="8b661-381">veri erişim işlemlerinin eşzamanlı uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8b661-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="8b661-382">LINQ sorguları da dahil olmak üzere sorguları destekleyen</span><span class="sxs-lookup"><span data-stu-id="8b661-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="8b661-383">kimlik bilgileri ve kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="8b661-383">credentials and authentication</span></span>

<span data-ttu-id="8b661-384">Bu konu bu konuları daha fazla araştırmaz.</span><span class="sxs-lookup"><span data-stu-id="8b661-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="8b661-385">Ek Yazma Teknikleri</span><span class="sxs-lookup"><span data-stu-id="8b661-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="8b661-386">Kendi tür sağlayıcılarınızı yazarken, aşağıdaki ek teknikleri kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="8b661-387">İsteğe Bağlı Tür ve Üye Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b661-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="8b661-388">ProvidedType API, AddMember sürümlerini geciktirdi.</span><span class="sxs-lookup"><span data-stu-id="8b661-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="8b661-389">Bu sürümler, türlerin isteğe bağlı alanlar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="8b661-390">Dizi türleri ve Genel Tür Instantiations sağlama</span><span class="sxs-lookup"><span data-stu-id="8b661-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="8b661-391">Sağlanan üyeleri (imzaları dizi türlerini, byref türlerini ve genel türlerin anlık `MakeArrayType`asyonlarını içerir) normal `MakePointerType`, ve `MakeGenericType` herhangi bir durumda <xref:System.Type>, dahil olmak üzere `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="8b661-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="8b661-392">Bazı durumlarda yardımcıyı ' da `ProvidedTypeBuilder.MakeGenericType`kullanmak zorunda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="8b661-393">Daha fazla ayrıntı için [Tip Sağlayıcı SDK belgelerine](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b661-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="8b661-394">Ölçü Ek Açıklamaları Nın Sağlanması</span><span class="sxs-lookup"><span data-stu-id="8b661-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="8b661-395">ProvidedTypes API ölçü ek açıklamaları sağlamak için yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="8b661-396">Örneğin, türü `float<kg>`sağlamak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b661-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="8b661-397">Türü `Nullable<decimal<kg/m^2>>`sağlamak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b661-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="8b661-398">Proje-Yerel veya Komut Dosyası-Yerel Kaynaklara Erişim</span><span class="sxs-lookup"><span data-stu-id="8b661-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="8b661-399">Bir tür sağlayıcının her örneği `TypeProviderConfig` inşaat sırasında bir değer verilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="8b661-400">Bu değer sağlayıcı için "çözüm klasörü" (diğer bir deyişle, derleme için proje klasörü veya komut dosyası içeren dizin), başvurulan derlemeler listesi ve diğer bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8b661-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="8b661-401">Örneğin</span><span class="sxs-lookup"><span data-stu-id="8b661-401">Invalidation</span></span>

<span data-ttu-id="8b661-402">Sağlayıcılar, F# dil hizmetine şema varsayımlarının değişmiş olabileceğini bildirmek için geçersizik sinyallerini yükseltebilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="8b661-403">Geçersiz işlem meydana geldiğinde, sağlayıcı, Visual Studio' da barındırılıyorsa bir daktişçi denetimi yeniden yapılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="8b661-404">Sağlayıcı F# Interactive'de veya F# Derleyicisi (fsc.exe) tarafından barındırıldığında bu sinyal yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="8b661-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="8b661-405">Önbelleğe Alma Şeması Bilgileri</span><span class="sxs-lookup"><span data-stu-id="8b661-405">Caching Schema Information</span></span>

<span data-ttu-id="8b661-406">Sağlayıcılar genellikle şema bilgilerine erişimi önbelleğe almalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="8b661-407">Önbelleğe alınan veriler, statik parametre olarak veya kullanıcı verisi olarak verilen bir dosya adı kullanılarak depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="8b661-408">Şema önbelleğe alma `LocalSchemaFile` `FSharp.Data.TypeProviders` örneği, derlemedeki tür sağlayıcılarındaki parametredir.</span><span class="sxs-lookup"><span data-stu-id="8b661-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="8b661-409">Bu sağlayıcıların uygulanmasında, bu statik parametre, ağ üzerinden veri kaynağına erişmek yerine, belirtilen yerel dosyadaki şema bilgilerini kullanmaya tür sağlayıcısını yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8b661-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="8b661-410">Önbelleğe alınmış şema bilgilerini kullanmak için statik parametreyi `ForceUpdate` `false`de .</span><span class="sxs-lookup"><span data-stu-id="8b661-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="8b661-411">Çevrimiçi ve çevrimdışı veri erişimini etkinleştirmek için benzer bir teknik kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="8b661-412">Destek Montajı</span><span class="sxs-lookup"><span data-stu-id="8b661-412">Backing Assembly</span></span>

<span data-ttu-id="8b661-413">Bir `.dll` veya `.exe` dosya derlediğinizde, oluşturulan türler için destek .dll dosyası statik olarak ortaya çıkan derlemeye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="8b661-414">Bu bağlantı, Ara Dil (IL) türü tanımları ve destek derlemesinden son derlemeye yönetilen tüm kaynaklar kopyalayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8b661-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="8b661-415">F# Interactive'i kullandığınızda, destek .dll dosyası kopyalanır ve bunun yerine doğrudan F# Interactive işlemine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8b661-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="8b661-416">Tip Sağlayıcılardan İstisnalar ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="8b661-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="8b661-417">Sağlanan türdeki tüm üyelerin tüm kullanımları özel durumlar getirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="8b661-418">Her durumda, bir tür sağlayıcısı bir özel durum atarsa, ana bilgisayar derleyicisi hatayı belirli bir tür sağlayıcısına bağlar.</span><span class="sxs-lookup"><span data-stu-id="8b661-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="8b661-419">Tür sağlayıcı özel durumları hiçbir zaman iç derleyici hatalarına neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="8b661-420">Tür sağlayıcıları uyarıları bildiremez.</span><span class="sxs-lookup"><span data-stu-id="8b661-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="8b661-421">Bir tür sağlayıcısı F# derleyicisinde, F# geliştirme ortamında veya F# Interactive'de barındırıldığında, bu sağlayıcıdan gelen tüm özel durumlar yakalanır.</span><span class="sxs-lookup"><span data-stu-id="8b661-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="8b661-422">İleti özelliği her zaman hata metnidir ve yığın izi görünmez.</span><span class="sxs-lookup"><span data-stu-id="8b661-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="8b661-423">Bir özel durum atacaksanız, aşağıdaki örnekleri atabilirsiniz: `System.NotSupportedException` `System.IO.IOException`, `System.Exception`, .</span><span class="sxs-lookup"><span data-stu-id="8b661-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="8b661-424">Oluşturulan Türleri Sağlama</span><span class="sxs-lookup"><span data-stu-id="8b661-424">Providing Generated Types</span></span>

<span data-ttu-id="8b661-425">Şimdiye kadar, bu belge silinmiş türleri sağlamak için nasıl açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b661-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="8b661-426">F#'daki tür sağlayıcı mekanizmasını, kullanıcıların programına gerçek .NET türü tanımları olarak eklenen oluşturulan türleri sağlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="8b661-427">Bir tür tanımı kullanarak oluşturulan türlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="8b661-428">F# 3.0 sürümünden bir parçası olan ProvidedTypes-0.2 yardımcı kodu, oluşturulan türleri sağlamak için yalnızca sınırlı bir desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b661-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="8b661-429">Oluşturulan bir tür tanımı için aşağıdaki ifadeler doğru olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8b661-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="8b661-430">`isErased``false`olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="8b661-431">Oluşturulan tür, oluşturulan kod parçaları `ProvidedAssembly()`için bir kapsayıcıyı temsil eden yeni oluşturulan bir yapıya eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b661-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="8b661-432">Sağlayıcı, diskte eşleşen bir .dll dosyası olan gerçek bir destek .NET .dll dosyasına sahip bir derlemeye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="8b661-433">Kurallar ve Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="8b661-433">Rules and Limitations</span></span>

<span data-ttu-id="8b661-434">Tür sağlayıcılar yazarken, aşağıdaki kuralları ve sınırlamaları aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8b661-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="8b661-435">Sağlanan türlere ulaşılabilir olmalıdır</span><span class="sxs-lookup"><span data-stu-id="8b661-435">Provided types must be reachable</span></span>

<span data-ttu-id="8b661-436">Sağlanan tüm türlere iç içe olmayan türlerden ulaşılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b661-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="8b661-437">İç içe olmayan `TypeProviderForNamespaces` türler, oluşturucuya veya ''ye `AddNamespace`çağrıda verilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="8b661-438">Örneğin, sağlayıcı bir tür `StaticClass.P : T`sağlıyorsa, T'nin iç içe olmayan bir tür olduğundan veya birinin altında iç içe olduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b661-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="8b661-439">Örneğin, bazı sağlayıcılar gibi `DataTypes` statik bir `T1, T2, T3, ...` sınıf bu türleri içeren var.</span><span class="sxs-lookup"><span data-stu-id="8b661-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="8b661-440">Aksi takdirde, hata, A derlemesinde T türüne bir başvuru bulunduğunu, ancak bu derlemede türün bulunamadığını söyler.</span><span class="sxs-lookup"><span data-stu-id="8b661-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="8b661-441">Bu hata görünürse, tüm alt türlerinize sağlayıcı türlerinden ulaşılabileceğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="8b661-442">Not: `T1, T2, T3...` Bu türlere *anında* uçuş türleri denir.</span><span class="sxs-lookup"><span data-stu-id="8b661-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="8b661-443">Bunları erişilebilir bir ad alanına veya bir üst türe koymayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b661-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="8b661-444">Tip Sağlayıcı Mekanizmasının Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="8b661-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="8b661-445">F#'daki tür sağlayıcı mekanizması aşağıdaki sınırlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="8b661-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="8b661-446">F# türü sağlayıcıları için temel altyapı, sağlanan genel türleri veya sağlanan genel yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8b661-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="8b661-447">Mekanizma, statik parametrelerle iç içe geçmiş türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8b661-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="8b661-448">Geliştirme İpuçları</span><span class="sxs-lookup"><span data-stu-id="8b661-448">Development Tips</span></span>

<span data-ttu-id="8b661-449">Geliştirme sürecinde aşağıdaki ipuçlarıyararlı bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="8b661-450">Visual Studio'nun iki örneğini çalıştırın</span><span class="sxs-lookup"><span data-stu-id="8b661-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="8b661-451">Bir örnekte tür sağlayıcısını geliştirebilir ve sağlayıcıyı diğerinde sınayabilirsiniz, çünkü test IDE,.dll dosyasında tür sağlayıcısının yeniden oluşturulmasını engelleyen bir kilit alır.</span><span class="sxs-lookup"><span data-stu-id="8b661-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="8b661-452">Bu nedenle, sağlayıcı ilk etapta yerleşik iken Visual Studio ikinci örneği kapatmanız gerekir ve sonra sağlayıcı inşa edildikten sonra ikinci örneği yeniden açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b661-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="8b661-453">fsc.exe çağrılarını kullanarak hata ayıklama türü sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="8b661-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="8b661-454">Aşağıdaki araçları kullanarak tür sağlayıcılarını çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b661-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="8b661-455">fsc.exe (F# komut satırı derleyicisi)</span><span class="sxs-lookup"><span data-stu-id="8b661-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="8b661-456">fsi.exe (F# İnteraktif derleyici)</span><span class="sxs-lookup"><span data-stu-id="8b661-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="8b661-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8b661-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="8b661-458">Genellikle bir test komut dosyası dosyası (örneğin, script.fsx) üzerinde fsc.exe kullanarak en kolay hata türü sağlayıcıları olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b661-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="8b661-459">Komut isteminden hata ayıklama başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="8b661-460">Yazdırma-stdout günlüğe kaydetmeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b661-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b661-461">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b661-461">See also</span></span>

- [<span data-ttu-id="8b661-462">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="8b661-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="8b661-463">Tip Sağlayıcı SDK</span><span class="sxs-lookup"><span data-stu-id="8b661-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
