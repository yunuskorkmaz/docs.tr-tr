---
title: 'Öğretici: tür sağlayıcısı oluşturma'
description: "Temel kavramları göstermek üzere çeşitli basit tür sağlayıcılarını inceleyerek F # 3,0 ' de kendi F # tür sağlayıcılarını oluşturmayı öğrenin."
ms.date: 11/04/2019
ms.openlocfilehash: 71225614ed983a76d35c214faa87bbad0fbb7d24
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810878"
---
# <a name="tutorial-create-a-type-provider"></a>Öğretici: tür sağlayıcısı oluşturma

F # içindeki tür sağlayıcısı mekanizması, bilgi zengin programlama desteğinin önemli bir parçasıdır. Bu öğreticide, temel kavramları göstermek için çeşitli basit tür sağlayıcılarının geliştirilmesi sırasında kendi tür sağlayıcılarınızın nasıl oluşturulduğu açıklanmaktadır. F # içindeki tür sağlayıcısı mekanizması hakkında daha fazla bilgi için bkz. [tür sağlayıcıları](index.md).

F # ekosistemi, yaygın olarak kullanılan Internet ve kurumsal veri Hizmetleri için bir dizi tür sağlayıcı içerir. Örnek:

- [FSharp. Data](https://fsharp.github.io/FSharp.Data/) , JSON, XML, CSV ve HTML belge biçimleri için tür sağlayıcıları içerir.

- [SqlProvider](https://fsprojects.github.io/SQLProvider/) , bu veri kaynaklarında bir nesne eşlemesi ve F # LINQ SORGULARı aracılığıyla SQL veritabanlarına kesin olarak belirlenmiş erişim sağlar.

- [FSharp. Data. SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) , F # ' de T-SQL ' y i, derleme zamanında denetlenmiş ekleme için bir dizi tür sağlayıcıya sahiptir.

- [FSharp. Data. TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) , yalnızca SQL, Entity Framework, OData ve wsdl veri hizmetlerine erişim için .NET Framework programlamayla birlikte kullanılmak üzere daha eski bir tür sağlayıcıları kümesidir.

Gerektiğinde, özel tür sağlayıcıları oluşturabilir veya diğerlerinin oluşturduğu tür sağlayıcılarına başvurabilirsiniz. Örneğin, kuruluşunuz her biri kendi kararlı veri şemasına sahip büyük ve artan sayıda adlandırılmış veri kümesi sağlayan bir veri hizmetine sahip olabilir. Şemaları okuyan ve geçerli veri kümelerini programcıya kesin olarak belirlenmiş bir şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.

## <a name="before-you-start"></a>Başlamadan önce

Tür sağlayıcısı mekanizması öncelikle F # programlama deneyimine ekleme kararlı veriler ve hizmet bilgileri alanları için tasarlanmıştır.

Bu mekanizma, program yürütmesi sırasında, program mantığıyla ilgili şekilde, şema değişiklikleri olan ekleme bilgi alanları için tasarlanmamıştır. Ayrıca, bu etki alanı geçerli kullanımlar içerse de mekanizma, dil içi meta programlama için tasarlanmamıştır. Bu mekanizmayı yalnızca gerektiğinde ve bir tür sağlayıcının geliştirilmesi çok yüksek değer veren bir şekilde kullanmanız gerekir.

Bir şemanın kullanılamadığı bir tür sağlayıcısı yazmadan kaçınmanız gerekir. Benzer şekilde, normal (veya hatta var olan) bir .NET kitaplığının yeterli olacağı bir tür sağlayıcısını yazmadan kaçınmanız gerekir.

Başlamadan önce aşağıdaki soruları sorabilirsiniz:

- Bilgi kaynağınız için bir şemanız mı var? Öyleyse, F # ve .NET türü sistemine ne tür bir eşleme yapılır?

- Uygulamanız için bir başlangıç noktası olarak var olan (dinamik olarak yazılmış) bir API kullanabilir miyim?

- Siz ve kuruluşunuz, yazma sağlayıcısını bir süre sonra yazmak için yeterli sayıda kullanımlarına sahip olacak mı? Normal bir .NET kitaplığı gereksinimlerinizi karşılayacak mı?

- Şemanız ne kadar değişir?

- Kodlama sırasında değişsin mi?

- Kodlama oturumları arasında değişiklik olacak mı?

- Program yürütme sırasında değişsin mi?

Tür sağlayıcıları, şemanın çalışma zamanında ve derlenmiş kodun kullanım ömrü boyunca tutarlı olduğu durumlara en iyi şekilde uygundur.

## <a name="a-simple-type-provider"></a>Basit tür sağlayıcısı

Bu örnek, `examples` [F # tür sağlayıcısı SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)dizinindeki örneklere benzer şekilde Samples. HelloWorldTypeProvider ' dır. Aşağıdaki kod, F # imza söz dizimini kullanarak ve dışındaki tüm ayrıntıları atlayarak gösterildiği gibi, sağlayıcı 100 silinmiş türler içeren bir "tür alanı" kullanılabilir hale getirir `Type1` . Silinen türler hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [silinen sağlanmış türler hakkındaki ayrıntılara](#details-about-erased-provided-types) bakın.

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

Belirtilen tür ve üyelerin kümesinin statik olarak bilindiğine unutmayın. Bu örnek, sağlayıcıların bir şemaya bağlı olan türleri sağlama özelliğinden yararlanır. Tür sağlayıcısı 'nın uygulanması aşağıdaki kodda özetlenmiştir ve Ayrıntılar bu konunun sonraki bölümlerinde ele alınmıştır.

> [!WARNING]
> Bu kod ile çevrimiçi örnekler arasında farklılıklar olabilir.

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

Bu sağlayıcıyı kullanmak için Visual Studio 'nun ayrı bir örneğini açın, bir F # betiği oluşturun ve ardından aşağıdaki kodun gösterdiği gibi #r kullanarak betiğinizden sağlayıcıya bir başvuru ekleyin:

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

Daha sonra `Samples.HelloWorldTypeProvider` tür sağlayıcısının oluşturduğu ad alanı altındaki türleri arayın.

Sağlayıcıyı yeniden yapılandırmadan önce, Visual Studio 'nun tüm örneklerini ve sağlayıcı DLL 'yi kullanan F# Etkileşimli kapattığınızdan emin olun. Aksi takdirde, çıkış DLL 'SI kilitlendiğinden bir yapı hatası oluşur.

Print deyimlerini kullanarak bu sağlayıcıda hata ayıklamak için, sağlayıcıda bir sorun ortaya çıkaran bir betik oluşturun ve ardından aşağıdaki kodu kullanın:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Visual Studio 'yu kullanarak bu sağlayıcıda hata ayıklamak için, Visual Studio Geliştirici Komut İstemi yönetici kimlik bilgileriyle açın ve şu komutu çalıştırın:

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternatif olarak, Visual Studio 'yu açın, hata ayıkla menüsünü açın, `Debug/Attach to process…` öğesini seçin ve `devenv` komut dosyanızı düzenlemekte olduğunuz başka bir işleme ekleyin. Bu yöntemi kullanarak, ikinci örneğe (tam IntelliSense ve diğer özelliklerle) kolayca ifade yazarak tür sağlayıcıda belirli mantığı daha kolay bir şekilde hedefleyebilirsiniz.

Oluşturulan koddaki hataları daha iyi tanımlamak için Yalnızca kendi kodum hata ayıklamayı devre dışı bırakabilirsiniz. Bu özelliğin nasıl etkinleştirileceği veya devre dışı bırakılacağı hakkında bilgi için bkz. [hata ayıklayıcıyla kod aracılığıyla gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger). Ayrıca, `Debug` menüyü açıp `Exceptions` veya Ctrl + Alt + E tuşlarını seçerek veya iletişim kutusunu açmak için bir kez daha seçerek, birinci şans özel durum yakalama 'yı da ayarlayabilirsiniz `Exceptions` . Bu iletişim kutusunda, altında `Common Language Runtime Exceptions` , `Thrown` onay kutusunu işaretleyin.

### <a name="implementation-of-the-type-provider"></a>Tür sağlayıcısı 'nın uygulanması

Bu bölümde, tür sağlayıcısı uygulamasının asıl bölümlerinde adım adım gösterilmektedir. İlk olarak, türü özel tür sağlayıcının kendisi için tanımlarsınız:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Bu tür ortak olmalıdır ve bu türü [TypeProvider](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderattribute.html) özniteliğiyle işaretlemeniz gerekir; böylece derleyici, ayrı bir F # projesi türü içeren derlemeye başvurduğunda tür sağlayıcısını tanıyacaktır. *Yapılandırma* parametresi isteğe bağlıdır ve varsa, F # derleyicisinin oluşturduğu tür sağlayıcısı örneği için bağlamsal yapılandırma bilgilerini içerir.

Daha sonra, [ITypeInfo arabirimini Uygularınızda](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-itypeprovider.html) . Bu durumda, `TypeProviderForNamespaces` türü `ProvidedTypes` API 'den temel tür olarak kullanırsınız. Bu yardımcı türü, her biri doğrudan sınırlı sayıda sabit, ekip tarafından sağlanmış tür içeren bir dizi sağlanmış ad alanı için sınırlı bir koleksiyon sağlayabilir. Bu *bağlamda sağlayıcı,* gerekli olmasalar veya kullanılmasa bile türler oluşturur.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Ardından, belirtilen türler için ad alanını belirten yerel özel değerleri tanımlayın ve tür sağlayıcısı derlemesini bulun. Bu derleme daha sonra, belirtilen silinen türlerin mantıksal üst türü olarak kullanılır.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Sonra, type1... her bir türü sağlamak için bir işlev oluşturun. Type100. Bu işlev, bu konunun ilerleyen kısımlarında daha ayrıntılı olarak açıklanmıştır.

```fsharp
let makeOneProvidedType (n:int) = …
```

Ardından, belirtilen 100 türünü oluşturun:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Sonra, türleri bir belirtilen ad alanı olarak ekleyin:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Son olarak, bir tür sağlayıcısı DLL 'SI oluşturduğunuz bir derleme özniteliği ekleyin:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Bir tür ve üyelerini sağlama

`makeOneProvidedType`İşlevi, türlerin birini sağlamanın gerçek işini yapar.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Bu adım, bu işlevin uygulamasını açıklar. İlk olarak, belirtilen türü oluşturun (örneğin, type1, ne zaman n = 1, ne zaman Type57, n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Aşağıdaki noktaları dikkate almanız gerekir:

- Bu sunulan tür silindi.  Temel türün olduğunu gösterdiğiniz, `obj` örnekler derlenmiş kodda [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) türünde değerler olarak görünür.

- İç içe olmayan bir tür belirttiğinizde, derlemeyi ve ad alanını belirtmeniz gerekir. Silinen türler için derleme, tür sağlayıcısı derlemesinin kendisi olmalıdır.

Sonra, türe XML belgesi ekleyin. Bu belge geciktiğinde, diğer bir deyişle, konak derleyicisine ihtiyaç duyduğunda isteğe bağlı olarak hesaplanır.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Daha sonra, bir sağlanmış statik özelliği türüne eklersiniz:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Bu özelliğin alınması, her zaman "Merhaba!" dizesi olarak değerlendirilir. `GetterCode`Özelliği için, ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu temsil eden bir F # teklifini kullanır. Alıntılar hakkında daha fazla bilgi için bkz. [kod teklifleri (F #)](../../language-reference/code-quotations.md).

Özelliğe XML belgesi ekleyin.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Şimdi, belirtilen özelliği belirtilen türe ekleyin. Belirtilen üyeyi bir ve yalnızca bir türe bağlamanız gerekir. Aksi takdirde, üyeye hiçbir şekilde erişilemeyecektir.

```fsharp
t.AddMember staticProp
```

Şimdi parametre alan bir belirtilen Oluşturucu oluşturun.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode`Oluşturucu için, Oluşturucu çağrıldığında konak derleyicisinin oluşturduğu kodu temsil eden bir F # teklifini döndürür. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10()
```

Belirtilen türde bir örnek, "nesne verileri" temel alınan verilerle oluşturulur. Alıntılanmış kod, bu verilen türün (belirtilen türü bildirdiğiniz sırada belirttiğiniz şekilde) bu tür için bir değer olduğu için [obj](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-obj.html) 'e bir dönüştürme içerir.

Oluşturucuya XML belgesi ekleyin ve verilen oluşturucuyu belirtilen türe ekleyin:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Bir parametre alan ikinci bir sağlanmış Oluşturucu oluşturun:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode`Oluşturucusunun yeniden için, ana bilgisayar derleyicisinin metoda bir çağrı için oluşturduğu kodu temsil eden bir F # teklifini döndürür. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10("ten")
```

Belirtilen türde bir örnek, "on" temel alınan verilerle oluşturulur. `InvokeCode`İşlevin bir teklif döndürdüğünü zaten fark etmiş olabilirsiniz. Bu işlevin girişi, Oluşturucu parametresi başına bir ifade listesidir. Bu durumda, tek parametre değerini temsil eden bir ifade ' de kullanılabilir `args.[0]` . Oluşturucuya yapılan bir çağrının kodu, döndürülen değeri silinen türe zorlar `obj` . İkinci sağlanmış oluşturucuyu türe ekledikten sonra, bir sağlanmış örnek özelliği oluşturursunuz:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Bu özelliğin alınması, Gösterim nesnesi olan dize uzunluğunu döndürür. `GetterCode`Özelliği, ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu belirten bir F # teklifini döndürür. Benzer şekilde `InvokeCode` , `GetterCode` işlev bir alıntı döndürür. Ana bilgisayar derleyicisi, bu işlevi bir bağımsız değişken listesiyle çağırır. Bu durumda, bağımsız değişkenler yalnızca, alıcı çağrıldığında, kullanarak erişebileceğiniz örneği temsil eden tek bir ifade içerir `args.[0]` . `GetterCode`Daha sonra, silinen türdeki sonuç teklifine daha sonra uygulanması `obj` ve derleyicinin nesnenin bir dize olduğu türleri denetlemek için mekanizmayı karşılamak üzere bir dönüştürme kullanılır. Bir sonraki bölümü, `makeOneProvidedType` tek parametreli bir örnek yöntemi sağlar.

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

Son olarak, 100 iç içe geçmiş özellikler içeren bir iç içe türü oluşturun. Bu iç içe türün oluşturulması ve özellikleri gecikmiştir, diğer bir deyişle isteğe bağlı olarak hesaplanır.

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

### <a name="details-about-erased-provided-types"></a>Silinen sağlanmış türler hakkındaki ayrıntılar

Bu bölümdeki örnek yalnızca *silinmiş sağlanan türleri*sağlar ve aşağıdaki durumlarda özellikle yararlı olur:

- Yalnızca veri ve yöntemleri içeren bir bilgi alanı için sağlayıcı yazarken.

- Doğru çalışma zamanı türü semantiğinin, bilgi alanının pratik kullanımı açısından kritik olmadığı bir sağlayıcı yazarken.

- Daha büyük bir bilgi alanı için bir sağlayıcı yazarken ve bilgi alanı için gerçek .NET türleri üretmek için teknik olarak uygun olmayan bir şekilde.

Bu örnekte, belirtilen her tür türü olarak silinir `obj` ve türün tüm kullanımları derlenmiş kodda tür olarak görünür `obj` . Aslında, bu örneklerdeki temeldeki nesneler dizelerdir, ancak tür `System.Object` .net derlenen kodda olduğu gibi görünecektir. ERASURE türünde tüm kullanımlar sayesinde, açık kutulamayı, kutudan çıkarma ve çıkarma türlerini alt alta yazmak için öğesini kullanabilirsiniz. Bu durumda, geçerli olmayan bir dönüştürme özel durumu, nesne kullanıldığında ortaya çıkabilir. Sağlayıcı çalışma zamanı, yanlış gösterimlerine karşı korumaya yardımcı olmak için kendi özel gösterim türünü tanımlayabilir. Silinen türleri F # içinde tanımlayamazsınız. Yalnızca sunulan türler silinebilir. Tür sağlayıcınız için silinen türler veya silinen türler sağlayan bir sağlayıcı kullanarak hem pratik hem de anlamsal olan sonuçları anlamanız gerekir. Silinen bir türün gerçek bir .NET türü yoktur. Bu nedenle, türü üzerinde doğru yansıma yapılamaz ve çalışma zamanı yayınlarını ve tam çalışma zamanı türü semantiğini kullanan diğer teknikleri kullanırsanız, silinen türleri alt dikey alabilirsiniz. Silinen türlerin alt sürümü sıklıkla çalışma zamanında tür atama özel durumlarına neden olur.

### <a name="choosing-representations-for-erased-provided-types"></a>Silinen sağlanmış türler için gösterimler seçme

Silinen bazı türlerin kullanımları için hiçbir temsili gerekmez. Örneğin, silinen sağlanmış tür yalnızca statik özellikler ve Üyeler ve hiçbir Oluşturucu içerebilir; hiçbir yöntem veya özellik türün bir örneğini döndürmez. Silinen bir tür örneğe ulaşabilseniz, aşağıdaki soruları göz önünde bulundurmanız gerekir:

**Bir belirtilen türün silinme nedir?**

- Bir belirtilen türün silinme türü derlenmiş .net kodunda nasıl görünür?

- Belirtilen silinen bir sınıf türünün silinme her zaman türün devralma zincirindeki ilk silinmeyen temel türdür.

- Belirtilen silinen bir arabirim türünün silinme her zaman olur `System.Object` .

**Belirtilen türde temsiller nelerdir?**

- Silinmiş bir sağlanmış tür için olası nesneler kümesi, temsilleri olarak adlandırılır. Bu belgedeki örnekte, tüm silinen sağlanmış türlerin gösterimleri `Type1..Type100` her zaman dize nesneleridir.

Bir belirtilen türün tüm temsilleri, belirtilen türün silinme ile uyumlu olmalıdır. (Aksi halde, F # derleyicisi tür sağlayıcısı kullanımı için bir hata verir veya geçerli olmayan doğrulanamayan .NET kodu oluşturulur. Bir tür sağlayıcısı geçerli olmayan bir temsili veren kodu döndürürse geçerli değildir.)

Aşağıdaki yaklaşımlardan birini kullanarak, sunulan nesneler için bir temsili seçebilirsiniz, her ikisi de çok yaygındır:

- Yalnızca var olan bir .NET türü üzerinde kesin olarak belirlenmiş bir sarmalayıcı sağlıyorsanız, bu, genellikle bu türde silme, söz konusu türün örneklerini temsiller veya her ikisi için de anlamlı hale getirir. Bu yaklaşım, bu tür üzerindeki mevcut yöntemlerin büyük bir kısmının, kesin olarak belirlenmiş sürümü kullanırken hala anlamlı hale geldiğinde uygundur.

- Var olan herhangi bir .NET API 'sinden önemli ölçüde farklı bir API oluşturmak istiyorsanız, belirtilen türler için tür ve gösterimler olacak çalışma zamanı türleri oluşturmak mantıklı olur.

Bu belgedeki örnek, dizeleri, belirtilen nesnelerin temsilleri olarak kullanır. Genellikle, diğer nesneleri temsiller için kullanmak uygun olabilir. Örneğin, bir sözlüğü özellik paketi olarak kullanabilirsiniz:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternatif olarak, bir veya daha fazla çalışma zamanı işlemiyle birlikte, temsili oluşturmak için çalışma zamanında kullanılacak tür sağlayıcınızda bir tür tanımlayabilirsiniz:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Daha sonra, belirtilen Üyeler bu nesne türünün örneklerini oluşturabilir:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Bu durumda, (isteğe bağlı olarak), bu türü oluştururken aşağıdaki gibi belirterek bu türü bir tür olarak kullanabilirsiniz `baseType` `ProvidedTypeDefinition` :

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Temel dersler

Önceki bölümde, bir dizi türü, özelliği ve yöntemi sağlayan basit bir silme türü sağlayıcısı oluşturma konusu açıklanmaktadır. Bu bölümde ayrıca, bir tür sağlayıcısından silinen türler sağlamanın avantajları ve dezavantajları ve silinen türlerin açıklanabileceği avantajlar da dahil olmak üzere ERASURE türü kavramı açıklanmıştı.

## <a name="a-type-provider-that-uses-static-parameters"></a>Statik parametreleri kullanan bir tür sağlayıcısı

Statik veriler tarafından tür sağlayıcılarını Parametreleştirme özelliği, sağlayıcının herhangi bir yerel veya uzak veriye erişmesi gerekmeyen durumlarda bile çok sayıda ilginç senaryo sağlar. Bu bölümde, bir sağlayıcıyı bir araya getirmek için bazı temel tekniklerin öğrenirsiniz.

### <a name="type-checked-regex-provider"></a>Denetlenen Regex sağlayıcısını yazın

<xref:System.Text.RegularExpressions.Regex>Aşağıdaki derleme zamanı garantisi sağlayan bir arabirimdeki .net kitaplıklarını sarmalayan normal ifadeler için bir tür sağlayıcısı uygulamak istediğinizi düşünelim:

- Normal bir ifadenin geçerli olup olmadığı doğrulanıyor.

- Normal ifadede herhangi bir grup adına dayalı eşleşmeler üzerinde adlandırılmış özellikler sağlama.

Bu bölümde, bu `RegexTyped` avantajları sağlamak üzere normal ifade deseninin parametreleştiren bir tür oluşturmak için tür sağlayıcılarının nasıl kullanılacağı gösterilmektedir. Sağlanan model geçerli değilse derleyici bir hata bildirir ve tür sağlayıcısı, eşleşmeler üzerinde adlandırılmış özellikler kullanarak erişebilmek için grupları düzeninden ayıklayabilir. Bir tür sağlayıcısı tasarladığınızda, sunulan API 'nin son kullanıcılara nasıl bakacağınızı ve bu tasarımın .NET koduna nasıl çevrileceğini göz önünde bulundurmanız gerekir. Aşağıdaki örnek, bu tür bir API 'nin, alan kodu bileşenlerini almak için nasıl kullanılacağını gösterir:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Aşağıdaki örnek, tür sağlayıcısının bu çağrıları nasıl dönüştürdüğünde gösterir:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Aşağıdaki noktalara dikkat edin:

- Standart Regex türü parametreli türü temsil eder `RegexTyped` .

- `RegexTyped`Oluşturucu, bir normal ifade oluşturucusuna çağrı ile sonuçlanır ve bu da, düzenin statik tür bağımsız değişkenini geçer.

- `Match`Yönteminin sonuçları standart tür ile temsil edilir <xref:System.Text.RegularExpressions.Match> .

- Her bir adlandırılmış Grup, belirtilen bir özellik ile sonuçlanır ve özelliğe erişilmesi, bir eşleşmenin koleksiyonunda bir dizin oluşturucunun kullanılmasına neden olur `Groups` .

Aşağıdaki kod, bu tür bir sağlayıcıyı uygulayan mantığın çekirdekdir ve bu örnek, tüm üyelerin eklenmesi belirtilen türe atlar. Eklenen her üye hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki ilgili bölüme bakın. Tam kod için, CodePlex Web sitesindeki [F # 3,0 örnek paketinden](https://archive.codeplex.com/?p=fsharp3sample) örneği indirin.

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

Aşağıdaki noktalara dikkat edin:

- Tür sağlayıcısı iki statik parametre alır: zorunlu olan `pattern` ve, `options` isteğe bağlı olan (varsayılan bir değer sağlandığı için).

- Statik bağımsız değişkenler sağlandığında, normal ifadenin bir örneğini oluşturursunuz. Bu örnek, Regex yanlış biçimlendirilmişse bir özel durum oluşturur ve bu hata kullanıcılara bildirilir.

- `DefineStaticParameters`Geri çağırma içinde, bağımsız değişkenler sağlandıktan sonra döndürülecek türü tanımlarsınız.

- `HideObjectMethods`IntelliSense deneyiminin kolaylaştırmaya devam edebilmesi için bu kod doğru olarak ayarlanır. Bu öznitelik,, `Equals` , `GetHashCode` `Finalize` ve üyelerinin, `GetType` belirtilen bir nesne için IntelliSense listelerinden gizlenmesine neden olur.

- `obj`Yöntemin temel türü olarak kullanırsınız, ancak bir `Regex` sonraki örnekte gösterildiği gibi bu türün çalışma zamanı temsili olarak bir nesnesi kullanırsınız.

- Bir `Regex` normal ifade geçerli olmadığında oluşturucuya yapılan çağrı bir oluşturur <xref:System.ArgumentException> . Derleyici bu özel durumu yakalar ve derleme zamanında veya Visual Studio Düzenleyicisi 'nde kullanıcıya bir hata mesajı bildirir. Bu özel durum, normal ifadelerin bir uygulama çalıştırmadan doğrulanmasını sağlar.

Yukarıda tanımlanan tür hiçbir anlamlı Yöntem veya özellik içermediğinden henüz yararlı değildir. İlk olarak, statik bir `IsMatch` Yöntem ekleyin:

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

Önceki kod `IsMatch` , girdi olarak bir dize alan ve döndüren bir yöntemi tanımlar `bool` . Tek karmaşık bölüm, `args` tanım içindeki bağımsız değişkenin kullanımı `InvokeCode` . Bu örnekte, `args` Bu yöntemin bağımsız değişkenlerini temsil eden tekliflerin bir listesidir. Yöntem bir örnek yöntemi ise, ilk bağımsız değişken bağımsız değişkenini temsil eder `this` . Ancak, bir statik yöntem için bağımsız değişkenler yalnızca yöntemin açık bağımsız değişkenlerinden biridir. Alıntılanmış değerin türünün belirtilen dönüş türüyle (Bu durumda) eşleşmesi gerektiğini unutmayın `bool` . Ayrıca, bu kodun, `AddXmlDoc` IntelliSense aracılığıyla sağlayabilmeniz için, sunulan yöntemin de yararlı belgeler içerdiğinden emin olmak için yöntemini kullandığını unutmayın.

Sonra bir örnek eşleşme yöntemi ekleyin. Ancak, bu yöntem, `Match` grupların kesin olarak belirlenmiş bir biçimde erişilebilmesi için, belirtilen türde bir değer döndürmelidir. Bu nedenle, önce türü bildirirsiniz `Match` . Bu tür statik bir bağımsız değişken olarak sağlanan modele bağlı olduğundan, bu tür parametreli tür tanımı içinde iç içe olmalıdır:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Sonra her grup için eşleşme türüne bir özellik eklersiniz. Çalışma zamanında, bir eşleşme değer olarak temsil edildiğinde <xref:System.Text.RegularExpressions.Match> , özelliği tanımlayan teklifin <xref:System.Text.RegularExpressions.Match.Groups> ilgili grubu almak için dizinlenmiş özelliği kullanması gerekir.

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

Yine, XML belgelerini verilen özelliğe eklebileceğinizi unutmayın. Ayrıca bir işlev sağlanmışsa bir özelliğin okunabilmesi `GetterCode` ve bir `SetterCode` işlev sağlandıysa özelliğin yazılabileceği, sonuçta elde edilen özelliğin salt okunurdur.

Artık bu türden bir değer döndüren bir örnek yöntemi oluşturabilirsiniz `Match` :

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

Bir örnek yöntemi oluştururken, `args.[0]` `RegexTyped` yöntemin çağrıldığı örneği temsil eder ve `args.[1]` giriş bağımsız değişkenidir.

Son olarak, belirtilen türdeki örneklerin oluşturulabilmesi için bir Oluşturucu sağlayın.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Oluşturucu yalnızca, bir nesneye yeniden paketlenmiş standart bir .NET Regex örneği oluşturulmasını siler, çünkü bu, `obj` belirtilen türün erasiyidir. Bu değişiklik ile, konusunda daha önce belirtilen örnek API kullanımı beklendiği gibi çalışmaktadır. Aşağıdaki kod tamamlandı ve son:

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

### <a name="key-lessons"></a>Temel dersler

Bu bölümde, statik parametrelerinde çalışan bir tür sağlayıcısı oluşturma konusu açıklanmaktadır. Sağlayıcı statik parametreyi denetler ve değerini temel alarak işlemler sağlar.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Yerel veriler tarafından desteklenen bir tür sağlayıcısı

Genellikle, tür sağlayıcılarının API 'Leri yalnızca statik parametrelere değil, yerel veya uzak sistemlerden da sunmalarına izin vermek isteyebilirsiniz. Bu bölümde yerel veri dosyaları gibi yerel verileri temel alan tür sağlayıcıları açıklanmaktadır.

### <a name="simple-csv-file-provider"></a>Basit CSV dosya sağlayıcısı

Basit bir örnek olarak, virgülle ayrılmış değer (CSV) biçiminde bilimsel verilere erişmek için bir tür sağlayıcısı düşünün. Bu bölümde, aşağıdaki tabloda gösterildiği gibi, CSV dosyalarının bir başlık satırı ve ardından kayan nokta verilerinin bulunduğu varsayılmaktadır:

|Uzaklık (ölçüm)|Süre (saniye)|
|----------------|-------------|
|50.0|3.7|
|100,0|5,2|
|150,0|6.4|

Bu bölümde, `Distance` türünde bir özelliği `float<meter>` ve türünde bir özelliği olan satırları almak için kullanabileceğiniz bir türün nasıl sağlayacağınız gösterilmektedir `Time` `float<second>` . Basitlik için aşağıdaki varsayımlar yapılır:

- Üst bilgi adları, birim-daha küçüktür veya "ad (birim)" biçiminde ve virgül içermez.

- [FSharp. Data. UnitSystems. sı. UnitNames modülü (F #)](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitnames.html) modülünün tanımladığı birimler, tüm sistem uluslararası (sı) birimleridir.

- Birimler, bileşik yerine (örneğin, ölçüm/saniye) tamamen basittir.

- Tüm sütunlar kayan nokta verileri içerir.

Daha kapsamlı bir sağlayıcı bu kısıtlamaları gevyordu.

İlk adım, API 'nin nasıl görüneceğini düşünmelidir. `info.csv`Önceki tablodaki içeriğe sahip bir dosya (virgülle ayrılmış biçimde) verildiğinde, sağlayıcının kullanıcıları aşağıdaki örneğe benzer bir kod yazamayacak:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Bu durumda, derleyici bu çağrıları aşağıdaki örnekteki gibi bir şeye dönüştürmelidir:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

En uygun çeviri tür sağlayıcısının tür sağlayıcısının derlemesinde gerçek bir tür tanımlamasını gerektirir `CsvFile` . Tür sağlayıcıları, önemli mantığı kaydırmak için genellikle birkaç yardımcı türü ve yöntemi kullanır. Ölçüler çalışma zamanında silindiğinden, bir `float[]` satır için silinmiş tür olarak bir kullanabilirsiniz. Derleyici farklı sütunları farklı ölçü türlerine sahip olacak şekilde değerlendirir. Örneğin, örneğimizde ilk sütunda tür `float<meter>` ve ikincisi vardır `float<second>` . Ancak, silinen temsili oldukça basit kalabilir.

Aşağıdaki kod, uygulamanın çekirdeğini gösterir.

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

Uygulamayla ilgili aşağıdaki noktaları dikkate alın:

- Aşırı yüklenmiş oluşturucular, özgün dosyanın veya özdeş bir şemaya sahip olan birinin okunmasını sağlar. Bu model, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazdığınızda yaygındır ve bu model yerel bir dosyanın uzak veriler için şablon olarak kullanılmasına izin verir.

- Göreli dosya adlarını çözümlemek için tür sağlayıcısı oluşturucusuna geçirilen [TypeProviderConfig](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-compilerservices-typeproviderconfig.html) değerini kullanabilirsiniz.

- `AddDefinitionLocation`Yöntemi, belirtilen özelliklerin konumunu tanımlamak için kullanabilirsiniz. Bu nedenle, `Go To Definition` sağlanmış bir özellik üzerinde kullanıyorsanız, CSV dosyası Visual Studio 'da açılır.

- `ProvidedMeasureBuilder`Türü, sı birimleri aramak ve ilgili türleri oluşturmak için kullanabilirsiniz `float<_>` .

### <a name="key-lessons"></a>Temel dersler

Bu bölümde, veri kaynağının içinde bulunan basit bir şemaya sahip bir yerel veri kaynağı için bir tür sağlayıcısı oluşturma konusu açıklanmaktadır.

## <a name="going-further"></a>Daha fazla

Aşağıdaki bölümler, daha fazla çalışma için öneriler içerir.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Silinen türler için derlenmiş koda göz atın

Tür sağlayıcısının kullanımına yayılan koda karşılık gelen bir fikir vermek için, `HelloWorldTypeProvider` Bu konunun önceki kısımlarında kullanılan öğesini kullanarak aşağıdaki işleve bakın.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

ildasm.exe kullanarak, ortaya çıkan ve derlenmiş kodun bir görüntüsü aşağıda verilmiştir:

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

Örnekte gösterildiği gibi, türünün ve özelliğinin tüm bahsetmeler silinmiş `Type1` ve `InstanceProperty` yalnızca ilgili çalışma zamanı türlerinde işlemler bırakılıyor.

### <a name="design-and-naming-conventions-for-type-providers"></a>Tür sağlayıcıları için tasarım ve adlandırma kuralları

Tür sağlayıcıları yazarken aşağıdaki kuralları gözlemleyin.

**Bağlantı protokolleri Için sağlayıcılar** Genel olarak, veri ve hizmet bağlantı protokollerinin (OData veya SQL bağlantıları gibi) çoğu için sağlayıcı dll 'Lerinin adları veya ile bitmelidir `TypeProvider` `TypeProviders` . Örneğin, aşağıdaki dizeye benzer bir DLL adı kullanın:

`Fabrikam.Management.BasicTypeProviders.dll`

Belirttiğiniz türlerin karşılık gelen ad alanının üyesi olduğundan emin olun ve uygulanan bağlantı protokolünü belirtin:

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Genel kodlama Için yardımcı program sağlayıcıları**.  Normal ifadeler gibi bir yardımcı program türü sağlayıcı için, aşağıdaki örnekte gösterildiği gibi tür sağlayıcısı bir temel kitaplığın parçası olabilir:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Bu durumda, sunulan tür normal .NET tasarım kurallarına göre uygun bir noktada görünür:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Tek veri kaynakları**. Bazı tür sağlayıcıları tek bir ayrılmış veri kaynağına bağlanır ve yalnızca verileri sağlar. Bu durumda, `TypeProvider` son eki bırakmalısınız ve .net adlandırma için normal kuralları kullanmanız gerekir:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Daha fazla bilgi için, `GetConnection` Bu konunun ilerleyen kısımlarında açıklanan tasarım kuralına bakın.

### <a name="design-patterns-for-type-providers"></a>Tür sağlayıcıları için tasarım desenleri

Aşağıdaki bölümlerde, tür sağlayıcıları yazarken kullanabileceğiniz tasarım desenleri açıklanır.

#### <a name="the-getconnection-design-pattern"></a>GetConnection tasarım deseninin

`GetConnection`Aşağıdaki örnekte gösterildiği gibi, FSharp.Data.TypeProviders.dll tür sağlayıcıları tarafından kullanılan kalıbı kullanmak için çoğu tür sağlayıcı yazılmalıdır:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Uzak veri ve hizmetler tarafından desteklenen tür sağlayıcıları

Uzak veri ve hizmetler tarafından desteklenen bir tür sağlayıcısı oluşturmadan önce, bağlı programlamaya ait bir dizi sorunu düşünmeniz gerekir. Bu sorunlar aşağıdaki konuları içerir:

- Şema eşleme

- şema değişikliği durumunda liilte ve geçersiz kılma

- şema önbelleğe alma

- veri erişim işlemlerinin zaman uyumsuz uygulamaları

- LINQ sorguları dahil destekleyici sorgular

- kimlik bilgileri ve kimlik doğrulama

Bu konu, bu sorunları daha ayrıntılı bir şekilde araştırmaz.

### <a name="additional-authoring-techniques"></a>Ek yazma teknikleri

Kendi tür sağlayıcılarınızı yazdığınızda, aşağıdaki ek teknikleri kullanmak isteyebilirsiniz.

### <a name="creating-types-and-members-on-demand"></a>Istek üzerine türler ve Üyeler oluşturma

ProvidedType API 'SI, AddMember 'ın gecikmeli sürümlerini içerir.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Bu sürümler, türlerin isteğe bağlı alanlarını oluşturmak için kullanılır.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Dizi türleri ve genel tür örneklemeleri sağlama

, `MakeArrayType` `MakePointerType` , Ve `MakeGenericType` dahil olmak üzere herhangi bir örneğinde normal,, ve ' <xref:System.Type> yi `ProvidedTypeDefinitions` kullanarak, belirtilen üyeleri (imzaları dizi türleri, ByRef türleri ve genel türlerin örneklemeleri dahil) yaparsınız.

> [!NOTE]
> Bazı durumlarda, içinde yardımcı kullanmanız gerekebilir `ProvidedTypeBuilder.MakeGenericType` .  Daha fazla bilgi için bkz. [tür sağlayıcısı SDK belgeleri](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) .

### <a name="providing-unit-of-measure-annotations"></a>Ölçü birimi ek açıklamaları sağlama

ProvidedTypes API 'SI, ölçü ek açıklamaları sağlamak için yardımcılar sağlar. Örneğin, türü sağlamak için `float<kg>` aşağıdaki kodu kullanın:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Türü sağlamak için `Nullable<decimal<kg/m^2>>` aşağıdaki kodu kullanın:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Proje-yerel veya betiğe yerel kaynaklara erişme

Bir tür sağlayıcının her örneğine, `TypeProviderConfig` oluşturma sırasında bir değer verilebilir. Bu değer, sağlayıcının "çözüm klasörünü" içerir (yani, derleme için proje klasörü veya bir betiği içeren dizin), başvurulan derlemelerin listesi ve diğer bilgiler.

### <a name="invalidation"></a>Geçersiz kılma

Sağlayıcılar, F # dil hizmetini şema varsayımına değiştiği hakkında bilgilendirmek için doğrulama sinyalleri oluşturabilir. Invalidation gerçekleştiğinde, sağlayıcı Visual Studio 'da barındırılıyorsa bir typecheck, yinelendi olur. Bu sinyal, sağlayıcı F# Etkileşimli veya F # derleyicisi (fsc.exe) tarafından barındırılıyorsa yok sayılır.

### <a name="caching-schema-information"></a>Şema bilgilerini önbelleğe alma

Sağlayıcılar genellikle şema bilgilerine erişimi önbelleğe almalıdır. Önbelleğe alınan veriler, statik bir parametre veya Kullanıcı verileri olarak verilen bir dosya adı kullanılarak depolanmalıdır. Şema önbelleğe alma örneği, `LocalSchemaFile` derlemedeki tür sağlayıcılarındaki parametredir `FSharp.Data.TypeProviders` . Bu statik parametre, bu sağlayıcıları uygulamada, tür sağlayıcısını ağ üzerinden veri kaynağına erişmek yerine, belirtilen yerel dosyadaki şema bilgilerini kullanacak şekilde yönlendirir. Önbelleğe alınmış şema bilgilerini kullanmak için statik parametresini olarak da ayarlamanız gerekir `ForceUpdate` `false` . Çevrimiçi ve çevrimdışı veri erişimini etkinleştirmek için benzer bir teknik kullanabilirsiniz.

### <a name="backing-assembly"></a>Derleme yedekleniyor

Bir `.dll` veya `.exe` dosyası derlerken, oluşturulan türler için yedekleme. dll dosyası, sonuçta elde edilen derlemeye statik olarak bağlanır. Bu bağlantı, ara dil (IL) türü tanımlarını ve yönetilen herhangi bir kaynağı, yedekleme derlemesinden son derlemeye kopyalayarak oluşturulur. F# Etkileşimli kullandığınızda, yedekleme. dll dosyası kopyalanmaz ve bunun yerine doğrudan F# Etkileşimli işleme yüklenir.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Tür sağlayıcılarından özel durumlar ve Tanılamalar

Belirtilen türlerden tüm üyelerin tüm kullanımları özel durumlar oluşturabilir. Her durumda, bir tür sağlayıcı bir özel durum oluşturursa, ana bilgisayar derleyicisi hatayı belirli bir tür sağlayıcısına göre öznitelikler.

- Tür sağlayıcısı özel durumları asla iç derleyici hatalarına neden olmamalıdır.

- Tür sağlayıcıları uyarıları bildirememektedir.

- Bir tür sağlayıcısı F # derleyicisinde, F # geliştirme ortamında veya F# Etkileşimli barındırıldığı zaman, o sağlayıcıdan gelen tüm özel durumlar yakalanır. Ileti özelliği her zaman hata metindir ve yığın izlemesi görünmez. Bir özel durum oluşturacaksanız aşağıdaki örnekleri atabilirsiniz: `System.NotSupportedException` , `System.IO.IOException` , `System.Exception` .

#### <a name="providing-generated-types"></a>Oluşturulan türleri sağlama

Şimdiye kadar bu belgede, silinen türlerin nasıl sağlanması açıklanmıştı. Ayrıca, kullanıcıların programına gerçek .NET tür tanımları olarak eklenen üretilmiş türleri sağlamak için F # içinde tür sağlayıcısı mekanizmasını kullanabilirsiniz. Bir tür tanımı kullanarak oluşturulan sağlanmış türlere başvurmanız gerekir.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

F # 3,0 sürümünün parçası olan ProvidedTypes-0,2 yardımcı kodu yalnızca oluşturulan türleri sağlamak için sınırlı desteğe sahiptir. Oluşturulan bir tür tanımı için aşağıdaki deyimler doğru olmalıdır:

- `isErased` olarak ayarlanmalıdır `false` .

- Oluşturulan tür, `ProvidedAssembly()` oluşturulan kod parçaları için bir kapsayıcıyı temsil eden yeni oluşturulmuş bir şekilde eklenmiş olmalıdır.

- Sağlayıcıda, diskte eşleşen bir. dll dosyası olan gerçek bir .NET. dll dosyasına sahip bir derleme olmalıdır.

## <a name="rules-and-limitations"></a>Kurallar ve sınırlamalar

Tür sağlayıcılarını yazdığınızda aşağıdaki kuralları ve sınırlamaları aklınızda bulundurun.

### <a name="provided-types-must-be-reachable"></a>Belirtilen türlere ulaşılabilir olmalıdır

Tüm sağlanmış türler, iç içe olmayan türlerden ulaşılabilir olmalıdır. İç içe olmayan türler, oluşturucuya yapılan çağrıda veya öğesine yapılan çağrıda verilir `TypeProviderForNamespaces` `AddNamespace` . Örneğin, sağlayıcı bir tür sağlıyorsa `StaticClass.P : T` T 'nin, iç içe olmayan bir tür ya da bir iç içe geçmiş olduğundan emin olmanız gerekir.

Örneğin, bazı sağlayıcılardan bu türleri içeren gibi bir statik sınıf vardır `DataTypes` `T1, T2, T3, ...` . Aksi takdirde hata, derleme A 'da T türüne başvurunun bulunduğunu söyler, ancak tür Bu derlemede bulunamadı. Bu hata görünürse, tüm alt türlerine sağlayıcı türlerinden ulaşılamadığından emin olun. Note: Bu `T1, T2, T3...` türler *, hareket halindeyken* türler olarak adlandırılır. Bunları erişilebilir bir ad alanına veya üst türe getirmeyi unutmayın.

### <a name="limitations-of-the-type-provider-mechanism"></a>Tür sağlayıcısı mekanizmasıyla ilgili sınırlamalar

F # içindeki tür sağlayıcısı mekanizması aşağıdaki sınırlamalara sahiptir:

- F # içindeki tür sağlayıcıları için temeldeki altyapı, sağlanmış genel türleri veya sağlanmış genel yöntemleri desteklemez.

- Mekanizması statik parametrelerle iç içe geçmiş türleri desteklemez.

## <a name="development-tips"></a>Geliştirme İpuçları

Geliştirme sürecinde aşağıdaki ipuçlarını yararlı bulabilirsiniz:

### <a name="run-two-instances-of-visual-studio"></a>Visual Studio 'nun iki örneğini çalıştırın

Test IDE, tür sağlayıcının yeniden oluşturulmasını önleyen. dll dosyasında bir kilit alacak olduğundan, tür sağlayıcısını bir örnek içinde geliştirebilir ve sağlayıcıyı başka bir örnekte test edebilirsiniz. Bu nedenle, sağlayıcı ilk örnekte derlenirken Visual Studio 'nun ikinci örneğini kapatmanız gerekir ve ardından sağlayıcı oluşturulduktan sonra ikinci örneği yeniden açmanız gerekir.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>fsc.exe etkinleştirmeleri kullanarak tür sağlayıcılarını hata ayıkla

Aşağıdaki araçları kullanarak tür sağlayıcılarını çağırabilirsiniz:

- fsc.exe (F # komut satırı derleyicisi)

- fsi.exe (F# Etkileşimli derleyicisi)

- devenv.exe (Visual Studio)

Genellikle, tür sağlayıcılarının bir test betik dosyasında fsc.exe kullanarak en kolay şekilde hata ayıklaması yapabilirsiniz (örneğin, Script. FSX). Bir komut isteminden bir hata ayıklayıcı başlatabilirsiniz.

```console
devenv /debugexe fsc.exe script.fsx
```

  Print-stdout günlük kaydını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Sağlayıcıları](index.md)
- [Tür sağlayıcısı SDK 'Sı](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
