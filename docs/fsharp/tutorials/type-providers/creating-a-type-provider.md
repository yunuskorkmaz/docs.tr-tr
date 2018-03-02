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
ms.openlocfilehash: c09f8abe4dd46453cb6cc5ed7dbb6f60dbf0ad98
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="tutorial-creating-a-type-provider"></a>Eğitmen: tür sağlayıcısı oluşturma

> [!NOTE]
Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.

F # 3.0 türü sağlayıcısı yönteminde kendi bilgi zengin programlama desteği önemli bir parçasıdır. Bu öğretici, temel kavramları göstermek için birkaç basit tür sağlayıcıları geliştirme adım adım ilerlemenizi sağlayarak kendi tür sağlayıcıları oluşturma açıklanmaktadır. F # tür sağlayıcısı mekanizması hakkında daha fazla bilgi için bkz: [tür sağlayıcıları](index.md).

F # 3.0 yaygın olarak kullanılan Internet ve kurumsal veri hizmetleri için birkaç yerleşik türü sağlayıcıları içerir. Bu tür sağlayıcıları basit ve normal ilişkisel veritabanlarının ve ağ tabanlı OData ve WSDL hizmetlere erişmenizi. Bu sağlayıcılar de F # LINQ sorguları bu veri kaynaklarının kullanımını destekler.

Gerektiğinde özel tür sağlayıcıları oluşturabilir veya başkalarının oluşturmuş olduğunuz tür sağlayıcıları başvuruda bulunabilir. Örneğin, kuruluşunuzun büyük ve artan çeşitli adlandırılmış veri kümeleri, her biri kendi kararlı veri sağlayan veri hizmeti olabilir. Şemalar okuyan ve geçerli veri kümeleri için programcı kesin türü belirtilmiş şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.


## <a name="before-you-start"></a>Başlamadan önce
Türü sağlayıcısı mekanizması öncelikle kararlı veri ve hizmet bilgi alanları F programlama deneyimine # diline injecting için tasarlanmıştır.

Bu mekanizma program mantığı için uygun olan şekilde program yürütme sırasında şema değişiklikleri bilgi alanları injecting için tasarlanmış değil. Ayrıca, bazı geçerli kullanımlarını o etki alanını içeren olsa bile mekanizması içi dil için meta programlama tasarlanmış değil. Burada tür sağlayıcısı geliştirme çok yüksek bir değer verir ve bu düzenek yalnızca gerekli olduğunda kullanmalısınız.

Burada bir şema kullanılamaz tür sağlayıcısı yazma kaçınmalısınız. Benzer şekilde, tür sağlayıcısı sıradan (veya hatta var olan yerlerde) yazma kaçınmalısınız .NET kitaplığı yeterli.

Başlamadan önce aşağıdaki soruları sormaya:


- Bilgi kaynağınız için bir şema var mı? Bu durumda, F # ve .NET tür sistemi eşlemeye nedir?

- Bir başlangıç noktası olarak varolan bir (dinamik olarak yazılan) API uygulamanız için kullanabilir miyim?

- Ve kuruluşunuzun, tür sağlayıcısı yazmayı faydalı yapmak için yeterli kullanımlarını gerekiyor mu? Normal bir .NET kitaplığı ihtiyaçlarınızı karşılamak?

- Ne kadar şemanızı değişir mi?

- Kodlama sırasında değişir mi?

- Oturumları kodlama arasında değişir mi?

- Program yürütülmesi sırasında değişir mi?

Tür sağlayıcıları şema çalışma zamanında ve derlenmiş kod kullanım ömrü süresince kararlı olduğu durumlar için uygundur.


## <a name="a-simple-type-provider"></a>Bir basit tür sağlayıcısı
Bu örnek Samples.HelloWorldTypeProvider içinde olduğu `SampleProviders\Providers` dizininde [F # 3.0 örnek paketi](https://fsharp3sample.codeplex.com) Codeplex Web sitesinde. Sağlayıcısını 100 silinen türlerini F # imza sözdizimini kullanarak ve dışında tüm için ayrıntıları atlama aşağıdaki gösterildiği gibi kodu içeren bir "türü alanı" kullanılabilir hale getirir `Type1`. Silinen türleri hakkında daha fazla bilgi için bkz: [ayrıntılar hakkında silinmesi sağlanan türleri](#details-about-erased-provided-types) bu konuda daha sonra.

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

Dizi türleri ve sağlanan üyeleri statik olarak bilinen unutmayın. Bu örnek üzerinde bir şema bağımlı türleri sağlayabilme sağlayıcılarının yararlanın değil. Tür sağlayıcısı uygulaması aşağıdaki kodda özetlenen ve Ayrıntılar, bu konunun sonraki bölümlerinde ele alınmaktadır.


>[!WARNING] 
Bu kod ve çevrimiçi örnekleri arasında bazı küçük adlandırma farklar olabilir.

```fsharp
namespace Samples.FSharp.HelloWorldTypeProvider

open System
open System.Reflection
open Samples.FSharp.ProvidedTypes
open Microsoft.FSharp.Core.CompilerServices
open Microsoft.FSharp.Quotations

// This type defines the type provider. When compiled to a DLL, it can be added
// as a reference to an F# command-line compilation, script, or project.
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this = 

  // Inheriting from this type provides implementations of ITypeProvider 
  // in terms of the provided types below.
  inherit TypeProviderForNamespaces()

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

Bu sağlayıcı kullanmak için Visual Studio 2012 ayrı bir örneği açın, F # komut dosyası oluşturabilir ve sonra aşağıdaki kodu gösterildiği gibi #r kullanarak kodunuzu sağlayıcı için bir başvuru ekleyin:

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

Türleri altında Ara `Samples.HelloWorldTypeProvider` türü sağlayıcısı oluşturulan ad alanı.

Sağlayıcıyı yeniden derleyin önce sağlayıcısını DLL kullanmakta olduğunuz tüm örneklerini Visual Studio ve F # Etkileşimli kapattığınızdan emin olun. Aksi takdirde, DLL çıkış kilitli olduğundan bir derleme hatası meydana gelir.

Bu sağlayıcı yazdırma deyimleri kullanarak hata ayıklamak için sağlayıcı ile ilgili bir sorun kullanıma sunan bir komut dosyası olun ve sonra aşağıdaki kodu kullanabilirsiniz:

```fsharp
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Visual Studio kullanarak bu sağlayıcı hatalarını ayıklamak için yönetici kimlik bilgileriyle Visual Studio komut istemi açın ve aşağıdaki komutu çalıştırın:

```fsharp
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternatif olarak, Visual Studio'yu açın, hata ayıklama menüsünü açın, seçin `Debug/Attach to process…`ve başka ekleme `devenv` burada düzenlediğiniz komut dosyanızı işlem. Bu yöntemi kullanarak, ikinci örneğiyle (IntelliSense ve diğer özellikleri) içine etkileşimli olarak ifadeleri yazarak, tür sağlayıcısı belirli mantığı daha kolay hedefleyebilirsiniz.

Oluşturulan kod hataları daha iyi tanımlamak için hata ayıklama sadece kendi kodumu devre dışı bırakabilirsiniz. Etkinleştirmek veya bu özelliği devre dışı bırakma hakkında daha fazla bilgi için bkz: [hata ayıklayıcısı ile kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger). Ayrıca, aynı zamanda açarak yakalama ilk fırsat özel durum ayarlayabilirsiniz `Debug` menüsüne ve ardından seçme `Exceptions` veya açmak için Ctrl + Alt + E tuşları seçerek `Exceptions` iletişim kutusu. Bu iletişim kutusunda, altında `Common Language Runtime Exceptions`seçin `Thrown` onay kutusu.


### <a name="implementation-of-the-type-provider"></a>Uygulama türü sağlayıcısı
Bu bölümde tür sağlayıcısı uygulamasının asıl bölümleri anlatılmaktadır. İlk olarak, özel tür sağlayıcısı için kendisini türünü tanımlayın:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Bu tür genel olmalıdır ve onunla işaretlemelisiniz [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) ayrı bir F # proje türünü içeren bütünleştirilmiş kodun başvurduğunda derleyici tür sağlayıcısı tanıyabilmesi için öznitelik. *Config* parametre isteğe bağlıdır ve, varsa, F # derleyici oluşturur türü sağlayıcısı örneği için bağlamsal yapılandırma bilgilerini içerir.

Ardından, uygulamanız [Itypeprovider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) arabirimi. Bu durumda, kullandığınız `TypeProviderForNamespaces` gelen yazın `ProvidedTypes` bir taban türü olarak API. Ad alanları, her biri doğrudan sınırlı sayıda sabit içeren, isteğini önleyebiliriz sağlanan türleri sağlanan bu yardımcı türü sınırlı koleksiyonu isteğini önleyebiliriz sağlayabilir. Sağlayıcı bu bağlamda *isteğini önleyebiliriz* kullanılan gerekli veya değil olsa bile türleri oluşturur.

```fsharp
inherit TypeProviderForNamespaces()
```

Ardından, sağlanan türleri için ad alanı belirtin yerel özel değerleri tanımlayın ve türü sağlayıcı derlemesi kendisini bulun. Bu derleme daha sonra sağlanan silinen türleri mantıksal üst türü olarak kullanılır.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Ardından, Type1 türlerinin her biri sağlamak için bir işlev oluştur... Type100. Bu işlev, bu konunun ilerleyen bölümlerinde daha ayrıntılı açıklanmıştır.

```fsharp
let makeOneProvidedType (n:int) = …
```

Ardından, 100 sağlanan türleri oluştur:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Ardından, türleri sağlanan bir ad alanı Ekle:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Son olarak, tür sağlayıcısı DLL oluşturmakta olduğunuz gösteren bir derleme özniteliği ekleyin:

```fsharp
[<assembly:TypeProviderAssembly>] 
do()
```

### <a name="providing-one-type-and-its-members"></a>Tür ve üyelerini sağlama
`makeOneProvidedType` İşlevi türlerinden birini sağlama gerçek iş yapar.

```fsharp
let makeOneProvidedType (n:int) = 
…
```

Bu adım, bu işlev uygulaması açıklanmaktadır. İlk olarak, sağlanan türü oluşturun (örneğin, Type1, n zaman = 1 veya Type57, = 57 n olduğunda).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code, 
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly,namespaceName,
"Type" + string n,
baseType = Some typeof<obj>)
```

Aşağıdaki noktalara dikkat edin:


- Bu tür silebilmeniz sağlanır.  Temel türü olduğunu belirtmek için `obj`, örnekleri, tür değerleri olarak görünür [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) derlenmiş kod.
<br />

- Bir iç içe olmayan türü belirttiğinizde, derleme ve ad alanı belirtmeniz gerekir. Silinen türleri için derleme türü sağlayıcı derlemesi kendisi olmalıdır.
<br />

Ardından, XML belgeleri türüne ekleyin. Bu belge, yani ertelendi, ana bilgisayar derleyici gerekiyorsa isteğe bağlı hesaplanır.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Sonraki türü için sağlanan bir statik özellik ekleyin:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty", 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ "Hello!" @@>))
```

Bu özellik alma dizesi "Hello!" her zaman değerlendirir. `GetterCode` Özelliği almak için konak derleyici oluşturur kodunu temsil eden bir F # tırnak, özelliğini kullanır. Teklifleri hakkında daha fazla bilgi için bkz: [kod tırnak işaretleri (F #)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

XML belgeleri özelliğine ekleyin.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Şimdi sağlanan özellik sağlanan türüne bağlayın. Tek bir tür için sağlanan üyesi ilişkilendirmeniz gerekir. Aksi takdirde, üye hiçbir zaman erişilebilir olacaktır.

```fsharp
t.AddMember staticProp
```

Şimdi parametre almayan bir sağlanan Oluşturucu oluşturun.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ], 
InvokeCode= (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode` Oluşturucusu Oluşturucu çağrıldığında, ana bilgisayar derleyici oluşturan kodu temsil eden bir F # tırnak, döndürür. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10()
```

Sağlanan türünün bir örneği temel alınan verilerle "Nesne verileri" oluşturulur. Dönüştürme için tırnak işaretli kodu içerir [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) silinmesini türü olduğundan (sağlanan türü bildirilmedi zaman belirttiğiniz gibi) bu tür sağlanan.

XML belgeleri oluşturucuya ekleyin ve sağlanan tür için sağlanan bir oluşturucu ekleyin:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Bir parametre alan ikinci bir sağlanan Oluşturucusu oluşturun:

```fsharp
let ctor2 = 
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ], 
InvokeCode= (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode` Oluşturucusu konak derleyici yöntemine bir çağrı için oluşturulan kodu temsil eden bir F # tırnak, yeniden döndürür. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10("ten")
```

Sağlanan türünün bir örneği temel alınan verilerle "on" oluşturulur. Zaten, fark etmiş olabilirsiniz `InvokeCode` işlevi bir teklif döndürür. Bu işlev giriş ifadeleri, her Oluşturucusu parametresi için bir listesidir. Bu durumda, tek bir parametre değeri temsil eden bir ifade kullanılabilir `args.[0]`. Silinen türü dönüş değerini Oluşturucusu çağrısı için kod olacak şekilde zorlar `obj`. İkinci sağlanan Oluşturucusu türüne ekledikten sonra sağlanan örnek özellik oluşturun:

```fsharp
let instanceProp = 
ProvidedProperty(propertyName = "InstanceProperty", 
propertyType = typeof<int>, 
GetterCode= (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Bu özellik alma gösterimi nesne dize uzunluğunu döndürür. `GetterCode` Özelliği özelliği almak için konak derleyici oluşturur kod belirtir F # tırnak döndürür. Gibi `InvokeCode`, `GetterCode` işlevi bir teklif döndürür. Ana bilgisayar derleyici bu işlevi bağımsız değişken listesini kullanarak çağırır. Bu durumda, kullanarak erişebileceğiniz sonra alıcı adlandırılan, örneği temsil eden yalnızca tek bir ifade bağımsız değişkenleri ekleyin `args.[0]`. Uygulaması `GetterCode` silinen yazın sonuç tırnak içine splices `obj`, ve bir cast türleri nesnesinin bir dize olduğunu denetleme derleyicinin mekanizması karşılamak için kullanılır. Sonraki bölümü `makeOneProvidedType` bir parametresiyle örnek yöntemi sağlar.

```fsharp
let instanceMeth = 
ProvidedMethod(methodName = "InstanceMethod", 
parameters = [ProvidedParameter("x",typeof<int>)], 
returnType = typeof<char>, 
InvokeCode = (fun args -> 
<@@ ((%%(args.[0]) : obj) :?> string).Chars(%%(args.[1]) : int) @@>))

instanceMeth.AddXmlDocDelayed(fun () -> "This is an instance method")
// Add the instance method to the type.
t.AddMember instanceMeth
```

Son olarak, 100 iç içe özellikler içeren bir iç içe geçmiş türü oluşturun. Bu oluşturulmasını türü ve özelliklerini iç içe geçmiş, yani ertelendi, isteğe bağlı hesaplanır.

```fsharp
t.AddMembersDelayed(fun () -> 
let nestedType = ProvidedTypeDefinition("NestedType",
Some typeof<obj>

)

nestedType.AddMembersDelayed (fun () -> 
let staticPropsInNestedType = 
[ for i in 1 .. 100 do
let valueOfTheProperty = "I am string "  + string i

let p = ProvidedProperty(propertyName = "StaticProperty" + string i, 
propertyType = typeof<string>, 
IsStatic=true,
GetterCode= (fun args -> <@@ valueOfTheProperty @@>))

p.AddXmlDocDelayed(fun () -> 
sprintf "This is StaticProperty%d on NestedType" i)

yield p ]
staticPropsInNestedType)

[nestedType])

// The result of makeOneProvidedType is the type.
t
```

### <a name="details-about-erased-provided-types"></a>Silinen sağlanan türleri hakkında ayrıntılar
Bu bölümdeki örnek yalnızca sağlar *sağlanan türleri silinmesi*, aşağıdaki durumlarda özellikle yararlı olan:


- Ne zaman yalnızca veri ve yöntemleri içeren bir bilgi alanı için bir sağlayıcı yazıyorsanız.
<br />

- Ne zaman burada doğru çalışma zamanı türü anlamları bilgi alanı pratik kullanım için kritik olmayan bir sağlayıcı yazıyorsanız.
<br />

- Ne zaman büyük ve birbirine bağlı bilgi alanı için gerçek .NET türleri oluşturmak için teknik olarak uygun olmayan bir bilgi alanı için bir sağlayıcı yazıyorsanız.
<br />

Bu örnekte, her tür yazmak için silinir sağlanan `obj`, ve türü tüm kullanımlarını türü olarak görünür `obj` derlenmiş kod. Aslında, arka plandaki nesneleri bu örneklerde dizelerdir, ancak türü olarak görünür `System.Object` .NET derlenmiş kod. Türü silinme tüm kullanıcılarına açık kutulama kullanabileceğiniz gibi kutudan çıkarma ve atama bozmaya için türleri silinebilir. Bu durumda, nesne kullanıldığında, geçerli olmayan bir yayın özel durumu neden olabilir. Bir sağlayıcı çalışma zamanı false ifadeleri karşı korunmasına yardımcı olmak için kendi özel gösterim türü tanımlayabilirsiniz. F # içinde kendisi silinen türleri tanımlayamazsınız. Yalnızca sağlanan türleri silinebilir. Hem pratik ayrımlar anlamanız gerekir ve anlam ya da kullanmanın silinen türleri, tür sağlayıcısı veya sağlayan bir sağlayıcı için türleri silinebilir. Silinen bir türü gerçek .NET tür yok. Bu nedenle, doğru yansıma türü üzerinden yapamayacağı ve çalışma zamanı atamalar ve üzerinde tam çalışma zamanı türü anlamları kullanan başka teknikler kullanırsanız, silinen türleri bozmaya. Silinen türlerinin alt sürüme cast türü özel durumları çalışma zamanında sık sonuçlanır.


### <a name="choosing-representations-for-erased-provided-types"></a>Sağlanan türleri Beyanları silebilmeniz için seçme
Bazı silinen sağlananlardan kullanımları hiçbir gösterimi gereklidir. Örneğin, silinen türü yalnızca statik özellikler ve üyeleri ve oluşturucu yok içerebilir ve yöntemleri ya da özellikleri türünün bir örneği döndürecektir sağlanan. Tür sağlanan bir silinen örneklerini erişebiliyorsa, aşağıdaki soruları göz önünde bulundurmalısınız:


- Sağlanan tür silinmesini nedir?
<br />
  - Sağlanan tür silinmesini türü derlenmiş .NET kodunda görünme ' dir.
<br />

  - Sağlanan silinen sınıf türü silinme her zaman ilk silinmesi olmayan türün temel türünü devralma zincirinde ' dir.
<br />

  - Sağlanan silinen arabirim türü silinmesini her zaman olduğu `System.Object`.
<br />

- Sağlanan tür gösterimlerini nelerdir?
<br />
  - Bir silinen tür sağlanan için olası nesne kümesini kendi Beyanları çağrılır. Bu belgedeki örnekte tüm silinen sağlanan gösterimlerini türleri `Type1..Type100` her zaman dize nesneleridir.
<br />

Sağlanan bir türdeki tüm Beyanları sağlanan türü silinme ile uyumlu olması gerekir. (Aksi halde, F # derleyici hata türü sağlayıcısı için bir kullanım alır ya da geçersiz doğrulanamayan .NET kodu oluşturulur. Tür sağlayıcısı geçersiz bir gösterimi verir kodu döndürmesi durumunda geçerli değil.)

Her ikisi de çok yaygın aşağıdaki yaklaşımlardan birini kullanarak sağlanan nesneleri temsili seçebilirsiniz:


- Varolan bir .NET türünü yalnızca kesin türü belirtilmiş bir sarmalayıcı sağlıyorsanız, genellikle o türüne silme, bu türdeki örneklerin Beyanları veya her ikisini de olarak kullanmak türünüz için mantıklıdır. Bu türün varolan yöntemleri çoğunu hala kesin türü belirtilmiş sürümünü kullanırken anlamlı olduğunda bu uygun bir yaklaşımdır.
<br />

- Var olan tüm .NET API önemli ölçüde farklı bir API oluşturmak istiyorsanız, bu tür silinme ve Beyanları sağlanan türleri için çalışma zamanı türleri oluşturmak için anlamlıdır.
<br />

Bu belge örnekte dizelerini sağlanan nesneleri gösterimlerini kullanır. Genellikle, diğer nesneler için temsili kullanmak uygun olabilir. Örneğin, bir özellik paketi olarak bir sözlük kullanabilirsiniz:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternatif olarak, çalışma zamanında bir veya daha fazla çalışma zamanı işlemleri birlikte bir gösterim oluşturmak için kullanılan, tür sağlayıcısı tür tanımlama:

```fsharp
type DataObject() =
let data = Dictionary<string,obj>()
member x.RuntimeOperation() = data.Count
```

Sağlanan üyeleri, ardından bu nesne türü örnekleri oluşturabileceğiniz:

```fsharp
ProvidedConstructor(parameters = [], 
InvokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Bu durumda, (isteğe bağlı) bu tür türü silinme bu türü olarak belirterek kullanabilirsiniz `baseType` oluşturulurken `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

`Key Lessons`

Önceki bölümde bir dizi türleri, özellikleri ve yöntemleri sağlayan basit bir silme tür sağlayıcısı oluşturma açıklanmıştır. Bu bölümde ayrıca bazı avantajları ve dezavantajları türü sağlayıcıdan silinen türleri sağlama dahil olmak üzere türü silinme kavramı açıklandığı ve Silinen türleri gösterimlerini ele alınan.


## <a name="a-type-provider-that-uses-static-parameters"></a>Statik parametreleri kullanan bir tür sağlayıcısı
Tür sağlayıcıları tarafından statik verileri Parametreleştirme olanağı bile sağlayıcı yerel veya uzak verilere erişmek gerektiğinde değil durumlarda birçok ilginç senaryolara olanak sağlar. Bu bölümde, böyle bir sağlayıcı bir araya getirilmesi için bazı temel tekniklerini öğreneceksiniz.


### <a name="type-checked-regex-provider"></a>Regex sağlayıcısı türü işaretli
.NET sarmalar türü sağlayıcısı normal ifadeler için uygulamak istediğiniz düşünün `System.Text.RegularExpressions.Regex` aşağıdaki derleme zamanı garanti sağlayan bir arabirimi kitaplıklarında:


- Normal bir ifade geçerli olup olmadığını doğrulanıyor.
<br />

- Tüm grup adlarını normal ifadede dayalı eşleşmeler üzerinde adlandırılmış özelliklerinin sağlanması.
<br />

Bu bölümde tür sağlayıcıları oluşturmak için nasıl kullanılacağı gösterilmiştir bir `RegExProviderType` normal ifade deseni bu kazanımları sağlamak için parameterizes yazın. Derleyici, belirtilen desenle geçerli değil ve böylece eşleşmeleri özellikleri adlandırılmış kullanarak erişebilir türü sağlayıcısı düzeni grupları ayıklayabilirsiniz bir hata bildirir. Tür sağlayıcısı tasarlarken, sunulan API'si nasıl görünmelidir düşünmelisiniz son kullanıcılar ve bu tasarımı .NET kodu için nasıl çevirir. Aşağıdaki örnek, alan kodunu bileşenlerini almak için bu tür bir API kullanmak gösterilmektedir:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Aşağıdaki örnek, tür sağlayıcısı bu çağrılarının nasıl çevirir gösterir:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Aşağıdaki noktalara dikkat edin:


- Standart Regex türü parametreli temsil eden `RegexTyped` türü.
<br />

- `RegexTyped` Deseni için statik tür bağımsız değişkeni geçirme Regex Oluşturucusu çağrısına Oluşturucusu sonuçlanıyor.
<br />

- Sonuçlarını `Match` yöntemi Standart tarafından temsil edilen `System.Text.RegularExpressions.Match` türü.
<br />

- Sağlanan özelliğinde her adlandırılmış grubu sonuçları ve özellik erişme sonuçlanıyor eşleşmeyi'nın bir dizin oluşturucu kullanımını `Groups` koleksiyonu.
<br />

Aşağıdaki kodu böyle bir sağlayıcı uygulamak için mantığı çekirdek ve bu örnek sağlanan türü için tüm üyelerinin eklenmesini atlar. Eklenen her üye hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde uygun bölümüne bakın. Tam kodunu örnekten karşıdan [F # 3.0 örnek paketi](https://fsharp3sample.codeplex.com) Codeplex Web sitesinde.

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
let ty = ProvidedTypeDefinition(
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


- Tür sağlayıcısı iki statik parametreleri alır: `pattern`, zorunlu olduğu ve `options`, hangi isteğe bağlı (varsayılan bir değer sağlandığı için).
<br />

- Statik bağımsız değişkenleri sağlanan sonra normal ifade örneği oluşturun. Bu örnek, Regex hatalı biçimlendirilmiş ise ve bu hata kullanıcılara bildirilecek bir özel durum oluşturur.
<br />

- İçinde `DefineStaticParameters` geri değişkenleri sağlanan sonra döndürülecek tür tanımlayın.
<br />

- Bu kod ayarlar `HideObjectMethods` IntelliSense deneyimi kolaylaştırılmış kalması true. Bu öznitelik neden `Equals`, `GetHashCode`, `Finalize`, ve `GetType` üyelerinin atlanması için sağlanan nesne için IntelliSense listelerden.
<br />

- Kullandığınız `obj` yöntemi, ancak temel türünü kullanacağınız gibi bir `Regex` nesnesi olarak sonraki örnekte gösterildiği gibi bu tür, çalışma zamanı gösterimi.
<br />

- Çağrı `Regex` Oluşturucusu oluşturur bir `System.ArgumentException` zaman normal bir ifade değil geçerli. Derleyici, bu özel durum yakalar ve derleme zamanında ya da Visual Studio düzenleyicisinde bir hata iletisi kullanıcıya bildirir. Bu özel bir uygulamayı çalıştırmadan doğrulanması normal ifadeler sağlar.
<br />

Herhangi bir anlamlı yöntemleri veya özellikleri içermediğinden yukarıda tanımlanan türü henüz yararlı olmaz. İlk olarak, statik ekleyin `IsMatch` yöntemi:

```fsharp
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string." 
ty.AddMember isMatch
```

Önceki kod yöntemi tanımlar `IsMatch`, hangi giriş olarak bir dize alıp döndüren bir `bool`. Kullanımını yalnızca hassas parçasıdır `args` bağımsız değişkeni içinde `InvokeCode` tanımı. Bu örnekte, `args` bağımsız değişkenler için bu yöntemi temsil eden bir tırnak işaretleri listesidir. Yöntemi bir örnek yöntemi ise, ilk bağımsız değişkeni temsil eden `this` bağımsız değişkeni. Ancak, statik bir yöntem için tüm yalnızca açık bağımsız değişkenleri yöntemi için bağımsız değişkenleri şunlardır. Not tırnak işaretli değerin türü belirtilen dönüş türü eşleşmesi gerekir (Bu durumda, `bool`). Ayrıca bu kodu kullanır Not `AddXmlDoc` yöntemi sağlanan yöntem IntelliSense sağlayabilir yararlı belgelerine sahip olduğundan emin olun.

Ardından, bir örnek Match yöntemi ekler. Ancak, bu yöntem bir sağlanan değerini döndürmelidir `Match` grupları kesin türü belirtilmiş bir biçimde erişilebilir yazın. Bu nedenle, ilk bildirdiğiniz `Match` türü. Bu tür statik bir bağımsız değişken olarak sağlanan düzeni bağlı olduğundan, bu tür parametreli tür tanımı içinde iç içe gerekir:

```fsharp
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

ty.AddMember matchTy
```

Her grup için eşleşme türü için bir özellik ekleyin. Çalışma zamanında bir eşleşme olarak temsil edilen bir `System.Text.RegularExpressions.Match` değer özelliği tanımlar tırnak kullanmalısınız `System.Text.RegularExpressions.Match.Groups` ilgili grup almak için özellik dizini.

```fsharp
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember prop
```

Yeniden sağlanan özelliğine XML belgeleri eklediğiniz unutmayın. Ayrıca bir özellik varsa okunabilir Not bir `GetterCode` işlevi sağlanır ve özelliği, yazılabilir bir `SetterCode` işlevi sağlanır, sonuçta elde edilen özelliği salt okunur şekilde.

Bu değer döndüren bir örnek yöntemi oluşturabilirsiniz artık `Match` türü:

```fsharp
let matchMethod = 
ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first ocurrence of this regular expression" 

ty.AddMember matchMeth
```

Örnek yöntemi, oluşturduğunuz çünkü `args.[0]` temsil eden `RegexTyped` örneği üzerinde yöntemi çağrılır ve `args.[1]` giriş bağımsız değişkeni.

Son olarak, belirtilen türdeki örneklerin oluşturulan bir oluşturucu sağlayın.

```fsharp
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)
ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Kurucu yalnızca bir nesneye olduğundan yeniden Kutulu standart bir .NET Regex örnek oluşturulmasını siler `obj` silinme sağlanan türünde değil. Bu değişiklikle konuda daha önce belirtilen örnek API kullanım beklendiği gibi çalışır. Aşağıdaki kod, tam ve son:

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



let ty = ProvidedTypeDefinition(
thisAssembly, 
rootNamespace, 
typeName, 
baseType = Some baseTy)

ty.AddXmlDoc "A strongly typed interface to the regular expression '%s'"

// Provide strongly typed version of Regex.IsMatch static method.
let isMatch = ProvidedMethod(
methodName = "IsMatch", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = typeof<bool>, 
IsStaticMethod = true,
InvokeCode = fun args -> <@@ Regex.IsMatch(%%args.[0], pattern) @@>) 

isMatch.AddXmlDoc "Indicates whether the regular expression finds a match in the specified input string"

ty.AddMember isMatch

// Provided type for matches
// Again, erase to obj even though the representation will always be a Match
let matchTy = ProvidedTypeDefinition(
"MatchType", 
baseType = Some baseTy, 
HideObjectMethods = true)

// Nest the match type within parameterized Regex type.
ty.AddMember matchTy

// Add group properties to match type
for group in r.GetGroupNames() do
// Ignore the group named 0, which represents all input.
if group <> "0" then
let prop = ProvidedProperty(
propertyName = group, 
propertyType = typeof<Group>, 
GetterCode = fun args -> <@@ ((%%args.[0]:obj) :?> Match).Groups.[group] @@>)
prop.AddXmlDoc(sprintf @"Gets the ""%s"" group from this match" group)
matchTy.AddMember(prop)

// Provide strongly typed version of Regex.Match instance method.
let matchMeth = ProvidedMethod(
methodName = "Match", 
parameters = [ProvidedParameter("input", typeof<string>)], 
returnType = matchTy, 
InvokeCode = fun args -> <@@ ((%%args.[0]:obj) :?> Regex).Match(%%args.[1]) :> obj @@>)
matchMeth.AddXmlDoc "Searches the specified input string for the first occurence of this regular expression"

ty.AddMember matchMeth

// Declare a constructor.
let ctor = ProvidedConstructor(
parameters = [], 
InvokeCode = fun args -> <@@ Regex(pattern) :> obj @@>)

// Add documentation to the constructor.
ctor.AddXmlDoc "Initializes a regular expression instance"

ty.AddMember ctor

ty
| _ -> failwith "unexpected parameter values")) 

do this.AddNamespace(rootNamespace, [regexTy])

[<TypeProviderAssembly>]
do ()
```

`Key Lessons`

Bu bölümde statik parametrelerinin üzerinde çalıştığı bir tür sağlayıcısı oluşturma açıklanmıştır. Sağlayıcı statik parametresinin denetler ve onun değere göre işlemler sağlar.


## <a name="a-type-provider-that-is-backed-by-local-data"></a>Yerel veri tarafından desteklenen bir tür sağlayıcısı
Sık yalnızca statik parametreleri aynı zamanda yerel veya uzak sistemlerden bilgi göre API'leri sunmak için tür sağlayıcıları isteyebilirsiniz. Bu bölümde yerel veri dosyaları gibi yerel verileri esas alan tür sağlayıcıları anlatılmaktadır.


### <a name="simple-csv-file-provider"></a>Basit CSV dosya sağlayıcısı
Basit bir örnek olarak, tür sağlayıcısı virgülle ayrılmış değer (CSV) biçiminde bilimsel verilerine erişmek için göz önünde bulundurun. Bu bölümde, aşağıdaki tabloda gösterildiği gibi CSV dosyaları kayan nokta verisi tarafından izlenen bir başlık satırı içerdiğini varsayar:



|Uzaklık (ölçer)|Süresi (saniye)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|
Bu bölümde satırlarla almak için kullanabileceğiniz bir türü sağlamak nasıl gösterilmiştir bir `Distance` türündeki özelliği `float<meter>` ve `Time` türündeki özelliği `float<second>`. Kolaylık olması için aşağıdaki varsayımlar oluşturulur:


- Üstbilgi adlardır ya da birimi daha az veya "Ad (birim)" biçiminde olması ve virgül hiçbirini içeremez.
<br />

- Birimleridir tüm Systeme uluslararası (SI) birimi olarak [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Modülü (F #)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modülü tanımlar.
<br />

- Tüm basit birimler (örneğin, ölçüm) bileşik (örneğin, ölçüm/saniye) yerine.
<br />

- Kayan nokta verisi tüm sütunları içeriyor.
<br />

Daha eksiksiz bir sağlayıcı, bu kısıtlamalar çözmek.

Yeniden ilk API nasıl görünmelidir dikkate alınması gereken adımdır. Verilen bir `info.csv` dosyası (biçiminde virgülle ayrılmış) önceki tablosundan içerikle sağlayıcısının kullanıcıların aşağıdaki örneğe benzer bir kod yazın gerekir:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Bu durumda, derleyici bu çağrıları aşağıdaki örneğe benzer bir şey dönüştürmeniz:

```fsharp
let info = new MiniCsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

En iyi çeviri gerçek tanımlamak tür sağlayıcısı gerektirir `CsvFile` türü sağlayıcının derlemesindeki türü. Tür sağlayıcıları genellikle birkaç yardımcı türleri ve yöntemleri üzerinde önemli mantığı sarmalamak için kullanır. Ölçüleri çalışma zamanında silebilmeniz için kullanabileceğiniz bir `float[]` bir satır için silinen türü. Derleyici, farklı sütunlardan farklı ölçü türlerine sahip olarak kabul eder. Örneğin, ilk sütunun örneğimizde türüne sahip `float<meter>`, ve ikinci olan `float<second>`. Ancak, silinen gösterimi oldukça basit kalabilir.

Aşağıdaki kod uygulama çekirdek gösterir.

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
inherit TypeProviderForNamespaces()

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

let prop = ProvidedProperty(fieldName, fieldTy, 
GetterCode = fun [row] -> <@@ (%%row:float[]).[i] @@>)

// Add metadata that defines the property's location in the referenced file.
prop.AddDefinitionLocation(1, headers.[i].Index + 1, filename)
rowTy.AddMember(prop) 

// Define the provided type, erasing to CsvFile.
let ty = ProvidedTypeDefinition(asm, ns, tyName, Some(typeof<CsvFile>))

// Add a parameterless constructor that loads the file that was used to define the schema.
let ctor0 = ProvidedConstructor([], 
InvokeCode = fun [] -> <@@ CsvFile(resolvedFilename) @@>)
ty.AddMember ctor0

// Add a constructor that takes the file name to load.
let ctor1 = ProvidedConstructor([ProvidedParameter("filename", typeof<string>)], 
InvokeCode = fun [filename] -> <@@ CsvFile(%%filename) @@>)
ty.AddMember ctor1

// Add a more strongly typed Data property, which uses the existing property at runtime.
let prop = ProvidedProperty("Data", typedefof<seq<_>>.MakeGenericType(rowTy), 
GetterCode = fun [csvFile] -> <@@ (%%csvFile:CsvFile).Data @@>)
ty.AddMember prop

// Add the row type as a nested type.
ty.AddMember rowTy
ty)

// Add the type to the namespace.
do this.AddNamespace(ns, [csvTy])
```

Uygulanmasıyla ilgili aşağıdaki noktalara dikkat edin:


- Aşırı yüklenmiş Oluşturucular, özgün dosya veya okumak için özdeş bir şema içeren izin verin. Bu deseni, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazma ve bu deseni için Uzak Veri şablon olarak kullanılacak yerel bir dosyaya verir yaygındır.
<br />  Kullanabileceğiniz [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) göreli dosya adları çözümlemek için türü sağlayıcısı oluşturucuya geçirilen değer.
<br />

- Kullanabileceğiniz `AddDefinitionLocation` sağlanan özellikler konumunu tanımlamak için yöntem. Bu nedenle, kullanırsanız `Go To Definition` sağlanan bir özellik, CSV dosyasını Visual Studio'da açın.
<br />

- Kullanabileceğiniz `ProvidedMeasureBuilder` türü SI birimler aramak için ve ilgili oluşturmak için `float<_>` türleri.
<br />

`Key Lessons`

Bu bölüm veri kaynağındaki kendisini içeren basit bir şema ile yerel bir veri kaynağı için tür sağlayıcısı oluşturma açıklanmıştır.


## <a name="going-further"></a>Daha fazla işlenmesini
Aşağıdaki bölümlerde daha ayrıntılı incelemesi için öneriler içerir.


### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Silinen türleri için derlenmiş kod bakma
Ne tür sağlayıcısı kullanımını yayılan koduna karşılık gelen bazı fikir vermek için aşağıdaki işlevini kullanarak araması `HelloWorldTypeProvider` bu konunun önceki kısımlarında kullanılır.

```fsharp
let function1 () = 
let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
obj1.InstanceProperty
```

Görüntüyü ildasm.exe kullanarak decompiled sonuç kodunun şöyledir:

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

Türündeki tüm belirtilenlerden örnekte gösterildiği gibi `Type1` ve `InstanceProperty` özelliği silinmesi, yalnızca çalışma zamanı türleri üzerinde işlem söz konusu çıkılıyor.


### <a name="design-and-naming-conventions-for-type-providers"></a>Tasarım ve tür sağlayıcıları için adlandırma kuralları
Tür sağlayıcıları yazarken aşağıdaki kuralları inceleyin.


- `Providers for Connectivity Protocols`
<br />  Veri ve hizmet bağlantısı gibi protokoller için OData veya SQL bağlantıları, çoğu Sağlayıcı DLL adları genel olarak, bitmelidir `TypeProvider` veya `TypeProviders`. Örneğin, aşağıdaki dize şuna benzer bir DLL adı kullanın:
<br />

```
  Fabrikam.Management.BasicTypeProviders.dll
```

  Sağlanan türleri karşılık gelen ad alanı üyesi olan ve sizin uygulanan bağlantı protokolü belirtmek emin olun:
<br />

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

- `Utility Providers for General Coding`
<br />  Yardımcı programı tür sağlayıcısı için gibi normal ifadeler için tür sağlayıcısı aşağıdaki örnekte gösterildiği gibi bir temel kitaplığı parçası olabilir:
<br />

```fsharp
  #r "Fabrikam.Core.Text.Utilities.dll"
```

  Bu durumda, sağlanan türü normal .NET tasarım kurallarına göre uygun bir noktada görünür:
<br />

```fsharp
  open Fabrikam.Core.Text.RegexTyped
  
  let regex = new RegexTyped<"a+b+a+b+">()
```

- `Singleton Data Sources`
<br />  Bazı tür sağlayıcıları bir tek bir adanmış veri kaynağına bağlanmak ve yalnızca veriler sağlar. Bu durumda bırak `TypeProvider` sonek ve .NET adlandırma için normal kuralları kullanın:
<br />

```fsharp
  #r "Fabrikam.Data.Freebase.dll"
  
  let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

  Daha fazla bilgi için bkz: `GetConnection` tasarım bu konunun ilerleyen bölümlerinde açıklanan kuralı.
<br />


### <a name="design-patterns-for-type-providers"></a>Tür sağlayıcıları için Tasarım desenleri
Aşağıdaki bölümlerde tasarım desenleri tür sağlayıcıları yazarken kullanabileceğiniz açıklanmaktadır.


#### <a name="the-getconnection-design-pattern"></a>GetConnection tasarım deseni
Çoğu tür sağlayıcılarını kullanacak şekilde yazılıp `GetConnection` aşağıdaki örnekte gösterildiği gibi FSharp.Data.TypeProviders.dll, türü sağlayıcıları tarafından kullanılan deseni:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Uzak Veri ve hizmetler tarafından desteklenen tür sağlayıcıları
Uzak Veri ve hizmetler tarafından desteklenen bir tür sağlayıcısı oluşturmadan önce bir dizi bağlı programlamada devredilen sorunları dikkate almanız gerekir. Bu sorunları aşağıdaki konuları içerir:


- Şema eşleme
<br />

- liveness ve şema değişikliği varlığında geçersiz kılma
<br />

- Şema önbelleğe alma
<br />

- Veri erişim işlemleri zaman uyumsuz uygulamaları
<br />

- LINQ sorguları da dahil, sorguların destekleme
<br />

- kimlik bilgileri ve kimlik doğrulama
<br />

Bu konu, bu sorunlar daha fazla keşfedin değil.


### <a name="additional-authoring-techniques"></a>Ek yazma teknikleri
Kendi tür sağlayıcıları yazdığınızda, aşağıdaki ek teknikler kullanmak isteyebilirsiniz.


- `Creating Types and Members On-Demand`
<br />  ProvidedType API AddMember sürümleri Gecikmeli.
<br />

```fsharp
  type ProvidedType =
  member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
  member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

  Bu sürümleri, isteğe bağlı alanları türleri oluşturmak için kullanılır.
<br />

- `Providing Array, ByRef, and Pointer types`
<br />  Normal kullanarak (dizi türleri, byref türleri ve genel türler işlemlerinden içerir, imzalar) sağlanan üyeleri yaptığınız `MakeArrayType`, `MakePointerType`, ve `MakeGenericType` System.Type, herhangi bir örneğinin üzerinde de dahil olmak üzere `ProvidedTypeDefinitions`.
<br />

- `Providing Unit of Measure Annotations`
<br />  ProvidedTypes API ölçü ek açıklamaları sağlayan Yardımcıları sağlar. Örneğin, türü sağlamak için `float<kg>`, aşağıdaki kodu kullanın:
<br />

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Türü sağlamak için `Nullable<decimal<kg/m^2>>`, aşağıdaki kodu kullanın:
<br />

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

- `Accessing Project-Local or Script-Local Resources`
<br />  Her tür sağlayıcısı örneği verilen bir `TypeProviderConfig` oluşturma sırasında değeri. Bu değer "Çözümleme klasörü" sağlayıcısı (diğer bir deyişle, derleme veya bir komut dosyası içeren dizin için proje klasör), başvurulan bir derleme listesi ve diğer bilgileri içerir.
<br />

- `Invalidation`
<br />  Sağlayıcıları şema varsayımlar değişmiş olabilir F # dili hizmet bildirmek için geçersiz kılma sinyalleri yükseltebilirsiniz. Geçersiz kılma ortaya çıktığında, sağlayıcı Visual Studio'da barındırılıyorsa bir typecheck alınabilir. Bu sinyal sağlayıcısı F # Etkileşimli veya F # derleyici (fsc.exe) tarafından barındırıldığında yoksayılacak.
<br />

- `Caching Schema Information`
<br />  Sağlayıcılar genellikle şema bilgilere erişimi önbelleğe gerekir. Statik bir parametre veya kullanıcı verisi olarak verilen bir dosya adı kullanarak önbelleğe alınan verilerin depolanması gerekir. Şema önbelleğe alma, bir örnek verilmiştir `LocalSchemaFile` türü sağlayıcıları parametresinde `FSharp.Data.TypeProviders` derleme. Bu sağlayıcılar uygulamasında statik Bu parametre ağ üzerinden veri kaynağına erişme yerine belirtilen yerel dosyasında şema bilgileri kullanmak için tür sağlayıcısı yönlendirir. Önbelleğe alınan şema bilgileri kullanmak için de statik parametresinin ayarlamalısınız `ForceUpdate` için `false`. Çevrimiçi ve çevrimdışı veri erişimi etkinleştirmek için benzer bir tekniği kullanabilirsiniz.
<br />

- `Backing Assembly`
<br />  .Dll veya .exe dosyasının derlerken oluşturulan türleri için yedekleme .dll dosyası statik olarak elde edilen derlemeye bağlı. Bu bağlantı, Ara dile (IL) tür tanımları ve yönetilen kaynakları son derlemeyi yedekleme derlemeye kopyalayarak oluşturulur. F # Etkileşimli kullandığınızda, yedekleme .dll dosyasını kopyaladığınız değil ve bunun yerine doğrudan F # Etkileşimli işlemine yüklenir.
<br />

- `Exceptions and Diagnostics from Type Providers`
<br />  Sağlanan türleri tüm üyelerinden tüm kullanımlarını özel durumlar oluşturma. Tür sağlayıcısı bir özel durum oluşturursa tüm durumlarda belirli tür sağlayıcısı için hata konak derleyici öznitelikleri.
<br />
  - Özel durumlar hiçbir zaman iç derleyici hatalarına neden sağlayıcı yazın.
<br />

  - Tür sağlayıcıları uyarıları raporlayamazsınız.
<br />

  - Tür sağlayıcısı F # derleyici, F # geliştirme ortamı ya da F # Etkileşimli içinde barındırıldığında, bu sağlayıcısından tüm özel durumları yakalanır. İleti özelliği her zaman hata metindir ve hiçbir yığın izlemesi görünür. Bir özel durum kullanacaksanız, aşağıdaki örneklerde atabilirsiniz:
<br />
    - `System.NotSupportedException`
<br />

    - `System.IO.IOException`
<br />

    - `System.Exception`
<br />


#### <a name="providing-generated-types"></a>Oluşturulan türler sağlar
Şu ana kadar bu belgede açıklanan nasıl silinen türler sağlar. Ayrıca türü sağlayıcısı mekanizması F #'de kullanıcıların programa gerçek .NET türü tanımları olarak eklenen oluşturulan türleri sağlamak için kullanabilirsiniz. Sizin için oluşturulan türleri bir tür tanımı kullanılarak sağlanan başvurmalıdır.

```fsharp
open Microsoft.FSharp.TypeProviders 

type Service = ODataService<" https://services.odata.org/Northwind/Northwind.svc/">
```

F # 3.0 sürümünün bir parçası olan ProvidedTypes 0.2 yardımcı kod yalnızca oluşturulan türleri sağlamak için destek sınırlıdır. Aşağıdaki deyimleri için oluşturulan tür tanımı doğru olması gerekir:


- IsErased ayarlanmalıdır `false`.
<br />

- Sağlayıcı gerçek destekleyen .NET .dll dosyasının disk üzerinde eşleşen bir .dll dosyası ile bir derlemeyi olması gerekir.
<br />

Ayrıca çağırmalısınız `ConvertToGenerated` , iç içe geçmiş türler form oluşturulan türleri kapalı kümesi sağlanan kök türünde. Bu çağrı verilen sağlanan tür tanımı ve kendi iç içe geçmiş tür tanımlarını bir derleme halinde yayar ve ayarlar `Assembly` bu derleme dönmek için tüm sağlanan tür tanımları özelliği. Yalnızca kök türündeki derleme özelliği ilk kez eriştiğinde derleme yayınlanır. Türü için generative türü bildirimi işlerken konak F # derleyici bu özellik erişin.


## <a name="rules-and-limitations"></a>Kurallar ve sınırlamalar
Tür sağlayıcıları yazdığınızda, aşağıdaki kurallar ve sınırlamalar göz önünde bulundurun.


- `Provided types must be reachable.`
<br />  Tüm girildi. türleri iç içe olmayan türlerinden erişilebilir olmalıdır. İç içe olmayan türleri çağrısında verilir `TypeProviderForNamespaces` Oluşturucusu veya yapılan bir çağrı `AddNamespace`. Örneğin, bir tür sağlayıcısı sağlarsa, `StaticClass.P : T`, T yuvalanmış olmayan bir tür veya iç içe geçmiş altında bir olduğundan emin olmanız gerekir.
<br />  Örneğin, bazı sağlayıcılar gibi statik sınıf sahip `DataTypes` bu içeren `T1, T2, T3, ...` türleri. Aksi halde, bir derlemede T türü bir başvuru bulundu, ancak bu derleme içinde tür bulunamadı hata söyler. Bu hata varsa, tüm alt sağlayıcı türlerinden erişilebildiğini doğrulayın. Not: Bu `T1, T2, T3...` türleri denir *üzerinde-çalışma sırasında* türleri. Erişilebilir bir ad alanı veya bir üst tür koyabilir unutmayın.
<br />

- `Limitations of the Type Provider Mechanism`
<br />  F # tür sağlayıcısı mekanizması aşağıdaki sınırlamalara sahiptir:
<br />
  - Genel türleri veya genel yöntemler sağlanan sağlanan F # tür sağlayıcıları için temel altyapıyı desteklemiyor.
<br />

  - Mekanizması statik parametrelerle iç içe geçmiş türler desteklemiyor.
<br />

- `Limitations of the ProvidedTypes Support Code`
<br />  `ProvidedTypes` Destek kod, aşağıdaki kurallar ve sınırlamalar vardır:
<br />
  1. Dizinli alıcılar ve ayarlayıcılar ile sağlanan özellikler uygulanmadı.
<br />

  2. Sağlanan olayları uygulanmadı.
<br />

  3. Sağlanan türleri ve bilgi nesneleri, yalnızca F # tür sağlayıcısı mekanizması için kullanılmalıdır. Bunlar genellikle daha System.Type nesneler olarak kullanılabilir değil.
<br />

  4. Yöntem uygulamalarını tanımlamak tırnak işaretleri kullanabilirsiniz yapıları birkaç sınırlamaları vardır. Kaynak koduna ProvidedTypes - için başvurabilirsiniz*sürüm* hangi yapıları tırnak işaretleri içinde desteklenen görmek için.
<br />

- `Type providers must generate output assemblies that are .dll files, not .exe files.`
<br />


## <a name="development-tips"></a>Geliştirme İpuçları
Aşağıdaki ipuçları geliştirme sürecinde yararlı.


- `Run Two Instances of Visual Studio.` Tür sağlayıcısı bir örneğinde geliştirmek ve test IDE yeniden oluşturulan tür sağlayıcısı engeller .dll dosyası üzerinde bir kilit sürer çünkü sağlayıcıyı diğer sınayın. Bu nedenle, Visual Studio ikinci bir örneğini sağlayıcı ilk örnekte yerleşik olarak bulunur ve daha sonra sağlayıcının oluşturulduktan sonra ikinci örneği yeniden açmanız gerekir kapatmanız gerekir.
<br />

- `Debug type providers by using invocations of fsc.exe.` Tür sağlayıcıları aşağıdaki araçları kullanarak çağırabilirsiniz:
<br />
  - fsc.exe (F # komut satırı derleyicisi)
<br />

  - fsi.exe (F # Etkileşimli derleyicisi)
<br />

  - devenv.exe (Visual Studio)
<br />

  Tür sağlayıcıları test betiği (örneğin, script.fsx) üzerinde fsc.exe kullanarak, en kolay genellikle ayıklayabilirsiniz. Hata ayıklayıcı komut isteminden başlatabilirsiniz.
<br />

```
  devenv /debugexe fsc.exe script.fsx
```

  Yazdırma stdout günlüğünü kullanabilirsiniz.
<br />


## <a name="see-also"></a>Ayrıca Bkz.
[Tür Sağlayıcıları](index.md)
