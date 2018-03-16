---
title: "Eğitmen: Tür Sağlayıcısı Oluşturma (F#)"
description: "Temel kavramları göstermek için birkaç basit tür sağlayıcıları inceleyerek F # 3. 0'da kendi F # tür sağlayıcıları oluşturmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 82bec076-19d4-470c-979f-6c3a14b7c70a
ms.openlocfilehash: 30d1c20d66fd0a193c05c97ee726a886f98356ad
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2018
---
# <a name="tutorial-creating-a-type-provider"></a><span data-ttu-id="a547c-104">Eğitmen: tür sağlayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a547c-104">Tutorial: Creating a Type Provider</span></span>

<span data-ttu-id="a547c-105">Türü sağlayıcısı F # kendi bilgi zengin programlama desteği için önemli bir bölümü mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-105">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="a547c-106">Bu öğretici, temel kavramları göstermek için birkaç basit tür sağlayıcıları geliştirme adım adım ilerlemenizi sağlayarak kendi tür sağlayıcıları oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-106">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="a547c-107">F # tür sağlayıcısı mekanizması hakkında daha fazla bilgi için bkz: [tür sağlayıcıları](index.md).</span><span class="sxs-lookup"><span data-stu-id="a547c-107">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="a547c-108">F # ekosistemi tür sağlayıcıları yaygın olarak kullanılan Internet ve kurumsal veri hizmetleri için bir aralığı içerir.</span><span class="sxs-lookup"><span data-stu-id="a547c-108">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="a547c-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a547c-109">For example:</span></span>

- <span data-ttu-id="a547c-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) biçimleri JSON, XML, CSV ve HTML belge türü sağlayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="a547c-110">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="a547c-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) bu veri kaynaklarının sorguları bir nesne eşleme ve F # LINQ üzerinden SQL veritabanlarını kesin türü belirtilmiş erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-111">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="a547c-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sahip bir derleme zamanı tür sağlayıcıları işaretli T-SQL F # katıştırma.</span><span class="sxs-lookup"><span data-stu-id="a547c-112">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="a547c-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) kullanmak için tür sağlayıcıları ile SQL, Entity Framework, OData ve WSDL Veri Hizmetleri erişmek için yalnızca .NET Framework programlama daha eski bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="a547c-113">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="a547c-114">Gerektiğinde özel tür sağlayıcıları oluşturabilir veya başkalarının oluşturmuş olduğunuz tür sağlayıcıları başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-114">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="a547c-115">Örneğin, kuruluşunuzun büyük ve artan çeşitli adlandırılmış veri kümeleri, her biri kendi kararlı veri sağlayan veri hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-115">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="a547c-116">Şemalar okuyan ve geçerli veri kümeleri için programcı kesin türü belirtilmiş şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-116">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>


## <a name="before-you-start"></a><span data-ttu-id="a547c-117">Başlamadan önce</span><span class="sxs-lookup"><span data-stu-id="a547c-117">Before You Start</span></span>

<span data-ttu-id="a547c-118">Türü sağlayıcısı mekanizması öncelikle kararlı veri ve hizmet bilgi alanları F programlama deneyimine # diline injecting için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a547c-118">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="a547c-119">Bu mekanizma program mantığı için uygun olan şekilde program yürütme sırasında şema değişiklikleri bilgi alanları injecting için tasarlanmış değil.</span><span class="sxs-lookup"><span data-stu-id="a547c-119">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="a547c-120">Ayrıca, bazı geçerli kullanımlarını o etki alanını içeren olsa bile mekanizması içi dil için meta programlama tasarlanmış değil.</span><span class="sxs-lookup"><span data-stu-id="a547c-120">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="a547c-121">Burada tür sağlayıcısı geliştirme çok yüksek bir değer verir ve bu düzenek yalnızca gerekli olduğunda kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a547c-121">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="a547c-122">Burada bir şema kullanılamaz tür sağlayıcısı yazma kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a547c-122">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="a547c-123">Benzer şekilde, tür sağlayıcısı sıradan (veya hatta var olan yerlerde) yazma kaçınmalısınız .NET kitaplığı yeterli.</span><span class="sxs-lookup"><span data-stu-id="a547c-123">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="a547c-124">Başlamadan önce aşağıdaki soruları sormaya:</span><span class="sxs-lookup"><span data-stu-id="a547c-124">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="a547c-125">Bilgi kaynağınız için bir şema var mı?</span><span class="sxs-lookup"><span data-stu-id="a547c-125">Do you have a schema for your information source?</span></span> <span data-ttu-id="a547c-126">Bu durumda, F # ve .NET tür sistemi eşlemeye nedir?</span><span class="sxs-lookup"><span data-stu-id="a547c-126">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="a547c-127">Bir başlangıç noktası olarak varolan bir (dinamik olarak yazılan) API uygulamanız için kullanabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="a547c-127">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="a547c-128">Ve kuruluşunuzun, tür sağlayıcısı yazmayı faydalı yapmak için yeterli kullanımlarını gerekiyor mu?</span><span class="sxs-lookup"><span data-stu-id="a547c-128">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="a547c-129">Normal bir .NET kitaplığı ihtiyaçlarınızı karşılamak?</span><span class="sxs-lookup"><span data-stu-id="a547c-129">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="a547c-130">Ne kadar şemanızı değişir mi?</span><span class="sxs-lookup"><span data-stu-id="a547c-130">How much will your schema change?</span></span>

- <span data-ttu-id="a547c-131">Kodlama sırasında değişir mi?</span><span class="sxs-lookup"><span data-stu-id="a547c-131">Will it change during coding?</span></span>

- <span data-ttu-id="a547c-132">Oturumları kodlama arasında değişir mi?</span><span class="sxs-lookup"><span data-stu-id="a547c-132">Will it change between coding sessions?</span></span>

- <span data-ttu-id="a547c-133">Program yürütülmesi sırasında değişir mi?</span><span class="sxs-lookup"><span data-stu-id="a547c-133">Will it change during program execution?</span></span>

<span data-ttu-id="a547c-134">Tür sağlayıcıları şema çalışma zamanında ve derlenmiş kod kullanım ömrü süresince kararlı olduğu durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="a547c-134">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>


## <a name="a-simple-type-provider"></a><span data-ttu-id="a547c-135">Bir basit tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a547c-135">A Simple Type Provider</span></span>

<span data-ttu-id="a547c-136">Bu örnek Samples.HelloWorldTypeProvider, örnekleri benzer olduğunu `examples` dizininde [F # tür sağlayıcısı SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span><span class="sxs-lookup"><span data-stu-id="a547c-136">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="a547c-137">Sağlayıcısını 100 silinen türlerini F # imza sözdizimini kullanarak ve dışında tüm için ayrıntıları atlama aşağıdaki gösterildiği gibi kodu içeren bir "türü alanı" kullanılabilir hale getirir `Type1`.</span><span class="sxs-lookup"><span data-stu-id="a547c-137">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="a547c-138">Silinen türleri hakkında daha fazla bilgi için bkz: [ayrıntılar hakkında silinmesi sağlanan türleri](#details-about-erased-provided-types) bu konuda daha sonra.</span><span class="sxs-lookup"><span data-stu-id="a547c-138">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

    /// This is an instance property.
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

<span data-ttu-id="a547c-139">Dizi türleri ve sağlanan üyeleri statik olarak bilinen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-139">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="a547c-140">Bu örnek üzerinde bir şema bağımlı türleri sağlayabilme sağlayıcılarının yararlanın değil.</span><span class="sxs-lookup"><span data-stu-id="a547c-140">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="a547c-141">Tür sağlayıcısı uygulaması aşağıdaki kodda özetlenen ve Ayrıntılar, bu konunun sonraki bölümlerinde ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-141">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>


>[!WARNING] 
<span data-ttu-id="a547c-142">Bu kod ve çevrimiçi Örnekler arasındaki farklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-142">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="a547c-143">Bu sağlayıcı kullanmak için Visual Studio ayrı bir örneği açın, F # komut dosyası oluşturabilir ve sonra aşağıdaki kodu gösterildiği gibi #r kullanarak kodunuzu sağlayıcı için bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a547c-143">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="a547c-144">Türleri altında Ara `Samples.HelloWorldTypeProvider` türü sağlayıcısı oluşturulan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="a547c-144">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="a547c-145">Sağlayıcıyı yeniden derleyin önce sağlayıcısını DLL kullanmakta olduğunuz tüm örneklerini Visual Studio ve F # Etkileşimli kapattığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a547c-145">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="a547c-146">Aksi takdirde, DLL çıkış kilitli olduğundan bir derleme hatası meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="a547c-146">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="a547c-147">Bu sağlayıcı yazdırma deyimleri kullanarak hata ayıklamak için sağlayıcı ile ilgili bir sorun kullanıma sunan bir komut dosyası olun ve sonra aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-147">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="a547c-148">Visual Studio kullanarak bu sağlayıcı hatalarını ayıklamak için yönetici kimlik bilgileriyle Visual Studio komut istemi açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a547c-148">To debug this provider by using Visual Studio, open the Visual Studio command prompt with administrative credentials, and run the following command:</span></span>

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="a547c-149">Alternatif olarak, Visual Studio'yu açın, hata ayıklama menüsünü açın, seçin `Debug/Attach to process…`ve başka ekleme `devenv` burada düzenlediğiniz komut dosyanızı işlem.</span><span class="sxs-lookup"><span data-stu-id="a547c-149">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="a547c-150">Bu yöntemi kullanarak, ikinci örneğiyle (IntelliSense ve diğer özellikleri) içine etkileşimli olarak ifadeleri yazarak, tür sağlayıcısı belirli mantığı daha kolay hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-150">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="a547c-151">Oluşturulan kod hataları daha iyi tanımlamak için hata ayıklama sadece kendi kodumu devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-151">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="a547c-152">Etkinleştirmek veya bu özelliği devre dışı bırakma hakkında daha fazla bilgi için bkz: [hata ayıklayıcısı ile kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="a547c-152">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="a547c-153">Ayrıca, aynı zamanda açarak yakalama ilk fırsat özel durum ayarlayabilirsiniz `Debug` menüsüne ve ardından seçme `Exceptions` veya açmak için Ctrl + Alt + E tuşları seçerek `Exceptions` iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="a547c-153">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="a547c-154">Bu iletişim kutusunda, altında `Common Language Runtime Exceptions`seçin `Thrown` onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="a547c-154">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>


### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="a547c-155">Uygulama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a547c-155">Implementation of the Type Provider</span></span>

<span data-ttu-id="a547c-156">Bu bölümde tür sağlayıcısı uygulamasının asıl bölümleri anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-156">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="a547c-157">İlk olarak, özel tür sağlayıcısı için kendisini türünü tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="a547c-157">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="a547c-158">Bu tür genel olmalıdır ve onunla işaretlemelisiniz [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) ayrı bir F # proje türünü içeren bütünleştirilmiş kodun başvurduğunda derleyici tür sağlayıcısı tanıyabilmesi için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a547c-158">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="a547c-159">*Config* parametre isteğe bağlıdır ve, varsa, F # derleyici oluşturur türü sağlayıcısı örneği için bağlamsal yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a547c-159">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="a547c-160">Ardından, uygulamanız [Itypeprovider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a547c-160">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="a547c-161">Bu durumda, kullandığınız `TypeProviderForNamespaces` gelen yazın `ProvidedTypes` bir taban türü olarak API.</span><span class="sxs-lookup"><span data-stu-id="a547c-161">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="a547c-162">Ad alanları, her biri doğrudan sınırlı sayıda sabit içeren, isteğini önleyebiliriz sağlanan türleri sağlanan bu yardımcı türü sınırlı koleksiyonu isteğini önleyebiliriz sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-162">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="a547c-163">Sağlayıcı bu bağlamda *isteğini önleyebiliriz* kullanılan gerekli veya değil olsa bile türleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a547c-163">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="a547c-164">Ardından, sağlanan türleri için ad alanı belirtin yerel özel değerleri tanımlayın ve türü sağlayıcı derlemesi kendisini bulun.</span><span class="sxs-lookup"><span data-stu-id="a547c-164">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="a547c-165">Bu derleme daha sonra sağlanan silinen türleri mantıksal üst türü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a547c-165">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="a547c-166">Ardından, Type1 türlerinin her biri sağlamak için bir işlev oluştur... Type100.</span><span class="sxs-lookup"><span data-stu-id="a547c-166">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="a547c-167">Bu işlev, bu konunun ilerleyen bölümlerinde daha ayrıntılı açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a547c-167">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="a547c-168">Ardından, 100 sağlanan türleri oluştur:</span><span class="sxs-lookup"><span data-stu-id="a547c-168">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="a547c-169">Ardından, türleri sağlanan bir ad alanı Ekle:</span><span class="sxs-lookup"><span data-stu-id="a547c-169">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="a547c-170">Son olarak, tür sağlayıcısı DLL oluşturmakta olduğunuz gösteren bir derleme özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a547c-170">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="a547c-171">Tür ve üyelerini sağlama</span><span class="sxs-lookup"><span data-stu-id="a547c-171">Providing One Type And Its Members</span></span>

<span data-ttu-id="a547c-172">`makeOneProvidedType` İşlevi türlerinden birini sağlama gerçek iş yapar.</span><span class="sxs-lookup"><span data-stu-id="a547c-172">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) = 
…
```

<span data-ttu-id="a547c-173">Bu adım, bu işlev uygulaması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-173">This step explains the implementation of this function.</span></span> <span data-ttu-id="a547c-174">İlk olarak, sağlanan türü oluşturun (örneğin, Type1, n zaman = 1 veya Type57, = 57 n olduğunda).</span><span class="sxs-lookup"><span data-stu-id="a547c-174">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="a547c-175">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="a547c-175">You should note the following points:</span></span>

- <span data-ttu-id="a547c-176">Bu tür silebilmeniz sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-176">This provided type is erased.</span></span>  <span data-ttu-id="a547c-177">Temel türü olduğunu belirtmek için `obj`, örnekleri, tür değerleri olarak görünür [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) derlenmiş kod.</span><span class="sxs-lookup"><span data-stu-id="a547c-177">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="a547c-178">Bir iç içe olmayan türü belirttiğinizde, derleme ve ad alanı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-178">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="a547c-179">Silinen türleri için derleme türü sağlayıcı derlemesi kendisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-179">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="a547c-180">Ardından, XML belgeleri türüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a547c-180">Next, add XML documentation to the type.</span></span> <span data-ttu-id="a547c-181">Bu belge, yani ertelendi, ana bilgisayar derleyici gerekiyorsa isteğe bağlı hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-181">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="a547c-182">Sonraki türü için sağlanan bir statik özellik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a547c-182">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
                                  propertyType = typeof<string>, 
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="a547c-183">Bu özellik alma dizesi "Hello!" her zaman değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a547c-183">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="a547c-184">`GetterCode` Özelliği almak için konak derleyici oluşturur kodunu temsil eden bir F # tırnak, özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-184">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="a547c-185">Teklifleri hakkında daha fazla bilgi için bkz: [kod tırnak işaretleri (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="a547c-185">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="a547c-186">XML belgeleri özelliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a547c-186">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="a547c-187">Şimdi sağlanan özellik sağlanan türüne bağlayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-187">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="a547c-188">Tek bir tür için sağlanan üyesi ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-188">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="a547c-189">Aksi takdirde, üye hiçbir zaman erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a547c-189">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="a547c-190">Şimdi parametre almayan bir sağlanan Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a547c-190">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="a547c-191">`InvokeCode` Oluşturucusu Oluşturucu çağrıldığında, ana bilgisayar derleyici oluşturan kodu temsil eden bir F # tırnak, döndürür.</span><span class="sxs-lookup"><span data-stu-id="a547c-191">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="a547c-192">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-192">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="a547c-193">Sağlanan türünün bir örneği temel alınan verilerle "Nesne verileri" oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a547c-193">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="a547c-194">Dönüştürme için tırnak işaretli kodu içerir [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) silinmesini türü olduğundan (sağlanan türü bildirilmedi zaman belirttiğiniz gibi) bu tür sağlanan.</span><span class="sxs-lookup"><span data-stu-id="a547c-194">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="a547c-195">XML belgeleri oluşturucuya ekleyin ve sağlanan tür için sağlanan bir oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a547c-195">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="a547c-196">Bir parametre alan ikinci bir sağlanan Oluşturucusu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a547c-196">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="a547c-197">`InvokeCode` Oluşturucusu konak derleyici yöntemine bir çağrı için oluşturulan kodu temsil eden bir F # tırnak, yeniden döndürür.</span><span class="sxs-lookup"><span data-stu-id="a547c-197">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="a547c-198">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-198">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="a547c-199">Sağlanan türünün bir örneği temel alınan verilerle "on" oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a547c-199">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="a547c-200">Zaten, fark etmiş olabilirsiniz `InvokeCode` işlevi bir teklif döndürür.</span><span class="sxs-lookup"><span data-stu-id="a547c-200">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="a547c-201">Bu işlev giriş ifadeleri, her Oluşturucusu parametresi için bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="a547c-201">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="a547c-202">Bu durumda, tek bir parametre değeri temsil eden bir ifade kullanılabilir `args.[0]`.</span><span class="sxs-lookup"><span data-stu-id="a547c-202">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="a547c-203">Silinen türü dönüş değerini Oluşturucusu çağrısı için kod olacak şekilde zorlar `obj`.</span><span class="sxs-lookup"><span data-stu-id="a547c-203">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="a547c-204">İkinci sağlanan Oluşturucusu türüne ekledikten sonra sağlanan örnek özellik oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a547c-204">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp = 
    ProvidedProperty(propertyName = "InstanceProperty", 
                     propertyType = typeof<int>, 
                     getterCode= (fun args -> 
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="a547c-205">Bu özellik alma gösterimi nesne dize uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a547c-205">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="a547c-206">`GetterCode` Özelliği özelliği almak için konak derleyici oluşturur kod belirtir F # tırnak döndürür.</span><span class="sxs-lookup"><span data-stu-id="a547c-206">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="a547c-207">Gibi `InvokeCode`, `GetterCode` işlevi bir teklif döndürür.</span><span class="sxs-lookup"><span data-stu-id="a547c-207">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="a547c-208">Ana bilgisayar derleyici bu işlevi bağımsız değişken listesini kullanarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="a547c-208">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="a547c-209">Bu durumda, kullanarak erişebileceğiniz sonra alıcı adlandırılan, örneği temsil eden yalnızca tek bir ifade bağımsız değişkenleri ekleyin `args.[0]`. Uygulaması `GetterCode` silinen yazın sonuç tırnak içine splices `obj`, ve bir cast türleri nesnesinin bir dize olduğunu denetleme derleyicinin mekanizması karşılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a547c-209">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="a547c-210">Sonraki bölümü `makeOneProvidedType` bir parametresiyle örnek yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="a547c-211">Son olarak, 100 iç içe özellikler içeren bir iç içe geçmiş türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a547c-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="a547c-212">Bu oluşturulmasını türü ve özelliklerini iç içe geçmiş, yani ertelendi, isteğe bağlı hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="a547c-213">Silinen sağlanan türleri hakkında ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a547c-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="a547c-214">Bu bölümdeki örnek yalnızca sağlar *sağlanan türleri silinmesi*, aşağıdaki durumlarda özellikle yararlı olan:</span><span class="sxs-lookup"><span data-stu-id="a547c-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="a547c-215">Ne zaman yalnızca veri ve yöntemleri içeren bir bilgi alanı için bir sağlayıcı yazıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a547c-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="a547c-216">Ne zaman burada doğru çalışma zamanı türü anlamları bilgi alanı pratik kullanım için kritik olmayan bir sağlayıcı yazıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a547c-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="a547c-217">Ne zaman büyük ve birbirine bağlı bilgi alanı için gerçek .NET türleri oluşturmak için teknik olarak uygun olmayan bir bilgi alanı için bir sağlayıcı yazıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a547c-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="a547c-218">Bu örnekte, her tür yazmak için silinir sağlanan `obj`, ve türü tüm kullanımlarını türü olarak görünür `obj` derlenmiş kod.</span><span class="sxs-lookup"><span data-stu-id="a547c-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="a547c-219">Aslında, arka plandaki nesneleri bu örneklerde dizelerdir, ancak türü olarak görünür `System.Object` .NET derlenmiş kod.</span><span class="sxs-lookup"><span data-stu-id="a547c-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="a547c-220">Türü silinme tüm kullanıcılarına açık kutulama kullanabileceğiniz gibi kutudan çıkarma ve atama bozmaya için türleri silinebilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="a547c-221">Bu durumda, nesne kullanıldığında, geçerli olmayan bir yayın özel durumu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="a547c-222">Bir sağlayıcı çalışma zamanı false ifadeleri karşı korunmasına yardımcı olmak için kendi özel gösterim türü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="a547c-223">F # içinde kendisi silinen türleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a547c-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="a547c-224">Yalnızca sağlanan türleri silinebilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-224">Only provided types may be erased.</span></span> <span data-ttu-id="a547c-225">Hem pratik ayrımlar anlamanız gerekir ve anlam ya da kullanmanın silinen türleri, tür sağlayıcısı veya sağlayan bir sağlayıcı için türleri silinebilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="a547c-226">Silinen bir türü gerçek .NET tür yok.</span><span class="sxs-lookup"><span data-stu-id="a547c-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="a547c-227">Bu nedenle, doğru yansıma türü üzerinden yapamayacağı ve çalışma zamanı atamalar ve üzerinde tam çalışma zamanı türü anlamları kullanan başka teknikler kullanırsanız, silinen türleri bozmaya.</span><span class="sxs-lookup"><span data-stu-id="a547c-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="a547c-228">Silinen türlerinin alt sürüme cast türü özel durumları çalışma zamanında sık sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>


### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="a547c-229">Sağlanan türleri Beyanları silebilmeniz için seçme</span><span class="sxs-lookup"><span data-stu-id="a547c-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="a547c-230">Bazı silinen sağlananlardan kullanımları hiçbir gösterimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a547c-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="a547c-231">Örneğin, silinen türü yalnızca statik özellikler ve üyeleri ve oluşturucu yok içerebilir ve yöntemleri ya da özellikleri türünün bir örneği döndürecektir sağlanan.</span><span class="sxs-lookup"><span data-stu-id="a547c-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="a547c-232">Tür sağlanan bir silinen örneklerini erişebiliyorsa, aşağıdaki soruları göz önünde bulundurmalısınız:</span><span class="sxs-lookup"><span data-stu-id="a547c-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="a547c-233">**Sağlanan tür silinmesini nedir?**</span><span class="sxs-lookup"><span data-stu-id="a547c-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="a547c-234">Sağlanan tür silinmesini türü derlenmiş .NET kodunda görünme ' dir.</span><span class="sxs-lookup"><span data-stu-id="a547c-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="a547c-235">Sağlanan silinen sınıf türü silinme her zaman ilk silinmesi olmayan türün temel türünü devralma zincirinde ' dir.</span><span class="sxs-lookup"><span data-stu-id="a547c-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="a547c-236">Sağlanan silinen arabirim türü silinmesini her zaman olduğu `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="a547c-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="a547c-237">**Sağlanan tür gösterimlerini nelerdir?**</span><span class="sxs-lookup"><span data-stu-id="a547c-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="a547c-238">Bir silinen tür sağlanan için olası nesne kümesini kendi Beyanları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a547c-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="a547c-239">Bu belgedeki örnekte tüm silinen sağlanan gösterimlerini türleri `Type1..Type100` her zaman dize nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="a547c-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="a547c-240">Sağlanan bir türdeki tüm Beyanları sağlanan türü silinme ile uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="a547c-241">(Aksi halde, F # derleyici hata türü sağlayıcısı için bir kullanım alır ya da geçersiz doğrulanamayan .NET kodu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a547c-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="a547c-242">Tür sağlayıcısı geçersiz bir gösterimi verir kodu döndürmesi durumunda geçerli değil.)</span><span class="sxs-lookup"><span data-stu-id="a547c-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="a547c-243">Her ikisi de çok yaygın aşağıdaki yaklaşımlardan birini kullanarak sağlanan nesneleri temsili seçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="a547c-244">Varolan bir .NET türünü yalnızca kesin türü belirtilmiş bir sarmalayıcı sağlıyorsanız, genellikle o türüne silme, bu türdeki örneklerin Beyanları veya her ikisini de olarak kullanmak türünüz için mantıklıdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="a547c-245">Bu türün varolan yöntemleri çoğunu hala kesin türü belirtilmiş sürümünü kullanırken anlamlı olduğunda bu uygun bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="a547c-246">Var olan tüm .NET API önemli ölçüde farklı bir API oluşturmak istiyorsanız, bu tür silinme ve Beyanları sağlanan türleri için çalışma zamanı türleri oluşturmak için anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="a547c-247">Bu belge örnekte dizelerini sağlanan nesneleri gösterimlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="a547c-248">Genellikle, diğer nesneler için temsili kullanmak uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="a547c-249">Örneğin, bir özellik paketi olarak bir sözlük kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="a547c-250">Alternatif olarak, çalışma zamanında bir veya daha fazla çalışma zamanı işlemleri birlikte bir gösterim oluşturmak için kullanılan, tür sağlayıcısı tür tanımlama:</span><span class="sxs-lookup"><span data-stu-id="a547c-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="a547c-251">Sağlanan üyeleri, ardından bu nesne türü örnekleri oluşturabileceğiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [], 
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="a547c-252">Bu durumda, (isteğe bağlı) bu tür türü silinme bu türü olarak belirterek kullanabilirsiniz `baseType` oluşturulurken `ProvidedTypeDefinition`:</span><span class="sxs-lookup"><span data-stu-id="a547c-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="a547c-253">Önemli dersleri</span><span class="sxs-lookup"><span data-stu-id="a547c-253">Key Lessons</span></span>

<span data-ttu-id="a547c-254">Önceki bölümde bir dizi türleri, özellikleri ve yöntemleri sağlayan basit bir silme tür sağlayıcısı oluşturma açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a547c-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="a547c-255">Bu bölümde ayrıca bazı avantajları ve dezavantajları türü sağlayıcıdan silinen türleri sağlama dahil olmak üzere türü silinme kavramı açıklandığı ve Silinen türleri gösterimlerini ele alınan.</span><span class="sxs-lookup"><span data-stu-id="a547c-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>


## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="a547c-256">Statik parametreleri kullanan bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a547c-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="a547c-257">Tür sağlayıcıları tarafından statik verileri Parametreleştirme olanağı bile sağlayıcı yerel veya uzak verilere erişmek gerektiğinde değil durumlarda birçok ilginç senaryolara olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="a547c-258">Bu bölümde, böyle bir sağlayıcı bir araya getirilmesi için bazı temel tekniklerini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>


### <a name="type-checked-regex-provider"></a><span data-ttu-id="a547c-259">Regex sağlayıcısı türü işaretli</span><span class="sxs-lookup"><span data-stu-id="a547c-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="a547c-260">.NET sarmalar türü sağlayıcısı normal ifadeler için uygulamak istediğiniz düşünün <xref:System.Text.RegularExpressions.Regex> aşağıdaki derleme zamanı garanti sağlayan bir arabirimi kitaplıklarında:</span><span class="sxs-lookup"><span data-stu-id="a547c-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="a547c-261">Normal bir ifade geçerli olup olmadığını doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="a547c-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="a547c-262">Tüm grup adlarını normal ifadede dayalı eşleşmeler üzerinde adlandırılmış özelliklerinin sağlanması.</span><span class="sxs-lookup"><span data-stu-id="a547c-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="a547c-263">Bu bölümde tür sağlayıcıları oluşturmak için nasıl kullanılacağı gösterilmiştir bir `RegexTyped` normal ifade deseni bu kazanımları sağlamak için parameterizes yazın.</span><span class="sxs-lookup"><span data-stu-id="a547c-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="a547c-264">Derleyici, belirtilen desenle geçerli değil ve böylece eşleşmeleri özellikleri adlandırılmış kullanarak erişebilir türü sağlayıcısı düzeni grupları ayıklayabilirsiniz bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="a547c-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="a547c-265">Tür sağlayıcısı tasarlarken, sunulan API'si nasıl görünmelidir düşünmelisiniz son kullanıcılar ve bu tasarımı .NET kodu için nasıl çevirir.</span><span class="sxs-lookup"><span data-stu-id="a547c-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="a547c-266">Aşağıdaki örnek, alan kodunu bileşenlerini almak için bu tür bir API kullanmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a547c-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="a547c-267">Aşağıdaki örnek, tür sağlayıcısı bu çağrılarının nasıl çevirir gösterir:</span><span class="sxs-lookup"><span data-stu-id="a547c-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="a547c-268">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="a547c-268">Note the following points:</span></span>

- <span data-ttu-id="a547c-269">Standart Regex türü parametreli temsil eden `RegexTyped` türü.</span><span class="sxs-lookup"><span data-stu-id="a547c-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="a547c-270">`RegexTyped` Deseni için statik tür bağımsız değişkeni geçirme Regex Oluşturucusu çağrısına Oluşturucusu sonuçlanıyor.</span><span class="sxs-lookup"><span data-stu-id="a547c-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="a547c-271">Sonuçlarını `Match` yöntemi Standart tarafından temsil edilen <xref:System.Text.RegularExpressions.Match> türü.</span><span class="sxs-lookup"><span data-stu-id="a547c-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="a547c-272">Sağlanan özelliğinde her adlandırılmış grubu sonuçları ve özellik erişme sonuçlanıyor eşleşmeyi'nın bir dizin oluşturucu kullanımını `Groups` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a547c-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="a547c-273">Aşağıdaki kodu böyle bir sağlayıcı uygulamak için mantığı çekirdek ve bu örnek sağlanan türü için tüm üyelerinin eklenmesini atlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="a547c-274">Eklenen her üye hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde uygun bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a547c-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="a547c-275">Tam kodunu örnekten karşıdan [F # 3.0 örnek paketi](https://fsharp3sample.codeplex.com) Codeplex Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="a547c-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://fsharp3sample.codeplex.com) on the Codeplex website.</span></span>

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

<span data-ttu-id="a547c-276">Aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="a547c-276">Note the following points:</span></span>

- <span data-ttu-id="a547c-277">Tür sağlayıcısı iki statik parametreleri alır: `pattern`, zorunlu olduğu ve `options`, hangi isteğe bağlı (varsayılan bir değer sağlandığı için).</span><span class="sxs-lookup"><span data-stu-id="a547c-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="a547c-278">Statik bağımsız değişkenleri sağlanan sonra normal ifade örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a547c-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="a547c-279">Bu örnek, Regex hatalı biçimlendirilmiş ise ve bu hata kullanıcılara bildirilecek bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a547c-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="a547c-280">İçinde `DefineStaticParameters` geri değişkenleri sağlanan sonra döndürülecek tür tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="a547c-281">Bu kod ayarlar `HideObjectMethods` IntelliSense deneyimi kolaylaştırılmış kalması true.</span><span class="sxs-lookup"><span data-stu-id="a547c-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="a547c-282">Bu öznitelik neden `Equals`, `GetHashCode`, `Finalize`, ve `GetType` üyelerinin atlanması için sağlanan nesne için IntelliSense listelerden.</span><span class="sxs-lookup"><span data-stu-id="a547c-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="a547c-283">Kullandığınız `obj` yöntemi, ancak temel türünü kullanacağınız gibi bir `Regex` nesnesi olarak sonraki örnekte gösterildiği gibi bu tür, çalışma zamanı gösterimi.</span><span class="sxs-lookup"><span data-stu-id="a547c-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="a547c-284">Çağrı `Regex` Oluşturucusu oluşturur bir <xref:System.ArgumentException> zaman normal bir ifade değil geçerli.</span><span class="sxs-lookup"><span data-stu-id="a547c-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="a547c-285">Derleyici, bu özel durum yakalar ve derleme zamanında ya da Visual Studio düzenleyicisinde bir hata iletisi kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="a547c-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="a547c-286">Bu özel bir uygulamayı çalıştırmadan doğrulanması normal ifadeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="a547c-287">Herhangi bir anlamlı yöntemleri veya özellikleri içermediğinden yukarıda tanımlanan türü henüz yararlı olmaz.</span><span class="sxs-lookup"><span data-stu-id="a547c-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="a547c-288">İlk olarak, statik ekleyin `IsMatch` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a547c-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="a547c-289">Önceki kod yöntemi tanımlar `IsMatch`, hangi giriş olarak bir dize alıp döndüren bir `bool`.</span><span class="sxs-lookup"><span data-stu-id="a547c-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="a547c-290">Kullanımını yalnızca hassas parçasıdır `args` bağımsız değişkeni içinde `InvokeCode` tanımı.</span><span class="sxs-lookup"><span data-stu-id="a547c-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="a547c-291">Bu örnekte, `args` bağımsız değişkenler için bu yöntemi temsil eden bir tırnak işaretleri listesidir.</span><span class="sxs-lookup"><span data-stu-id="a547c-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="a547c-292">Yöntemi bir örnek yöntemi ise, ilk bağımsız değişkeni temsil eden `this` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a547c-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="a547c-293">Ancak, statik bir yöntem için tüm yalnızca açık bağımsız değişkenleri yöntemi için bağımsız değişkenleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a547c-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="a547c-294">Not tırnak işaretli değerin türü belirtilen dönüş türü eşleşmesi gerekir (Bu durumda, `bool`).</span><span class="sxs-lookup"><span data-stu-id="a547c-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="a547c-295">Ayrıca bu kodu kullanır Not `AddXmlDoc` yöntemi sağlanan yöntem IntelliSense sağlayabilir yararlı belgelerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a547c-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="a547c-296">Ardından, bir örnek Match yöntemi ekler.</span><span class="sxs-lookup"><span data-stu-id="a547c-296">Next, add an instance Match method.</span></span> <span data-ttu-id="a547c-297">Ancak, bu yöntem bir sağlanan değerini döndürmelidir `Match` grupları kesin türü belirtilmiş bir biçimde erişilebilir yazın.</span><span class="sxs-lookup"><span data-stu-id="a547c-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="a547c-298">Bu nedenle, ilk bildirdiğiniz `Match` türü.</span><span class="sxs-lookup"><span data-stu-id="a547c-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="a547c-299">Bu tür statik bir bağımsız değişken olarak sağlanan düzeni bağlı olduğundan, bu tür parametreli tür tanımı içinde iç içe gerekir:</span><span class="sxs-lookup"><span data-stu-id="a547c-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy = 
    ProvidedTypeDefinition(
        "MatchType", 
        baseType = Some baseTy, 
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="a547c-300">Her grup için eşleşme türü için bir özellik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a547c-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="a547c-301">Çalışma zamanında bir eşleşme olarak temsil edilen bir <xref:System.Text.RegularExpressions.Match> değer özelliği tanımlar tırnak kullanmalısınız <xref:System.Text.RegularExpressions.Match.Groups> ilgili grup almak için özellik dizini.</span><span class="sxs-lookup"><span data-stu-id="a547c-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="a547c-302">Yeniden sağlanan özelliğine XML belgeleri eklediğiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="a547c-303">Ayrıca bir özellik varsa okunabilir Not bir `GetterCode` işlevi sağlanır ve özelliği, yazılabilir bir `SetterCode` işlevi sağlanır, sonuçta elde edilen özelliği salt okunur şekilde.</span><span class="sxs-lookup"><span data-stu-id="a547c-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="a547c-304">Bu değer döndüren bir örnek yöntemi oluşturabilirsiniz artık `Match` türü:</span><span class="sxs-lookup"><span data-stu-id="a547c-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="a547c-305">Örnek yöntemi, oluşturduğunuz çünkü `args.[0]` temsil eden `RegexTyped` örneği üzerinde yöntemi çağrılır ve `args.[1]` giriş bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a547c-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="a547c-306">Son olarak, belirtilen türdeki örneklerin oluşturulan bir oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor = 
    ProvidedConstructor(
        parameters = [], 
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="a547c-307">Kurucu yalnızca bir nesneye olduğundan yeniden Kutulu standart bir .NET Regex örnek oluşturulmasını siler `obj` silinme sağlanan türünde değil.</span><span class="sxs-lookup"><span data-stu-id="a547c-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="a547c-308">Bu değişiklikle konuda daha önce belirtilen örnek API kullanım beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="a547c-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="a547c-309">Aşağıdaki kod, tam ve son:</span><span class="sxs-lookup"><span data-stu-id="a547c-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="a547c-310">Önemli dersleri</span><span class="sxs-lookup"><span data-stu-id="a547c-310">Key Lessons</span></span>

<span data-ttu-id="a547c-311">Bu bölümde statik parametrelerinin üzerinde çalıştığı bir tür sağlayıcısı oluşturma açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a547c-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="a547c-312">Sağlayıcı statik parametresinin denetler ve onun değere göre işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-312">The provider checks the static parameter and provides operations based on its value.</span></span>


## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="a547c-313">Yerel veri tarafından desteklenen bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a547c-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="a547c-314">Sık yalnızca statik parametreleri aynı zamanda yerel veya uzak sistemlerden bilgi göre API'leri sunmak için tür sağlayıcıları isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="a547c-315">Bu bölümde yerel veri dosyaları gibi yerel verileri esas alan tür sağlayıcıları anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-315">This section discusses type providers that are based on local data, such as local data files.</span></span>


### <a name="simple-csv-file-provider"></a><span data-ttu-id="a547c-316">Basit CSV dosya sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a547c-316">Simple CSV File Provider</span></span>

<span data-ttu-id="a547c-317">Basit bir örnek olarak, tür sağlayıcısı virgülle ayrılmış değer (CSV) biçiminde bilimsel verilerine erişmek için göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a547c-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="a547c-318">Bu bölümde, aşağıdaki tabloda gösterildiği gibi CSV dosyaları kayan nokta verisi tarafından izlenen bir başlık satırı içerdiğini varsayar:</span><span class="sxs-lookup"><span data-stu-id="a547c-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>


|<span data-ttu-id="a547c-319">Uzaklık (ölçer)</span><span class="sxs-lookup"><span data-stu-id="a547c-319">Distance (meter)</span></span>|<span data-ttu-id="a547c-320">Süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="a547c-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="a547c-321">50.0</span><span class="sxs-lookup"><span data-stu-id="a547c-321">50.0</span></span>|<span data-ttu-id="a547c-322">3.7</span><span class="sxs-lookup"><span data-stu-id="a547c-322">3.7</span></span>|
|<span data-ttu-id="a547c-323">100.0</span><span class="sxs-lookup"><span data-stu-id="a547c-323">100.0</span></span>|<span data-ttu-id="a547c-324">5.2</span><span class="sxs-lookup"><span data-stu-id="a547c-324">5.2</span></span>|
|<span data-ttu-id="a547c-325">150.0</span><span class="sxs-lookup"><span data-stu-id="a547c-325">150.0</span></span>|<span data-ttu-id="a547c-326">6.4</span><span class="sxs-lookup"><span data-stu-id="a547c-326">6.4</span></span>|

<span data-ttu-id="a547c-327">Bu bölümde satırlarla almak için kullanabileceğiniz bir türü sağlamak nasıl gösterilmiştir bir `Distance` türündeki özelliği `float<meter>` ve `Time` türündeki özelliği `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="a547c-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="a547c-328">Kolaylık olması için aşağıdaki varsayımlar oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="a547c-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="a547c-329">Üstbilgi adlardır ya da birimi daha az veya "Ad (birim)" biçiminde olması ve virgül hiçbirini içeremez.</span><span class="sxs-lookup"><span data-stu-id="a547c-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="a547c-330">Birimleridir tüm Systeme uluslararası (SI) birimi olarak [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Modülü (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modülü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-330">Units are all Systeme International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="a547c-331">Tüm basit birimler (örneğin, ölçüm) bileşik (örneğin, ölçüm/saniye) yerine.</span><span class="sxs-lookup"><span data-stu-id="a547c-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="a547c-332">Kayan nokta verisi tüm sütunları içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a547c-332">All columns contain floating point data.</span></span>

<span data-ttu-id="a547c-333">Daha eksiksiz bir sağlayıcı, bu kısıtlamalar çözmek.</span><span class="sxs-lookup"><span data-stu-id="a547c-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="a547c-334">Yeniden ilk API nasıl görünmelidir dikkate alınması gereken adımdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="a547c-335">Verilen bir `info.csv` dosyası (biçiminde virgülle ayrılmış) önceki tablosundan içerikle sağlayıcısının kullanıcıların aşağıdaki örneğe benzer bir kod yazın gerekir:</span><span class="sxs-lookup"><span data-stu-id="a547c-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="a547c-336">Bu durumda, derleyici bu çağrıları aşağıdaki örneğe benzer bir şey dönüştürmeniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="a547c-337">En iyi çeviri gerçek tanımlamak tür sağlayıcısı gerektirir `CsvFile` türü sağlayıcının derlemesindeki türü.</span><span class="sxs-lookup"><span data-stu-id="a547c-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="a547c-338">Tür sağlayıcıları genellikle birkaç yardımcı türleri ve yöntemleri üzerinde önemli mantığı sarmalamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="a547c-339">Ölçüleri çalışma zamanında silebilmeniz için kullanabileceğiniz bir `float[]` bir satır için silinen türü.</span><span class="sxs-lookup"><span data-stu-id="a547c-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="a547c-340">Derleyici, farklı sütunlardan farklı ölçü türlerine sahip olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a547c-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="a547c-341">Örneğin, ilk sütunun örneğimizde türüne sahip `float<meter>`, ve ikinci olan `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="a547c-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="a547c-342">Ancak, silinen gösterimi oldukça basit kalabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="a547c-343">Aşağıdaki kod uygulama çekirdek gösterir.</span><span class="sxs-lookup"><span data-stu-id="a547c-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="a547c-344">Uygulanmasıyla ilgili aşağıdaki noktalara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="a547c-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="a547c-345">Aşırı yüklenmiş Oluşturucular, özgün dosya veya okumak için özdeş bir şema içeren izin verin.</span><span class="sxs-lookup"><span data-stu-id="a547c-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="a547c-346">Bu deseni, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazma ve bu deseni için Uzak Veri şablon olarak kullanılacak yerel bir dosyaya verir yaygındır.</span><span class="sxs-lookup"><span data-stu-id="a547c-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="a547c-347">Kullanabileceğiniz [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) göreli dosya adları çözümlemek için türü sağlayıcısı oluşturucuya geçirilen değer.</span><span class="sxs-lookup"><span data-stu-id="a547c-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="a547c-348">Kullanabileceğiniz `AddDefinitionLocation` sağlanan özellikler konumunu tanımlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="a547c-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="a547c-349">Bu nedenle, kullanırsanız `Go To Definition` sağlanan bir özellik, CSV dosyasını Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="a547c-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="a547c-350">Kullanabileceğiniz `ProvidedMeasureBuilder` türü SI birimler aramak için ve ilgili oluşturmak için `float<_>` türleri.</span><span class="sxs-lookup"><span data-stu-id="a547c-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="a547c-351">Önemli dersleri</span><span class="sxs-lookup"><span data-stu-id="a547c-351">Key Lessons</span></span>

<span data-ttu-id="a547c-352">Bu bölüm veri kaynağındaki kendisini içeren basit bir şema ile yerel bir veri kaynağı için tür sağlayıcısı oluşturma açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a547c-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>


## <a name="going-further"></a><span data-ttu-id="a547c-353">Daha fazla işlenmesini</span><span class="sxs-lookup"><span data-stu-id="a547c-353">Going Further</span></span>

<span data-ttu-id="a547c-354">Aşağıdaki bölümlerde daha ayrıntılı incelemesi için öneriler içerir.</span><span class="sxs-lookup"><span data-stu-id="a547c-354">The following sections include suggestions for further study.</span></span>


### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="a547c-355">Silinen türleri için derlenmiş kod bakma</span><span class="sxs-lookup"><span data-stu-id="a547c-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="a547c-356">Ne tür sağlayıcısı kullanımını yayılan koduna karşılık gelen bazı fikir vermek için aşağıdaki işlevini kullanarak araması `HelloWorldTypeProvider` bu konunun önceki kısımlarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a547c-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () = 
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="a547c-357">Görüntüyü ildasm.exe kullanarak decompiled sonuç kodunun şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a547c-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="a547c-358">Türündeki tüm belirtilenlerden örnekte gösterildiği gibi `Type1` ve `InstanceProperty` özelliği silinmesi, yalnızca çalışma zamanı türleri üzerinde işlem söz konusu çıkılıyor.</span><span class="sxs-lookup"><span data-stu-id="a547c-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>


### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="a547c-359">Tasarım ve tür sağlayıcıları için adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="a547c-359">Design and Naming Conventions for Type Providers</span></span>
<span data-ttu-id="a547c-360">Tür sağlayıcıları yazarken aşağıdaki kuralları inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a547c-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="a547c-361">**Bağlantı protokolleri için sağlayıcıları** veri ve hizmet bağlantısı gibi protokoller için OData veya SQL bağlantıları, çoğu Sağlayıcı DLL adları genel olarak, bitmelidir `TypeProvider` veya `TypeProviders`.</span><span class="sxs-lookup"><span data-stu-id="a547c-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="a547c-362">Örneğin, aşağıdaki dize şuna benzer bir DLL adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="a547c-362">For example, use a DLL name that resembles the following string:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.dll
```

<span data-ttu-id="a547c-363">Sağlanan türleri karşılık gelen ad alanı üyesi olan ve sizin uygulanan bağlantı protokolü belirtmek emin olun:</span><span class="sxs-lookup"><span data-stu-id="a547c-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="a547c-364">**Genel kodlamak için yardımcı programı sağlayıcıları**.</span><span class="sxs-lookup"><span data-stu-id="a547c-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="a547c-365">Yardımcı programı tür sağlayıcısı için gibi normal ifadeler için tür sağlayıcısı aşağıdaki örnekte gösterildiği gibi bir temel kitaplığı parçası olabilir:</span><span class="sxs-lookup"><span data-stu-id="a547c-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="a547c-366">Bu durumda, sağlanan türü normal .NET tasarım kurallarına göre uygun bir noktada görünür:</span><span class="sxs-lookup"><span data-stu-id="a547c-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="a547c-367">**Singleton veri kaynaklarını**.</span><span class="sxs-lookup"><span data-stu-id="a547c-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="a547c-368">Bazı tür sağlayıcıları bir tek bir adanmış veri kaynağına bağlanmak ve yalnızca veriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="a547c-369">Bu durumda bırak `TypeProvider` sonek ve .NET adlandırma için normal kuralları kullanın:</span><span class="sxs-lookup"><span data-stu-id="a547c-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"
  
let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="a547c-370">Daha fazla bilgi için bkz: `GetConnection` tasarım bu konunun ilerleyen bölümlerinde açıklanan kuralı.</span><span class="sxs-lookup"><span data-stu-id="a547c-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>


### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="a547c-371">Tür sağlayıcıları için Tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="a547c-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="a547c-372">Aşağıdaki bölümlerde tasarım desenleri tür sağlayıcıları yazarken kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a547c-372">The following sections describe design patterns you can use when authoring type providers.</span></span>


#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="a547c-373">GetConnection tasarım deseni</span><span class="sxs-lookup"><span data-stu-id="a547c-373">The GetConnection Design Pattern</span></span>
<span data-ttu-id="a547c-374">Çoğu tür sağlayıcılarını kullanacak şekilde yazılıp `GetConnection` aşağıdaki örnekte gösterildiği gibi FSharp.Data.TypeProviders.dll, türü sağlayıcıları tarafından kullanılan deseni:</span><span class="sxs-lookup"><span data-stu-id="a547c-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="a547c-375">Uzak Veri ve hizmetler tarafından desteklenen tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a547c-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="a547c-376">Uzak Veri ve hizmetler tarafından desteklenen bir tür sağlayıcısı oluşturmadan önce bir dizi bağlı programlamada devredilen sorunları dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="a547c-377">Bu sorunları aşağıdaki konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="a547c-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="a547c-378">Şema eşleme</span><span class="sxs-lookup"><span data-stu-id="a547c-378">schema mapping</span></span>

- <span data-ttu-id="a547c-379">liveness ve şema değişikliği varlığında geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a547c-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="a547c-380">Şema önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="a547c-380">schema caching</span></span>

- <span data-ttu-id="a547c-381">Veri erişim işlemleri zaman uyumsuz uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a547c-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="a547c-382">LINQ sorguları da dahil, sorguların destekleme</span><span class="sxs-lookup"><span data-stu-id="a547c-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="a547c-383">kimlik bilgileri ve kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="a547c-383">credentials and authentication</span></span>

<span data-ttu-id="a547c-384">Bu konu, bu sorunlar daha fazla keşfedin değil.</span><span class="sxs-lookup"><span data-stu-id="a547c-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="a547c-385">Ek yazma teknikleri</span><span class="sxs-lookup"><span data-stu-id="a547c-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="a547c-386">Kendi tür sağlayıcıları yazdığınızda, aşağıdaki ek teknikler kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="a547c-387">Türleri ve üyeleri isteğe bağlı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a547c-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="a547c-388">ProvidedType API AddMember sürümleri Gecikmeli.</span><span class="sxs-lookup"><span data-stu-id="a547c-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="a547c-389">Bu sürümleri, isteğe bağlı alanları türleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a547c-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="a547c-390">Dizi türleri ve genel türü örneklemesi sağlama</span><span class="sxs-lookup"><span data-stu-id="a547c-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="a547c-391">Normal kullanarak (dizi türleri, byref türleri ve genel türler işlemlerinden içerir, imzalar) sağlanan üyeleri yaptığınız `MakeArrayType`, `MakePointerType`, ve `MakeGenericType` herhangi bir örneğinin üzerinde <xref:System.Type>gibi `ProvidedTypeDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="a547c-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="a547c-392">Bazı durumlarda yardımcı kullanmak zorunda kalabilirsiniz `ProvidedTypeBuilder.MakeGenericType`.</span><span class="sxs-lookup"><span data-stu-id="a547c-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="a547c-393">Bkz: [türü sağlayıcısı SDK Belgeleri](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="a547c-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="a547c-394">Ölçüm açıklamalarının birim sağlama</span><span class="sxs-lookup"><span data-stu-id="a547c-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="a547c-395">ProvidedTypes API ölçü ek açıklamaları sağlayan Yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a547c-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="a547c-396">Örneğin, türü sağlamak için `float<kg>`, aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a547c-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="a547c-397">Türü sağlamak için `Nullable<decimal<kg/m^2>>`, aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a547c-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="a547c-398">Proje-yerel veya komut dosyası yerel kaynaklara erişme</span><span class="sxs-lookup"><span data-stu-id="a547c-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="a547c-399">Her tür sağlayıcısı örneği verilen bir `TypeProviderConfig` oluşturma sırasında değeri.</span><span class="sxs-lookup"><span data-stu-id="a547c-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="a547c-400">Bu değer "Çözümleme klasörü" sağlayıcısı (diğer bir deyişle, derleme veya bir komut dosyası içeren dizin için proje klasör), başvurulan bir derleme listesi ve diğer bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a547c-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="a547c-401">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a547c-401">Invalidation</span></span>

<span data-ttu-id="a547c-402">Sağlayıcıları şema varsayımlar değişmiş olabilir F # dili hizmet bildirmek için geçersiz kılma sinyalleri yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="a547c-403">Geçersiz kılma ortaya çıktığında, sağlayıcı Visual Studio'da barındırılıyorsa bir typecheck alınabilir.</span><span class="sxs-lookup"><span data-stu-id="a547c-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="a547c-404">Bu sinyal sağlayıcısı F # Etkileşimli veya F # derleyici (fsc.exe) tarafından barındırıldığında yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="a547c-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="a547c-405">Şema bilgileri önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="a547c-405">Caching Schema Information</span></span>

<span data-ttu-id="a547c-406">Sağlayıcılar genellikle şema bilgilere erişimi önbelleğe gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="a547c-407">Statik bir parametre veya kullanıcı verisi olarak verilen bir dosya adı kullanarak önbelleğe alınan verilerin depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="a547c-408">Şema önbelleğe alma, bir örnek verilmiştir `LocalSchemaFile` türü sağlayıcıları parametresinde `FSharp.Data.TypeProviders` derleme.</span><span class="sxs-lookup"><span data-stu-id="a547c-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="a547c-409">Bu sağlayıcılar uygulamasında statik Bu parametre ağ üzerinden veri kaynağına erişme yerine belirtilen yerel dosyasında şema bilgileri kullanmak için tür sağlayıcısı yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="a547c-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="a547c-410">Önbelleğe alınan şema bilgileri kullanmak için de statik parametresinin ayarlamalısınız `ForceUpdate` için `false`.</span><span class="sxs-lookup"><span data-stu-id="a547c-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="a547c-411">Çevrimiçi ve çevrimdışı veri erişimi etkinleştirmek için benzer bir tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="a547c-412">Derleme yedekleme</span><span class="sxs-lookup"><span data-stu-id="a547c-412">Backing Assembly</span></span>

<span data-ttu-id="a547c-413">Olduğunda, derleme bir `.dll` veya `.exe` dosyası, yedekleme .dll dosyası oluşturulan türleri statik olarak bağlı elde edilen derlemeye.</span><span class="sxs-lookup"><span data-stu-id="a547c-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="a547c-414">Bu bağlantı, Ara dile (IL) tür tanımları ve yönetilen kaynakları son derlemeyi yedekleme derlemeye kopyalayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a547c-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="a547c-415">F # Etkileşimli kullandığınızda, yedekleme .dll dosyasını kopyaladığınız değil ve bunun yerine doğrudan F # Etkileşimli işlemine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="a547c-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="a547c-416">Özel durum ve tanılama tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a547c-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="a547c-417">Sağlanan türleri tüm üyelerinden tüm kullanımlarını özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a547c-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="a547c-418">Tür sağlayıcısı bir özel durum oluşturursa tüm durumlarda belirli tür sağlayıcısı için hata konak derleyici öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a547c-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="a547c-419">Özel durumlar hiçbir zaman iç derleyici hatalarına neden sağlayıcı yazın.</span><span class="sxs-lookup"><span data-stu-id="a547c-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="a547c-420">Tür sağlayıcıları uyarıları raporlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a547c-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="a547c-421">Tür sağlayıcısı F # derleyici, F # geliştirme ortamı ya da F # Etkileşimli içinde barındırıldığında, bu sağlayıcısından tüm özel durumları yakalanır.</span><span class="sxs-lookup"><span data-stu-id="a547c-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="a547c-422">İleti özelliği her zaman hata metindir ve hiçbir yığın izlemesi görünür.</span><span class="sxs-lookup"><span data-stu-id="a547c-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="a547c-423">Bir özel durum kullanacaksanız, aşağıdaki örneklerde atabilirsiniz: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="a547c-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="a547c-424">Oluşturulan türler sağlar</span><span class="sxs-lookup"><span data-stu-id="a547c-424">Providing Generated Types</span></span>

<span data-ttu-id="a547c-425">Şu ana kadar bu belgede silinen türleri sağlamak nasıl açıklandığı.</span><span class="sxs-lookup"><span data-stu-id="a547c-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="a547c-426">Ayrıca türü sağlayıcısı mekanizması F #'de kullanıcıların programa gerçek .NET türü tanımları olarak eklenen oluşturulan türleri sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="a547c-427">Sizin için oluşturulan türleri bir tür tanımı kullanılarak sağlanan başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="a547c-428">F # 3.0 sürümünün bir parçası olan ProvidedTypes 0.2 yardımcı kod yalnızca oluşturulan türleri sağlamak için destek sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="a547c-429">Aşağıdaki deyimleri için oluşturulan tür tanımı doğru olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="a547c-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="a547c-430">`isErased` ayarlanmalıdır `false`.</span><span class="sxs-lookup"><span data-stu-id="a547c-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="a547c-431">Oluşturulan tür eklenmelidir yeni oluşturulan için `ProvidedAssembly()`, oluşturulan kod parçaları için bir kapsayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a547c-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="a547c-432">Sağlayıcı gerçek destekleyen .NET .dll dosyasının disk üzerinde eşleşen bir .dll dosyası ile bir derlemeyi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>


## <a name="rules-and-limitations"></a><span data-ttu-id="a547c-433">Kurallar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="a547c-433">Rules and Limitations</span></span>

<span data-ttu-id="a547c-434">Tür sağlayıcıları yazdığınızda, aşağıdaki kurallar ve sınırlamalar göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a547c-434">When you write type providers, keep the following rules and limitations in mind.</span></span>


### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="a547c-435">Sağlanan türleri erişilebilir olması gerekir</span><span class="sxs-lookup"><span data-stu-id="a547c-435">Provided types must be reachable</span></span>

<span data-ttu-id="a547c-436">Tüm girildi. türleri iç içe olmayan türlerinden erişilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a547c-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="a547c-437">İç içe olmayan türleri çağrısında verilir `TypeProviderForNamespaces` Oluşturucusu veya yapılan bir çağrı `AddNamespace`.</span><span class="sxs-lookup"><span data-stu-id="a547c-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="a547c-438">Örneğin, bir tür sağlayıcısı sağlarsa, `StaticClass.P : T`, T yuvalanmış olmayan bir tür veya iç içe geçmiş altında bir olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="a547c-439">Örneğin, bazı sağlayıcılar gibi statik sınıf sahip `DataTypes` bu içeren `T1, T2, T3, ...` türleri.</span><span class="sxs-lookup"><span data-stu-id="a547c-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="a547c-440">Aksi halde, bir derlemede T türü bir başvuru bulundu, ancak bu derleme içinde tür bulunamadı hata söyler.</span><span class="sxs-lookup"><span data-stu-id="a547c-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="a547c-441">Bu hata varsa, tüm alt sağlayıcı türlerinden erişilebildiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="a547c-442">Not: Bu `T1, T2, T3...` türleri denir *üzerinde-çalışma sırasında* türleri.</span><span class="sxs-lookup"><span data-stu-id="a547c-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="a547c-443">Erişilebilir bir ad alanı veya bir üst tür koyabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="a547c-444">Türü sağlayıcısı mekanizması sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="a547c-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="a547c-445">F # tür sağlayıcısı mekanizması aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a547c-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="a547c-446">Genel türleri veya genel yöntemler sağlanan sağlanan F # tür sağlayıcıları için temel altyapıyı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a547c-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="a547c-447">Mekanizması statik parametrelerle iç içe geçmiş türler desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a547c-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="a547c-448">Geliştirme İpuçları</span><span class="sxs-lookup"><span data-stu-id="a547c-448">Development Tips</span></span>

<span data-ttu-id="a547c-449">Aşağıdaki ipuçları geliştirme sürecinde yararlı.</span><span class="sxs-lookup"><span data-stu-id="a547c-449">You might find the following tips helpful during the development process.</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="a547c-450">Visual Studio iki örneklerinde Çalıştır</span><span class="sxs-lookup"><span data-stu-id="a547c-450">Run Two Instances of Visual Studio</span></span>

<span data-ttu-id="a547c-451">Tür sağlayıcısı bir örneğinde geliştirmek ve test IDE yeniden oluşturulan tür sağlayıcısı engeller .dll dosyası üzerinde bir kilit sürer çünkü sağlayıcıyı diğer sınayın.</span><span class="sxs-lookup"><span data-stu-id="a547c-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="a547c-452">Bu nedenle, Visual Studio ikinci bir örneğini sağlayıcı ilk örnekte yerleşik olarak bulunur ve daha sonra sağlayıcının oluşturulduktan sonra ikinci örneği yeniden açmanız gerekir kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a547c-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="a547c-453">Tür sağlayıcıları fsc.exe çağrılarını kullanarak hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a547c-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="a547c-454">Tür sağlayıcıları aşağıdaki araçları kullanarak çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a547c-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="a547c-455">fsc.exe (F # komut satırı derleyicisi)</span><span class="sxs-lookup"><span data-stu-id="a547c-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="a547c-456">fsi.exe (F # Etkileşimli derleyicisi)</span><span class="sxs-lookup"><span data-stu-id="a547c-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="a547c-457">devenv.exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="a547c-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="a547c-458">Tür sağlayıcıları test betiği (örneğin, script.fsx) üzerinde fsc.exe kullanarak, en kolay genellikle ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="a547c-459">Hata ayıklayıcı komut isteminden başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-459">You can launch a debugger from a command prompt.</span></span>

```
  devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="a547c-460">Yazdırma stdout günlüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a547c-460">You can use print-to-stdout logging.</span></span>


## <a name="see-also"></a><span data-ttu-id="a547c-461">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a547c-461">See Also</span></span>

* [<span data-ttu-id="a547c-462">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="a547c-462">Type Providers</span></span>](index.md)

* [<span data-ttu-id="a547c-463">SDK türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a547c-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)

