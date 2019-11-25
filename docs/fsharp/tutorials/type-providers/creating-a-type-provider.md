---
title: 'Öğretici: tür sağlayıcısı oluşturma'
description: Temel kavramları göstermek üzere çeşitli basit F# tür sağlayıcılarını inceleyerek F# 3,0 'de kendi tür sağlayıcılarınızı oluşturmayı öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 8df893669b8ee04bad366dbe42a55c83d1f5a8fe
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968366"
---
# <a name="tutorial-create-a-type-provider"></a><span data-ttu-id="c5a1b-103">Öğretici: tür sağlayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5a1b-103">Tutorial: Create a Type Provider</span></span>

<span data-ttu-id="c5a1b-104">İçindeki F# tür sağlayıcısı mekanizması, bilgi zengin programlama desteğinin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-104">The type provider mechanism in F# is a significant part of its support for information rich programming.</span></span> <span data-ttu-id="c5a1b-105">Bu öğreticide, temel kavramları göstermek için çeşitli basit tür sağlayıcılarının geliştirilmesi sırasında kendi tür sağlayıcılarınızın nasıl oluşturulduğu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-105">This tutorial explains how to create your own type providers by walking you through the development of several simple type providers to illustrate the basic concepts.</span></span> <span data-ttu-id="c5a1b-106">İçindeki F#tür sağlayıcısı mekanizması hakkında daha fazla bilgi için bkz. [tür sağlayıcıları](index.md).</span><span class="sxs-lookup"><span data-stu-id="c5a1b-106">For more information about the type provider mechanism in F#, see [Type Providers](index.md).</span></span>

<span data-ttu-id="c5a1b-107">Ekosistem, F# yaygın olarak kullanılan Internet ve kurumsal veri Hizmetleri için bir dizi tür sağlayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-107">The F# ecosystem contains a range of type providers for commonly used Internet and enterprise data services.</span></span> <span data-ttu-id="c5a1b-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-108">For example:</span></span>

- <span data-ttu-id="c5a1b-109">[FSharp. Data](https://fsharp.github.io/FSharp.Data/) , JSON, XML, CSV ve HTML belge biçimleri için tür sağlayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-109">[FSharp.Data](https://fsharp.github.io/FSharp.Data/) includes type providers for JSON, XML, CSV and HTML document formats.</span></span>

- <span data-ttu-id="c5a1b-110">[SqlProvider](https://fsprojects.github.io/SQLProvider/) , bu veri kaynaklarında bir nesne eşlemesi ve F# LINQ sorguları aracılığıyla SQL veritabanlarına kesin olarak yazılmış erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-110">[SQLProvider](https://fsprojects.github.io/SQLProvider/) provides strongly-typed access to SQL databases through a object mapping and F# LINQ queries against these data sources.</span></span>

- <span data-ttu-id="c5a1b-111">[FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) , içindeki T-SQL ' F#y i, derleme zamanında denetlenmiş ekleme için bir dizi tür sağlayıcıya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-111">[FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) has a set of type providers for compile-time checked embedding of T-SQL in F#.</span></span>

- <span data-ttu-id="c5a1b-112">[FSharp. Data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) , yalnızca SQL, Entity Framework, OData ve wsdl veri hizmetlerine erişim için .NET Framework programlamayla birlikte kullanılmak üzere daha eski bir tür sağlayıcıları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-112">[FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) is an older set of type providers for use only with .NET Framework programming for accessing SQL, Entity Framework, OData and WSDL data services.</span></span>

<span data-ttu-id="c5a1b-113">Gerektiğinde, özel tür sağlayıcıları oluşturabilir veya diğerlerinin oluşturduğu tür sağlayıcılarına başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-113">Where necessary, you can create custom type providers, or you can reference type providers that others have created.</span></span> <span data-ttu-id="c5a1b-114">Örneğin, kuruluşunuz her biri kendi kararlı veri şemasına sahip büyük ve artan sayıda adlandırılmış veri kümesi sağlayan bir veri hizmetine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-114">For example, your organization could have a data service that provides a large and growing number of named data sets, each with its own stable data schema.</span></span> <span data-ttu-id="c5a1b-115">Şemaları okuyan ve geçerli veri kümelerini programcıya kesin olarak belirlenmiş bir şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-115">You can create a type provider that reads the schemas and presents the current data sets to the programmer in a strongly typed way.</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c5a1b-116">Başlamadan önce</span><span class="sxs-lookup"><span data-stu-id="c5a1b-116">Before You Start</span></span>

<span data-ttu-id="c5a1b-117">Tür sağlayıcısı mekanizması öncelikle F# programlama deneyimine ekleme kararlı veriler ve hizmet bilgileri alanları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-117">The type provider mechanism is primarily designed for injecting stable data and service information spaces into the F# programming experience.</span></span>

<span data-ttu-id="c5a1b-118">Bu mekanizma, program yürütmesi sırasında, program mantığıyla ilgili şekilde, şema değişiklikleri olan ekleme bilgi alanları için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-118">This mechanism isn’t designed for injecting information spaces whose schema changes during program execution in ways that are relevant to program logic.</span></span> <span data-ttu-id="c5a1b-119">Ayrıca, bu etki alanı geçerli kullanımlar içerse de mekanizma, dil içi meta programlama için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-119">Also, the mechanism isn't designed for intra-language meta-programming, even though that domain contains some valid uses.</span></span> <span data-ttu-id="c5a1b-120">Bu mekanizmayı yalnızca gerektiğinde ve bir tür sağlayıcının geliştirilmesi çok yüksek değer veren bir şekilde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-120">You should use this mechanism only where necessary and where the development of a type provider yields very high value.</span></span>

<span data-ttu-id="c5a1b-121">Bir şemanın kullanılamadığı bir tür sağlayıcısı yazmadan kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-121">You should avoid writing a type provider where a schema isn't available.</span></span> <span data-ttu-id="c5a1b-122">Benzer şekilde, normal (veya hatta var olan) bir .NET kitaplığının yeterli olacağı bir tür sağlayıcısını yazmadan kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-122">Likewise, you should avoid writing a type provider where an ordinary (or even an existing) .NET library would suffice.</span></span>

<span data-ttu-id="c5a1b-123">Başlamadan önce aşağıdaki soruları sorabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-123">Before you start, you might ask the following questions:</span></span>

- <span data-ttu-id="c5a1b-124">Bilgi kaynağınız için bir şemanız mı var?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-124">Do you have a schema for your information source?</span></span> <span data-ttu-id="c5a1b-125">Bu durumda, F# ve .net tür sistemine ne eşleme yapılır?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-125">If so, what’s the mapping into the F# and .NET type system?</span></span>

- <span data-ttu-id="c5a1b-126">Uygulamanız için bir başlangıç noktası olarak var olan (dinamik olarak yazılmış) bir API kullanabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-126">Can you use an existing (dynamically typed) API as a starting point for your implementation?</span></span>

- <span data-ttu-id="c5a1b-127">Siz ve kuruluşunuz, yazma sağlayıcısını bir süre sonra yazmak için yeterli sayıda kullanımlarına sahip olacak mı?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-127">Will you and your organization have enough uses of the type provider to make writing it worthwhile?</span></span> <span data-ttu-id="c5a1b-128">Normal bir .NET kitaplığı gereksinimlerinizi karşılayacak mı?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-128">Would a normal .NET library meet your needs?</span></span>

- <span data-ttu-id="c5a1b-129">Şemanız ne kadar değişir?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-129">How much will your schema change?</span></span>

- <span data-ttu-id="c5a1b-130">Kodlama sırasında değişsin mi?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-130">Will it change during coding?</span></span>

- <span data-ttu-id="c5a1b-131">Kodlama oturumları arasında değişiklik olacak mı?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-131">Will it change between coding sessions?</span></span>

- <span data-ttu-id="c5a1b-132">Program yürütme sırasında değişsin mi?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-132">Will it change during program execution?</span></span>

<span data-ttu-id="c5a1b-133">Tür sağlayıcıları, şemanın çalışma zamanında ve derlenmiş kodun kullanım ömrü boyunca tutarlı olduğu durumlara en iyi şekilde uygundur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-133">Type providers are best suited to situations where the schema is stable at runtime and during the lifetime of compiled code.</span></span>

## <a name="a-simple-type-provider"></a><span data-ttu-id="c5a1b-134">Basit tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c5a1b-134">A Simple Type Provider</span></span>

<span data-ttu-id="c5a1b-135">Bu örnek, [ F# tür sağlayıcısı SDK 'sının](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)`examples` dizinindeki örneklere benzer şekilde Samples. HelloWorldTypeProvider ' dır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-135">This sample is Samples.HelloWorldTypeProvider, similar to the samples in the `examples` directory of the [F# Type Provider SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/).</span></span> <span data-ttu-id="c5a1b-136">Aşağıdaki kod, imza söz dizimini kullanarak F# ve `Type1`hariç tüm ayrıntıları atlayarak, sağlayıcı 100 silinen türler içeren bir "tür alanı" kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-136">The provider makes available a "type space" that contains 100 erased types, as the following code shows by using F# signature syntax and omitting the details for all except `Type1`.</span></span> <span data-ttu-id="c5a1b-137">Silinen türler hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [silinen sağlanmış türler hakkındaki ayrıntılara](#details-about-erased-provided-types) bakın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-137">For more information about erased types, see [Details About Erased Provided Types](#details-about-erased-provided-types) later in this topic.</span></span>

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

<span data-ttu-id="c5a1b-138">Belirtilen tür ve üyelerin kümesinin statik olarak bilindiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-138">Note that the set of types and members provided is statically known.</span></span> <span data-ttu-id="c5a1b-139">Bu örnek, sağlayıcıların bir şemaya bağlı olan türleri sağlama özelliğinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-139">This example doesn't leverage the ability of providers to provide types that depend on a schema.</span></span> <span data-ttu-id="c5a1b-140">Tür sağlayıcısı 'nın uygulanması aşağıdaki kodda özetlenmiştir ve Ayrıntılar bu konunun sonraki bölümlerinde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-140">The implementation of the type provider is outlined in the following code, and the details are covered in later sections of this topic.</span></span>

> [!WARNING]
> <span data-ttu-id="c5a1b-141">Bu kod ile çevrimiçi örnekler arasında farklılıklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-141">There may be differences between this code and the online samples.</span></span>

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

<span data-ttu-id="c5a1b-142">Bu sağlayıcıyı kullanmak için, Visual Studio 'nun ayrı bir örneğini açın, bir F# betik oluşturun ve ardından aşağıdaki kodun gösterdiği gibi #r kullanarak betiğinizden sağlayıcıya bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-142">To use this provider, open a separate instance of Visual Studio, create an F# script, and then add a reference to the provider from your script by using #r as the following code shows:</span></span>

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

<span data-ttu-id="c5a1b-143">Daha sonra tür sağlayıcısının oluşturduğu `Samples.HelloWorldTypeProvider` ad alanı altındaki türleri arayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-143">Then look for the types under the `Samples.HelloWorldTypeProvider` namespace that the type provider generated.</span></span>

<span data-ttu-id="c5a1b-144">Sağlayıcıyı yeniden yapılandırmadan önce, sağlayıcı DLL 'yi kullanan tüm Visual Studio ve F# etkileşimli örneklerini kapattığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-144">Before you recompile the provider, make sure that you have closed all instances of Visual Studio and F# Interactive that are using the provider DLL.</span></span> <span data-ttu-id="c5a1b-145">Aksi takdirde, çıkış DLL 'SI kilitlendiğinden bir yapı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-145">Otherwise, a build error will occur because the output DLL will be locked.</span></span>

<span data-ttu-id="c5a1b-146">Print deyimlerini kullanarak bu sağlayıcıda hata ayıklamak için, sağlayıcıda bir sorun ortaya çıkaran bir betik oluşturun ve ardından aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-146">To debug this provider by using print statements, make a script that exposes a problem with the provider, and then use the following code:</span></span>

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="c5a1b-147">Visual Studio 'yu kullanarak bu sağlayıcıda hata ayıklamak için, Visual Studio Geliştirici Komut İstemi yönetici kimlik bilgileriyle açın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-147">To debug this provider by using Visual Studio, open the Developer Command Prompt for Visual Studio with administrative credentials, and run the following command:</span></span>

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

<span data-ttu-id="c5a1b-148">Alternatif olarak, Visual Studio 'yu açın, hata ayıkla menüsünü açın, `Debug/Attach to process…`seçin ve komut dosyanızı düzenlemekte olduğunuz başka bir `devenv` işlemine iliştirin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-148">As an alternative, open Visual Studio, open the Debug menu, choose `Debug/Attach to process…`, and attach to another `devenv` process where you’re editing your script.</span></span> <span data-ttu-id="c5a1b-149">Bu yöntemi kullanarak, ikinci örneğe (tam IntelliSense ve diğer özelliklerle) kolayca ifade yazarak tür sağlayıcıda belirli mantığı daha kolay bir şekilde hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-149">By using this method, you can more easily target particular logic in the type provider by interactively typing expressions into the second instance (with full IntelliSense and other features).</span></span>

<span data-ttu-id="c5a1b-150">Oluşturulan koddaki hataları daha iyi tanımlamak için Yalnızca kendi kodum hata ayıklamayı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-150">You can disable Just My Code debugging to better identify errors in generated code.</span></span> <span data-ttu-id="c5a1b-151">Bu özelliğin nasıl etkinleştirileceği veya devre dışı bırakılacağı hakkında bilgi için bkz. [hata ayıklayıcıyla kod aracılığıyla gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span><span class="sxs-lookup"><span data-stu-id="c5a1b-151">For information about how to enable or disable this feature, see [Navigating through Code with the Debugger](/visualstudio/debugger/navigating-through-code-with-the-debugger).</span></span> <span data-ttu-id="c5a1b-152">Ayrıca, `Debug` menüsünü açıp `Exceptions` ' i seçerek veya Ctrl + Alt + E tuşlarını seçerek `Exceptions` iletişim kutusunu açmak için birinci şans özel durum yakalama 'yı da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-152">Also, you can also set first-chance exception catching by opening the `Debug` menu and then choosing `Exceptions` or by choosing the Ctrl+Alt+E keys to open the `Exceptions` dialog box.</span></span> <span data-ttu-id="c5a1b-153">Bu iletişim kutusunda, `Common Language Runtime Exceptions`altında `Thrown` onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-153">In that dialog box, under `Common Language Runtime Exceptions`, select the `Thrown` check box.</span></span>

### <a name="implementation-of-the-type-provider"></a><span data-ttu-id="c5a1b-154">Tür sağlayıcısı 'nın uygulanması</span><span class="sxs-lookup"><span data-stu-id="c5a1b-154">Implementation of the Type Provider</span></span>

<span data-ttu-id="c5a1b-155">Bu bölümde, tür sağlayıcısı uygulamasının asıl bölümlerinde adım adım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-155">This section walks you through the principal sections of the type provider implementation.</span></span> <span data-ttu-id="c5a1b-156">İlk olarak, türü özel tür sağlayıcının kendisi için tanımlarsınız:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-156">First, you define the type for the custom type provider itself:</span></span>

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

<span data-ttu-id="c5a1b-157">Bu tür ortak olmalıdır ve bu türü [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) özniteliğiyle işaretlemeniz gerekir; böylece derleyici tür sağlayıcısını, ayrı F# bir proje türü içeren derlemeye başvurduğunda tür sağlayıcısını tanıyacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-157">This type must be public, and you must mark it with the [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) attribute so that the compiler will recognize the type provider when a separate F# project references the assembly that contains the type.</span></span> <span data-ttu-id="c5a1b-158">*Yapılandırma* parametresi isteğe bağlıdır ve varsa, F# derleyicinin oluşturduğu tür sağlayıcısı örneği için bağlamsal yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-158">The *config* parameter is optional, and, if present, contains contextual configuration information for the type provider instance that the F# compiler creates.</span></span>

<span data-ttu-id="c5a1b-159">Daha sonra, [ITypeInfo arabirimini Uygularınızda](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) .</span><span class="sxs-lookup"><span data-stu-id="c5a1b-159">Next, you implement the [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) interface.</span></span> <span data-ttu-id="c5a1b-160">Bu durumda, `ProvidedTypes` API 'sindeki `TypeProviderForNamespaces` türünü temel tür olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-160">In this case, you use the `TypeProviderForNamespaces` type from the `ProvidedTypes` API as a base type.</span></span> <span data-ttu-id="c5a1b-161">Bu yardımcı türü, her biri doğrudan sınırlı sayıda sabit, ekip tarafından sağlanmış tür içeren bir dizi sağlanmış ad alanı için sınırlı bir koleksiyon sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-161">This helper type can provide a finite collection of eagerly provided namespaces, each of which directly contains a finite number of fixed, eagerly provided types.</span></span> <span data-ttu-id="c5a1b-162">Bu *bağlamda sağlayıcı,* gerekli olmasalar veya kullanılmasa bile türler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-162">In this context, the provider *eagerly* generates types even if they aren't needed or used.</span></span>

```fsharp
inherit TypeProviderForNamespaces(config)
```

<span data-ttu-id="c5a1b-163">Ardından, belirtilen türler için ad alanını belirten yerel özel değerleri tanımlayın ve tür sağlayıcısı derlemesini bulun.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-163">Next, define local private values that specify the namespace for the provided types, and find the type provider assembly itself.</span></span> <span data-ttu-id="c5a1b-164">Bu derleme daha sonra, belirtilen silinen türlerin mantıksal üst türü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-164">This assembly is used later as the logical parent type of the erased types that are provided.</span></span>

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

<span data-ttu-id="c5a1b-165">Sonra, type1... her bir türü sağlamak için bir işlev oluşturun. Type100.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-165">Next, create a function to provide each of the types Type1…Type100.</span></span> <span data-ttu-id="c5a1b-166">Bu işlev, bu konunun ilerleyen kısımlarında daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-166">This function is explained in more detail later in this topic.</span></span>

```fsharp
let makeOneProvidedType (n:int) = …
```

<span data-ttu-id="c5a1b-167">Ardından, belirtilen 100 türünü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-167">Next, generate the 100 provided types:</span></span>

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

<span data-ttu-id="c5a1b-168">Sonra, türleri bir belirtilen ad alanı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-168">Next, add the types as a provided namespace:</span></span>

```fsharp
do this.AddNamespace(namespaceName, types)
```

<span data-ttu-id="c5a1b-169">Son olarak, bir tür sağlayıcısı DLL 'SI oluşturduğunuz bir derleme özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-169">Finally, add an assembly attribute that indicates that you are creating a type provider DLL:</span></span>

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a><span data-ttu-id="c5a1b-170">Bir tür ve üyelerini sağlama</span><span class="sxs-lookup"><span data-stu-id="c5a1b-170">Providing One Type And Its Members</span></span>

<span data-ttu-id="c5a1b-171">`makeOneProvidedType` işlevi, türlerden birini sağlamanın gerçek işini yapar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-171">The `makeOneProvidedType` function does the real work of providing one of the types.</span></span>

```fsharp
let makeOneProvidedType (n:int) =
…
```

<span data-ttu-id="c5a1b-172">Bu adım, bu işlevin uygulamasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-172">This step explains the implementation of this function.</span></span> <span data-ttu-id="c5a1b-173">İlk olarak, belirtilen türü oluşturun (örneğin, type1, ne zaman n = 1, ne zaman Type57, n = 57).</span><span class="sxs-lookup"><span data-stu-id="c5a1b-173">First, create the provided type (for example, Type1, when n = 1, or Type57, when n = 57).</span></span>

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

<span data-ttu-id="c5a1b-174">Aşağıdaki noktaları dikkate almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-174">You should note the following points:</span></span>

- <span data-ttu-id="c5a1b-175">Bu sunulan tür silindi.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-175">This provided type is erased.</span></span>  <span data-ttu-id="c5a1b-176">Temel türün `obj`olduğunu gösterdiğiniz örnekler, derlenmiş kodda [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) türünde değerler olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-176">Because you indicate that the base type is `obj`, instances will appear as values of type [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) in compiled code.</span></span>

- <span data-ttu-id="c5a1b-177">İç içe olmayan bir tür belirttiğinizde, derlemeyi ve ad alanını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-177">When you specify a non-nested type, you must specify the assembly and namespace.</span></span> <span data-ttu-id="c5a1b-178">Silinen türler için derleme, tür sağlayıcısı derlemesinin kendisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-178">For erased types, the assembly should be the type provider assembly itself.</span></span>

<span data-ttu-id="c5a1b-179">Sonra, türe XML belgesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-179">Next, add XML documentation to the type.</span></span> <span data-ttu-id="c5a1b-180">Bu belge geciktiğinde, diğer bir deyişle, konak derleyicisine ihtiyaç duyduğunda isteğe bağlı olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-180">This documentation is delayed, that is, computed on-demand if the host compiler needs it.</span></span>

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

<span data-ttu-id="c5a1b-181">Daha sonra, bir sağlanmış statik özelliği türüne eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-181">Next you add a provided static property to the type:</span></span>

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

<span data-ttu-id="c5a1b-182">Bu özelliğin alınması, her zaman "Merhaba!" dizesi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-182">Getting this property will always evaluate to the string "Hello!".</span></span> <span data-ttu-id="c5a1b-183">Özelliği için `GetterCode`, ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu temsil eden bir F# alıntı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-183">The `GetterCode` for the property uses an F# quotation, which represents the code that the host compiler generates for getting the property.</span></span> <span data-ttu-id="c5a1b-184">Alıntılar hakkında daha fazla bilgi için bkz. [kod teklifleriF#()](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span><span class="sxs-lookup"><span data-stu-id="c5a1b-184">For more information about quotations, see [Code Quotations (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).</span></span>

<span data-ttu-id="c5a1b-185">Özelliğe XML belgesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-185">Add XML documentation to the property.</span></span>

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

<span data-ttu-id="c5a1b-186">Şimdi, belirtilen özelliği belirtilen türe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-186">Now attach the provided property to the provided type.</span></span> <span data-ttu-id="c5a1b-187">Belirtilen üyeyi bir ve yalnızca bir türe bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-187">You must attach a provided member to one and only one type.</span></span> <span data-ttu-id="c5a1b-188">Aksi takdirde, üyeye hiçbir şekilde erişilemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-188">Otherwise, the member will never be accessible.</span></span>

```fsharp
t.AddMember staticProp
```

<span data-ttu-id="c5a1b-189">Şimdi parametre alan bir belirtilen Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-189">Now create a provided constructor that takes no parameters.</span></span>

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

<span data-ttu-id="c5a1b-190">Oluşturucu için `InvokeCode`, Oluşturucu çağrıldığında konak F# derleyicisinin oluşturduğu kodu temsil eden bir alıntı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-190">The `InvokeCode` for the constructor returns an F# quotation, which represents the code that the host compiler generates when the constructor is called.</span></span> <span data-ttu-id="c5a1b-191">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-191">For example, you can use the following constructor:</span></span>

```fsharp
new Type10()
```

<span data-ttu-id="c5a1b-192">Belirtilen türde bir örnek, "nesne verileri" temel alınan verilerle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-192">An instance of the provided type will be created with underlying data "The object data".</span></span> <span data-ttu-id="c5a1b-193">Alıntılanmış kod, bu verilen türün (belirtilen türü bildirdiğiniz sırada belirttiğiniz şekilde) bu tür için bir değer olduğu için [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) 'e bir dönüştürme içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-193">The quoted code includes a conversion to [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) because that type is the erasure of this provided type (as you specified when you declared the provided type).</span></span>

<span data-ttu-id="c5a1b-194">Oluşturucuya XML belgesi ekleyin ve verilen oluşturucuyu belirtilen türe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-194">Add XML documentation to the constructor, and add the provided constructor to the provided type:</span></span>

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

<span data-ttu-id="c5a1b-195">Bir parametre alan ikinci bir sağlanmış Oluşturucu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-195">Create a second provided constructor that takes one parameter:</span></span>

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

<span data-ttu-id="c5a1b-196">Oluşturucuya yönelik `InvokeCode`, ana bilgisayar derleyicisinin F# metoda bir çağrı için oluşturduğu kodu temsil eden bir alıntı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-196">The `InvokeCode` for the constructor again returns an F# quotation, which represents the code that the host compiler generated for a call to the method.</span></span> <span data-ttu-id="c5a1b-197">Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-197">For example, you can use the following constructor:</span></span>

```fsharp
new Type10("ten")
```

<span data-ttu-id="c5a1b-198">Belirtilen türde bir örnek, "on" temel alınan verilerle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-198">An instance of the provided type is created with underlying data "ten".</span></span> <span data-ttu-id="c5a1b-199">`InvokeCode` işlevinin bir teklif döndürdüğünü fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-199">You may have already noticed that the `InvokeCode` function returns a quotation.</span></span> <span data-ttu-id="c5a1b-200">Bu işlevin girişi, Oluşturucu parametresi başına bir ifade listesidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-200">The input to this function is a list of expressions, one per constructor parameter.</span></span> <span data-ttu-id="c5a1b-201">Bu durumda, tek parametre değerini temsil eden bir ifade `args.[0]`kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-201">In this case, an expression that represents the single parameter value is available in `args.[0]`.</span></span> <span data-ttu-id="c5a1b-202">Oluşturucuya yapılan bir çağrının kodu, dönüş değerini `obj`silinen türe zorlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-202">The code for a call to the constructor coerces the return value to the erased type `obj`.</span></span> <span data-ttu-id="c5a1b-203">İkinci sağlanmış oluşturucuyu türe ekledikten sonra, bir sağlanmış örnek özelliği oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-203">After you add the second provided constructor to the type, you create a provided instance property:</span></span>

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

<span data-ttu-id="c5a1b-204">Bu özelliğin alınması, Gösterim nesnesi olan dize uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-204">Getting this property will return the length of the string, which is the representation object.</span></span> <span data-ttu-id="c5a1b-205">`GetterCode` özelliği, ana bilgisayar F# derleyicisinin özelliği almak için oluşturduğu kodu belirten bir alıntı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-205">The `GetterCode` property returns an F# quotation that specifies the code that the host compiler generates to get the property.</span></span> <span data-ttu-id="c5a1b-206">`InvokeCode`gibi `GetterCode` işlevi bir tırnak döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-206">Like `InvokeCode`, the `GetterCode` function returns a quotation.</span></span> <span data-ttu-id="c5a1b-207">Ana bilgisayar derleyicisi, bu işlevi bir bağımsız değişken listesiyle çağırır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-207">The host compiler calls this function with a list of arguments.</span></span> <span data-ttu-id="c5a1b-208">Bu durumda, bağımsız değişkenler yalnızca alıcının çağrıldığı örneği temsil eden tek ifadeyi içerir, bu da `args.[0]`kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-208">In this case, the arguments include just the single expression that represents the instance upon which the getter is being called, which you can access by using `args.[0]`.</span></span> <span data-ttu-id="c5a1b-209">`GetterCode` uygulanması daha sonra, silinen türdeki `obj`sonuç teklifine göre belirlenir ve derleyicinin nesnenin bir dize olduğu türleri denetlemek için mekanizmasını karşılamak üzere bir dönüştürme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-209">The implementation of `GetterCode` then splices into the result quotation at the erased type `obj`, and a cast is used to satisfy the compiler's mechanism for checking types that the object is a string.</span></span> <span data-ttu-id="c5a1b-210">`makeOneProvidedType` sonraki bölümü, tek parametreli bir örnek yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-210">The next part of `makeOneProvidedType` provides an instance method with one parameter.</span></span>

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

<span data-ttu-id="c5a1b-211">Son olarak, 100 iç içe geçmiş özellikler içeren bir iç içe türü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-211">Finally, create a nested type that contains 100 nested properties.</span></span> <span data-ttu-id="c5a1b-212">Bu iç içe türün oluşturulması ve özellikleri gecikmiştir, diğer bir deyişle isteğe bağlı olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-212">The creation of this nested type and its properties is delayed, that is, computed on-demand.</span></span>

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

### <a name="details-about-erased-provided-types"></a><span data-ttu-id="c5a1b-213">Silinen sağlanmış türler hakkındaki ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c5a1b-213">Details about Erased Provided Types</span></span>

<span data-ttu-id="c5a1b-214">Bu bölümdeki örnek yalnızca *silinmiş sağlanan türleri*sağlar ve aşağıdaki durumlarda özellikle yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-214">The example in this section provides only *erased provided types*, which are particularly useful in the following situations:</span></span>

- <span data-ttu-id="c5a1b-215">Yalnızca veri ve yöntemleri içeren bir bilgi alanı için sağlayıcı yazarken.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-215">When you are writing a provider for an information space that contains only data and methods.</span></span>

- <span data-ttu-id="c5a1b-216">Doğru çalışma zamanı türü semantiğinin, bilgi alanının pratik kullanımı açısından kritik olmadığı bir sağlayıcı yazarken.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-216">When you are writing a provider where accurate runtime-type semantics aren't critical for practical use of the information space.</span></span>

- <span data-ttu-id="c5a1b-217">Daha büyük bir bilgi alanı için bir sağlayıcı yazarken ve bilgi alanı için gerçek .NET türleri üretmek için teknik olarak uygun olmayan bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-217">When you are writing a provider for an information space that is so large and interconnected that it isn’t technically feasible to generate real .NET types for the information space.</span></span>

<span data-ttu-id="c5a1b-218">Bu örnekte, belirtilen her tür `obj`türüne silinir ve türün tüm kullanımları derlenmiş kodda `obj` tür olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-218">In this example, each provided type is erased to type `obj`, and all uses of the type will appear as type `obj` in compiled code.</span></span> <span data-ttu-id="c5a1b-219">Aslında, bu örneklerdeki temeldeki nesneler dizelerdir, ancak tür, .NET derlenmiş kodunda `System.Object` olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-219">In fact, the underlying objects in these examples are strings, but the type will appear as `System.Object` in .NET compiled code.</span></span> <span data-ttu-id="c5a1b-220">ERASURE türünde tüm kullanımlar sayesinde, açık kutulamayı, kutudan çıkarma ve çıkarma türlerini alt alta yazmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-220">As with all uses of type erasure, you can use explicit boxing, unboxing, and casting to subvert erased types.</span></span> <span data-ttu-id="c5a1b-221">Bu durumda, geçerli olmayan bir dönüştürme özel durumu, nesne kullanıldığında ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-221">In this case, a cast exception that isn’t valid may result when the object is used.</span></span> <span data-ttu-id="c5a1b-222">Sağlayıcı çalışma zamanı, yanlış gösterimlerine karşı korumaya yardımcı olmak için kendi özel gösterim türünü tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-222">A provider runtime can define its own private representation type to help protect against false representations.</span></span> <span data-ttu-id="c5a1b-223">Silinen türleri F# kendi kendine tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-223">You can’t define erased types in F# itself.</span></span> <span data-ttu-id="c5a1b-224">Yalnızca sunulan türler silinebilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-224">Only provided types may be erased.</span></span> <span data-ttu-id="c5a1b-225">Tür sağlayıcınız için silinen türler veya silinen türler sağlayan bir sağlayıcı kullanarak hem pratik hem de anlamsal olan sonuçları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-225">You must understand the ramifications, both practical and semantic, of using either erased types for your type provider or a provider that provides erased types.</span></span> <span data-ttu-id="c5a1b-226">Silinen bir türün gerçek bir .NET türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-226">An erased type has no real .NET type.</span></span> <span data-ttu-id="c5a1b-227">Bu nedenle, türü üzerinde doğru yansıma yapılamaz ve çalışma zamanı yayınlarını ve tam çalışma zamanı türü semantiğini kullanan diğer teknikleri kullanırsanız, silinen türleri alt dikey alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-227">Therefore, you cannot do accurate reflection over the type, and you might subvert erased types if you use runtime casts and other techniques that rely on exact runtime type semantics.</span></span> <span data-ttu-id="c5a1b-228">Silinen türlerin alt sürümü sıklıkla çalışma zamanında tür atama özel durumlarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-228">Subversion of erased types frequently results in type cast exceptions at runtime.</span></span>

### <a name="choosing-representations-for-erased-provided-types"></a><span data-ttu-id="c5a1b-229">Silinen sağlanmış türler için gösterimler seçme</span><span class="sxs-lookup"><span data-stu-id="c5a1b-229">Choosing Representations for Erased Provided Types</span></span>

<span data-ttu-id="c5a1b-230">Silinen bazı türlerin kullanımları için hiçbir temsili gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-230">For some uses of erased provided types, no representation is required.</span></span> <span data-ttu-id="c5a1b-231">Örneğin, silinen sağlanmış tür yalnızca statik özellikler ve Üyeler ve hiçbir Oluşturucu içerebilir; hiçbir yöntem veya özellik türün bir örneğini döndürmez.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-231">For example, the erased provided type might contain only static properties and members and no constructors, and no methods or properties would return an instance of the type.</span></span> <span data-ttu-id="c5a1b-232">Silinen bir tür örneğe ulaşabilseniz, aşağıdaki soruları göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-232">If you can reach instances of an erased provided type, you must consider the following questions:</span></span>

<span data-ttu-id="c5a1b-233">**Bir belirtilen türün silinme nedir?**</span><span class="sxs-lookup"><span data-stu-id="c5a1b-233">**What is the erasure of a provided type?**</span></span>

- <span data-ttu-id="c5a1b-234">Bir belirtilen türün silinme türü derlenmiş .net kodunda nasıl görünür?</span><span class="sxs-lookup"><span data-stu-id="c5a1b-234">The erasure of a provided type is how the type appears in compiled .NET code.</span></span>

- <span data-ttu-id="c5a1b-235">Belirtilen silinen bir sınıf türünün silinme her zaman türün devralma zincirindeki ilk silinmeyen temel türdür.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-235">The erasure of a provided erased class type is always the first non-erased base type in the inheritance chain of the type.</span></span>

- <span data-ttu-id="c5a1b-236">Belirtilen silinen bir arabirim türünün silinme her zaman `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-236">The erasure of a provided erased interface type is always `System.Object`.</span></span>

<span data-ttu-id="c5a1b-237">**Belirtilen türde temsiller nelerdir?**</span><span class="sxs-lookup"><span data-stu-id="c5a1b-237">**What are the representations of a provided type?**</span></span>

- <span data-ttu-id="c5a1b-238">Silinmiş bir sağlanmış tür için olası nesneler kümesi, temsilleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-238">The set of possible objects for an erased provided type are called its representations.</span></span> <span data-ttu-id="c5a1b-239">Bu belgedeki örnekte, tüm silinmiş `Type1..Type100` sağlanmış türlerin gösterimleri her zaman dize nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-239">In the example in this document, the representations of all the erased provided types `Type1..Type100` are always string objects.</span></span>

<span data-ttu-id="c5a1b-240">Bir belirtilen türün tüm temsilleri, belirtilen türün silinme ile uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-240">All representations of a provided type must be compatible with the erasure of the provided type.</span></span> <span data-ttu-id="c5a1b-241">(Aksi halde, F# derleyici tür sağlayıcısı kullanımı için bir hata verir ya da geçerli olmayan doğrulanamayan .NET kodu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-241">(Otherwise, either the F# compiler will give an error for a use of the type provider, or unverifiable .NET code that isn't valid will be generated.</span></span> <span data-ttu-id="c5a1b-242">Bir tür sağlayıcısı geçerli olmayan bir temsili veren kodu döndürürse geçerli değildir.)</span><span class="sxs-lookup"><span data-stu-id="c5a1b-242">A type provider isn’t valid if it returns code that gives a  representation that isn't valid.)</span></span>

<span data-ttu-id="c5a1b-243">Aşağıdaki yaklaşımlardan birini kullanarak, sunulan nesneler için bir temsili seçebilirsiniz, her ikisi de çok yaygındır:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-243">You can choose a representation for provided objects by using either of the following approaches, both of which are very common:</span></span>

- <span data-ttu-id="c5a1b-244">Yalnızca var olan bir .NET türü üzerinde kesin olarak belirlenmiş bir sarmalayıcı sağlıyorsanız, bu, genellikle bu türde silme, söz konusu türün örneklerini temsiller veya her ikisi için de anlamlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-244">If you're simply providing a strongly typed wrapper over an existing .NET type, it often makes sense for your type to erase to that type, use instances of that type as representations, or both.</span></span> <span data-ttu-id="c5a1b-245">Bu yaklaşım, bu tür üzerindeki mevcut yöntemlerin büyük bir kısmının, kesin olarak belirlenmiş sürümü kullanırken hala anlamlı hale geldiğinde uygundur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-245">This approach is appropriate when most of the existing methods on that type still make sense when using the strongly typed version.</span></span>

- <span data-ttu-id="c5a1b-246">Var olan herhangi bir .NET API 'sinden önemli ölçüde farklı bir API oluşturmak istiyorsanız, belirtilen türler için tür ve gösterimler olacak çalışma zamanı türleri oluşturmak mantıklı olur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-246">If you want to create an API that differs significantly from any existing .NET API, it makes sense to create runtime types that will be the type erasure and representations for the provided types.</span></span>

<span data-ttu-id="c5a1b-247">Bu belgedeki örnek, dizeleri, belirtilen nesnelerin temsilleri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-247">The example in this document uses strings as representations of provided objects.</span></span> <span data-ttu-id="c5a1b-248">Genellikle, diğer nesneleri temsiller için kullanmak uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-248">Frequently, it may be appropriate to use other objects for representations.</span></span> <span data-ttu-id="c5a1b-249">Örneğin, bir sözlüğü özellik paketi olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-249">For example, you may use a dictionary as a property bag:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

<span data-ttu-id="c5a1b-250">Alternatif olarak, bir veya daha fazla çalışma zamanı işlemiyle birlikte, temsili oluşturmak için çalışma zamanında kullanılacak tür sağlayıcınızda bir tür tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-250">As an alternative, you may define a type in your type provider that will be used at runtime to form the representation, along with one or more runtime operations:</span></span>

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

<span data-ttu-id="c5a1b-251">Daha sonra, belirtilen Üyeler bu nesne türünün örneklerini oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-251">Provided members can then construct instances of this object type:</span></span>

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

<span data-ttu-id="c5a1b-252">Bu durumda, `ProvidedTypeDefinition`oluştururken `baseType` olarak bu türü belirterek, bu türü silinme türü olarak kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-252">In this case, you may (optionally) use this type as the type erasure by specifying this type as the `baseType` when constructing the `ProvidedTypeDefinition`:</span></span>

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a><span data-ttu-id="c5a1b-253">Temel dersler</span><span class="sxs-lookup"><span data-stu-id="c5a1b-253">Key Lessons</span></span>

<span data-ttu-id="c5a1b-254">Önceki bölümde, bir dizi türü, özelliği ve yöntemi sağlayan basit bir silme türü sağlayıcısı oluşturma konusu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-254">The previous section explained how to create a simple erasing type provider that provides a range of types, properties, and methods.</span></span> <span data-ttu-id="c5a1b-255">Bu bölümde ayrıca, bir tür sağlayıcısından silinen türler sağlamanın avantajları ve dezavantajları ve silinen türlerin açıklanabileceği avantajlar da dahil olmak üzere ERASURE türü kavramı açıklanmıştı.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-255">This section also explained the concept of type erasure, including some of the advantages and disadvantages of providing erased types from a type provider, and discussed representations of erased types.</span></span>

## <a name="a-type-provider-that-uses-static-parameters"></a><span data-ttu-id="c5a1b-256">Statik parametreleri kullanan bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c5a1b-256">A Type Provider That Uses Static Parameters</span></span>

<span data-ttu-id="c5a1b-257">Statik veriler tarafından tür sağlayıcılarını Parametreleştirme özelliği, sağlayıcının herhangi bir yerel veya uzak veriye erişmesi gerekmeyen durumlarda bile çok sayıda ilginç senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-257">The ability to parameterize type providers by static data enables many interesting scenarios, even in cases when the provider doesn't need to access any local or remote data.</span></span> <span data-ttu-id="c5a1b-258">Bu bölümde, bir sağlayıcıyı bir araya getirmek için bazı temel tekniklerin öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-258">In this section, you’ll learn some basic techniques for putting together such a provider.</span></span>

### <a name="type-checked-regex-provider"></a><span data-ttu-id="c5a1b-259">Denetlenen Regex sağlayıcısını yazın</span><span class="sxs-lookup"><span data-stu-id="c5a1b-259">Type Checked Regex Provider</span></span>

<span data-ttu-id="c5a1b-260">Aşağıdaki derleme zamanı garantisi sağlayan bir arabirimdeki .NET <xref:System.Text.RegularExpressions.Regex> kitaplıklarını sarmalayan normal ifadeler için bir tür sağlayıcısı uygulamak istediğinizi düşünün:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-260">Imagine that you want to implement a type provider for regular expressions that wraps the .NET <xref:System.Text.RegularExpressions.Regex> libraries in an interface that provides the following compile-time guarantees:</span></span>

- <span data-ttu-id="c5a1b-261">Normal bir ifadenin geçerli olup olmadığı doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-261">Verifying whether a regular expression is valid.</span></span>

- <span data-ttu-id="c5a1b-262">Normal ifadede herhangi bir grup adına dayalı eşleşmeler üzerinde adlandırılmış özellikler sağlama.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-262">Providing named properties on matches that are based on any group names in the regular expression.</span></span>

<span data-ttu-id="c5a1b-263">Bu bölümde, bu avantajları sağlamak üzere normal ifade deseninin parametrelendirmesi için bir `RegexTyped` türü oluşturmak üzere tür sağlayıcılarının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-263">This section shows you how to use type providers to create a `RegexTyped` type that the regular expression pattern parameterizes to provide these benefits.</span></span> <span data-ttu-id="c5a1b-264">Sağlanan model geçerli değilse derleyici bir hata bildirir ve tür sağlayıcısı, eşleşmeler üzerinde adlandırılmış özellikler kullanarak erişebilmek için grupları düzeninden ayıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-264">The compiler will report an error if the supplied pattern isn't valid, and the type provider can extract the groups from the pattern so that you can access them by using named properties on matches.</span></span> <span data-ttu-id="c5a1b-265">Bir tür sağlayıcısı tasarladığınızda, sunulan API 'nin son kullanıcılara nasıl bakacağınızı ve bu tasarımın .NET koduna nasıl çevrileceğini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-265">When you design a type provider, you should consider how its exposed API should look to end users and how this design will translate to .NET code.</span></span> <span data-ttu-id="c5a1b-266">Aşağıdaki örnek, bu tür bir API 'nin, alan kodu bileşenlerini almak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-266">The following example shows how to use such an API to get the components of the area code:</span></span>

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

<span data-ttu-id="c5a1b-267">Aşağıdaki örnek, tür sağlayıcısının bu çağrıları nasıl dönüştürdüğünde gösterir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-267">The following example shows how the type provider translates these calls:</span></span>

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

<span data-ttu-id="c5a1b-268">Aşağıdaki noktaları dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-268">Note the following points:</span></span>

- <span data-ttu-id="c5a1b-269">Standart Regex türü parametreli `RegexTyped` türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-269">The standard Regex type represents the parameterized `RegexTyped` type.</span></span>

- <span data-ttu-id="c5a1b-270">`RegexTyped` Oluşturucu, bir normal ifade oluşturucusuna çağrı ile sonuçlanır ve bu, düzenin statik tür bağımsız değişkenini geçirerek.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-270">The `RegexTyped` constructor results in a call to the Regex constructor, passing in the static type argument for the pattern.</span></span>

- <span data-ttu-id="c5a1b-271">`Match` yönteminin sonuçları, standart <xref:System.Text.RegularExpressions.Match> türü tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-271">The results of the `Match` method are represented by the standard <xref:System.Text.RegularExpressions.Match> type.</span></span>

- <span data-ttu-id="c5a1b-272">Her bir adlandırılmış Grup, belirtilen bir özellik ile sonuçlanır ve özelliğe erişmek, eşleşmenin `Groups` koleksiyonundaki bir dizin oluşturucunun kullanımıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-272">Each named group results in a provided property, and accessing the property results in a use of an indexer on a match’s `Groups` collection.</span></span>

<span data-ttu-id="c5a1b-273">Aşağıdaki kod, bu tür bir sağlayıcıyı uygulayan mantığın çekirdekdir ve bu örnek, tüm üyelerin eklenmesi belirtilen türe atlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-273">The following code is the core of the logic to implement such a provider, and this example omits the addition of all members to the provided type.</span></span> <span data-ttu-id="c5a1b-274">Eklenen her üye hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki ilgili bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-274">For information about each added member, see the appropriate section later in this topic.</span></span> <span data-ttu-id="c5a1b-275">Tam kod için, CodePlex Web sitesindeki [ F# 3,0 örnek paketinden](https://archive.codeplex.com/?p=fsharp3sample) örneği indirin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-275">For the full code, download the sample from the [F# 3.0 Sample Pack](https://archive.codeplex.com/?p=fsharp3sample) on the CodePlex website.</span></span>

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

<span data-ttu-id="c5a1b-276">Aşağıdaki noktaları dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-276">Note the following points:</span></span>

- <span data-ttu-id="c5a1b-277">Tür sağlayıcısı iki statik parametre alır: zorunlu olan `pattern`ve isteğe bağlı olan `options`(varsayılan değer sağlandığı için).</span><span class="sxs-lookup"><span data-stu-id="c5a1b-277">The type provider takes two static parameters: the `pattern`, which is mandatory, and the `options`, which are optional (because a default value is provided).</span></span>

- <span data-ttu-id="c5a1b-278">Statik bağımsız değişkenler sağlandığında, normal ifadenin bir örneğini oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-278">After the static arguments are supplied, you create an instance of the regular expression.</span></span> <span data-ttu-id="c5a1b-279">Bu örnek, Regex yanlış biçimlendirilmişse bir özel durum oluşturur ve bu hata kullanıcılara bildirilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-279">This instance will throw an exception if the Regex is malformed, and this error will be reported to users.</span></span>

- <span data-ttu-id="c5a1b-280">`DefineStaticParameters` geri çağırması içinde, bağımsız değişkenler sağlandıktan sonra döndürülecek türü tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-280">Within the `DefineStaticParameters` callback, you define the type that will be returned after the arguments are supplied.</span></span>

- <span data-ttu-id="c5a1b-281">Bu kod, IntelliSense deneyiminin kolaylaştırmaya devam edebilmesi için `HideObjectMethods` true olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-281">This code sets `HideObjectMethods` to true so that the IntelliSense experience will remain streamlined.</span></span> <span data-ttu-id="c5a1b-282">Bu öznitelik, `Equals`, `GetHashCode`, `Finalize`ve `GetType` üyelerinin, sunulan bir nesne için IntelliSense listelerinden gizlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-282">This attribute causes the `Equals`, `GetHashCode`, `Finalize`, and `GetType` members to be suppressed from IntelliSense lists for a provided object.</span></span>

- <span data-ttu-id="c5a1b-283">Yöntemin temel türü olarak `obj` kullanırsınız, ancak sonraki örnekte gösterildiği gibi bu türün çalışma zamanı temsili olarak bir `Regex` nesnesi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-283">You use `obj` as the base type of the method, but you’ll use a `Regex` object as the runtime representation of this type, as the next example shows.</span></span>

- <span data-ttu-id="c5a1b-284">`Regex` oluşturucusuna yapılan çağrı, normal bir ifade geçerli olmadığında bir <xref:System.ArgumentException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-284">The call to the `Regex` constructor throws a <xref:System.ArgumentException> when a regular expression isn’t valid.</span></span> <span data-ttu-id="c5a1b-285">Derleyici bu özel durumu yakalar ve derleme zamanında veya Visual Studio Düzenleyicisi 'nde kullanıcıya bir hata mesajı bildirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-285">The compiler catches this exception and reports an error message to the user at compile time or in the Visual Studio editor.</span></span> <span data-ttu-id="c5a1b-286">Bu özel durum, normal ifadelerin bir uygulama çalıştırmadan doğrulanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-286">This exception enables regular expressions to be validated without running an application.</span></span>

<span data-ttu-id="c5a1b-287">Yukarıda tanımlanan tür hiçbir anlamlı Yöntem veya özellik içermediğinden henüz yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-287">The type defined above isn't useful yet because it doesn’t contain any meaningful methods or properties.</span></span> <span data-ttu-id="c5a1b-288">İlk olarak, statik bir `IsMatch` yöntemi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-288">First, add a static `IsMatch` method:</span></span>

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

<span data-ttu-id="c5a1b-289">Önceki kod, girdi olarak bir dize alan ve bir `bool`döndüren `IsMatch`bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-289">The previous code defines a method `IsMatch`, which takes a string as input and returns a `bool`.</span></span> <span data-ttu-id="c5a1b-290">Tek karmaşık bölüm, `InvokeCode` tanımında `args` bağımsız değişkeninin kullanılması.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-290">The only tricky part is the use of the `args` argument within the `InvokeCode` definition.</span></span> <span data-ttu-id="c5a1b-291">Bu örnekte `args`, bu yöntemin bağımsız değişkenlerini temsil eden tekliflerin bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-291">In this example, `args` is a list of quotations that represents the arguments to this method.</span></span> <span data-ttu-id="c5a1b-292">Yöntem bir örnek yöntemi ise, ilk bağımsız değişken `this` bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-292">If the method is an instance method, the first argument represents the `this` argument.</span></span> <span data-ttu-id="c5a1b-293">Ancak, bir statik yöntem için bağımsız değişkenler yalnızca yöntemin açık bağımsız değişkenlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-293">However, for a static method, the arguments are all just the explicit arguments to the method.</span></span> <span data-ttu-id="c5a1b-294">Alıntılanmış değerin türünün belirtilen dönüş türüyle (Bu durumda `bool`) eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-294">Note that the type of the quoted value should match the specified return type (in this case, `bool`).</span></span> <span data-ttu-id="c5a1b-295">Ayrıca, bu kodun, IntelliSense aracılığıyla sağlayabilmeniz için, sunulan yöntemin de yararlı belgeler içerdiğinden emin olmak için `AddXmlDoc` yöntemini kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-295">Also note that this code uses the `AddXmlDoc` method to make sure that the provided method also has useful documentation, which you can supply through IntelliSense.</span></span>

<span data-ttu-id="c5a1b-296">Sonra bir örnek eşleşme yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-296">Next, add an instance Match method.</span></span> <span data-ttu-id="c5a1b-297">Ancak, bu yöntem, grupların kesin olarak belirlenmiş bir biçimde erişilebilmesi için, belirtilen `Match` türünün bir değerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-297">However, this method should return a value of a provided `Match` type so that the groups can be accessed in a strongly typed fashion.</span></span> <span data-ttu-id="c5a1b-298">Bu nedenle, önce `Match` türünü bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-298">Thus, you first declare the `Match` type.</span></span> <span data-ttu-id="c5a1b-299">Bu tür statik bir bağımsız değişken olarak sağlanan modele bağlı olduğundan, bu tür parametreli tür tanımı içinde iç içe olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-299">Because this type depends on the pattern that was supplied as a static argument, this type must be nested within the parameterized type definition:</span></span>

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

<span data-ttu-id="c5a1b-300">Sonra her grup için eşleşme türüne bir özellik eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-300">You then add one property to the Match type for each group.</span></span> <span data-ttu-id="c5a1b-301">Çalışma zamanında, bir eşleşme <xref:System.Text.RegularExpressions.Match> değeri olarak temsil edildiğinde, özelliği tanımlayan teklifin ilgili grubu almak için <xref:System.Text.RegularExpressions.Match.Groups> dizinli özelliğini kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-301">At runtime, a match is represented as a <xref:System.Text.RegularExpressions.Match> value, so the quotation that defines the property must use the <xref:System.Text.RegularExpressions.Match.Groups> indexed property to get the relevant group.</span></span>

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

<span data-ttu-id="c5a1b-302">Yine, XML belgelerini verilen özelliğe eklebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-302">Again, note that you’re adding XML documentation to the provided property.</span></span> <span data-ttu-id="c5a1b-303">Ayrıca, bir `GetterCode` işlevi sağlanırsa özelliğin okunabilmesi ve bir `SetterCode` işlevi sağlandıysa özelliğin yazılabileceği, sonuçta elde edilen özelliğin salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-303">Also note that a property can be read if a `GetterCode` function is provided, and the property can be written if a `SetterCode` function is provided, so the resulting property is read only.</span></span>

<span data-ttu-id="c5a1b-304">Artık bu `Match` türünde bir değer döndüren bir örnek yöntemi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-304">Now you can create an instance method that returns a value of this `Match` type:</span></span>

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

<span data-ttu-id="c5a1b-305">Bir örnek yöntemi oluştururken `args.[0]`, yöntemin çağrıldığı `RegexTyped` örneğini temsil eder ve `args.[1]` giriş bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-305">Because you are creating an instance method, `args.[0]` represents the `RegexTyped` instance on which the method is being called, and `args.[1]` is the input argument.</span></span>

<span data-ttu-id="c5a1b-306">Son olarak, belirtilen türdeki örneklerin oluşturulabilmesi için bir Oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-306">Finally, provide a constructor so that instances of the provided type can be created.</span></span>

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

<span data-ttu-id="c5a1b-307">Oluşturucu yalnızca, bir nesneye yeniden paketlenmiş standart bir .net Regex örneği oluşturulmasını siler, çünkü `obj`, belirtilen türün silinme ' dır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-307">The constructor merely erases to the creation of a standard .NET Regex instance, which is again boxed to an object because `obj` is the erasure of the provided type.</span></span> <span data-ttu-id="c5a1b-308">Bu değişiklik ile, konusunda daha önce belirtilen örnek API kullanımı beklendiği gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-308">With that change, the sample API usage that specified earlier in the topic works as expected.</span></span> <span data-ttu-id="c5a1b-309">Aşağıdaki kod tamamlandı ve son:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-309">The following code is complete and final:</span></span>

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

### <a name="key-lessons"></a><span data-ttu-id="c5a1b-310">Temel dersler</span><span class="sxs-lookup"><span data-stu-id="c5a1b-310">Key Lessons</span></span>

<span data-ttu-id="c5a1b-311">Bu bölümde, statik parametrelerinde çalışan bir tür sağlayıcısı oluşturma konusu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-311">This section explained how to create a type provider that operates on its static parameters.</span></span> <span data-ttu-id="c5a1b-312">Sağlayıcı statik parametreyi denetler ve değerini temel alarak işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-312">The provider checks the static parameter and provides operations based on its value.</span></span>

## <a name="a-type-provider-that-is-backed-by-local-data"></a><span data-ttu-id="c5a1b-313">Yerel veriler tarafından desteklenen bir tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c5a1b-313">A Type Provider That Is Backed By Local Data</span></span>

<span data-ttu-id="c5a1b-314">Genellikle, tür sağlayıcılarının API 'Leri yalnızca statik parametrelere değil, yerel veya uzak sistemlerden da sunmalarına izin vermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-314">Frequently you might want type providers to present APIs based on not only static parameters but also information from local or remote systems.</span></span> <span data-ttu-id="c5a1b-315">Bu bölümde yerel veri dosyaları gibi yerel verileri temel alan tür sağlayıcıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-315">This section discusses type providers that are based on local data, such as local data files.</span></span>

### <a name="simple-csv-file-provider"></a><span data-ttu-id="c5a1b-316">Basit CSV dosya sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c5a1b-316">Simple CSV File Provider</span></span>

<span data-ttu-id="c5a1b-317">Basit bir örnek olarak, virgülle ayrılmış değer (CSV) biçiminde bilimsel verilere erişmek için bir tür sağlayıcısı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-317">As a simple example, consider a type provider for accessing scientific data in Comma Separated Value (CSV) format.</span></span> <span data-ttu-id="c5a1b-318">Bu bölümde, aşağıdaki tabloda gösterildiği gibi, CSV dosyalarının bir başlık satırı ve ardından kayan nokta verilerinin bulunduğu varsayılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-318">This section assumes that the CSV files contain a header row followed by floating point data, as the following table illustrates:</span></span>

|<span data-ttu-id="c5a1b-319">Uzaklık (ölçüm)</span><span class="sxs-lookup"><span data-stu-id="c5a1b-319">Distance (meter)</span></span>|<span data-ttu-id="c5a1b-320">Süre (saniye)</span><span class="sxs-lookup"><span data-stu-id="c5a1b-320">Time (second)</span></span>|
|----------------|-------------|
|<span data-ttu-id="c5a1b-321">50,0</span><span class="sxs-lookup"><span data-stu-id="c5a1b-321">50.0</span></span>|<span data-ttu-id="c5a1b-322">3,7</span><span class="sxs-lookup"><span data-stu-id="c5a1b-322">3.7</span></span>|
|<span data-ttu-id="c5a1b-323">100,0</span><span class="sxs-lookup"><span data-stu-id="c5a1b-323">100.0</span></span>|<span data-ttu-id="c5a1b-324">5,2</span><span class="sxs-lookup"><span data-stu-id="c5a1b-324">5.2</span></span>|
|<span data-ttu-id="c5a1b-325">150,0</span><span class="sxs-lookup"><span data-stu-id="c5a1b-325">150.0</span></span>|<span data-ttu-id="c5a1b-326">6,4</span><span class="sxs-lookup"><span data-stu-id="c5a1b-326">6.4</span></span>|

<span data-ttu-id="c5a1b-327">Bu bölümde, `float<meter>` türünde bir `Distance` özelliği ve `float<second>`türünde bir `Time` özelliği olan satırları almak için kullanabileceğiniz bir tür sağlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-327">This section shows how to provide a type that you can use to get rows with a `Distance` property of type `float<meter>` and a `Time` property of type `float<second>`.</span></span> <span data-ttu-id="c5a1b-328">Basitlik için aşağıdaki varsayımlar yapılır:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-328">For simplicity, the following assumptions are made:</span></span>

- <span data-ttu-id="c5a1b-329">Üst bilgi adları, birim-daha küçüktür veya "ad (birim)" biçiminde ve virgül içermez.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-329">Header names are either unit-less or have the form "Name (unit)" and don't contain commas.</span></span>

- <span data-ttu-id="c5a1b-330">Birimler, [Microsoft. FSharp. Data. UnitSystems. sı. UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modülünün tanımladığı tüm sistem uluslararası (sı) birimleridir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-330">Units are all System International (SI) units as the [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Module (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) module defines.</span></span>

- <span data-ttu-id="c5a1b-331">Birimler, bileşik yerine (örneğin, ölçüm/saniye) tamamen basittir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-331">Units are all simple (for example, meter) rather than compound (for example, meter/second).</span></span>

- <span data-ttu-id="c5a1b-332">Tüm sütunlar kayan nokta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-332">All columns contain floating point data.</span></span>

<span data-ttu-id="c5a1b-333">Daha kapsamlı bir sağlayıcı bu kısıtlamaları gevyordu.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-333">A more complete provider would loosen these restrictions.</span></span>

<span data-ttu-id="c5a1b-334">İlk adım, API 'nin nasıl görüneceğini düşünmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-334">Again the first step is to consider how the API should look.</span></span> <span data-ttu-id="c5a1b-335">Önceki tablodaki içeriğe sahip bir `info.csv` dosyası (virgülle ayrılmış biçimde) verildiğinde, sağlayıcının kullanıcıları aşağıdaki örneğe benzer bir kod yazabilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-335">Given an `info.csv` file with the contents from the previous table (in comma-separated format), users of the provider should be able to write code that resembles the following example:</span></span>

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

<span data-ttu-id="c5a1b-336">Bu durumda, derleyici bu çağrıları aşağıdaki örnekteki gibi bir şeye dönüştürmelidir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-336">In this case, the compiler should convert these calls into something like the following example:</span></span>

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

<span data-ttu-id="c5a1b-337">En uygun çeviri tür sağlayıcısının tür sağlayıcısının derlemesinde gerçek bir `CsvFile` türünü tanımlamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-337">The optimal translation will require the type provider to define a real `CsvFile` type in the type provider's assembly.</span></span> <span data-ttu-id="c5a1b-338">Tür sağlayıcıları, önemli mantığı kaydırmak için genellikle birkaç yardımcı türü ve yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-338">Type providers often rely on a few helper types and methods to wrap important logic.</span></span> <span data-ttu-id="c5a1b-339">Ölçüler çalışma zamanında silindiğinden, bir satır için silinen tür olarak bir `float[]` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-339">Because measures are erased at runtime, you can use a `float[]` as the erased type for a row.</span></span> <span data-ttu-id="c5a1b-340">Derleyici farklı sütunları farklı ölçü türlerine sahip olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-340">The compiler will treat different columns as having different measure types.</span></span> <span data-ttu-id="c5a1b-341">Örneğin, örneğimizdeki ilk sütunun türü `float<meter>`, ikincisi ise `float<second>`.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-341">For example, the first column in our example has type `float<meter>`, and the second has `float<second>`.</span></span> <span data-ttu-id="c5a1b-342">Ancak, silinen temsili oldukça basit kalabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-342">However, the erased representation can remain quite simple.</span></span>

<span data-ttu-id="c5a1b-343">Aşağıdaki kod, uygulamanın çekirdeğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-343">The following code shows the core of the implementation.</span></span>

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

<span data-ttu-id="c5a1b-344">Uygulamayla ilgili aşağıdaki noktaları dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-344">Note the following points about the implementation:</span></span>

- <span data-ttu-id="c5a1b-345">Aşırı yüklenmiş oluşturucular, özgün dosyanın veya özdeş bir şemaya sahip olan birinin okunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-345">Overloaded constructors allow either the original file or one that has an identical schema to be read.</span></span> <span data-ttu-id="c5a1b-346">Bu model, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazdığınızda yaygındır ve bu model yerel bir dosyanın uzak veriler için şablon olarak kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-346">This pattern is common when you write a type provider for local or remote data sources, and this pattern allows a local file to be used as the template for remote data.</span></span>

- <span data-ttu-id="c5a1b-347">Göreli dosya adlarını çözümlemek için tür sağlayıcısı oluşturucusuna geçirilen [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) değerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-347">You can use the [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) value that’s passed in to the type provider constructor to resolve relative file names.</span></span>

- <span data-ttu-id="c5a1b-348">`AddDefinitionLocation` yöntemini, belirtilen özelliklerin konumunu tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-348">You can use the `AddDefinitionLocation` method to define the location of the provided properties.</span></span> <span data-ttu-id="c5a1b-349">Bu nedenle, sağlanmış bir özellikte `Go To Definition` kullanıyorsanız, CSV dosyası Visual Studio 'da açılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-349">Therefore, if you use `Go To Definition` on a provided property, the CSV file will open in Visual Studio.</span></span>

- <span data-ttu-id="c5a1b-350">`ProvidedMeasureBuilder` türünü, sı birimleri aramak ve ilgili `float<_>` türlerini oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-350">You can use the `ProvidedMeasureBuilder` type to look up the SI units and to generate the relevant `float<_>` types.</span></span>

### <a name="key-lessons"></a><span data-ttu-id="c5a1b-351">Temel dersler</span><span class="sxs-lookup"><span data-stu-id="c5a1b-351">Key Lessons</span></span>

<span data-ttu-id="c5a1b-352">Bu bölümde, veri kaynağının içinde bulunan basit bir şemaya sahip bir yerel veri kaynağı için bir tür sağlayıcısı oluşturma konusu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-352">This section explained how to create a type provider for a local data source with a simple schema that's contained in the data source itself.</span></span>

## <a name="going-further"></a><span data-ttu-id="c5a1b-353">Daha fazla</span><span class="sxs-lookup"><span data-stu-id="c5a1b-353">Going Further</span></span>

<span data-ttu-id="c5a1b-354">Aşağıdaki bölümler, daha fazla çalışma için öneriler içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-354">The following sections include suggestions for further study.</span></span>

### <a name="a-look-at-the-compiled-code-for-erased-types"></a><span data-ttu-id="c5a1b-355">Silinen türler için derlenmiş koda göz atın</span><span class="sxs-lookup"><span data-stu-id="c5a1b-355">A Look at the Compiled Code for Erased Types</span></span>

<span data-ttu-id="c5a1b-356">Tür sağlayıcısının kullanımına yayılan koda karşılık gelen bir fikir vermek için, bu konunun önceki kısımlarında kullanılan `HelloWorldTypeProvider` kullanarak aşağıdaki işleve bakın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-356">To give you some idea of how the use of the type provider corresponds to the code that's emitted, look at the following function by using the `HelloWorldTypeProvider` that's used earlier in this topic.</span></span>

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

<span data-ttu-id="c5a1b-357">Ildadsm. exe kullanılarak derlenen ortaya çıkan kodun bir görüntüsü aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-357">Here’s an image of the resulting code decompiled by using ildasm.exe:</span></span>

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

<span data-ttu-id="c5a1b-358">Örnekte gösterildiği gibi, tür `Type1` ve `InstanceProperty` özelliğinin tüm bahsetmeler silinmiş ve yalnızca ilgili çalışma zamanı türlerinde işlemler bırakılıyor.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-358">As the example shows, all mentions of the type `Type1` and the `InstanceProperty` property have been erased, leaving only operations on the runtime types involved.</span></span>

### <a name="design-and-naming-conventions-for-type-providers"></a><span data-ttu-id="c5a1b-359">Tür sağlayıcıları için tasarım ve adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="c5a1b-359">Design and Naming Conventions for Type Providers</span></span>

<span data-ttu-id="c5a1b-360">Tür sağlayıcıları yazarken aşağıdaki kuralları gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-360">Observe the following conventions when authoring type providers.</span></span>

<span data-ttu-id="c5a1b-361">**Bağlantı protokolleri Için sağlayıcılar** Genellikle, veri ve hizmet bağlantı protokollerinin (OData veya SQL bağlantıları gibi) çoğu için sağlayıcı dll 'Lerinin adları `TypeProvider` veya `TypeProviders`bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-361">**Providers for Connectivity Protocols** In general, names of most provider DLLs for data and service connectivity protocols, such as OData or SQL connections, should end in `TypeProvider` or `TypeProviders`.</span></span> <span data-ttu-id="c5a1b-362">Örneğin, aşağıdaki dizeye benzer bir DLL adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-362">For example, use a DLL name that resembles the following string:</span></span>

`Fabrikam.Management.BasicTypeProviders.dll`

<span data-ttu-id="c5a1b-363">Belirttiğiniz türlerin karşılık gelen ad alanının üyesi olduğundan emin olun ve uygulanan bağlantı protokolünü belirtin:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-363">Ensure that your provided types are members of the corresponding namespace, and indicate the connectivity protocol that you implemented:</span></span>

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

<span data-ttu-id="c5a1b-364">**Genel kodlama Için yardımcı program sağlayıcıları**.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-364">**Utility Providers for General Coding**.</span></span>  <span data-ttu-id="c5a1b-365">Normal ifadeler gibi bir yardımcı program türü sağlayıcı için, aşağıdaki örnekte gösterildiği gibi tür sağlayıcısı bir temel kitaplığın parçası olabilir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-365">For a utility type provider such as that for regular expressions, the type provider may be part of a base library, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

<span data-ttu-id="c5a1b-366">Bu durumda, sunulan tür normal .NET tasarım kurallarına göre uygun bir noktada görünür:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-366">In this case, the provided type would appear at an appropriate point according to normal .NET design conventions:</span></span>

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

<span data-ttu-id="c5a1b-367">**Tek veri kaynakları**.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-367">**Singleton Data Sources**.</span></span> <span data-ttu-id="c5a1b-368">Bazı tür sağlayıcıları tek bir ayrılmış veri kaynağına bağlanır ve yalnızca verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-368">Some type providers connect to a single dedicated data source and provide only data.</span></span> <span data-ttu-id="c5a1b-369">Bu durumda, `TypeProvider` sonekini bırakıp .NET adlandırma için normal kuralları kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-369">In this case, you should drop the `TypeProvider` suffix and use normal conventions for .NET naming:</span></span>

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

<span data-ttu-id="c5a1b-370">Daha fazla bilgi için, bu konunun ilerleyen kısımlarında açıklanan `GetConnection` tasarım kuralına bakın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-370">For more information, see the `GetConnection` design convention that's described later in this topic.</span></span>

### <a name="design-patterns-for-type-providers"></a><span data-ttu-id="c5a1b-371">Tür sağlayıcıları için tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="c5a1b-371">Design Patterns for Type Providers</span></span>

<span data-ttu-id="c5a1b-372">Aşağıdaki bölümlerde, tür sağlayıcıları yazarken kullanabileceğiniz tasarım desenleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-372">The following sections describe design patterns you can use when authoring type providers.</span></span>

#### <a name="the-getconnection-design-pattern"></a><span data-ttu-id="c5a1b-373">GetConnection tasarım deseninin</span><span class="sxs-lookup"><span data-stu-id="c5a1b-373">The GetConnection Design Pattern</span></span>

<span data-ttu-id="c5a1b-374">Çoğu tür sağlayıcı, aşağıdaki örnekte gösterildiği gibi FSharp. Data. TypeProviders. dll içindeki tür sağlayıcıları tarafından kullanılan `GetConnection` modelini kullanmak için yazılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-374">Most type providers should be written to use the `GetConnection` pattern that's used by the type providers in FSharp.Data.TypeProviders.dll, as the following example shows:</span></span>

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a><span data-ttu-id="c5a1b-375">Uzak veri ve hizmetler tarafından desteklenen tür sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c5a1b-375">Type Providers Backed By Remote Data and Services</span></span>

<span data-ttu-id="c5a1b-376">Uzak veri ve hizmetler tarafından desteklenen bir tür sağlayıcısı oluşturmadan önce, bağlı programlamaya ait bir dizi sorunu düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-376">Before you create a type provider that's backed by remote data and services, you must consider a range of issues that are inherent in connected programming.</span></span> <span data-ttu-id="c5a1b-377">Bu sorunlar aşağıdaki konuları içerir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-377">These issues include the following considerations:</span></span>

- <span data-ttu-id="c5a1b-378">Şema eşleme</span><span class="sxs-lookup"><span data-stu-id="c5a1b-378">schema mapping</span></span>

- <span data-ttu-id="c5a1b-379">şema değişikliği durumunda liilte ve geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="c5a1b-379">liveness and invalidation in the presence of schema change</span></span>

- <span data-ttu-id="c5a1b-380">şema önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="c5a1b-380">schema caching</span></span>

- <span data-ttu-id="c5a1b-381">veri erişim işlemlerinin zaman uyumsuz uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c5a1b-381">asynchronous implementations of data access operations</span></span>

- <span data-ttu-id="c5a1b-382">LINQ sorguları dahil destekleyici sorgular</span><span class="sxs-lookup"><span data-stu-id="c5a1b-382">supporting queries, including LINQ queries</span></span>

- <span data-ttu-id="c5a1b-383">kimlik bilgileri ve kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="c5a1b-383">credentials and authentication</span></span>

<span data-ttu-id="c5a1b-384">Bu konu, bu sorunları daha ayrıntılı bir şekilde araştırmaz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-384">This topic doesn't explore these issues further.</span></span>

### <a name="additional-authoring-techniques"></a><span data-ttu-id="c5a1b-385">Ek yazma teknikleri</span><span class="sxs-lookup"><span data-stu-id="c5a1b-385">Additional Authoring Techniques</span></span>

<span data-ttu-id="c5a1b-386">Kendi tür sağlayıcılarınızı yazdığınızda, aşağıdaki ek teknikleri kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-386">When you write your own type providers, you might want to use the following additional techniques.</span></span>

### <a name="creating-types-and-members-on-demand"></a><span data-ttu-id="c5a1b-387">Istek üzerine türler ve Üyeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5a1b-387">Creating Types and Members On-Demand</span></span>

<span data-ttu-id="c5a1b-388">ProvidedType API 'SI, AddMember 'ın gecikmeli sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-388">The ProvidedType API has delayed versions of AddMember.</span></span>

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

<span data-ttu-id="c5a1b-389">Bu sürümler, türlerin isteğe bağlı alanlarını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-389">These versions are used to create on-demand spaces of types.</span></span>

### <a name="providing-array-types-and-generic-type-instantiations"></a><span data-ttu-id="c5a1b-390">Dizi türleri ve genel tür örneklemeleri sağlama</span><span class="sxs-lookup"><span data-stu-id="c5a1b-390">Providing Array types and Generic Type Instantiations</span></span>

<span data-ttu-id="c5a1b-391">`ProvidedTypeDefinitions`dahil olmak üzere herhangi bir <xref:System.Type>örneğine normal `MakeArrayType`, `MakePointerType`ve `MakeGenericType` kullanarak, imzaları dizi türleri, ByRef türleri ve genel türlerin örneklemeleri dahil) yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-391">You make provided members (whose signatures include array types, byref types, and instantiations of generic types) by using the normal `MakeArrayType`, `MakePointerType`, and `MakeGenericType` on any instance of <xref:System.Type>, including `ProvidedTypeDefinitions`.</span></span>

> [!NOTE]
> <span data-ttu-id="c5a1b-392">Bazı durumlarda `ProvidedTypeBuilder.MakeGenericType`Yardımcısı 'nı kullanmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-392">In some cases you may have to use the helper in `ProvidedTypeBuilder.MakeGenericType`.</span></span>  <span data-ttu-id="c5a1b-393">Daha fazla bilgi için bkz. [tür sağlayıcısı SDK belgeleri](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .</span><span class="sxs-lookup"><span data-stu-id="c5a1b-393">See the [Type Provider SDK documentation](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) for more details.</span></span>

### <a name="providing-unit-of-measure-annotations"></a><span data-ttu-id="c5a1b-394">Ölçü birimi ek açıklamaları sağlama</span><span class="sxs-lookup"><span data-stu-id="c5a1b-394">Providing Unit of Measure Annotations</span></span>

<span data-ttu-id="c5a1b-395">ProvidedTypes API 'SI, ölçü ek açıklamaları sağlamak için yardımcılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-395">The ProvidedTypes API provides helpers for providing measure annotations.</span></span> <span data-ttu-id="c5a1b-396">Örneğin, türü `float<kg>`sağlamak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-396">For example, to provide the type `float<kg>`, use the following code:</span></span>

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  <span data-ttu-id="c5a1b-397">`Nullable<decimal<kg/m^2>>`türünü sağlamak için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-397">To provide the type `Nullable<decimal<kg/m^2>>`, use the following code:</span></span>

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a><span data-ttu-id="c5a1b-398">Proje-yerel veya betiğe yerel kaynaklara erişme</span><span class="sxs-lookup"><span data-stu-id="c5a1b-398">Accessing Project-Local or Script-Local Resources</span></span>

<span data-ttu-id="c5a1b-399">Bir tür sağlayıcının her örneğine, oluşturma sırasında bir `TypeProviderConfig` değeri verilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-399">Each instance of a type provider can be given a `TypeProviderConfig` value during construction.</span></span> <span data-ttu-id="c5a1b-400">Bu değer, sağlayıcının "çözüm klasörünü" içerir (yani, derleme için proje klasörü veya bir betiği içeren dizin), başvurulan derlemelerin listesi ve diğer bilgiler.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-400">This value contains the "resolution folder" for the provider (that is, the project folder for the compilation or the directory that contains a script), the list of referenced assemblies, and other information.</span></span>

### <a name="invalidation"></a><span data-ttu-id="c5a1b-401">Geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="c5a1b-401">Invalidation</span></span>

<span data-ttu-id="c5a1b-402">Sağlayıcılar, F# dil hizmetine şema varsayımlarında değişiklik olduğunu bildirmek için doğrulama sinyalleri oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-402">Providers can raise invalidation signals to notify the F# language service that the schema assumptions may have changed.</span></span> <span data-ttu-id="c5a1b-403">Invalidation gerçekleştiğinde, sağlayıcı Visual Studio 'da barındırılıyorsa bir typecheck, yinelendi olur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-403">When invalidation occurs, a typecheck is redone if the provider is being hosted in Visual Studio.</span></span> <span data-ttu-id="c5a1b-404">Bu sinyal, sağlayıcı F# etkileşimli veya F# derleyici (FSC. exe) tarafından barındırılıyorsa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-404">This signal will be ignored when the provider is hosted in F# Interactive or by the F# Compiler (fsc.exe).</span></span>

### <a name="caching-schema-information"></a><span data-ttu-id="c5a1b-405">Şema bilgilerini önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="c5a1b-405">Caching Schema Information</span></span>

<span data-ttu-id="c5a1b-406">Sağlayıcılar genellikle şema bilgilerine erişimi önbelleğe almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-406">Providers must often cache access to schema information.</span></span> <span data-ttu-id="c5a1b-407">Önbelleğe alınan veriler, statik bir parametre veya Kullanıcı verileri olarak verilen bir dosya adı kullanılarak depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-407">The cached data should be stored by using a file name that's given as a static parameter or as user data.</span></span> <span data-ttu-id="c5a1b-408">Şema önbelleğe alma örneği, `FSharp.Data.TypeProviders` derlemesinde tür sağlayıcılarındaki `LocalSchemaFile` parametredir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-408">An example of schema caching is the `LocalSchemaFile` parameter in the type providers in the `FSharp.Data.TypeProviders` assembly.</span></span> <span data-ttu-id="c5a1b-409">Bu statik parametre, bu sağlayıcıları uygulamada, tür sağlayıcısını ağ üzerinden veri kaynağına erişmek yerine, belirtilen yerel dosyadaki şema bilgilerini kullanacak şekilde yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-409">In the implementation of these providers, this static parameter directs the type provider to use the schema information in the specified local file instead of accessing the data source over the network.</span></span> <span data-ttu-id="c5a1b-410">Önbelleğe alınmış şema bilgilerini kullanmak için, statik parametre `ForceUpdate` `false`olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-410">To use cached schema information, you must also set the static parameter `ForceUpdate` to `false`.</span></span> <span data-ttu-id="c5a1b-411">Çevrimiçi ve çevrimdışı veri erişimini etkinleştirmek için benzer bir teknik kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-411">You could use a similar technique to enable online and offline data access.</span></span>

### <a name="backing-assembly"></a><span data-ttu-id="c5a1b-412">Derleme yedekleniyor</span><span class="sxs-lookup"><span data-stu-id="c5a1b-412">Backing Assembly</span></span>

<span data-ttu-id="c5a1b-413">Bir `.dll` veya `.exe` dosyası derlerken, oluşturulan türler için yedekleme. dll dosyası, elde edilen derlemeye statik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-413">When you compile a `.dll` or `.exe` file, the backing .dll file for generated types is statically linked into the resulting assembly.</span></span> <span data-ttu-id="c5a1b-414">Bu bağlantı, ara dil (IL) türü tanımlarını ve yönetilen herhangi bir kaynağı, yedekleme derlemesinden son derlemeye kopyalayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-414">This link is created by copying the Intermediate Language (IL) type definitions and any managed resources from the backing assembly into the final assembly.</span></span> <span data-ttu-id="c5a1b-415">Etkileşimli 'yı kullandığınızda F# , yedekleme. dll dosyası kopyalanmaz ve bunun yerine doğrudan F# etkileşimli işleme yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-415">When you use F# Interactive, the backing .dll file isn't copied and is instead loaded directly into the F# Interactive process.</span></span>

### <a name="exceptions-and-diagnostics-from-type-providers"></a><span data-ttu-id="c5a1b-416">Tür sağlayıcılarından özel durumlar ve Tanılamalar</span><span class="sxs-lookup"><span data-stu-id="c5a1b-416">Exceptions and Diagnostics from Type Providers</span></span>

<span data-ttu-id="c5a1b-417">Belirtilen türlerden tüm üyelerin tüm kullanımları özel durumlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-417">All uses of all members from provided types may throw exceptions.</span></span> <span data-ttu-id="c5a1b-418">Her durumda, bir tür sağlayıcı bir özel durum oluşturursa, ana bilgisayar derleyicisi hatayı belirli bir tür sağlayıcısına göre öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-418">In all cases, if a type provider throws an exception, the host compiler attributes the error to a specific type provider.</span></span>

- <span data-ttu-id="c5a1b-419">Tür sağlayıcısı özel durumları asla iç derleyici hatalarına neden olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-419">Type provider exceptions should never result in internal compiler errors.</span></span>

- <span data-ttu-id="c5a1b-420">Tür sağlayıcıları uyarıları bildirememektedir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-420">Type providers can't report warnings.</span></span>

- <span data-ttu-id="c5a1b-421">Bir tür sağlayıcısı F# derleyicide, bir F# geliştirme ortamında veya F# etkileşimli olarak barındırılıyorsa, söz konusu sağlayıcıdan gelen tüm özel durumlar yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-421">When a type provider is hosted in the F# compiler, an F# development environment, or F# Interactive, all exceptions from that provider are caught.</span></span> <span data-ttu-id="c5a1b-422">Ileti özelliği her zaman hata metindir ve yığın izlemesi görünmez.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-422">The Message property is always the error text, and no stack trace appears.</span></span> <span data-ttu-id="c5a1b-423">Bir özel durum oluşturacaksanız şu örnekleri atabilirsiniz: `System.NotSupportedException`, `System.IO.IOException``System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-423">If you’re going to throw an exception, you can throw the following examples: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.</span></span>

#### <a name="providing-generated-types"></a><span data-ttu-id="c5a1b-424">Oluşturulan türleri sağlama</span><span class="sxs-lookup"><span data-stu-id="c5a1b-424">Providing Generated Types</span></span>

<span data-ttu-id="c5a1b-425">Şimdiye kadar bu belgede, silinen türlerin nasıl sağlanması açıklanmıştı.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-425">So far, this document has explained how to provide erased types.</span></span> <span data-ttu-id="c5a1b-426">Ayrıca, ' de F# tür sağlayıcısı mekanizmasını kullanarak, kullanıcıların programına gerçek .net tür tanımları olarak eklenen üretilmiş türleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-426">You can also use the type provider mechanism in F# to provide generated types, which are added as real .NET type definitions into the users' program.</span></span> <span data-ttu-id="c5a1b-427">Bir tür tanımı kullanarak oluşturulan sağlanmış türlere başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-427">You must refer to generated provided types by using a type definition.</span></span>

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

<span data-ttu-id="c5a1b-428">F# 3,0 sürümünün parçası olan ProvidedTypes-0,2 yardımcı kodu yalnızca oluşturulan türleri sağlamak için sınırlı desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-428">The ProvidedTypes-0.2 helper code that is part of the F# 3.0 release has only limited support for providing generated types.</span></span> <span data-ttu-id="c5a1b-429">Oluşturulan bir tür tanımı için aşağıdaki deyimler doğru olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-429">The following statements must be true for a generated type definition:</span></span>

- <span data-ttu-id="c5a1b-430">`isErased` `false`olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-430">`isErased` must be set to `false`.</span></span>

- <span data-ttu-id="c5a1b-431">Oluşturulan tür, oluşturulan kod parçaları için bir kapsayıcıyı temsil eden yeni oluşturulmuş bir `ProvidedAssembly()`eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-431">The generated type must be added to a newly constructed `ProvidedAssembly()`, which represents a container for generated code fragments.</span></span>

- <span data-ttu-id="c5a1b-432">Sağlayıcıda, diskte eşleşen bir. dll dosyası olan gerçek bir .NET. dll dosyasına sahip bir derleme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-432">The provider must have an assembly that has an actual backing .NET .dll file with a matching .dll file on disk.</span></span>

## <a name="rules-and-limitations"></a><span data-ttu-id="c5a1b-433">Kurallar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="c5a1b-433">Rules and Limitations</span></span>

<span data-ttu-id="c5a1b-434">Tür sağlayıcılarını yazdığınızda aşağıdaki kuralları ve sınırlamaları aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-434">When you write type providers, keep the following rules and limitations in mind.</span></span>

### <a name="provided-types-must-be-reachable"></a><span data-ttu-id="c5a1b-435">Belirtilen türlere ulaşılabilir olmalıdır</span><span class="sxs-lookup"><span data-stu-id="c5a1b-435">Provided types must be reachable</span></span>

<span data-ttu-id="c5a1b-436">Tüm sağlanmış türler, iç içe olmayan türlerden ulaşılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-436">All provided types should be reachable from the non-nested types.</span></span> <span data-ttu-id="c5a1b-437">İç içe olmayan türler `TypeProviderForNamespaces` oluşturucusuna yapılan çağrıda veya bir `AddNamespace`çağrısıyla verilir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-437">The non-nested types are given in the call to the `TypeProviderForNamespaces` constructor or a call to `AddNamespace`.</span></span> <span data-ttu-id="c5a1b-438">Örneğin, sağlayıcı `StaticClass.P : T`bir tür sağlıyorsa, T 'nin iç içe geçmiş olmayan bir tür ya da bir iç içe geçmiş olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-438">For example, if the provider provides a type `StaticClass.P : T`, you must ensure that T is either a non-nested type or nested under one.</span></span>

<span data-ttu-id="c5a1b-439">Örneğin, bazı sağlayıcılardan bu `T1, T2, T3, ...` türlerini içeren `DataTypes` gibi bir statik sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-439">For example, some providers have a static class such as `DataTypes` that contain these `T1, T2, T3, ...` types.</span></span> <span data-ttu-id="c5a1b-440">Aksi takdirde hata, derleme A 'da T türüne başvurunun bulunduğunu söyler, ancak tür Bu derlemede bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-440">Otherwise, the error says that a reference to type T in assembly A was found, but the type couldn't be found in that assembly.</span></span> <span data-ttu-id="c5a1b-441">Bu hata görünürse, tüm alt türlerine sağlayıcı türlerinden ulaşılamadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-441">If this error appears, verify that all your subtypes can be reached from the provider types.</span></span> <span data-ttu-id="c5a1b-442">Note: Bu `T1, T2, T3...` türler *, hareket halindeyken* türler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-442">Note: These `T1, T2, T3...` types are referred to as the *on-the-fly* types.</span></span> <span data-ttu-id="c5a1b-443">Bunları erişilebilir bir ad alanına veya üst türe getirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-443">Remember to put them in an accessible namespace or a parent type.</span></span>

### <a name="limitations-of-the-type-provider-mechanism"></a><span data-ttu-id="c5a1b-444">Tür sağlayıcısı mekanizmasıyla ilgili sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="c5a1b-444">Limitations of the Type Provider Mechanism</span></span>

<span data-ttu-id="c5a1b-445">İçindeki F# tür sağlayıcı mekanizması aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-445">The type provider mechanism in F# has the following limitations:</span></span>

- <span data-ttu-id="c5a1b-446">İçindeki F# tür sağlayıcılarının temeldeki altyapısı, sağlanmış genel türleri veya sağlanmış genel yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-446">The underlying infrastructure for type providers in F# doesn't support provided generic types or provided generic methods.</span></span>

- <span data-ttu-id="c5a1b-447">Mekanizması statik parametrelerle iç içe geçmiş türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-447">The mechanism doesn't support nested types with static parameters.</span></span>

## <a name="development-tips"></a><span data-ttu-id="c5a1b-448">Geliştirme İpuçları</span><span class="sxs-lookup"><span data-stu-id="c5a1b-448">Development Tips</span></span>

<span data-ttu-id="c5a1b-449">Geliştirme sürecinde aşağıdaki ipuçlarını yararlı bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-449">You might find the following tips helpful during the development process:</span></span>

### <a name="run-two-instances-of-visual-studio"></a><span data-ttu-id="c5a1b-450">Visual Studio 'nun iki örneğini çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c5a1b-450">Run two instances of Visual Studio</span></span>

<span data-ttu-id="c5a1b-451">Test IDE, tür sağlayıcının yeniden oluşturulmasını önleyen. dll dosyasında bir kilit alacak olduğundan, tür sağlayıcısını bir örnek içinde geliştirebilir ve sağlayıcıyı başka bir örnekte test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-451">You can develop the type provider in one instance and test the provider in the other because the test IDE will take a lock on the .dll file that prevents the type provider from being rebuilt.</span></span> <span data-ttu-id="c5a1b-452">Bu nedenle, sağlayıcı ilk örnekte derlenirken Visual Studio 'nun ikinci örneğini kapatmanız gerekir ve ardından sağlayıcı oluşturulduktan sonra ikinci örneği yeniden açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-452">Thus, you must close the second instance of Visual Studio while the provider is built in the first instance, and then you must reopen the second instance after the provider is built.</span></span>

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a><span data-ttu-id="c5a1b-453">FSC. exe ' nin etkinleştirmeleri kullanılarak tür sağlayıcılarının hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="c5a1b-453">Debug type providers by using invocations of fsc.exe</span></span>

<span data-ttu-id="c5a1b-454">Aşağıdaki araçları kullanarak tür sağlayıcılarını çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5a1b-454">You can invoke type providers by using the following tools:</span></span>

- <span data-ttu-id="c5a1b-455">FSC. exe ( F# komut satırı derleyicisi)</span><span class="sxs-lookup"><span data-stu-id="c5a1b-455">fsc.exe (The F# command line compiler)</span></span>

- <span data-ttu-id="c5a1b-456">fsi. exe ( F# etkileşimli derleyici)</span><span class="sxs-lookup"><span data-stu-id="c5a1b-456">fsi.exe (The F# Interactive compiler)</span></span>

- <span data-ttu-id="c5a1b-457">Devenv. exe (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="c5a1b-457">devenv.exe (Visual Studio)</span></span>

<span data-ttu-id="c5a1b-458">Bir test betik dosyasında (örneğin, Script. FSX) FSC. exe ' yi kullanarak genellikle tür sağlayıcılarının hatalarını kolayca ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-458">You can often debug type providers most easily by using fsc.exe on a test script file (for example, script.fsx).</span></span> <span data-ttu-id="c5a1b-459">Bir komut isteminden bir hata ayıklayıcı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-459">You can launch a debugger from a command prompt.</span></span>

```console
devenv /debugexe fsc.exe script.fsx
```

  <span data-ttu-id="c5a1b-460">Print-stdout günlük kaydını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-460">You can use print-to-stdout logging.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5a1b-461">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a1b-461">See also</span></span>

- [<span data-ttu-id="c5a1b-462">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c5a1b-462">Type Providers</span></span>](index.md)
- [<span data-ttu-id="c5a1b-463">Tür sağlayıcısı SDK 'Sı</span><span class="sxs-lookup"><span data-stu-id="c5a1b-463">The Type Provider SDK</span></span>](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
