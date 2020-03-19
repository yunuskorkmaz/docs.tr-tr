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
# <a name="tutorial-create-a-type-provider"></a>Öğretici: Tür Sağlayıcısı Oluşturma

F#'daki tür sağlayıcı mekanizması, bilgi açısından zengin programlama ya da destek desteğinin önemli bir parçasıdır. Bu öğretici, temel kavramları göstermek için birkaç basit tür sağlayıcıların geliştirilmesi ile size yol göstererek kendi türü sağlayıcıları oluşturmak için nasıl açıklar. F#'daki tür sağlayıcı mekanizması hakkında daha fazla bilgi için [Bkz.](index.md)

F# ekosistemi, yaygın olarak kullanılan Internet ve kurumsal veri hizmetleri için çeşitli tür sağlayıcıları içerir. Örnek:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON, XML, CSV ve HTML belge biçimleri için tür sağlayıcıları içerir.

- [SQLProvider,](https://fsprojects.github.io/SQLProvider/) nesne eşleme ve f# LINQ sorguları aracılığıyla bu veri kaynaklarına karşı güçlü bir şekilde daktio erişim sağlar.

- [FSharp.Data.SqlClient,](https://fsprojects.github.io/FSharp.Data.SqlClient/) T-SQL'in F#'da zaman kontrol edilmiş gömmesini derlemek için bir dizi tür sağlayıcısına sahiptir.

- [FSharp.Data.TypeProviders,](https://fsprojects.github.io/FSharp.Data.TypeProviders/) SQL, Entity Framework, OData ve WSDL veri hizmetlerine erişmek için yalnızca .NET Framework programlama ile kullanılmak üzere eski bir tür sağlayıcıları kümesidir.

Gerektiğinde, özel tür sağlayıcıları oluşturabilir veya başkalarının oluşturduğu tür sağlayıcılarına başvuruda bulunabilirsiniz. Örneğin, kuruluşunuzun her biri kendi kararlı veri şeması olan çok sayıda adlandırılmış veri kümesi sağlayan bir veri hizmeti olabilir. Şemaları okuyan ve geçerli veri kümelerini programcıya güçlü bir şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.

## <a name="before-you-start"></a>Başlamadan Önce

Tür sağlayıcı mekanizması öncelikle F# programlama deneyimine kararlı veri ve hizmet bilgi alanları enjekte etmek için tasarlanmıştır.

Bu mekanizma, program yürütme sırasında şema ları program mantığıyla ilgili şekillerde değişen bilgi alanlarını enjekte etmek için tasarlanmıyor. Ayrıca, bu etki alanı bazı geçerli kullanımlar içerse bile, mekanizma dil içi meta programlama için tasarlanmamıştır. Bu mekanizmayı yalnızca gerektiğinde ve bir tür sağlayıcısının geliştirilmesinin çok yüksek değer elde ettiği durumlarda kullanmalısınız.

Şema nın kullanılamadığı bir tür sağlayıcısı yazmaktan kaçınmalısınız. Aynı şekilde, sıradan (hatta varolan) .NET kitaplığı yeterli olacağını bir tür sağlayıcı yazmaktan kaçınmalısınız.

Başlamadan önce aşağıdaki soruları sorabilirsiniz:

- Bilgi kaynağınız için bir şema nız var mı? Eğer öyleyse, F# ve .NET tip sistemine haritalama nedir?

- Uygulamanız için başlangıç noktası olarak varolan (dinamik olarak daktive) API'yi kullanabilir misiniz?

- Siz ve kuruluşunuz, yazıyazmaya değer kılmak için tür sağlayıcının yeterli kullanımına sahip olacak mı? Normal bir .NET kitaplığı ihtiyaçlarınızı karşılar mı?

- Şemane ne kadar değişecek?

- Kodlama sırasında değişecek mi?

- Kodlama oturumları arasında değişecek mi?

- Program yürütme sırasında değişecek mi?

Tür sağlayıcıları, şemanın çalışma zamanında ve derlenmiş kodun ömrü boyunca kararlı olduğu durumlar için en uygun olandır.

## <a name="a-simple-type-provider"></a>Basit Bir Tür Sağlayıcı

Bu örnek Samples.HelloWorldTypeProvider, `examples` [F# Türü Sağlayıcı SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK/)dizini örneklerine benzer. Sağlayıcı, f# imza sözdizimini kullanarak ve hariç tüm ayrıntıları atlayarak aşağıdaki kodun gösterdiği gibi, 100 `Type1`silinmiş türü içeren bir "tür alanı" sunar. Silinen türler hakkında daha fazla bilgi için, bu konunun ilerleyen saatlerinde [Silinen Sağlanan Türler Hakkında Ayrıntılar'a](#details-about-erased-provided-types) bakın.

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

Sağlanan tür ve üye kümesinin statik olarak bilindiğini unutmayın. Bu örnek, sağlayıcıların şemaya bağlı türleri sağlama yeteneğinden yararlanmaz. Tür sağlayıcısının uygulanması aşağıdaki kodda özetlenmiştir ve ayrıntılar bu konunun sonraki bölümlerinde ele alınmıştır.

> [!WARNING]
> Bu kod ve çevrimiçi örnekler arasında farklılıklar olabilir.

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

Bu sağlayıcıyı kullanmak için Visual Studio'nun ayrı bir örneğini açın, bir F# komut dosyası oluşturun ve ardından aşağıdaki kodun gösterdiği gibi #r kullanarak komut dosyanızdan sağlayıcıya bir başvuru ekleyin:

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

Ardından, tür sağlayıcısının `Samples.HelloWorldTypeProvider` oluşturduğu ad alanı altındaki türleri arayın.

Sağlayıcıyı yeniden derlemeden önce, sağlayıcı DLL'yi kullanan Visual Studio ve F# Interactive'in tüm örneklerini kapattığınızdan emin olun. Aksi takdirde, çıkış DLL kilitli olacak, çünkü bir yapı hatası oluşur.

Yazdırma deyimleri kullanarak bu sağlayıcının hata sını ayıklamak için, sağlayıcıyla ilgili bir sorunu ortaya çıkaran bir komut dosyası yapın ve ardından aşağıdaki kodu kullanın:

```console
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Visual Studio'yu kullanarak bu sağlayıcının hatasını ayıklamak için, Visual Studio için Geliştirici Komut Komut Ustem'ini yönetim kimlik bilgileriyle açın ve aşağıdaki komutu çalıştırın:

```console
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternatif olarak Visual Studio'yu açın, Hata `Debug/Attach to process…`Ayıklama menüsünü `devenv` açın, komut dosyanızı düzenlediğiniz başka bir işleme seçin ve diğer bir işleme takın. Bu yöntemi kullanarak, ikinci örnekiçine ifadeleri etkileşimli olarak yazarak (tam IntelliSense ve diğer özelliklerle) tür sağlayıcısındaki belirli mantığı daha kolay hedefleyebilirsiniz.

Oluşturulan koddaki hataları daha iyi tanımlamak için Just My Code hata ayıklamadevre dışı bırakabilirsiniz. Bu özelliği etkinleştirme veya devre dışı etme hakkında bilgi için [hata ayıklayıcıyla Kod da Gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger)bölümüne bakın. Ayrıca, menüyü `Debug` açıp iletişim kutusunu açmak `Exceptions` `Exceptions` için Ctrl+Alt+E tuşlarını seçerek veya seçerek ilk şans özel durum yakalamayı da ayarlayabilirsiniz. Bu iletişim kutusunda, `Common Language Runtime Exceptions`altında , `Thrown` onay kutusunu seçin.

### <a name="implementation-of-the-type-provider"></a>Tip Sağlayıcının Uygulanması

Bu bölüm, tür sağlayıcı uygulamasının temel bölümleri boyunca size yol gösterir. İlk olarak, özel tür sağlayıcısıkendisi için türü tanımlarsınız:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Bu tür ortak olmalıdır ve derleyici türü içeren derleme derleme başvurur tür sağlayıcısı tanıyacak şekilde [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) özniteliği ile işaretlemeniz gerekir. *Config* parametresi isteğe bağlıdır ve varsa, F# derleyicisinin oluşturduğu tür sağlayıcı örneği için bağlamsal yapılandırma bilgileri içerir.

Ardından, [ITypeProvider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) arabirimini uygularsınız. Bu durumda, `TypeProviderForNamespaces` `ProvidedTypes` API'deki türü temel türü olarak kullanırsınız. Bu yardımcı türü, her biri doğrudan sınırlı sayıda sabit, hevesle sağlanan türleri içeren hevesle sağlanan ad alanlarının sınırlı bir koleksiyon sağlayabilir. Bu bağlamda, *sağlayıcı* gerekli olmasa veya kullanılmasa bile hevesle türleri oluşturur.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Ardından, sağlanan türler için ad alanını belirten yerel özel değerleri tanımlayın ve tür sağlayıcı derlemesinin kendisini bulun. Bu derleme daha sonra sağlanan silinmiş türlerin mantıksal üst türü olarak kullanılır.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Ardından, Type1 türlerinin her birini sağlamak için bir işlev oluşturun... Tip100. Bu işlev daha sonra bu konuda daha ayrıntılı olarak açıklanmıştır.

```fsharp
let makeOneProvidedType (n:int) = …
```

Ardından, sağlanan 100 türü oluşturun:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Ardından, sağlanan ad alanı olarak türleri ekleyin:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Son olarak, bir tür sağlayıcısı DLL oluşturduğunuzu gösteren bir derleme özniteliği ekleyin:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Tek Tip Ve Üyeleri Sağlama

İşlev, `makeOneProvidedType` türlerden birini sağlama nın gerçek işini yapar.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Bu adım, bu işlevin uygulanmasını açıklar. İlk olarak, sağlanan türü oluşturun (örneğin, Type1, ne zaman n = 1, veya Type57, ne zaman n = 57).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Aşağıdaki noktalara dikkat edin:

- Bu sağlanan tür silinir.  Temel türünün , `obj`örneklerin derlenmiş koddaki [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) türü değerleri olarak görüneceğini belirttiğiiçin.

- İç içe olmayan bir tür belirttiğiniz zaman, derlemeve ad alanını belirtmeniz gerekir. Silinen türler için, derleme türü sağlayıcı derlemenin kendisi olmalıdır.

Ardından, türüne XML belgeleri ekleyin. Bu dokümantasyon geciktirilir, diğer bir şekilde, ana bilgisayar derleyicisinin ihtiyacı varsa isteğe bağlı olarak hesaplanır.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Sonra türüne sağlanan statik özellik ekleyin:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Bu özelliği almak her zaman dize "Merhaba!" olarak değerlendirecektir. `GetterCode` Özellik için, ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu temsil eden bir F# alıntısı kullanır. Teklifler hakkında daha fazla bilgi için [Kod Alıntıları (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155)bölümüne bakın.

Tesise XML belgeleri ekleyin.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Şimdi sağlanan özelliği sağlanan türe takın. Sağlanan bir üyeyi bir ve yalnızca bir türe eklemeniz gerekir. Aksi takdirde, üyeye hiçbir zaman erişilemez.

```fsharp
t.AddMember staticProp
```

Şimdi hiçbir parametre gerektiren sağlanan bir oluşturucu oluşturun.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

Oluşturucu `InvokeCode` için, oluşturucu çağrıldığında ev sahibiderleyicinin oluşturduğu kodu temsil eden bir F# teklifi döndürür. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10()
```

Sağlanan tür bir örnek altta yatan veri "nesne verileri" ile oluşturulur. Teklif edilen kod, bu tür bu sağlanan türün silinmesi olduğundan (sağlanan türü beyan ettiğinizde belirttiğiniz gibi) [obj'ye](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) dönüştürme içerir.

Oluşturucuya XML belgeleri ekleyin ve sağlanan oluşturucuyu sağlanan türe ekleyin:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Bir parametre alan ikinci bir sağlanan oluşturucu oluşturun:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

Oluşturucu `InvokeCode` için yine, ana bilgisayar derleyicisinin yönteme çağrı için oluşturduğu kodu temsil eden bir F# teklifi döndürür. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10("ten")
```

Sağlanan tür bir örnek altta yatan veri "on" ile oluşturulur. İşlevin `InvokeCode` bir teklif döndürür önceden fark etmiş olabilirsiniz. Bu işleve giriş, yapılayıcı parametresi başına bir ifade listesidir. Bu durumda, tek parametre değerini temsil eden `args.[0]`bir ifade . Oluşturucuya yapılan bir çağrının kodu, silinen türe `obj`iade değerini zorlar. İkinci sağlanan oluşturucuyu türe ekledikten sonra, sağlanan bir örnek özelliği oluşturursunuz:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Bu özelliği almak, temsil nesnesi olan dize uzunluğunu döndürecektir. Özellik, `GetterCode` ana bilgisayar derleyicisinin özelliği almak için oluşturduğu kodu belirten bir F# teklifi döndürür. Gibi `InvokeCode`, `GetterCode` işlev bir teklif döndürür. Ana bilgisayar derleyicisi bu işlevi bağımsız değişkenlerin listesiyle çağırır. Bu durumda, bağımsız değişkenler, gönderenin çağrıldığı örneği temsil eden ve kullanarak `args.[0]`erişebileceğiniz tek bir ifadeyi içerir. Daha `GetterCode` sonra silinen türde `obj`sonuç teklif içine splices uygulanması ve bir döküm nesnebir dize olduğunu türleri denetlemek için derleyici mekanizmasını karşılamak için kullanılır. Bir sonraki `makeOneProvidedType` bölümü bir parametre ile bir örnek yöntemi sağlar.

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

Son olarak, 100 iç içe özellikleri içeren iç içe bir tür oluşturun. Bu iç içe tür ve özellikleri, yani isteğe bağlı olarak hesaplanan, gecikti.

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

### <a name="details-about-erased-provided-types"></a>Silinen Sağlanan Türler Hakkında Ayrıntılar

Bu bölümdeki örnek, özellikle aşağıdaki durumlarda yararlı olan yalnızca *silinmiş sağlanan türleri*sağlar:

- Yalnızca veri ve yöntem içeren bir bilgi alanı için bir sağlayıcı yazarken.

- Doğru çalışma zamanı türü semantik bilgi alanının pratik kullanımı için kritik olmayan bir sağlayıcı yazarken.

- Bir bilgi alanı için bir sağlayıcı yazarken, bilgi alanı için gerçek .NET türleri oluşturmak teknik olarak mümkün değildir.

Bu örnekte, sağlanan her tür `obj`türü türüne silinir ve türün tüm kullanımları derlenmiş kodda tür olarak `obj` görünür. Aslında, bu örneklerde altta yatan nesneler dizeleri, ancak `System.Object` türü .NET derlenmiş kod olarak görünür. Türü silme tüm kullanımları olduğu gibi, silinmiş türleri yıkmak için açık kutulama, unboxing ve döküm kullanabilirsiniz. Bu durumda, nesne kullanıldığında geçerli olmayan bir döküm özel durum oluşabilir. Sağlayıcı çalışma süresi, yanlış temsillere karşı korunmaya yardımcı olmak için kendi özel gösterim türünü tanımlayabilir. F# kendinde silinmiş türleri tanımlayamazsınız. Yalnızca sağlanan türler silinebilir. Hem pratik hem de anlamsal olarak, türü sağlayıcınız veya silinmiş türleri sağlayan bir sağlayıcı için silinmiş türleri kullanmanın sonuçlarını anlamanız gerekir. Silinmiş bir türün gerçek .NET türü yoktur. Bu nedenle, türü üzerinde doğru yansıma yapamaz ve tam çalışma zamanı türü semantiği dayanan çalışma zamanı dökümleri ve diğer teknikleri kullanırsanız silinmiş türleri yıkmak olabilir. Silinen türlerin alt alt alt sürümü sık sık çalışma zamanında tür döküm özel durumları ile sonuçlanır.

### <a name="choosing-representations-for-erased-provided-types"></a>Silinen Sağlanan Türler için Temsiller Seçme

Silinen sağlanan türlerin bazı kullanımları için, hiçbir gösterim gereklidir. Örneğin, silinen sağlanan tür yalnızca statik özellikler ve üyeler ve hiçbir oluşturucu içerebilir ve hiçbir yöntem veya özellik türün bir örneğini döndüremez. Silinmiş sağlanan tür örneklerine ulaşabiliyorsanız, aşağıdaki soruları göz önünde bulundurmanız gerekir:

**Sağlanan bir türün silinmesi nedir?**

- Sağlanan bir türün silinmesi, derlenmiş .NET kodunda türün nasıl göründüğüdür.

- Sağlanan silinmiş sınıf türünün silinmesi, her zaman türün kalıtım zincirindeki ilk silinmeyen taban türüdür.

- Sağlanan silinmiş arabirim türünün silinmesi her zaman `System.Object`.

**Sağlanan bir türün temsilleri nelerdir?**

- Silinmiş sağlanan bir tür için olası nesnelerin kümesi, gösterimleri olarak adlandırılır. Bu belgedeki örnekte, silinen tüm sağlanan türlerin `Type1..Type100` gösterimleri her zaman dize nesneleridir.

Sağlanan türün tüm gösterimleri, sağlanan türün silinmesi ile uyumlu olmalıdır. (Aksi takdirde, F# derleyicisi tür sağlayıcısının kullanımı için bir hata verir veya geçerli olmayan doğrulanamayan .NET kodu oluşturulur. Bir tür sağlayıcısı, geçerli olmayan bir gösterim veren kodu döndürürse geçerli değildir.)

Her ikisi de çok yaygın olan aşağıdaki yaklaşımlardan birini kullanarak sağlanan nesneler için bir gösterim seçebilirsiniz:

- Yalnızca varolan bir .NET türü üzerinde güçlü bir şekilde yazılan bir sarıcı sağlıyorsanız, türünüzün bu türe silinmesi genellikle mantıklı dır, bu türdeki örnekleri temsil olarak veya her ikisi de kullanın. Bu türdeki varolan yöntemlerin çoğu güçlü bir şekilde yazılan sürümü kullanırken hala mantıklı olduğunda bu yaklaşım uygundur.

- Varolan .NET API'den önemli ölçüde farklı bir API oluşturmak istiyorsanız, sağlanan türler için tür silme ve gösterimleri olacak çalışma zamanı türleri oluşturmak mantıklıdır.

Bu belgedeki örnek, dizeleri sağlanan nesnelerin gösterimi olarak kullanır. Sık sık, gösterimleri için diğer nesneleri kullanmak uygun olabilir. Örneğin, bir sözlük özelliği çantası olarak kullanabilirsiniz:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternatif olarak, tür sağlayıcınızda gösterimi oluşturmak için çalışma zamanında kullanılacak bir tür ve bir veya daha fazla çalışma zamanı işlemi tanımlayabilirsiniz:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Sağlanan üyeler daha sonra bu nesne türüörnekleri oluşturabilirsiniz:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Bu durumda, (isteğe bağlı olarak) bu türü, aşağıdakileri yaparken bu `baseType` tür olarak `ProvidedTypeDefinition`belirterek tür silme olarak kullanabilirsiniz:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Temel Dersler

Önceki bölümde, çeşitli türler, özellikler ve yöntemler sağlayan basit bir sileme türü sağlayıcısının nasıl oluşturulacak olduğu açıklanmıştır. Bu bölümde ayrıca, bir tür sağlayıcısından silinmiş türleri sağlamanın bazı avantajları ve dezavantajları da dahil olmak üzere, tür silme kavramı açıklanmış ve silinmiş türlerin gösterimleri tartışılmıştır.

## <a name="a-type-provider-that-uses-static-parameters"></a>Statik parametreler kullanan bir tür sağlayıcısı

Tür sağlayıcılarını statik verilerle parametreleme yeteneği, sağlayıcının herhangi bir yerel veya uzak veriye erişmesi gerekmediği durumlarda bile birçok ilginç senaryoya olanak tanır. Bu bölümde, böyle bir sağlayıcı bir araya getirmek için bazı temel teknikler öğreneceksiniz.

### <a name="type-checked-regex-provider"></a>Tip İşaretli Regex Sağlayıcısı

.NET <xref:System.Text.RegularExpressions.Regex> kitaplıklarını aşağıdaki derleme zamanı garantileri sağlayan bir arabirimde saran normal ifadeler için bir tür sağlayıcısı uygulamak istediğinizi düşünün:

- Normal bir ifadenin geçerli olup olmadığını doğrulama.

- Normal ifadedeki tüm grup adlarını temel alan eşleşmelerde adlandırılmış özellikler sağlama.

Bu bölümde, normal ifade deseni `RegexTyped` bu yararları sağlamak için parametreize bir tür oluşturmak için tür sağlayıcıları nasıl kullanılacağını gösterir. Derleyici, sağlanan desen geçerli değilse bir hata bildirir ve tür sağlayıcısı, eşleşmeler üzerinde adlandırılmış özellikleri kullanarak bunlara erişebilmeniz için grupları desenden ayıklayabilir. Bir tür sağlayıcısı tasarlarken, açıkta kalan API'sinin son kullanıcılara nasıl görünmesi gerektiğini ve bu tasarımın .NET koduna nasıl çevrileceğini düşünmelisiniz. Aşağıdaki örnek, alan kodunun bileşenlerini almak için böyle bir API'nin nasıl kullanılacağını gösterir:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Aşağıdaki örnek, tür sağlayıcısının bu çağrıları nasıl çevirdiği gösterilmektedir:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Aşağıdaki noktalara dikkat edin:

- Standart Regex türü parametreli `RegexTyped` türü temsil eder.

- Oluşturucu, `RegexTyped` Regex oluşturucuya çağrı yla sonuçlanır ve desen için statik tür bağımsız değişkenini geçer.

- Yöntemin `Match` sonuçları standart <xref:System.Text.RegularExpressions.Match> türe göre temsil edilir.

- Adlandırılmış her grup, sağlanan bir özellik ile sonuçlanır ve özellik erişim, eşleşmenin `Groups` koleksiyonunda bir dizinleyici nin kullanılmasıyla sonuçlanır.

Aşağıdaki kod, böyle bir sağlayıcıyı uygulama mantığının özüdür ve bu örnek, tüm üyelerin sağlanan türe eklenmesini atlar. Eklenen her üye hakkında bilgi için, daha sonra bu konuyla ilgili ilgili bölüme bakın. Tam kod için, örneği CodePlex web sitesindeki [F# 3.0 Örnek Paketi'nden](https://archive.codeplex.com/?p=fsharp3sample) indirin.

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

- Tür sağlayıcı iki statik parametre alır: zorunlu `pattern` `options`olan , ve isteğe bağlı olan (varsayılan değer sağlandığı için).

- Statik bağımsız değişkenler sağlandıktan sonra, normal ifadenin bir örneğini oluşturursunuz. Regex yanlış biçimlendirilmişse bu örnek bir özel durum oluşturur ve bu hata kullanıcılara bildirilir.

- Geri `DefineStaticParameters` arama da, bağımsız değişkenler sağlandıktan sonra döndürülecek türü tanımlarsınız.

- Bu `HideObjectMethods` kod, IntelliSense deneyiminin düzenli kalması için gerçeğe ayarlanır. Bu `Equals`öznitelik, `GetHashCode` `Finalize` `GetType` sağlanan bir nesne için IntelliSense listelerinden bastırılmasına neden olur.

- Yöntemin `obj` temel türü olarak kullanırsınız, ancak bir `Regex` sonraki örnekte görüldüğü gibi, bu türün çalışma zamanı gösterimi olarak bir nesne kullanırsınız.

- Düzenli bir `Regex` ifade geçerli olmadığında, oluşturucuya yapılan çağrı bir <xref:System.ArgumentException> hata atar. Derleyici bu özel durumu yakalar ve derleme zamanında veya Visual Studio düzenleyicisinde kullanıcıya bir hata iletisi bildirir. Bu özel durum, normal ifadelerin bir uygulama çalıştırılmadan doğrulanmasını sağlar.

Anlamlı yöntemler veya özellikler içermediğinden, yukarıda tanımlanan tür henüz yararlı değildir. İlk olarak, `IsMatch` statik bir yöntem ekleyin:

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

Önceki kod, bir `IsMatch`dize girişi olarak alır ve `bool`bir . döndürür bir yöntem tanımlar Tek zor kısmı `args` `InvokeCode` tanım içinde argüman kullanımıdır. Bu örnekte, `args` bu yönteme bağımsız değişkenleri temsil eden tırnak listesi dir. Yöntem bir örnek yöntemi ise, ilk `this` bağımsız değişken bağımsız değişkeni temsil eder. Ancak, statik bir yöntem için, bağımsız değişkenlerin tümü yönteme açık bağımsız değişkenlerdir. Teklif edilen değerin türünün belirtilen iade türüyle eşleşmesi `bool`gerektiğini unutmayın (bu durumda). Ayrıca, bu kodun, sağlanan yöntemin IntelliSense aracılığıyla sağlayabileceğiniz yararlı belgelere sahip olduğundan emin olmak için `AddXmlDoc` bu yöntemi kullandığını unutmayın.

Ardından, örnek Eşler yöntemi ekleyin. Ancak, bu yöntem, gruplara `Match` güçlü bir şekilde yazılması için sağlanan bir tür değerini döndürmelidir. Böylece, ilk `Match` türü bildirir. Bu tür statik bağımsız değişken olarak sağlanan desenbağlıdır, bu tür parametreli tür tanımı içinde iç içe gerekir:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Daha sonra her grup için Eşler türüne bir özellik eklersiniz. Çalışma zamanında, bir eşleşme bir <xref:System.Text.RegularExpressions.Match> değer olarak temsil edilir, bu nedenle özelliği <xref:System.Text.RegularExpressions.Match.Groups> tanımlayan teklif ilgili grubu almak için dizine sahip özelliği kullanmanız gerekir.

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

Yine, sağlanan özelliğe XML belgeleri eklediğinizi unutmayın. Ayrıca, bir `GetterCode` işlev sağlanmışsa bir özelliğin okunabileceğini ve `SetterCode` bir işlev sağlanırsa özelliğin yazılabilir olduğunu, böylece ortaya çıkan özelliğin yalnızca okunduğunu unutmayın.

Şimdi bu `Match` tür bir değer döndüren bir örnek yöntemi oluşturabilirsiniz:

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

Bir örnek yöntemi `args.[0]` oluşturduğunuziçin, `RegexTyped` yöntemin çağrıldığı örneği temsil `args.[1]` eder ve giriş bağımsız değişkenidir.

Son olarak, sağlanan tür örnekleri oluşturulabilir, böylece bir oluşturucu sağlayın.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Oluşturucu yalnızca standart bir .NET Regex örneğinin oluşturulmasını siler, bu `obj` da sağlanan türün silinmesi olduğundan yine bir nesneye kutulanır. Bu değişiklikle, konunun daha önce belirtilen örnek API kullanımı beklendiği gibi çalışır. Aşağıdaki kod tamamlandı ve son oldu:

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

### <a name="key-lessons"></a>Temel Dersler

Bu bölümde, statik parametreleri üzerinde çalışan bir tür sağlayıcısının nasıl oluşturulacak olduğu açıklanmıştır. Sağlayıcı statik parametreyi denetler ve değerine göre işlem sağlar.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Yerel Verilerle Desteklenen Bir Tür Sağlayıcısı

Sık sık tür sağlayıcılarının yalnızca statik parametrelere değil, yerel veya uzak sistemlerden gelen bilgilere de dayalı OLARAK API'ler sunmasını isteyebilirsiniz. Bu bölümde, yerel veri dosyaları gibi yerel verileri temel alan tür sağlayıcıları açıklanır.

### <a name="simple-csv-file-provider"></a>Basit CSV Dosya Sağlayıcısı

Basit bir örnek olarak, Virgülle Ayrılmış Değer (CSV) biçiminde bilimsel verilere erişmek için bir tür sağlayıcısı düşünün. Bu bölümde, Aşağıdaki tabloda gösterildiği gibi, CSV dosyalarının bir üstbilgi satırı ve ardından kayan nokta verileri içerdiğini varsayar:

|Mesafe (metre)|Zaman (ikinci)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Bu bölümde, tür özelliği `Distance` ve türü `float<meter>` `Time` `float<second>`özelliği olan satırları almak için kullanabileceğiniz bir tür nasıl sağlayabileceğinizi gösterir. Basitlik için aşağıdaki varsayımlar yapılır:

- Üstbilgi adları birimden azdır veya "Ad (birim)" formuna sahiptir ve virgül içermez.

- Birimler, [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Modülü (F#) modülü](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) olarak tanımladığı tüm System International (SI) birimleridir.

- Birimler bileşik yerine (örneğin, metre/saniye) basittir.

- Tüm sütunlar kayan nokta verilerini içerir.

Daha eksiksiz bir sağlayıcı bu kısıtlamaları gevşetecektir.

Yine ilk adım, API'nin nasıl görünmesi gerektiğini göz önünde bulundurmaktır. Önceki `info.csv` tablodaki içerikleri içeren bir dosya (virgülle ayrılmış biçimde) verildiğinde, sağlayıcının kullanıcıları aşağıdaki örneğe benzeyen kod yazabilmelidir:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Bu durumda, derleyici bu çağrıları aşağıdaki örnek gibi bir şeye dönüştürmelidir:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

En uygun çeviri, tür sağlayıcısının `CsvFile` montajında gerçek bir türü tanımlamasını gerektirir. Tür sağlayıcıları genellikle önemli mantığı sarmak için birkaç yardımcı türüne ve yöntemine güvenir. Ölçüler çalışma zamanında silindiği için, `float[]` bir satır için silinmiş tür olarak bir kullanabilirsiniz. Derleyici farklı sütunları farklı ölçü türlerine sahip olarak ele alacaktır. Örneğin, örneğimizdeki ilk sütuntürü `float<meter>`vardır ve `float<second>`ikinci . Ancak, silinen gösterim oldukça basit kalabilir.

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

Uygulama yla ilgili aşağıdaki noktalara dikkat edin:

- Aşırı yüklü oluşturucular, özgün dosyanın veya aynı şemaya sahip olanın okunmasını sağlar. Bu desen, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazdığınızda yaygındır ve bu desen, uzak veri şablonu olarak yerel bir dosyanın kullanılmasına izin verir.

- Göreli dosya adlarını çözümlemek için tür sağlayıcı oluşturucuya geçirilen [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) değerini kullanabilirsiniz.

- Sağlanan özelliklerin `AddDefinitionLocation` konumunu tanımlamak için yöntemi kullanabilirsiniz. Bu nedenle, `Go To Definition` sağlanan bir özellik üzerinde kullanırsanız, CSV dosyası Visual Studio'da açılır.

- `ProvidedMeasureBuilder` Türü, SI birimlerini aramak ve ilgili `float<_>` türleri oluşturmak için kullanabilirsiniz.

### <a name="key-lessons"></a>Temel Dersler

Bu bölümde, veri kaynağının kendisinde bulunan basit bir şemaya sahip yerel bir veri kaynağı için bir tür sağlayıcısının nasıl oluşturulacak olduğu açıklanmıştır.

## <a name="going-further"></a>Daha Ileri Gitmek

Aşağıdaki bölümlerde daha fazla çalışma için öneriler yer almaktadır.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Silinen Türler İçin Derlenmiş Koda Bir Bakış

Tür sağlayıcısının kullanımının yayılan koda nasıl karşılık geldiği hakkında size bir fikir vermek için, bu `HelloWorldTypeProvider` konuda daha önce kullanılan işlevi kullanarak aşağıdaki işleve bakın.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Burada ildasm.exe kullanılarak derlenen ortaya çıkan kodun bir görüntüsü:

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

Örnekte de görüldüğü gibi, tür `Type1` ve `InstanceProperty` özellik ile ilgili tüm sözler silinmiş, yalnızca çalışma zamanı türlerinde işlemler söz konusu.

### <a name="design-and-naming-conventions-for-type-providers"></a>Tip Sağlayıcılar için Tasarım ve Adlandırma Kuralları

Tür sağlayıcılar yazarken aşağıdaki kuralları izleyin.

**Bağlantı Protokolleri Sağlayıcıları** Genel olarak, Veri ve Hizmet bağlantı protokolleri için çoğu sağlayıcı DLs adları (OData `TypeProvider` veya `TypeProviders`SQL bağlantıları gibi) veya . Örneğin, aşağıdaki dize benzer bir DLL adı kullanın:

`Fabrikam.Management.BasicTypeProviders.dll`

Sağlanan türlerinizin ilgili ad alanının üyeleri olduğundan emin olun ve uyguladığınız bağlantı iletişimini belirtin:

```fsharp
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Genel Kodlama için Yardımcı Sağlayıcılar.**  Normal ifadeler gibi bir yardımcı program türü sağlayıcısı için, tür sağlayıcısı aşağıdaki örnekte görüldüğü gibi, temel kitaplığın bir parçası olabilir:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Bu durumda, sağlanan tür normal .NET tasarım kurallarına göre uygun bir noktada görünür:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Singleton Veri Kaynakları**. Bazı tür sağlayıcıları tek bir özel veri kaynağına bağlanır ve yalnızca veri sağlar. Bu durumda, `TypeProvider` sonek bırakmalı ve .NET adlandırma için normal kuralları kullanmalısınız:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Daha fazla bilgi `GetConnection` için, bu konuda daha sonra açıklanan tasarım kuralına bakın.

### <a name="design-patterns-for-type-providers"></a>Tip Sağlayıcılar için Tasarım Desenleri

Aşağıdaki bölümlerde, tür sağlayıcılarını yazarken kullanabileceğiniz tasarım desenleri açıklanabilir.

#### <a name="the-getconnection-design-pattern"></a>GetConnection Tasarım Deseni

Çoğu tür sağlayıcı, aşağıdaki `GetConnection` örnekte görüldüğü gibi, FSharp.Data.TypeProviders.dll'deki tür sağlayıcıları tarafından kullanılan deseni kullanmak için yazılmalıdır:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Uzaktan Veri ve Hizmetlerle Desteklenen Tip Sağlayıcıları

Uzak veri ve hizmetlertarafından desteklenen bir tür sağlayıcısı oluşturmadan önce, bağlı programlamanın doğasında olan bir dizi sorunu göz önünde bulundurmanız gerekir. Bu konular şunlardır:

- şema haritalama

- şema değişimi varlığında canlılık ve geçersizlik

- şema önbelleğe alma

- veri erişim işlemlerinin eşzamanlı uygulamaları

- LINQ sorguları da dahil olmak üzere sorguları destekleyen

- kimlik bilgileri ve kimlik doğrulama

Bu konu bu konuları daha fazla araştırmaz.

### <a name="additional-authoring-techniques"></a>Ek Yazma Teknikleri

Kendi tür sağlayıcılarınızı yazarken, aşağıdaki ek teknikleri kullanmak isteyebilirsiniz.

### <a name="creating-types-and-members-on-demand"></a>İsteğe Bağlı Tür ve Üye Oluşturma

ProvidedType API, AddMember sürümlerini geciktirdi.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Bu sürümler, türlerin isteğe bağlı alanlar oluşturmak için kullanılır.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Dizi türleri ve Genel Tür Instantiations sağlama

Sağlanan üyeleri (imzaları dizi türlerini, byref türlerini ve genel türlerin anlık `MakeArrayType`asyonlarını içerir) normal `MakePointerType`, ve `MakeGenericType` herhangi bir durumda <xref:System.Type>, dahil olmak üzere `ProvidedTypeDefinitions`.

> [!NOTE]
> Bazı durumlarda yardımcıyı ' da `ProvidedTypeBuilder.MakeGenericType`kullanmak zorunda kullanabilirsiniz.  Daha fazla ayrıntı için [Tip Sağlayıcı SDK belgelerine](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) bakın.

### <a name="providing-unit-of-measure-annotations"></a>Ölçü Ek Açıklamaları Nın Sağlanması

ProvidedTypes API ölçü ek açıklamaları sağlamak için yardımcıları sağlar. Örneğin, türü `float<kg>`sağlamak için aşağıdaki kodu kullanın:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Türü `Nullable<decimal<kg/m^2>>`sağlamak için aşağıdaki kodu kullanın:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Proje-Yerel veya Komut Dosyası-Yerel Kaynaklara Erişim

Bir tür sağlayıcının her örneği `TypeProviderConfig` inşaat sırasında bir değer verilebilir. Bu değer sağlayıcı için "çözüm klasörü" (diğer bir deyişle, derleme için proje klasörü veya komut dosyası içeren dizin), başvurulan derlemeler listesi ve diğer bilgileri içerir.

### <a name="invalidation"></a>Örneğin

Sağlayıcılar, F# dil hizmetine şema varsayımlarının değişmiş olabileceğini bildirmek için geçersizik sinyallerini yükseltebilir. Geçersiz işlem meydana geldiğinde, sağlayıcı, Visual Studio' da barındırılıyorsa bir daktişçi denetimi yeniden yapılır. Sağlayıcı F# Interactive'de veya F# Derleyicisi (fsc.exe) tarafından barındırıldığında bu sinyal yoksayılır.

### <a name="caching-schema-information"></a>Önbelleğe Alma Şeması Bilgileri

Sağlayıcılar genellikle şema bilgilerine erişimi önbelleğe almalıdır. Önbelleğe alınan veriler, statik parametre olarak veya kullanıcı verisi olarak verilen bir dosya adı kullanılarak depolanmalıdır. Şema önbelleğe alma `LocalSchemaFile` `FSharp.Data.TypeProviders` örneği, derlemedeki tür sağlayıcılarındaki parametredir. Bu sağlayıcıların uygulanmasında, bu statik parametre, ağ üzerinden veri kaynağına erişmek yerine, belirtilen yerel dosyadaki şema bilgilerini kullanmaya tür sağlayıcısını yönlendirir. Önbelleğe alınmış şema bilgilerini kullanmak için statik parametreyi `ForceUpdate` `false`de . Çevrimiçi ve çevrimdışı veri erişimini etkinleştirmek için benzer bir teknik kullanabilirsiniz.

### <a name="backing-assembly"></a>Destek Montajı

Bir `.dll` veya `.exe` dosya derlediğinizde, oluşturulan türler için destek .dll dosyası statik olarak ortaya çıkan derlemeye bağlanır. Bu bağlantı, Ara Dil (IL) türü tanımları ve destek derlemesinden son derlemeye yönetilen tüm kaynaklar kopyalayarak oluşturulur. F# Interactive'i kullandığınızda, destek .dll dosyası kopyalanır ve bunun yerine doğrudan F# Interactive işlemine yüklenir.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Tip Sağlayıcılardan İstisnalar ve Tanılama

Sağlanan türdeki tüm üyelerin tüm kullanımları özel durumlar getirebilir. Her durumda, bir tür sağlayıcısı bir özel durum atarsa, ana bilgisayar derleyicisi hatayı belirli bir tür sağlayıcısına bağlar.

- Tür sağlayıcı özel durumları hiçbir zaman iç derleyici hatalarına neden olmamalıdır.

- Tür sağlayıcıları uyarıları bildiremez.

- Bir tür sağlayıcısı F# derleyicisinde, F# geliştirme ortamında veya F# Interactive'de barındırıldığında, bu sağlayıcıdan gelen tüm özel durumlar yakalanır. İleti özelliği her zaman hata metnidir ve yığın izi görünmez. Bir özel durum atacaksanız, aşağıdaki örnekleri atabilirsiniz: `System.NotSupportedException` `System.IO.IOException`, `System.Exception`, .

#### <a name="providing-generated-types"></a>Oluşturulan Türleri Sağlama

Şimdiye kadar, bu belge silinmiş türleri sağlamak için nasıl açıklanmıştır. F#'daki tür sağlayıcı mekanizmasını, kullanıcıların programına gerçek .NET türü tanımları olarak eklenen oluşturulan türleri sağlamak için de kullanabilirsiniz. Bir tür tanımı kullanarak oluşturulan türlere başvurmanız gerekir.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

F# 3.0 sürümünden bir parçası olan ProvidedTypes-0.2 yardımcı kodu, oluşturulan türleri sağlamak için yalnızca sınırlı bir desteğe sahiptir. Oluşturulan bir tür tanımı için aşağıdaki ifadeler doğru olmalıdır:

- `isErased``false`olarak ayarlanmalıdır.

- Oluşturulan tür, oluşturulan kod parçaları `ProvidedAssembly()`için bir kapsayıcıyı temsil eden yeni oluşturulan bir yapıya eklenmelidir.

- Sağlayıcı, diskte eşleşen bir .dll dosyası olan gerçek bir destek .NET .dll dosyasına sahip bir derlemeye sahip olmalıdır.

## <a name="rules-and-limitations"></a>Kurallar ve Sınırlamalar

Tür sağlayıcılar yazarken, aşağıdaki kuralları ve sınırlamaları aklınızda bulundurun.

### <a name="provided-types-must-be-reachable"></a>Sağlanan türlere ulaşılabilir olmalıdır

Sağlanan tüm türlere iç içe olmayan türlerden ulaşılabilir olmalıdır. İç içe olmayan `TypeProviderForNamespaces` türler, oluşturucuya veya ''ye `AddNamespace`çağrıda verilir. Örneğin, sağlayıcı bir tür `StaticClass.P : T`sağlıyorsa, T'nin iç içe olmayan bir tür olduğundan veya birinin altında iç içe olduğundan emin olmalısınız.

Örneğin, bazı sağlayıcılar gibi `DataTypes` statik bir `T1, T2, T3, ...` sınıf bu türleri içeren var. Aksi takdirde, hata, A derlemesinde T türüne bir başvuru bulunduğunu, ancak bu derlemede türün bulunamadığını söyler. Bu hata görünürse, tüm alt türlerinize sağlayıcı türlerinden ulaşılabileceğini doğrulayın. Not: `T1, T2, T3...` Bu türlere *anında* uçuş türleri denir. Bunları erişilebilir bir ad alanına veya bir üst türe koymayı unutmayın.

### <a name="limitations-of-the-type-provider-mechanism"></a>Tip Sağlayıcı Mekanizmasının Sınırlamaları

F#'daki tür sağlayıcı mekanizması aşağıdaki sınırlamaları vardır:

- F# türü sağlayıcıları için temel altyapı, sağlanan genel türleri veya sağlanan genel yöntemleri desteklemez.

- Mekanizma, statik parametrelerle iç içe geçmiş türleri desteklemez.

## <a name="development-tips"></a>Geliştirme İpuçları

Geliştirme sürecinde aşağıdaki ipuçlarıyararlı bulabilirsiniz:

### <a name="run-two-instances-of-visual-studio"></a>Visual Studio'nun iki örneğini çalıştırın

Bir örnekte tür sağlayıcısını geliştirebilir ve sağlayıcıyı diğerinde sınayabilirsiniz, çünkü test IDE,.dll dosyasında tür sağlayıcısının yeniden oluşturulmasını engelleyen bir kilit alır. Bu nedenle, sağlayıcı ilk etapta yerleşik iken Visual Studio ikinci örneği kapatmanız gerekir ve sonra sağlayıcı inşa edildikten sonra ikinci örneği yeniden açmanız gerekir.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>fsc.exe çağrılarını kullanarak hata ayıklama türü sağlayıcıları

Aşağıdaki araçları kullanarak tür sağlayıcılarını çağırabilirsiniz:

- fsc.exe (F# komut satırı derleyicisi)

- fsi.exe (F# İnteraktif derleyici)

- devenv.exe (Visual Studio)

Genellikle bir test komut dosyası dosyası (örneğin, script.fsx) üzerinde fsc.exe kullanarak en kolay hata türü sağlayıcıları olabilir. Komut isteminden hata ayıklama başlatabilirsiniz.

```console
devenv /debugexe fsc.exe script.fsx
```

  Yazdırma-stdout günlüğe kaydetmeyi kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Sağlayıcıları](index.md)
- [Tip Sağlayıcı SDK](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
