---
title: 'Öğretici: Bir tür sağlayıcısı oluşturma'
description: Kendi oluşturmayı öğrenin F# tür sağlayıcıları F# İnceleme temel kavramları göstermek üzere birkaç basit tür sağlayıcıları tarafından 3.0.
ms.date: 02/02/2019
ms.openlocfilehash: 14e3035d03438aaaa2f6e64210f99e1f149db274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982624"
---
# <a name="tutorial-create-a-type-provider"></a>Öğretici: Bir tür sağlayıcısı oluşturma

Tür sağlayıcısı mekanizmasında F# kendi bilgi zengin programlama desteğinin önemli bir parçasıdır. Bu öğretici, kendi tür sağlayıcıları tarafından temel kavramları göstermek üzere birkaç basit tür sağlayıcısı geliştirmeden walking oluşturma açıklanmaktadır. Tür sağlayıcısı mekanizması hakkında daha fazla bilgi için F#, bkz: [tür sağlayıcıları](index.md).

F# Ekosistemi için yaygın olarak kullanılan Internet ve kurumsal veri hizmetlerinde tür sağlayıcıları aralığı içerir. Örneğin:

- [FSharp.Data](https://fsharp.github.io/FSharp.Data/) JSON, XML, CSV ve HTML biçimleri belge için tür sağlayıcıları içerir.

- [SQLProvider](https://fsprojects.github.io/SQLProvider/) türü kesin belirlenmiş bir nesne eşleme aracılığıyla SQL veritabanı erişim sağlar ve F# LINQ sorguları bu veri kaynaklarına karşı.

- [FSharp.Data.SqlClient](https://fsprojects.github.io/FSharp.Data.SqlClient/) sahip bir derleme zamanı için tür sağlayıcıları kümesini iade T-SQL ekleme F#.

- [FSharp.Data.TypeProviders](https://fsprojects.github.io/FSharp.Data.TypeProviders/) kullanmak için tür sağlayıcıları SQL, Entity Framework, OData ve WSDL veri hizmetlerine erişmek için yalnızca .NET Framework programlama ile daha eski bir kümesidir.

Gerektiğinde, özel tür sağlayıcılarınızı oluşturabilir veya başkalarının oluşturulan tür sağlayıcılarına başvurabilirsiniz. Örneğin, kuruluşunuz bir büyük ve artan sayıda adlandırılmış veri kümeleri, her biri kendi kararlı veri şemasına sahip sağlayan bir veri hizmeti olabilir. Şemaları okuyan ve geçerli veri kümelerini programcıya türü kesin belirlenmiş şekilde sunan bir tür sağlayıcısı oluşturabilirsiniz.

## <a name="before-you-start"></a>Başlamadan önce

Tür sağlayıcısı mekanizması, öncelikli olarak kararlı veri ve hizmet bilgileri alanları içine ekleme için tasarlanmıştır F# programlama deneyimi.

Bu mekanizma, program mantığına uygun şekilde, programın yürütülmesi sırasında şema değişiklikleri bilgi alanları ekleme için tasarlanmamıştır. Ayrıca, bu etki bazı geçerli kullanımlarını içerse mekanizması içi diller için meta programlama tasarlanmamıştır. Burada bir tür sağlayıcısı geliştirilmesini çok yüksek bir değer oluşturur ve bu mekanizma yalnızca gerekli olduğunda kullanmalısınız.

Burada bir şema kullanılamaz bir tür sağlayıcısı yazma kaçınmanız gerekir. Benzer şekilde, bir tür sağlayıcısı sıradan (veya hatta var olduğunda) yazma kaçınmalısınız .NET kitaplığı yeterli.

Başlamadan önce aşağıdaki soruları sormaya:

- Bilgi kaynağınız için bir şema var mı? Bu nedenle, bir eşlemeye nedir, F# ve tür sistemi .NET?

- Mevcut bir (dinamik olarak yazılan) API uygulamanız için başlangıç noktası olarak kullanabilir miyim?

- Sizin ve kuruluşunuzun yeterli yazmayı faydalı hale getirmek için tür sağlayıcısını kullanımları gerekir mi? Normal bir .NET kitaplığı, ihtiyaçlarınızı karşılayacak?

- Ne kadar şemanızı değişecek mi?

- Kodlama sırasında değişecek mi?

- Oturumlarının kodlama arasında değişir mi?

- Bu program yürütme sırasında değişecek mi?

Tür sağlayıcıları şema zamanında ve derlenmiş kod kullanım ömrü süresince kararlı olduğu durumlar için uygundur.

## <a name="a-simple-type-provider"></a>Bir basit tür sağlayıcısı

Bu örnek Samples.HelloWorldTypeProvider, örnekler, benzer olan `examples` dizininde [ F# tür sağlayıcı SDK'sı](https://github.com/fsprojects/FSharp.TypeProviders.SDK/). Sağlayıcı "kullanarak aşağıdaki kodun gösterdiği olarak 100 silinen türlerini içeren bir tür alanı" kullanılabilmesini F# imza söz dizimi ve hariç tüm sayfalarında için ayrıntıları atlama `Type1`. Silinen türleri hakkında daha fazla bilgi için bkz. [ayrıntılar hakkında silinmesi sağlanan türleri](#details-about-erased-provided-types) bu konuda.

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

Dizi türleri ve üyeleri sağlanan statik olarak bilinen unutmayın. Bu örnek, bir şemaya bağlı türleri sağlama yeteneği sağlayıcılarının yararlanarak değil. Tür sağlayıcısı uygulaması aşağıdaki kodda gösterilmiştir ve Ayrıntılar, bu konunun sonraki bölümlerinde ele alınmaktadır.

> [!WARNING]
> Bu kod ve çevrimiçi örnekleri arasındaki farklar olabilir.

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

Bu sağlayıcıyı kullanmak için Visual Studio ayrı bir örneğini açın, oluşturun bir F# betik ve ardından aşağıdaki kodun gösterdiği gibi #r kullanarak betiğinizi sağlayıcı için bir başvuru ekleyin:

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

Türleri altında bulun `Samples.HelloWorldTypeProvider` tür sağlayıcısını oluşturulan ad alanı.

Sağlayıcıyı yeniden derlemeden önce Visual Studio'nun tüm örneklerini kapalı emin olun ve F# Sağlayıcı DLL kullanarak etkileşimli. Aksi takdirde, çıkış DLL kilitli olduğundan bir yapı hatası meydana gelir.

Bu sağlayıcı yazdırma ifadeleri kullanarak hata ayıklamak için sağlayıcı ile ilgili bir sorun ortaya koyan bir betik olun ve ardından aşağıdaki kodu kullanın:

```
fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Visual Studio kullanarak bu sağlayıcı hata ayıklamak için yönetici kimlik bilgileriyle Visual Studio için geliştirici komut istemi açın ve aşağıdaki komutu çalıştırın:

```
devenv.exe /debugexe fsc.exe -r:bin\Debug\HelloWorldTypeProvider.dll script.fsx
```

Alternatif olarak, Visual Studio'yu açın, hata ayıklama menüsünü açın, `Debug/Attach to process…`ve başka bir ekleme `devenv` burada düzenlediğiniz komut dosyanızı işlem. Bu yöntemi kullanarak, ikinci örneği (tam IntelliSense ve diğer özellikleri) içine etkileşimli olarak ifadeleri yazarak belirli bir tür sağlayıcısı mantığında daha kolay hedef alabilirsiniz.

Oluşturulan kod hataları daha iyi tanımlamak için hata ayıklama Just My Code'u devre dışı bırakabilirsiniz. Etkinleştirme veya bu özelliği devre dışı bırakma hakkında daha fazla bilgi için bkz. [hata ayıklayıcısı ile kodlarda gezinme](/visualstudio/debugger/navigating-through-code-with-the-debugger). Ayrıca, ayrıca ilk fırsat özel durum yakalama açarak ayarlayabilirsiniz `Debug` menüsüne ve ardından `Exceptions` açmak için Ctrl + Alt + E tuşlarını seçerek veya `Exceptions` iletişim kutusu. Bu iletişim kutusunda, altında `Common Language Runtime Exceptions`seçin `Thrown` onay kutusu.

### <a name="implementation-of-the-type-provider"></a>Tür sağlayıcısı uygulaması

Bu bölüm asıl tür sağlayıcısı uygulama bölümleri boyunca size yol gösterir. İlk olarak, türü özel bir tür sağlayıcısı kendisi için tanımlayın:

```fsharp
[<TypeProvider>]
type SampleTypeProvider(config: TypeProviderConfig) as this =
```

Bu tür genel olmalıdır ve kendisiyle işaretlemek [TypeProvider](https://msdn.microsoft.com/library/bdf7b036-7490-4ace-b79f-c5f1b1b37947) derleyicinin tür sağlayıcısını ayrı bir zaman tanıyabilmesi için öznitelik F# proje türü içeren derlemeye başvurur. *Config* parametresi isteğe bağlıdır ve, varsa, tür sağlayıcısı örneği için bağlamsal yapılandırma bilgilerini içeren F# derleyici oluşturur.

Ardından, uygulamanız [Itypeprovider](https://msdn.microsoft.com/library/2c2b0571-843d-4a7d-95d4-0a7510ed5e2f) arabirimi. Bu durumda, kullandığınız `TypeProviderForNamespaces` türünü `ProvidedTypes` temel tür olarak API. Bu yardımcı türü her biri doğrudan sınırlı sayıda sabit içerir, ad alanları, türler eagerly sağlanan sağlanan sınırlı koleksiyonu eagerly sağlayabilir. Bu bağlamda, sağlayıcı *eagerly* bile kullanılan gerekli veya olmayan türleri oluşturur.

```fsharp
inherit TypeProviderForNamespaces(config)
```

Ardından, sağlanan türler için ad alanı belirten yerel özel değerleri tanımlayın ve tür sağlayıcısı derlemenin kendisini bulun. Bu derleme, daha sonra silinen türleri mantıksal üst türü olarak kullanılır.

```fsharp
let namespaceName = "Samples.HelloWorldTypeProvider"
let thisAssembly = Assembly.GetExecutingAssembly()
```

Ardından, her tür Type1 sağlamak için bir işlev oluşturun... Type100. Bu işlev, bu konunun ilerleyen bölümlerinde daha ayrıntılı açıklanmıştır.

```fsharp
let makeOneProvidedType (n:int) = …
```

Ardından, 100 sağlananlardan oluştur:

```fsharp
let types = [ for i in 1 .. 100 -> makeOneProvidedType i ]
```

Ardından, belirtilen bir ad alanı türleri ekleyin:

```fsharp
do this.AddNamespace(namespaceName, types)
```

Son olarak, bir tür sağlayıcısı DLL oluştururken bir bütünleştirilmiş kod özniteliği ekleyin:

```fsharp
[<assembly:TypeProviderAssembly>]
do()
```

### <a name="providing-one-type-and-its-members"></a>Bir tür ve üyeleri sağlama

`makeOneProvidedType` İşlevi türlerinden birini sağlayarak gerçek iş yapar.

```fsharp
let makeOneProvidedType (n:int) =
…
```

Bu adım, bu işlev uygulamasını açıklar. İlk olarak sağlanan türü oluşturun (örneğin, Type1, n, = 1 veya Type57, 57 = n olduğunda).

```fsharp
// This is the provided type. It is an erased provided type and, in compiled code,
// will appear as type 'obj'.
let t = ProvidedTypeDefinition(thisAssembly, namespaceName,
                               "Type" + string n,
                               baseType = Some typeof<obj>)
```

Aşağıdaki noktalara dikkat edin:

- Başka bir sağlanan türü silinir.  Temel tür olduğunu belirttiğinden `obj`, örnekleri, tür değerleri görünür [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) derlenmiş kodu.

- Bir iç içe türü belirttiğinizde, derlemeyi ve ad alanını belirtmeniz gerekir. Silinen türleri için derleme, tür sağlayıcısı derlemenin kendisini olması gerekir.

Ardından, XML belgeleri türüne ekleyin. Bu belge, yani gecikir, konak derleyici gerekiyorsa isteğe bağlı hesaplanan.

```fsharp
t.AddXmlDocDelayed (fun () -> sprintf "This provided type %s" ("Type" + string n))
```

Sonraki türüne sağlanan statik bir özellik ekleyin:

```fsharp
let staticProp = ProvidedProperty(propertyName = "StaticProperty",
                                  propertyType = typeof<string>,
                                  isStatic = true,
                                  getterCode = (fun args -> <@@ "Hello!" @@>))
```

Bu özellik alma "Hello!" dizesi her zaman değerlendirilir. `GetterCode` Özelliği için kullanan bir F# özelliği almak için konak derleyicinin ürettiği kodu temsil eden bir teklif. Teklifleri hakkında daha fazla bilgi için bkz: [kod tırnak işaretleri (F#)](https://msdn.microsoft.com/library/6f055397-a1f0-4f9a-927c-f0d7c6951155).

XML belgelerinde özellik ekleyin.

```fsharp
staticProp.AddXmlDocDelayed(fun () -> "This is a static property")
```

Artık sağlanan özelliği için sağlanan türü ekleyin. Belirtilen üye bir ve yalnızca bir türe eklemeniz gerekir. Aksi takdirde, üye hiç erişilebilir olacaktır.

```fsharp
t.AddMember staticProp
```

Parametre almayan sağlanan bir oluşturucu şimdi oluşturun.

```fsharp
let ctor = ProvidedConstructor(parameters = [ ],
                               invokeCode = (fun args -> <@@ "The object data" :> obj @@>))
```

`InvokeCode` Döndürür oluşturucusu için bir F# Oluşturucu çağrıldığında, konak Derleyicinin oluşturduğu kodu temsil eden bir teklif. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10()
```

Belirtilen türün bir örneğini "Nesne verilerini" ile temel alınan verileri oluşturulur. Tırnak işaretli kod dönüştürmeyi içerir [obj](https://msdn.microsoft.com/library/dcf2430f-702b-40e5-a0a1-97518bf137f7) silinmesini türü olduğundan (sağlanan türü olduğunda bildirdiğiniz belirttiğiniz gibi) bu türü sağlanmaktadır.

XML belgeleri oluşturucuyu ekleyin ve sağlanan türü için sağlanan oluşturucu ekleyin:

```fsharp
ctor.AddXmlDocDelayed(fun () -> "This is a constructor")

t.AddMember ctor
```

Bir parametre alan ikinci bir sağlanan Oluşturucu oluşturun:

```fsharp
let ctor2 =
ProvidedConstructor(parameters = [ ProvidedParameter("data",typeof<string>) ],
                    invokeCode = (fun args -> <@@ (%%(args.[0]) : string) :> obj @@>))
```

`InvokeCode` Oluşturucu yeniden döndürür bir F# konak derleyici yönteme bir çağrı için oluşturulan kodu temsil eden bir teklif. Örneğin, aşağıdaki oluşturucuyu kullanabilirsiniz:

```fsharp
new Type10("ten")
```

Belirtilen türün bir örneğini, temel alınan veriler "on" ile oluşturulur. Zaten fark etmiş `InvokeCode` tırnak işlevi döndürür. Bu işlev girişi ifadeleri, oluşturucu parametresi başına bir listesidir. Bu durumda, tek bir parametre değeri temsil eden bir ifade kullanılabilir `args.[0]`. Dönüş değeri silinen türü için oluşturucu çağrısı için kod olacak şekilde zorlar `obj`. İkinci sağlanan Oluşturucu türüne ekledikten sonra sağlanan örnek özellik oluşturun:

```fsharp
let instanceProp =
    ProvidedProperty(propertyName = "InstanceProperty",
                     propertyType = typeof<int>,
                     getterCode= (fun args ->
                        <@@ ((%%(args.[0]) : obj) :?> string).Length @@>))
instanceProp.AddXmlDocDelayed(fun () -> "This is an instance property")
t.AddMember instanceProp
```

Bu özellik alma gösterimi nesne dizenin uzunluğunu döndürür. `GetterCode` Özelliği döndürür bir F# teklif özellik get yapılmaya konak derleyicinin ürettiği kodu belirtir. Gibi `InvokeCode`, `GetterCode` tırnak işlevi döndürür. Konak derleyici bağımsız değişken listesiyle birlikte bu işlevi çağırır. Bu durumda, bağımsız değişkenleri yalnızca kullanarak erişebileceğiniz bağlı alıcı çağrılmakta olan, örneği temsil eden tek ifade ekleyin `args.[0]`. Uygulamasını `GetterCode` sonra silinen yazın sonucu tırnak içine splices `obj`, ve bir atama türü bir nesne bir dize olduğunu denetlemek için derleyicinin mekanizması karşılamak için kullanılır. Bir sonraki kısmına `makeOneProvidedType` bir parametre ile bir örnek yöntemi sağlar.

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

Son olarak, 100 iç içe özellikler içeren iç içe geçmiş bir tür oluşturun. Bu oluşturma türü ve özelliklerini iç içe geçmiş, yani gecikir, isteğe bağlı olarak hesaplanır.

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

### <a name="details-about-erased-provided-types"></a>Silinen sağlanan türleri hakkında ayrıntılar

Bu bölümdeki örnek yalnızca sağlar *sağlananlardan silinmesi*, aşağıdaki durumlarda özellikle yararlı olan:

- Ne zaman yalnızca verilere ve yöntemlere içeren bir bilgi alanı için bir sağlayıcı yazıyorsunuz.

- Ne zaman doğru çalışma zamanı türü anlamları burada bilgi alanı pratik kullanım için kritik olmayan bir sağlayıcı yazıyorsunuz.

- Ne zaman büyük ve birbirine bilgi alanı gerçek .NET türleri üretmek için teknik olarak uygulanabilir olmayan bir bilgi alan için bir sağlayıcı yazıyorsunuz.

Bu örnekte, her tür türüne silinir sağlanan `obj`, ve tüm kullanımları türü tür olarak görünür `obj` derlenmiş kodu. Aslında, bu örneklerde temel nesneler dizelerdir, ancak türü olarak görünür `System.Object` derlenmiş .NET kodu. Tür silme işlemini ile tüm kullanımları için açık kutulama kullanabileceğiniz gibi kutudan çıkarma ve atama bozmaya için türleri silinir. Bu durumda, nesne kullanıldığında geçerli olmayan bir yayın özel durumu neden olabilir. Bir sağlayıcı çalışma zamanı false ifadeleri karşı korumaya yardımcı olmak için kendi özel gösterimi türü tanımlayabilirsiniz. Silinen türlerinde tanımlanamaz F# kendisi. Yalnızca sağlanan türler silinebilir. Sonuçları, hem pratik anlamanız gerekir ve anlam kullanarak, silinen türleri, tür sağlayıcısı veya sağlayan bir sağlayıcı için türleri silinir. Silinen bir türü gerçek .NET tür yok. Bu nedenle, türü üzerinden çevrenin yansımasını yapamayacağı ve çalışma zamanı yayınları ve çalışma zamanı türü semantiği kullanan diğer teknikleri kullanırsanız silinen türleri bozmaya. Silinen türlerinin subversion çalışma zamanında tür özel durumlar sık sonuçlanır.

### <a name="choosing-representations-for-erased-provided-types"></a>Türleri sağlanan gösterimleri silinmesi için seçme

Bazı silinen sağlananlardan kullanımlar için hiçbir gösterimi gereklidir. Örneğin, silinen tür yalnızca statik özellikleri ve üyeleri ve Oluşturucusu içerebilir ve yöntem ya da özellikleri türün bir örneğini döndürür sağlanır. Silinen bir örneğini türü sağlanan erişebiliyorsa, aşağıdaki soruları göz önünde bulundurmalısınız:

**Belirtilen bir türün silinme nedir?**

- Belirtilen bir türün silinme türü'nın derlenmiş .NET kodu nasıl göründüğü üzerinedir.

- Sağlanan silinen sınıf türü silinme her zaman ilk silinebilir olmayan temel devralma zincirinde türü türüdür.

- Her zaman silinme silinen sağlanan arabirim türü olduğundan `System.Object`.

**Sağlanan türü temsillerini nelerdir?**

- Bir silinen sağlanan türü için olası nesne kümesini kendi gösterimleri çağrılır. Bu belgedeki örnekte, tüm silinen sağlanan temsillerini türleri `Type1..Type100` dize nesneler her zaman kullanılabilir.

Sağlanan türü tüm temsillerini silinmesini sağlanan türü ile uyumlu olması gerekir. (Aksi halde, ya da F# derleyici, bir tür sağlayıcısı kullanım için bir hata verir veya geçerli olmayan doğrulanamayan .NET kod üretilmeyecek. Bir tür sağlayıcısı geçersiz bir temsili veren kodu döndürmesi durumunda geçerli değil.)

Sağlanan nesneler için bir gösterimi ikisi için de çok yaygın olarak, aşağıdaki yaklaşımlardan birini kullanarak birini seçebilirsiniz:

- Üzerinde var olan bir .NET türü kesin olarak belirlenmiş bir sarmalayıcı yalnızca sağlıyorsanız, genellikle bu türe silmek, o türün örneklerinin gösterimleri veya her ikisi de olarak kullanın türünüz için mantıklıdır. Bu türün varolan yöntemleri çoğunu yine de kesin türdeki sürümü kullanılırken anlamlı olduğunda bu yaklaşım uygundur.

- Farklı bir API önemli ölçüde var olan bir .NET API'SİNDEN oluşturmak istiyorsanız, temsiller için sağlanan türler ve tür silme işlemini olacak çalışma zamanı türleri oluşturmak için mantıklıdır.

Bu belgede örnek sağlanan Nesne ifadeleri dizeleri kullanır. Genellikle, diğer nesneleri temsiller için kullanılmak üzere uygun olabilir. Örneğin, bir özellik paketi olarak bir sözlük kullanabilirsiniz:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new Dictionary<string,obj>()) :> obj @@>))
```

Alternatif olarak, türü Sağlayıcınızdaki çalışma zamanında bir veya daha fazla çalışma zamanı işlemlerinin yanı sıra bir gösterim oluşturmak için kullanılan bir tür tanımlayabilirsiniz:

```fsharp
type DataObject() =
    let data = Dictionary<string,obj>()
    member x.RuntimeOperation() = data.Count
```

Belirtilen üye, ardından bu nesne türü örnekleri oluşturabilirsiniz:

```fsharp
ProvidedConstructor(parameters = [],
    invokeCode= (fun args -> <@@ (new DataObject()) :> obj @@>))
```

Bu durumda, (isteğe bağlı) bu tür türü silinme bu türü olarak belirterek kullanabilirsiniz `baseType` oluştururken `ProvidedTypeDefinition`:

```fsharp
ProvidedTypeDefinition(…, baseType = Some typeof<DataObject> )
…
ProvidedConstructor(…, InvokeCode = (fun args -> <@@ new DataObject() @@>), …)
```

### <a name="key-lessons"></a>Önemli dersler

Önceki bölümde çeşitli türler, özellikler ve yöntemler sağlayan basit bir silme tür sağlayıcısı oluşturma açıklanmaktadır. Bu bölümde açıklanan bazı avantajları ve dezavantajları silinen türleri bir türü sağlayıcısından sağlayan dahil olmak üzere tür silme işlemini kavramını ve Silinen türleri temsillerini ele alınan.

## <a name="a-type-provider-that-uses-static-parameters"></a>Statik parametreler kullanan bir tür sağlayıcısı

Tür sağlayıcıları tarafından statik veri Parametreleştirme olanağı bile sağlayıcısı herhangi bir yerel veya uzak veri erişimi gerekmez, durumlarda çok ilginç senaryolarını etkinleştirir. Bu bölümde, böyle bir sağlayıcı bir araya getirilmesi için bazı temel tekniklerini öğreneceksiniz.

### <a name="type-checked-regex-provider"></a>Regex sağlayıcısı türü işaretli

.NET sarmalayan bir tür sağlayıcısı normal ifadeler için uygulamak istediğiniz Imagine <xref:System.Text.RegularExpressions.Regex> aşağıdaki derleme zamanı garanti sağlayan bir arabirimi kitaplıkları:

- Bir normal ifade geçerli olup olmadığını doğrulanıyor.

- Normal ifadede herhangi bir grup adı temel alan eşleşme adlandırılmış özellikleri sunuyor.

Bu bölümde tür sağlayıcıları oluşturmak için nasıl kullanılacağını gösteren bir `RegexTyped` normal ifade deseni aşağıdaki yararları sağlamak üzere parametreleştiren yazın. Derleyici, belirtilen desenle geçerli değil ve adlandırılmış eşleşmeleri Özellikler'i kullanarak erişebilmeleri tür sağlayıcısını grupları desenden ayıklayabilmeniz için bir hata rapor eder. Bir tür sağlayıcısı tasarlarken, açık bir API nasıl görünmelidir dikkate almanız gereken son kullanıcılar ve bu tasarım .NET kodu için nasıl çevirir. Aşağıdaki örnek, alan kodunu bileşenlerini almak için bu tür bir API kullanmayı gösterir:

```fsharp
type T = RegexTyped< @"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)">
let reg = T()
let result = T.IsMatch("425-555-2345")
let r = reg.Match("425-555-2345").Group_AreaCode.Value //r equals "425"
```

Aşağıdaki örnek, ne tür sağlayıcısı bu çağrıları çeviren gösterir:

```fsharp
let reg = new Regex(@"(?<AreaCode>^\d{3})-(?<PhoneNumber>\d{3}-\d{4}$)")
let result = reg.IsMatch("425-123-2345")
let r = reg.Match("425-123-2345").Groups.["AreaCode"].Value //r equals "425"
```

Aşağıdaki noktalara dikkat edin:

- Standart Regex tür parametreli temsil eden `RegexTyped` türü.

- `RegexTyped` Deseni için statik tür bağımsız değişkeni olarak geçirerek Regex oluşturucusuna bir çağrı Oluşturucusu sonuçlanıyor.

- Sonuçları `Match` yöntemi Standart tarafından temsil edilen <xref:System.Text.RegularExpressions.Match> türü.

- Belirtilen bir özelliği her adlandırılmış Grup sonuçları gruplayan ve özellik erişen bir kullanımıyla sonuçlanıyor bir dizin oluşturucusunda bir eşleşme'nın `Groups` koleksiyonu.

Aşağıdaki kodu bir tür sağlayıcısı için uygulanacak bir mantıksal çekirdek olduğunu ve sağlanan türü için tüm üyeleri Ayrıca bu örnek atlar. Her üye eklendi hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde ilgili bölüme bakın. Tam kod için içinden örneği karşıdan [ F# 3.0 örnek paketi](https://archive.codeplex.com/?p=fsharp3sample) CodePlex Web sitesinde.

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

- Tür sağlayıcısını iki statik parametreleri alır: `pattern`, zorunlu olan ve `options`, (varsayılan değer sağlandığı için) isteğe bağlı olduğu.

- Statik bağımsız değişkenler sağlanan sonra normal ifade örneği oluşturun. Bu örnek, normal ifade hatalı biçimlendirilmiş ve kullanıcılara bu hata bildirilir bir özel durum oluşturur.

- İçinde `DefineStaticParameters` geri bağımsız değişkenler sağlanan sonra döndürülecek tür tanımlayın.

- Bu kod ayarlar `HideObjectMethods` IntelliSense deneyimi kolaylaştırılmış kalması true. Bu öznitelik neden `Equals`, `GetHashCode`, `Finalize`, ve `GetType` atlanması üyelerinin sağlanan nesne için IntelliSense listelerden.

- Kullandığınız `obj` yöntemi, ancak temel türünü kullanırsınız gibi bir `Regex` sonraki örnekte gösterildiği gibi bu tür, çalışma zamanı temsili olarak nesnesi.

- Çağrı `Regex` Oluşturucusu oluşturur bir <xref:System.ArgumentException> ne zaman bir normal ifade geçerli değil. Derleyici, bu özel durumu yakalar ve derleme zamanında ya da Visual Studio düzenleyicisinde bir hata iletisi kullanıcıya bildirir. Bu durum, bir uygulamayı çalıştırmadan doğrulanması için normal ifadeler sağlar.

Yukarıda tanımlanan tür henüz herhangi bir anlamlı yöntemleri veya özellikleri içermediğinden kullanışlı değildir. İlk olarak, bir statik ekleyin `IsMatch` yöntemi:

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

Önceki kod, bir yöntem tanımlar `IsMatch`, giriş olarak bir dize alır ve döndürür bir `bool`. Kullanımı yalnızca hassas parçasıdır `args` bağımsız değişkeni içinde `InvokeCode` tanımı. Bu örnekte, `args` bu yönteme bağımsız değişkenleri temsil eden teklif listesi verilmiştir. Yöntemi bir örnek yöntem ise, ilk bağımsız değişken temsil eden `this` bağımsız değişken. Ancak, statik bir yöntem için yalnızca tüm açık bağımsız değişkenler yöntemi için bağımsız değişkenler. Tırnak işaretli değerinin türü belirtilen dönüş türü eşleşmelidir Not (Bu durumda, `bool`). Ayrıca bu kodu kullanan Not `AddXmlDoc` yöntemi sağlanan yöntem aynı zamanda IntelliSense sağladığınız kullanışlı belgeler olduğundan emin olun.

Ardından, bir örneği Match yöntemi ekleyin. Ancak, bu yöntem bir sağlanan değerini döndürmelidir `Match` grupları türü kesin belirlenmiş bir biçimde erişilebilir olacak şekilde yazın. Bu nedenle, öncelikle bildirin `Match` türü. Bu tür bir statik bağımsız değişken olarak sağlanan deseni bağlı olduğundan bu tür parametreli tür tanımı içinde iç içe olmamalıdır:

```fsharp
let matchTy =
    ProvidedTypeDefinition(
        "MatchType",
        baseType = Some baseTy,
        hideObjectMethods = true)

ty.AddMember matchTy
```

Her grup için eşleşme türü için bir özellik ekleyin. Çalışma zamanında bir eşleşme olarak temsil edilen bir <xref:System.Text.RegularExpressions.Match> değeri özelliğini tanımlar tırnak kullanmalısınız <xref:System.Text.RegularExpressions.Match.Groups> ilgili grubun almak için özelliğin dizini.

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

XML belgeleri için sağlanan özellik ekliyoruz yeniden unutmayın. Ayrıca, bir özelliği okunabilir Not bir `GetterCode` işlevi sağlanır ve özelliği, yazılabilir bir `SetterCode` işlevi sağlanır, sonuçta elde edilen özelliği salt okunur şekilde.

Bu değer döndüren bir örnek yöntemi oluşturabilirsiniz artık `Match` türü:

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

Bir örnek yöntemi oluşturduğunuzdan `args.[0]` temsil `RegexTyped` üzerinde yöntemi çağrılmakta olan, örnek ve `args.[1]` giriş bağımsız değişkeni.

Son olarak, belirtilen türdeki örneklerin oluşturulan bir oluşturucu sağlayın.

```fsharp
let ctor =
    ProvidedConstructor(
        parameters = [],
        invokeCode = fun args -> <@@ Regex(pattern, options) :> obj @@>)

ctor.AddXmlDoc("Initializes a regular expression instance.")

ty.AddMember ctor
```

Oluşturucu yalnızca bir nesneye olduğundan yeniden paketlenmiş bir standart .NET normal ifade örneği oluşturulmasını siler `obj` sağlanan türü silinmesini olduğu. Bu değişiklik, bu konuda daha önce belirtilen örnek API kullanımı beklendiği gibi çalışır. Aşağıdaki kod, tam ve son:

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

### <a name="key-lessons"></a>Önemli dersler

Bu bölümde, kendi statik parametrelerine göre işleyen bir tür sağlayıcısı oluşturma açıklanmıştır. Sağlayıcı statik parametresinin denetler ve, değerini temel alarak işlemler sağlar.

## <a name="a-type-provider-that-is-backed-by-local-data"></a>Yerel veri tarafından desteklenen bir tür sağlayıcısı

Genellikle, yalnızca statik parametreler aynı zamanda bilgi yerel veya uzak sistemlerden dayalı API'leri sunmak için tür sağlayıcıları isteyebilirsiniz. Bu bölümde, yerel veri dosyaları gibi yerel verileri temel alan bir tür sağlayıcıları ele alınmaktadır.

### <a name="simple-csv-file-provider"></a>Basit bir CSV dosya sağlayıcısı

Basit bir örnek olarak, bir tür sağlayıcısı virgülle ayrılmış değer (CSV) biçimini bilimsel veri erişimi için göz önünde bulundurun. Bu bölümde aşağıdaki tabloda gösterildiği gibi kayan nokta verisi tarafından izlenen bir üst bilgi satırı CSV dosyaları içerdiğini varsayar:

|Uzaklık (ölçer)|Süresi (saniye)|
|----------------|-------------|
|50.0|3.7|
|100.0|5.2|
|150.0|6.4|

Bu bölüm nasıl satırlarla almak için kullanabileceğiniz bir türü gösterir bir `Distance` türünün özelliği `float<meter>` ve `Time` türünün özelliği `float<second>`. Kolaylık olması için aşağıdaki varsayımların oluşturulur:

- Üst bilgi adları olan ya da birimi daha az veya "(birim) adı" sahiptir ve virgül içermeyen.

- Birimlerin tüm sistem uluslararası (sı) birimi olarak [Microsoft.FSharp.Data.UnitSystems.SI.UnitNames Modülü (F#)](https://msdn.microsoft.com/library/3cb43485-11f5-4aa7-a779-558f19d4013b) modülü tanımlar.

- Birimlerin tüm basit (örneğin, ölçüm) bileşik (örneğin, ölçüm/saniye) yerine.

- Tüm sütunlar kayan nokta verisi içerir.

Daha eksiksiz bir sağlayıcı, bu kısıtlamalar çözmek.

Yeniden API'yi nasıl görünmelidir dikkate alınması gereken ilk adım olan. Verilen bir `info.csv` dosyası (biçiminde virgülle ayrılmış) önceki tablosundan içeriğiyle sağlayıcısının kullanıcılar aşağıdaki örneğe benzeyen kod yazabiliyor olmalıdır:

```fsharp
let info = new MiniCsv<"info.csv">()
for row in info.Data do
let time = row.Time
printfn "%f" (float time)
```

Bu durumda, derleyici aşağıdaki örnekte olduğu gibi bir şeyi bu çağrılar dönüştürmeniz gerekir:

```fsharp
let info = new CsvFile("info.csv")
for row in info.Data do
let (time:float) = row.[1]
printfn "%f" (float time)
```

En uygun çeviri gerçek tanımlamak tür sağlayıcısını gerektirecek `CsvFile` derlemesindeki tür sağlayıcısının türü. Tür sağlayıcıları, genellikle birkaç Yardımcısı türleri ve yöntemleri üzerinde önemli mantık sarmalamak için kullanır. Çalışma zamanında ölçümleri silinmeden için kullanabileceğiniz bir `float[]` bir satır için silinen türü. Derleyicinin farklı sütundan farklı ölçü türlerine sahip olarak değerlendirir. Örneğin, Örneğimizdeki ilk sütunda türünde `float<meter>`, ve ikinci `float<second>`. Ancak, silinen gösterimi oldukça basit kalabilir.

Aşağıdaki kod, çekirdek uygulamasının gösterir.

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

Uygulama hakkında aşağıdaki noktalara dikkat edin:

- Özgün dosya veya okumak için bir aynı şemaya sahip bir aşırı yüklü oluşturucular sağlar. Bu düzen, yerel veya uzak veri kaynakları için bir tür sağlayıcısı yazma ve uzak veri için şablon olarak kullanılacak bir yerel dosya bu deseni tanır yaygındır.

- Kullanabileceğiniz [TypeProviderConfig](https://msdn.microsoft.com/library/1cda7b9a-3d07-475d-9315-d65e1c97eb44) göreli dosya adlarını çözümlemek için tür sağlayıcı oluşturucuya geçirilen değer.

- Kullanabileceğiniz `AddDefinitionLocation` sağlanan özellikler konumunu tanımlamak için yöntemi. Bu nedenle, kullanırsanız `Go To Definition` sağlanan bir özellik, CSV dosyasını Visual Studio'da açılır.

- Kullanabileceğiniz `ProvidedMeasureBuilder` türü sı birimler arayın ve ilgili oluşturmak üzere `float<_>` türleri.

### <a name="key-lessons"></a>Önemli dersler

Bu bölümde, veri kaynağında kendisini içeren basit bir şemaya sahip bir yerel veri kaynağı için bir tür sağlayıcısı oluşturma açıklanmıştır.

## <a name="going-further"></a>Daha fazla devam

Aşağıdaki bölümlerde daha fazla araştırma için öneriler içerir.

### <a name="a-look-at-the-compiled-code-for-erased-types"></a>Silinen türleri için derlenmiş kod bakma

Ne tür sağlayıcısını kullanımını yayılan koduna karşılık gelen hakkında biraz fikir vermek için aşağıdaki işlevi kullanarak araması `HelloWorldTypeProvider` bu konunun önceki bölümlerinde kullanılır.

```fsharp
let function1 () =
    let obj1 = Samples.HelloWorldTypeProvider.Type1("some data")
    obj1.InstanceProperty
```

Sonuç kodunu ildasm.exe kullanarak decompiled görüntüsü aşağıda verilmiştir:

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

Tüm bahsetmeleri türü örnekte gösterildiği gibi `Type1` ve `InstanceProperty` özelliği silinmesi, yalnızca çalışma zamanı türleri üzerinde işlemler dahil çıkılıyor.

### <a name="design-and-naming-conventions-for-type-providers"></a>Tasarım ve adlandırma kuralları için tür sağlayıcıları

Tür sağlayıcıları yazarken aşağıdaki kurallar gözlemleyin.

**Bağlantı protokoller için sağlayıcıları** genel olarak, veri ve hizmet bağlantısı gibi protokolleri OData veya SQL bağlantıları için çoğu sağlayıcısı DLL'leri adlarını bitmelidir `TypeProvider` veya `TypeProviders`. Örneğin, aşağıdaki dize şuna benzer bir DLL adı kullanın:

```
  Fabrikam.Management.BasicTypeProviders.dll
```

Sağlanan türlerinizi karşılık gelen ad alanının üyeleri ve uygulanan bağlantı protokolü belirtmek emin olun:

```
  Fabrikam.Management.BasicTypeProviders.WmiConnection<…>
  Fabrikam.Management.BasicTypeProviders.DataProtocolConnection<…>
```

**Genel olarak kodlamak için yardımcı program sağlayıcıları**.  Yardımcı programı için bir tür sağlayıcısı gibi normal ifadeler için tür sağlayıcısı aşağıdaki örnekte gösterildiği gibi bir temel kitaplığının bir parçası olabilir:

```fsharp
#r "Fabrikam.Core.Text.Utilities.dll"
```

Bu durumda, sağlanan türü normal .NET Tasarım Kuralları göre uygun bir noktada görünür:

```fsharp
  open Fabrikam.Core.Text.RegexTyped

  let regex = new RegexTyped<"a+b+a+b+">()
```

**Tekli veri kaynakları**. Bazı tür sağlayıcılarını tek bir adanmış veri kaynağına bağlanmak ve yalnızca veriler sağlar. Bu durumda, düşmelidir `TypeProvider` sonek ve .NET normal kuralları kullanın:

```fsharp
#r "Fabrikam.Data.Freebase.dll"

let data = Fabrikam.Data.Freebase.Astronomy.Asteroids
```

Daha fazla bilgi için `GetConnection` tasarım bu konunun ilerleyen bölümlerinde açıklanan kuralı.

### <a name="design-patterns-for-type-providers"></a>Tür sağlayıcıları için Tasarım desenleri

Aşağıdaki bölümlerde tasarım desenleri tür sağlayıcıları yazarken kullanabileceğiniz açıklanmaktadır.

#### <a name="the-getconnection-design-pattern"></a>GetConnection tasarım deseni

Çoğu tür sağlayıcıları kullanan yazılması gerektiğini `GetConnection` aşağıdaki örnekte gösterildiği gibi FSharp.Data.typeproviders.dll tür sağlayıcıları tarafından kullanılan Desen:

```fsharp
#r "Fabrikam.Data.WebDataStore.dll"

type Service = Fabrikam.Data.WebDataStore<…static connection parameters…>

let connection = Service.GetConnection(…dynamic connection parameters…)

let data = connection.Astronomy.Asteroids
```

#### <a name="type-providers-backed-by-remote-data-and-services"></a>Uzak Veri ve hizmetler tarafından desteklenen tür sağlayıcıları

Uzak Veri ve hizmetler tarafından desteklenen bir tür sağlayıcısı oluşturmadan önce bir dizi bağlı programlamada belirlidir sorunları dikkate almanız gerekir. Bu sorunları aşağıdaki önemli noktalar şunlardır:

- Şema eşleme

- canlılık ve şema değişikliği varlığında geçersiz kılma

- Şema önbelleğe alma

- Veri erişim işlemleri zaman uyumsuz uygulamaları

- LINQ sorguları da dahil olmak üzere, destekleyici sorguları

- kimlik bilgileri ve kimlik doğrulaması

Bu konu bu sorunların daha fazla keşfedin değil.

### <a name="additional-authoring-techniques"></a>Ek geliştirme teknikleri

Kendi tür sağlayıcıları yazdığınızda, aşağıdaki ek teknikler kullanmak isteyebilirsiniz.

### <a name="creating-types-and-members-on-demand"></a>Türler ve üyeler üzerine oluşturma

ProvidedType API sürümlerini AddMember Gecikmeli.

```fsharp
  type ProvidedType =
      member AddMemberDelayed  : (unit -> MemberInfo)      -> unit
      member AddMembersDelayed : (unit -> MemberInfo list) -> unit
```

Bu sürümler, isteğe bağlı alanları türleri oluşturmak için kullanılır.

### <a name="providing-array-types-and-generic-type-instantiations"></a>Dizi türleri ve genel tür Örneklemeleri sağlama

Belirtilen üye (dizi türleri ve byref türleriyle genel türlerin örneklemeleri dahil olan imzaları) normal kullanarak yaptığınız `MakeArrayType`, `MakePointerType`, ve `MakeGenericType` herhangi bir örneği üzerinde <xref:System.Type>de dahil olmak üzere `ProvidedTypeDefinitions`.

> [!NOTE]
> Bazı durumlarda yardımcı kullanmak zorunda kalabilirsiniz `ProvidedTypeBuilder.MakeGenericType`.  Bkz: [tür sağlayıcısı SDK Belgeleri](https://github.com/fsprojects/FSharp.TypeProviders.SDK/blob/master/README.md#explicit-construction-of-code-makegenerictype-makegenericmethod-and-uncheckedquotations) daha fazla ayrıntı için.

### <a name="providing-unit-of-measure-annotations"></a>Birim ölçü ek açıklamaları sağlama

ProvidedTypes API ölçü ek açıklamalar sağlayan Yardımcıları sağlar. Örneğin, türü sağlamak için `float<kg>`, aşağıdaki kodu kullanın:

```fsharp
  let measures = ProvidedMeasureBuilder.Default
  let kg = measures.SI "kilogram"
  let m = measures.SI "meter"
  let float_kg = measures.AnnotateType(typeof<float>,[kg])
```

  Türü sağlamak `Nullable<decimal<kg/m^2>>`, aşağıdaki kodu kullanın:

```fsharp
  let kgpm2 = measures.Ratio(kg, measures.Square m)
  let dkgpm2 = measures.AnnotateType(typeof<decimal>,[kgpm2])
  let nullableDecimal_kgpm2 = typedefof<System.Nullable<_>>.MakeGenericType [|dkgpm2 |]
```

### <a name="accessing-project-local-or-script-local-resources"></a>Proje yerel veya komut dosyası yerel kaynaklara erişme

Her bir tür sağlayıcısı örneğini verilen bir `TypeProviderConfig` oluşturma sırasında değeri. Bu değer, "Çözüm klasörü" sağlayıcısı (diğer bir deyişle, proje klasörü derleme veya bir komut dosyasını içeren dizin), başvurulan derlemelerin listesini ve diğer bilgileri içerir.

### <a name="invalidation"></a>Geçersiz kılma

Sağlayıcıları bildirmek için geçersiz kılma sinyalleri yükseltmek F# dil hizmeti, şema varsayımların değişmiş olabilir. Geçersiz kılma meydana geldiğinde, sağlayıcı Visual Studio'da barındırılıyorsa bir typecheck alınabilir. Bu sinyal sağlayıcısı içinde barındırıldığında yoksayılacak F# etkileşimli veya F# derleyici (fsc.exe).

### <a name="caching-schema-information"></a>Şema bilgileri önbelleğe alma

Sağlayıcıları, genellikle erişim için şema bilgileri önbelleğe gerekir. Kullanıcı verileri veya statik bir parametre olarak verilen dosya adı kullanarak önbelleğe alınmış verilerin depolanması gerekir. Şema önbelleğe alma, bir örnek verilmiştir `LocalSchemaFile` tür sağlayıcıları parametresinde `FSharp.Data.TypeProviders` derleme. Uygulama bu sağlayıcıları, ağ üzerinden veri kaynağına erişim yerine yerel belirtilen dosyada şema bilgileri kullanmak için tür sağlayıcısını statik Bu parametre yönlendirir. Önbelleğe alınan şema bilgileri kullanmak için de statik parametresinin ayarlamalısınız `ForceUpdate` için `false`. Benzer bir teknik, çevrimiçi ve çevrimdışı veri erişimi etkinleştirmek için kullanabilirsiniz.

### <a name="backing-assembly"></a>Derleme yedekleme

Derleme yaparken bir `.dll` veya `.exe` dosyası, yedekleme .dll dosyası oluşturulan türleri statik olarak bağlanan elde edilen bütünleştirilmiş kod içine. Bu bağlantı, son derlemeye yedekleme derlemeye Ara dil (IL) tür tanımları ve yönetilen kaynaklar kopyalayarak oluşturulur. Kullanırken F# etkileşimli, yedekleme .dll dosyası kopyalanmıyor ve bunun yerine doğrudan yüklenen F# etkileşimli işlem.

### <a name="exceptions-and-diagnostics-from-type-providers"></a>Özel durumlar ve tür sağlayıcıları'ndan tanılama

Sağlanan türlerinden tüm üyeleri tüm kullanımları, özel durumlar. Bir tür sağlayıcısı bir özel durum oluşturursa tüm durumlarda, belirli bir tür sağlayıcısı için konak derleyici hata öznitelikleri.

- Tür sağlayıcısı özel durumlar, hiçbir zaman içinde iç derleyici hatalarının neden olur.

- Tür sağlayıcıları uyarıları bildiremezsiniz.

- Ne zaman bir tür sağlayıcısı barındırılan F# derleyici, bir F# geliştirme ortamını veya F# etkileşimli, tüm özel durumlar söz konusu sağlayıcısından yakalanır. İleti özelliği her zaman hata metnini ve yığın izlemesi yok görünür. Bir özel durum oluşturmak için kullanacaksanız, aşağıdaki örneklerde oluşturabilecek: `System.NotSupportedException`, `System.IO.IOException`, `System.Exception`.

#### <a name="providing-generated-types"></a>Oluşturulan türleri sağlama

Şu ana kadar bu belgede silinen türler sağlamak üzere nasıl açıklandığı. Tür sağlayıcısı mekanizma kullanabilirsiniz F# oluşturulan türler sağlamak üzere hangi kullanıcıların programı olarak gerçek .NET türü tanımları eklenir. Oluşturulan türleri bir tür tanımı kullanarak sağlanan başvurmanız gerekir.

```fsharp
open Microsoft.FSharp.TypeProviders

type Service = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">
```

Parçasıdır ProvidedTypes 0.2 yardımcı kod F# 3.0 sürümü yalnızca sınırlı oluşturulan türleri sağlamak için desteğe sahiptir. Aşağıdaki deyimleri için oluşturulan tür tanımı true olması gerekir:

- `isErased` ayarlanmalıdır `false`.

- Oluşturulan tür eklenmelidir için yeni oluşturulan `ProvidedAssembly()`, oluşturulan kod parçaları için bir kapsayıcıyı temsil eder.

- Sağlayıcının bir gerçek destekleyen .NET .dll dosyası ile eşleşen bir .dll dosyası diskte sahip derlemeye olmalıdır.

## <a name="rules-and-limitations"></a>Kurallar ve sınırlamalar

Tür sağlayıcıları yazdığınızda, aşağıdaki kurallar ve sınırlamalar göz önünde bulundurun.

### <a name="provided-types-must-be-reachable"></a>Sağlanan türler erişilebilir olmalıdır.

Tüm türler iç içe olmayan türlerinden erişilebilmeli sağlanır. İç içe türleri çağrısında verilen `TypeProviderForNamespaces` oluşturucu veya çağrı `AddNamespace`. Örneğin, bir tür sağlayıcısı sağlıyorsa `StaticClass.P : T`, T iç içe türü veya altında iç içe geçmiş bir tane olduğundan emin olmalısınız.

Örneğin, bazı sağlayıcılar gibi statik bir sınıf sahip `DataTypes` bunlar içeren `T1, T2, T3, ...` türleri. Aksi takdirde, derlemesi T türünde bir başvuru bulundu, ancak türü bu derlemede bulunamadı hatası diyor. Bu hata yeniden görüntülenirse, tüm alt türleri sağlayıcı türlerinden erişilebildiğini doğrulayın. Not: Bunlar `T1, T2, T3...` türleri denir *üzerinde halindeyken* türleri. Erişilebilir bir ad alanı veya üst türü koymayı unutmayın.

### <a name="limitations-of-the-type-provider-mechanism"></a>Tür sağlayıcısı mekanizması sınırlamaları

Tür sağlayıcısı mekanizmasında F# aşağıdaki sınırlamalara sahiptir:

- Tür sağlayıcıları için temel alınan altyapı F# genel türleri veya genel yöntemler sağlanan sağlanan desteklemiyor.

- Mekanizması statik parametreler ile iç içe geçmiş türlerini desteklemez.

## <a name="development-tips"></a>Geliştirme İpuçları

Aşağıdaki ipuçları yardımcı geliştirme sürecinde bulabilirsiniz:

### <a name="run-two-instances-of-visual-studio"></a>Visual Studio iki örneğini çalıştırma

Tür sağlayıcısını bir örneğinde geliştirip test IDE yeniden oluşturulan tür sağlayıcısını engelleyen bir .dll dosyası üzerinde bir kilit etkinleştirilir çünkü sağlayıcı diğer test edebilirsiniz. Bu nedenle, Visual Studio'nun ikinci örneğini ağdaki ilk örnek sağlayıcısı oluşturulur ve ardından sağlayıcısı oluşturulduktan sonra ikinci örneğini yeniden açmanız gerekir kapatmanız gerekir.

### <a name="debug-type-providers-by-using-invocations-of-fscexe"></a>Tür sağlayıcıları fsc.exe çağrıları kullanarak hata ayıklama

Tür sağlayıcıları aşağıdaki araçları kullanarak çağırabilirsiniz:

- fsc.exe ( F# komut satırı derleyicisi)

- fsi.exe ( F# etkileşimli derleyici)

- Devenv.exe (Visual Studio)

Tür sağlayıcıları test betiği (örneğin, script.fsx) üzerinde fsc.exe kullanarak, en kolay genellikle ayıklayabilirsiniz. Bir hata ayıklayıcı bir komut isteminden başlatabilirsiniz.

```
  devenv /debugexe fsc.exe script.fsx
```

  Yazdırma için stdout'u günlüğe kaydetme kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Sağlayıcıları](index.md)
- [Tür sağlayıcısını SDK'sı](https://github.com/fsprojects/FSharp.TypeProviders.SDK)
