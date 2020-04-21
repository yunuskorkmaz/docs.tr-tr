---
title: F# kod biçimlendirme yönergeleri
description: F# kodunu biçimlendirme yönergelerini öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: b8be70dd29a04e71614308164e541b99a1724305
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739560"
---
# <a name="f-code-formatting-guidelines"></a>F# kod biçimlendirme yönergeleri

Bu makalede, F# kodunuzu şu şekilde biçimlendirecek şekilde kodunuzu biçimlendirecek yönergeler sunulmaktadır:

* Daha okunaklı
* Visual Studio ve diğer editörlerde biçimlendirme araçları ile uygulanan kurallara uygun olarak
* Çevrimiçi diğer kodlara benzer

Bu yönergeler, [Anh-Dung Phan'ın](https://github.com/dungpa) [F# Biçimlendirme Sözleşmeleri için kapsamlı bir kılavuza](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) dayanmaktadır.

## <a name="general-rules-for-indentation"></a>Girintinasyon için genel kurallar

F# varsayılan olarak önemli beyaz boşluk kullanır. Aşağıdaki yönergeler, bunun dayatabileceği bazı zorlukların nasıl ele aldayılabildiği konusunda rehberlik sağlamak için tasarlanmıştır.

### <a name="using-spaces"></a>Boşlukları kullanma

Girintisi gerektiğinde, sekmeleri değil boşlukları kullanmanız gerekir. En az bir boşluk gereklidir. Kuruluşunuz girintisi için kullanılacak alan sayısını belirtmek için kodlama standartları oluşturabilir; girintinin oluştuğu her düzeyde iki, üç veya dört girintin boşluk tipiktir.

**Girintinasyon başına dört boşluk öneririz.**

Bununla ilgili olarak, programların girintisi öznel bir konudur. Varyasyonlar tamam, ancak izlemeniz gereken ilk kural *girintinin tutarlılığıdır.* Genel olarak kabul görmüş bir girintin stili seçin ve kod tabanınız boyunca sistematik olarak kullanın.

## <a name="formatting-white-space"></a>Beyaz alanı biçimlendirme

F# beyaz alana duyarlıdır. Beyaz uzaydan en semantik uygun girinti ile kaplı olmasına rağmen, göz önünde bulundurulması gereken bazı diğer şeyler vardır.

### <a name="formatting-operators-in-arithmetic-expressions"></a>İşleçleri aritmetik ifadelerde biçimlendirme

Her zaman ikili aritmetik ifadeler etrafında beyaz boşluk kullanın:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Unary `-` işleçleri her zaman olumsuzladıkları değer tarafından hemen takip edilmelidir:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Işleci sonra `-` bir beyaz boşluk karakteri ekleme diğerleri için karışıklığa yol açabilir.

Özetle, her zaman önemlidir:

* İkili operatörleri beyaz alana surround
* Bir unary işlecinden sonra asla beyaz boşluk yok

İkili aritmetik işleç kılavuzu özellikle önemlidir. Belirli biçimlendirme `-` seçenekleriyle birleştirildiğinde, bir ikili işlecinin çevrelenmemesi, `-`onu unary olarak yorumlamaya neden olabilir.

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Özel bir operatör tanımını beyaz alanla çevrele

Operatör tanımını çevreleyen beyaz alanı her zaman kullanın:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

Birden fazla karakterle `*` başlayan ve birden fazla karaktere sahip olan herhangi bir özel işleç için, derleyici belirsizliğini önlemek için tanımın başına beyaz bir boşluk eklemeniz gerekir. Bu nedenle, tüm operatörlerin tanımlarını tek bir beyaz boşluk karakteriyle çevrelemenizi öneririz.

### <a name="surround-function-parameter-arrows-with-white-space"></a>Surround fonksiyon parametre okları ile beyaz boşluk

Bir işlevin imzasını tanımlarken, sembolün `->` etrafındaki beyaz boşluk kullanın:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>Beyaz boşluklu surround işlev bağımsız değişkenleri

Bir işlev tanımlarken, her bağımsız değişkenin etrafında beyaz boşluk kullanın.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a>Uzun üye tanımları için parametreleri yeni bir satıra yerleştirin

Çok uzun bir üye tanımınız varsa, parametreleri yeni satırlara yerleştirin ve bunları bir kapsam girin.

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

Bu, yapıcılar için de geçerlidir:

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a>Ek açıklamalar yazın

#### <a name="right-pad-function-argument-type-annotations"></a>Sağ pad işlev bağımsız değişken türü ek açıklamaları

Tür ek açıklamaları ile bağımsız değişkenleri tanımlarken, simgeden `:` sonra beyaz boşluk kullanın:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Beyaz boşluklu surround dönüş türü ek açıklamaları

Let-bound işleviveya değer türü ek açıklama (bir işlev durumunda dönüş türü), `:` önce ve sonra sembol beyaz boşluk kullanın:

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Boş satırları biçimlendirme

* Üst düzey işlevi ve sınıf tanımlarını iki boş satırla ayırın.
* Bir sınıf içindeki yöntem tanımları tek bir boş satırla ayrılır.
* İlgili işlev gruplarını ayırmak için ekstra boş satırlar (seyrek) kullanılabilir. Boş satırlar, bir grup ilgili tek gömlekli (örneğin, bir dizi kukla uygulama) arasında atlanabilir.
* Mantıksal bölümleri belirtmek için işlevlerde boş çizgiler kullanın.

## <a name="formatting-comments"></a>Açıklamaları biçimlendirme

Genellikle ML tarzı blok yorumlar üzerinde birden fazla çift eğik çizgi yorum tercih edin.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Satır satırlı yorumlar ilk harfi büyük harfle yazmalıdır.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Adlandırma kuralları

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Sınıfa bağlı, ifadeye bağlı ve desene bağlı değerler ve işlevler için camelCase'i kullanın

Yerel değişkenler olarak bağlanan tüm adlar için veya desen eşleşmeleri ve işlev tanımlarında camelCase kullanmak yaygın ve kabul edilen F# stilidir.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Sınıflarda yerel olarak bağlanan fonksiyonlar da camelCase kullanmalıdır.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Modüle bağlı ortak işlevler için camelCase'i kullanın

Modüle bağlı bir işlev genel API'nin bir parçasıysa, camelCase'i kullanmalıdır:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Dahili ve özel modüle bağlı değerler ve fonksiyonlar için camelCase'i kullanın

Aşağıdakiler de dahil olmak üzere özel modüle bağlı değerler için camelCase'i kullanın:

* Komut dosyalarındaki geçici işlevler

* Bir modülün veya türün iç uygulamasını oluşturan değerler

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Parametreler için camelCase'i kullanın

Tüm parametreler .NET adlandırma kurallarına uygun olarak camelCase kullanmalıdır.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Modüller için PascalCase'i kullanma

Tüm modüller (üst düzey, iç, özel, iç içe) PascalCase kullanmalıdır.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Tür bildirimleri, üyeler ve etiketler için PascalCase'i kullanın

Sınıflar, arabirimler, structs, sayısallaştırmalar, temsilciler, kayıtlar ve ayrımcı sendikalar tüm PascalCase ile adlandırılmalıdır. Kayıtlar ve ayrımcı sendikalar için tür ve etiketler deki üyeler de PascalCase kullanmalıdır.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>.NET'e özgü yapılar için PascalCase'i kullanın

Ad alanları, özel durumlar, olaylar`.dll` ve proje/ adlar da PascalCase kullanmalıdır. Bu, diğer .NET dillerinden gelen tüketimi tüketiciler için daha doğal hale getirmekle kalmıyor, aynı zamanda karşılaşma olasılığınız olan .NET adlandırma kurallarıyla da tutarlıdır.

### <a name="avoid-underscores-in-names"></a>Adlarda alt çizerlerden kaçının

Tarihsel olarak, bazı F# kitaplıkları adlarda alt çizerler kullanabilmiştir. Ancak, kısmen .NET adlandırma kurallarıyla çakıştığı için bu artık yaygın olarak kabul edilmez. Bununla ilgili olarak, bazı F# programcıları kısmen tarihsel nedenlerden dolayı vurguları yoğun bir şekilde kullanırlar ve hoşgörü ve saygı önemlidir. Ancak, stilgenellikle kullanmak için bir seçim var başkaları tarafından sevilmeyen olduğunu unutmayın.

Bir özel durum, alt çizlerin yaygın olduğu yerel bileşenlerle birlikte çalışmayı içerir.

### <a name="use-standard-f-operators"></a>Standart F# işleçlerini kullanma

Aşağıdaki işleçler F# standart kitaplığında tanımlanır ve eşdeğerleri tanımlamak yerine kullanılmalıdır. Kodu daha okunabilir ve deyimsel hale getirme eğiliminde olduğundan, bu işleçlerin kullanılması önerilir. OCaml veya diğer işlevsel programlama dilinde bir arka plan geliştiriciler farklı deyimler alışkın olabilir. Aşağıdaki liste önerilen F# işleçlerini özetler.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Genel ek sözdizimi (`Foo<T>`) için önek sözdizimini (`T Foo`)

F# hem genel adlandırma nın ML postfix stilini `int list`(örneğin,) hem de .NET stilini (örneğin) `list<int>`devralır. Beş özel tür dışında .NET stilini tercih edin:

1. F# Listeleri için, postfix `int list` formunu `list<int>`kullanın: yerine .
2. F# Seçenekleri için, postfix `int option` formunu `option<int>`kullanın: yerine .
3. F# Değer Seçenekleri için, postfix `int voption` formunu `voption<int>`kullanın: yerine .
4. F# dizileri için, sintaktik adı `int[]` kullanmak yerine `int array` veya `array<int>`.
5. Referans Hücreler için, `ref<int>` yerine `Ref<int>`kullanın `int ref` veya .

Diğer tüm türler için önek formunu kullanın.

## <a name="formatting-tuples"></a>Biçimlendirme tuples

Bir tuple instantiation parantez ve içinde delimiting virgül tek bir boşluk tarafından takip `(1, 2)`edilmelidir, örneğin: , `(x, y, z)`.

Tuples desen eşleşen parantez atlamak için yaygın olarak kabul edilir:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Tuple bir fonksiyonun geri dönüş değeri ise, parantez ibareleri atlamak da yaygın olarak kabul edilir:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

Özetle, parantez anlık değerlerini tercih edin, ancak desen eşleştirmesi veya geri dönüş değeri için tuples kullanırken, parantezlerden kaçınmak iyi olarak kabul edilir.

## <a name="formatting-discriminated-union-declarations"></a>Ayrımcı birlik bildirimlerini biçimlendirme

Dört boşluk `|` la tür tanımıgirini:

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>Ayrımcı sendikaları biçimlendirme

Birden çok satıra bölünmüş anında Ayrılmış Ayırmalı Sendikalar, içerdiği verileri girintisi içeren yeni bir kapsam vermelidir:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Kapanış parantezi de yeni bir satırda olabilir:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Kayıt bildirimlerini biçimlendirme

Dört boşluk `{` tarafından tür tanımı girintisi ve aynı satırda alan listesini başlatın:

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

Açıkara belirteci yeni bir satıra, kapanış jetonunu da yeni bir satıra yerleştirme, arabirim uygulamalarını veya üyeleri kayda dahil ediyorsanız tercih edilir:

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Kayıtları biçimlendirme

Kısa kayıtlar tek satırda yazılabilir:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Daha uzun olan kayıtlar etiketler için yeni satırlar kullanmalıdır:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Açılış belirteci yeni bir satıra yerleştirilme, içeriği tek bir kapsam üzerinde sekmeli ve yeni bir satırdaki kapanış belirteci aşağıdakiler varsa tercih edilir:

* Kayıtları farklı girinti kapsamları ile kod içinde taşıma
* Onları bir fonksiyona dönüştürme

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

Liste ve dizi öğeleri için de aynı kurallar geçerlidir.

## <a name="formatting-copy-and-update-record-expressions"></a>Kayıt ifadelerini biçimlendirme

Kopyala ve güncelleştir kayıt ifadesi hala bir kayıttır, bu nedenle benzer yönergeler geçerlidir.

Kısa ifadeler tek bir satıra sığabilir:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Daha uzun ifadeler yeni satırlar kullanmalıdır:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Ve kayıt kılavuzunda olduğu gibi, ayraçlar için ayrı satırlar ayırmak isteyebilirsiniz ve girinti bir kapsam ifade ile sağa. Bazı özel durumlarda, örneğin bir değeri parantez olmadan isteğe bağlı olarak sarmalamak gibi, bir ayraç'ı tek bir satırda tutmanız gerekebilir:

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a>Listeleri ve dizileri biçimlendirme

Işlecinin `x :: l` `::` etrafındaki boşluklarla yazın (bir`::` infix işlecidir, dolayısıyla boşluklarla çevrilidir).

Tek bir satırda bildirilen liste ve dizilerin açılış ayracından sonra ve kapanış ayracından önce bir boşluk olması gerekir:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Her zaman iki farklı ayraç benzeri işleçler arasında en az bir boşluk kullanın. Örneğin, bir ve bir `[` `{`arasında bir boşluk bırakın.

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

Aynı kılavuz listeler veya tuples dizileri için de geçerlidir.

Birden çok satıra bölünmüş listeler ve diziler, kayıtlar gibi benzer bir kural izler:

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

Ve kayıtlarda olduğu gibi, açma ve kapama parantezini kendi satırlarında bildirmek kodu niçin hareket ettireceğini ve işlevlerin içine girmesini kolaylaştırır.

Diziler oluştururken ve programlı listelerken, bir değer her zaman oluşturulduğunda `->` tercih `do ... yield` edin:

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

F# dilinin eski sürümlerinde, verilerin koşullu olarak oluşturulabileceği veya değerlendirilecek ardışık ifadeler olabileceği durumlarda belirtilmesi `yield` gerekir. Eski bir F# dili sürümüyle derlemeniz gerekiyorsa, bu `yield` anahtar kelimeleri atlayış etmeyi tercih edin:

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

Bazı durumlarda, `do...yield` okunabilirlik yardımcı olabilir. Bu olgular, öznel de olsa, dikkate alınmalıdır.

## <a name="formatting-if-expressions"></a>İfadeler varsa biçimlendirme

Koşullu ların girintisi, onları oluşturan ifadelerin boyutlarına bağlıdır. Eğer `cond` `e1` , `e2` ve kısa, sadece bir satırda bunları yazın:

```fsharp
if cond then e1 else e2
```

Ya `cond`, `e1` `e2` veya uzun, ancak çok satırlı değil:

```fsharp
if cond
then e1
else e2
```

İfadelerden herhangi biri çok satırlıysa:

```fsharp
if cond then
    e1
else
    e2
```

Birden fazla koşullu ile `elif` ve `else` aynı kapsamda `if`girintisi:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Desen eşleştirme yapıları

Girintisi olmayan bir eşleşmenin her yan tümcesi için a `|` kullanın. İfade kısaysa, her alt ifade de basitse tek bir satır kullanmayı düşünebilirsiniz.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Desen eşleşen okun sağındaki ifade çok büyükse, aşağıdaki satıra taşıyın, girindi bir adım . `match` / `|`

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Anonim işlevlerin desen eşleştirme, başlayarak `function`, genellikle çok fazla girintisi olmamalıdır. Örneğin, bir kapsamı aşağıdaki gibi girintisi gayet iyi:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Anahtar `let` kelime kullanılsa `let rec` `let` `function` bile, başladıktan sonra dört boşluk tarafından tanımlanan veya girintisi olması gereken işlevlerde desen eşleştirme:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Okları hizalamanızı önermiyoruz.

## <a name="formatting-trywith-expressions"></a>Try/with ifadelerini biçimlendirme

Özel durum türünde desen eşlemesi `with`.

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>Biçimlendirme fonksiyonu parametre uygulaması

Genel olarak, çoğu işlev parametre uygulaması aynı satırda yapılır.

Parametreleri yeni bir satırdaki bir işleve uygulamak istiyorsanız, bunları tek bir kapsamla girin.

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

Aynı kurallar işlev bağımsız değişkenleri olarak lambda ifadeler için geçerlidir. Bir lambda ifadesinin gövdesi ise, vücut başka bir çizgi olabilir, bir kapsam tarafından girintisi

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

Ancak, bir lambda ifadesinin gövdesi birden fazla satırsa, bir işleve tek bir bağımsız değişken olarak uygulanan çok satırlı bir yapı yerine onu ayrı bir işleve ayırmayı düşünün.

### <a name="formatting-infix-operators"></a>Ekiş işleçlerini biçimlendirme

Boşluklara göre ayrı işleçler. Bu kuralın bariz `!` istisnaları `.` ve işleçleridir.

Ekek ifadeleri aynı sütunda sıraya tamam:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Boru hattı operatörlerini biçimlendirme

Boru `|>` hattı operatörleri üzerinde çalıştıkları ifadelerin altına girmelidir.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>Modülleri biçimlendirme

Yerel bir modüldeki kod modüle göre girintisi olmalıdır, ancak üst düzey bir modüldeki kod girintinolmamalıdır. Ad alanı öğeleri girintisi gerekmez.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Nesne ifadelerini ve arabirimlerini biçimlendirme

Nesne ifadeleri ve arabirimleri dört boşluktan sonra `member` girintilen ile aynı şekilde hizalanmalıdır.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>İfadelerde beyaz alanı biçimlendirme

F# ifadelerinde gereksiz beyaz boşluktan kaçının.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Adlandırılmış bağımsız değişkenler de `=`çevreleyen boşluk olmamalıdır:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Öznitelikleri biçimlendirme

[Öznitelikler](../language-reference/attributes.md) bir yapının üzerine yerleştirilir:

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a>Parametrelere öznitelikleri biçimlendirme

Öznitelikler de parametreler üzerinde yer olabilir. Bu durumda, parametre ile aynı satıra ve addan önce yerleştirin:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Birden çok özniteliği biçimlendirme

Parametre olmayan bir yapıya birden çok öznitelik uygulandığında, satır başına bir öznitelik olacak şekilde yerleştirilmelidir:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Bir parametreye uygulandığında, aynı satırda olmalı ve `;` ayırıcı ile ayrılmış olmalıdır.

## <a name="formatting-literals"></a>Gerçek anlamları biçimlendirme

Özniteliği kullanan `Literal` [F# literals](../language-reference/literals.md) özniteliği kendi satırına yerleştirmeli ve PascalCase adlandırmasını kullanmalıdır:

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

Özniteliği değerle aynı satıra yerleştirmekten kaçının.
