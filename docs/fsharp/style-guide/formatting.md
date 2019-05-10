---
title: F#kod biçimlendirme yönergeleri
description: Biçimlendirme kuralları bilgi F# kod.
ms.date: 02/08/2019
ms.openlocfilehash: ce07bd800984ec082a522bc62cb487f786fa0510
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063598"
---
# <a name="f-code-formatting-guidelines"></a>F#kod biçimlendirme yönergeleri

Bu makalede kod biçimlendirme için yönergeler sunar. böylece, F# kodu:

* Genel olarak daha okunaklı görüntülenebilir
* Visual Studio Araçları ve diğer düzenleyiciler biçimlendirme tarafından uygulanan kuralları uygun olan
* Benzer şekilde diğer kod çevrimiçi

Bu kılavuzu temel alan [kapsamlı bir kılavuz F# biçimlendirme kuralları](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) tarafından [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Girinti için genel kurallar

F#önemli boşluk, varsayılan olarak kullanır. Aşağıdaki yönergeleri Bu getirebilir bazı zorluklar juggle nasıl dair yönergeler sağlamak üzere tasarlanmıştır.

### <a name="using-spaces"></a>Alanları kullanma

Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir. En az bir alan gereklidir. Kuruluşunuz için Girintileme kullanmak için boşluk sayısını belirtmek için kodlama standartları oluşturabilirsiniz. girinti girinti oluştuğu her düzeyde iki, üç veya dört boşluk tipiktir.

**Girinti başına 4 alan öneririz.**

Bu, programların girinti öznel bir konudur belirtti. Değişimleri Tamam, ancak izlemeniz gereken ilk kural *girinti tutarlılığını*. Genel olarak kabul edilen bir girinti stilini seçin ve kod temelinizde sistematik olarak kullanın.

## <a name="formatting-white-space"></a>Boşluk biçimlendirme

F#boşluk büyük/küçük harfe duyarlıdır. Çoğu semantiğe boşluk tarafından uygun girintisini ele alınmaktadır ancak dikkate alınması gereken bazı hususlar vardır.

### <a name="formatting-operators-in-arithmetic-expressions"></a>Biçimlendirme işleçleri aritmetik ifadelerde

Her zaman ikili aritmetik ifadeler beyaz boşluk kullanın:

```fsharp
let subtractThenAdd x = x - 1 + 3
```

Birli `-` işleçleri negating değeri her zaman olmalıdır hemen izleyin:

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

Sonra bir boşluk karakteri ekleme `-` işleci diğerleri için Kafa karışıklığına neden olabilir.

Özet olarak, her zaman önemlidir:

* İkili işleçler boşluk ile çevreleyen
* Hiçbir zaman bir birli işleç sonra boşluk sahip

İkili aritmetik işleç kılavuz özellikle önemlidir. Bir ikili kapsamak başarısız olan `-` bazı biçimlendirme seçeneklerini ile birleştirildiğinde işleci, bir tekil yorumlanması için açabilir `-`.

### <a name="surround-a-custom-operator-definition-with-white-space"></a>Boşluk içeren bir özel işleç tanımını çevreleyen

Her zaman bir işleç tanımını kapsamak için boşluk kullanın:

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

İle başlayan herhangi bir özel işleç için `*` ve birden fazla karakter olan, derleyici belirsizlik önlemek için tanım başlangıcına bir beyaz alanı eklemeniz gerekir. Bu nedenle, yalnızca tek bir boşluk karakteri ile tüm işleçleri tanımlarını çevreleyen öneririz.

### <a name="surround-function-parameter-arrows-with-white-space"></a>İşlev parametresi oklar boşluk ile çevreleyen

Bir işlev imzası tanımlarken, beyaz boşluk kullanmak `->` sembol:

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a>İşlev bağımsız değişkenleri boşluk ile çevreleyen

Bir işlev tanımlarken, her bağımsız değişken beyaz boşluk kullanın.

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="type-annotations"></a>Tür ek açıklamaları

#### <a name="right-pad-function-argument-type-annotations"></a>Sağ paneli işlevi bağımsız değişkeni tür ek açıklamaları

Tür ek açıklamaları değişkenleriyle tanımlarken, sonra boşluk kullanmak `:` sembol:

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a>Surround dönüş türü ek açıklamaları boşluk ile

Bir let bağlı işlev veya değer türü ek açıklaması içinde (dönüş türü bir işlev söz konusu olduğunda), önce ve sonra boşluk kullanmak `:` sembol:

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a>Boş satırlar biçimlendirme

* Ayrı en üst düzey işlev ve sınıf tanımları iki boş satırlar.
* Yöntemi tanımları bir sınıf içinde tek bir boş satır tarafından ayrılır.
* Ek boş satırlar (gerektiğinde) ilgili işlev gruplarını birbirinden ayırmak için kullanılabilir. Boş satırlar bir sürü ilgili one-liners (örneğin, sahte uygulamaları kümesi) arasında atlanabilir.
* Boş satırlar işlevleri'nde gerektiğinde, mantıksal bölümler belirtmek için kullanın.

## <a name="formatting-comments"></a>Açıklamalar Biçimlendirme

Genellikle birden çok çift eğik çizgi açıklamalarını derinlikli ML stil bloğu açıklamaları tercih eder.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Satır içi açıklamalara ilk harfini büyük harfe.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Adlandırma kuralları

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>CamelCase sınıfı bağlı, ifade bağlı ve bağlama deseni değerleri ve işlevleri için kullanın.

Sık karşılaşılan ve kabul edilen F# tüm adları desen veya yerel değişkenler olarak bağlı ve işlev tanımları camelCase stili.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Yerel olarak bağlı işlevler sınıflardaki camelCase de kullanmalısınız.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Genel modül bağlı işlevler için camelCase kullanın

Bir modül bağlı işlev genel API parçası olduğunda, camelCase kullanmanız gerekir:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>İç ve özel modül bağlı değerleri ve işlevleri için camelCase kullanın

CamelCase aşağıdakiler dahil olmak üzere özel modül bağlı değerleri için kullanın:

* Komut geçici işlevleri

* Değerleri modülü veya türü iç uygulama yapma

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>CamelCase parametrelerini kullanın.

Tüm parametreler camelCase .NET adlandırma kurallarına uygun olarak kullanmanız gerekir.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Modüller için PascalCase kullan

(Üst düzey, iç, özel, iç içe geçmiş) tüm modülleri PascalCase kullanmanız gerekir.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Tür bildirimleri, üyeleri ve etiketler için PascalCase kullanın

Sınıfları, arabirimleri, yapılar, numaralandırmalar, temsilciler, kayıtlar ve ayrılmış birleşimler tüm PascalCase ile adlandırılmalıdır. Üye türleri ve kayıtları ve ayrılmış birleşimler için etiketleri içinde PascalCase de kullanmalısınız.

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>.NET için iç yapılar için PascalCase kullanın

Ad alanları, özel durumlar, olayları ve proje /`.dll` adları PascalCase de kullanmalıdır. Yalnızca bu diğer .NET dilleri tüketicilere daha doğal tüketime yapar, ayrıca karşılaşma olasılığı yüksek olan .NET adlandırma kuralları ile tutarlı olur.

### <a name="avoid-underscores-in-names"></a>Adları alt çizgi kaçının

Tarihsel olarak, bazı F# kitaplıkları adları alt çizgi kullanılan. Kısmen, .NET adlandırma kuralları ile çakışıyor çünkü ancak bu artık yaygın olarak, kabul edilir. Bununla birlikte, bazı F# programcılar kullanın alt çizgi yoğun, kısmen geçmiş nedenlerle ve dayanıklılık ve saygı önemlidir. Ancak, bir seçeneğiniz mi kullanılacağını hakkında başkaları tarafından stili genellikle yanıtlamadığı unutmayın.

Bazı özel durumlar, alt çizgi yaygın olduğu yerel bileşenleriyle birlikte içerir.

### <a name="use-standard-f-operators"></a>Kullanım standart F# işleçleri

Aşağıdaki işleçleri tanımlanan F# standart kitaplığı ve tanımlama eşdeğerleri yerine kullanılmalıdır. Bu kod daha okunabilir ve kullanılan deyimsel bir hale gelir gibi bu işleçleri kullanarak önerilir. Arka plan OCaml veya işlev başka bir programlama dilinde geliştiricilere, farklı deyimleri için alışkın olabilir. Aşağıdaki liste önerilen özetler F# işleçleri.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Genel türler için öneki sözdizimini kullanın (`Foo<T>`) sonek söz dizimi yerine (`T Foo`)

F#genel türler adlandırma iki sonek ML stili devralır (örneğin, `int list`) öneki .NET stili yanı sıra (örneğin, `list<int>`). .NET stili dört belirli tür dışında tercih et:

1. İçin F# listeleri, sonek biçimi kullanın: `int list` yerine `list<int>`.
2. İçin F# seçenekleri, sonek biçimi kullanın: `int option` yerine `option<int>`.
3. İçin F# diziler, söz dizimi adı kullanın `int[]` yerine `int array` veya `array<int>`.
4. Başvuru hücreleri için kullanmak `int ref` yerine `ref<int>` veya `Ref<int>`.

Önek biçimi diğer tüm türleri için kullanın.

## <a name="formatting-tuples"></a>Diziler biçimlendirme

Parantez içine alınmış bir tanımlama grubu örneklemesine olmalıdır ve sınırlandırma virgül içinde tek bir boşluk, örneğin gelmelidir: `(1, 2)`, `(x, y, z)`.

Parantez içinde tanımlama desen eşleştirme atlamak için yaygın olarak kabul edilir:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

Tanımlama grubu işlevinin dönüş değerini ise parantez atlamak için yaygın olarak kabul edilir:

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

Özet olarak, parantez içine alınmış demet örneklemeleri tercih eder, ancak tanımlama grubu desen eşleştirme veya bir dönüş değeri için kullanılırken, parantez önlemek ince değerlendirilir.

## <a name="formatting-discriminated-union-declarations"></a>Ayırt edici birleşim bildirimleri biçimlendirme

Girinti `|` 4 boşluklarla tür tanımı:

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

## <a name="formatting-discriminated-unions"></a>Ayrılmış birleşimler biçimlendirme

Örneklenen ayrılmış birden çok satırda ayrılmış birleşimler, girinti ile yeni bir kapsam içerdiği veri vermeniz gerekir:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Kapatma parantezinden ayrıca yeni bir satıra olabilir:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Biçimlendirme kayıt bildirimi

Girinti `{` türü tanımı tarafından 4 alanları ve alan listesinde aynı satırda başlatın:

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

Yeni bir satır ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek arabirim uygulamaları veya üyeleri kaydında bildiriyorsanız tercih edilir:

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a>Kayıtları biçimlendirme

Kısa kayıtları tek satırda yazılabilir:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Uzun kayıtları yeni satırlar için etiketleri kullanmanız gerekir:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Açılış yerleştirme belirteci yeni bir satıra içerikleri üzerinde bir kapsam sekmeli ve yeni bir satıra kapatma belirteci kullanıyorsanız tercih edilir:

* Kod girintileme farklı kapsamlarla kayıtları dolaşma
* Bir işleve öğesine ekleyerek sorgularınızı

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

Bu kuralların listesi ve dizi öğeleri için geçerlidir.

## <a name="formatting-copy-and-update-record-expressions"></a>Kopyalama ve güncelleştirme kayıt ifadeleri biçimlendirme

Benzer yönergeleri uygulamak için bir kayıt kopyalama ve güncelleştirme hala bir kayıt ifadesidir.

Kısa ifade tek bir satırda uygun:

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

Daha uzun ifadeleri, yeni satırları kullanmanız gerekir:

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Ve olarak kayıt yönergeleriyle, için küme ayraçlarını ayrı satırlara atayın ve bir kapsam ifadesiyle sağ girinti isteyebilirsiniz. Parantez olmadan isteğe bağlı bir değerle kaydırma gibi bazı özel durumlarda, tek bir satırda bir küme ayracı tutmanız gerekebileceğini unutmayın:

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

## <a name="formatting-lists-and-arrays"></a>Biçimlendirme listeler ve diziler

Yazma `x :: l` etrafındaki boşlukları ile `::` işleci (`::` dolayısıyla boşluklarla çevrili bir içtakı işleci).

Liste ve tek bir satıra bildirilen diziler boşlukla ayraç sonra ve kapatma köşeli ayraç önce sahip olmalıdır:

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

Her zaman en az bir alanı arasında iki farklı küme ayracı gibi işleçler kullanın. Örneğin, arasına boşluk bırakın bir `[` ve `{`.

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

Aynı kılavuz listeler veya diziler dizileri için geçerlidir.

Kayıtlar gibi listeler ve birden çok satırda bölme diziler benzer bir kural uygulayın:

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

Ve kayıtlarla olduğu gibi açılış ve kapanış köşeli ayraçlar kendi satırında bildirme taşıma kodda gezinmeye ve İşlevler halinde yöneltme kolaylaştıracaktır.

## <a name="formatting-if-expressions"></a>Biçimlendirme IF ifadeleri

Koşullular girintilerini bunları oluşturan ifadeler boyutlarını bağlıdır. Varsa `cond`, `e1` ve `e2` kısa ve basit bunları bir satıra yazın:

```fsharp
if cond then e1 else e2
```

Ya da `cond`, `e1` veya `e2` uzun, ancak çok satırlı değil:

```fsharp
if cond
then e1
else e2
```

Herhangi bir ifadenin çok satırlı varsa:

```fsharp
if cond then
    e1
else
    e2
```

İle birden çok koşullular `elif` ve `else` aynı kapsamda girintili `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Desen eşleştirme yapıları

Kullanım bir `|` her bir match yan tümcesinin hiçbir girintilemeli. Kısa ifade ise, her alt ifade de basit ise tek bir satırı kullanarak düşünebilirsiniz.

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

İfade sağ tarafındaki oka desen çok büyük ise, taşıyabilir girintili bir adımdan aşağıdaki satırı `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Desen tarafından başlangıç anonim işlev eşleme `function`, genellikle çok Girintile değil. Örneğin, bir kapsam şu şekilde girintileme uygundur:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Desen tarafından tanımlanan İşlevler, `let` veya `let rec` girintili 4 boşluk, başlattıktan sonra olmalıdır `let`bile `function` anahtar sözcüğü kullanılır:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Oklar hizalama önermiyoruz.

## <a name="formatting-trywith-expressions"></a>Biçimlendirme bir try / ifadelerle

Özel durum türüne göre desen girintili aynı düzeyde `with`.

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

## <a name="formatting-function-parameter-application"></a>İşlev parametresi uygulama biçimlendirme

Genel olarak, çoğu işlev parametre uygulama aynı çizgi üzerinde gerçekleştirilir.

Yeni bir satıra bir işlev parametreleri uygulamak istiyorsanız, bunları bir kapsama göre Girintile.

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

Aynı yönergeleri işlevi bağımsız değişken olarak lambda ifadeleri için geçerlidir. Bir lambda ifadesinin gövdesi gövdesi başka bir satır varsa bir kapsamla girintili

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

Ancak, bir lambda ifadesinin gövdesinin birden fazla satır varsa bunu ayrı bir işleve hesaba katarak göz önünde bulundurun yerine tek bir bağımsız değişken bir işleve uygulanmış bir çok satırlı yapısı vardır.

### <a name="formatting-infix-operators"></a>Biçimlendirme içtakı işleçleri

Boşluklarla ayrı işleçler. Bu kuralın istisnaları belirgin `!` ve `.` işleçleri.

İçtakı ifadeler aynı sütunda eklemedir Tamam şunlardır:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Ardışık Düzen operatörleri biçimlendirme

İşlem hattı `|>` işleçleri, bunlar çalışır ifadeleri altında gitmesini.

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

### <a name="formatting-modules"></a>Modüller biçimlendirme

Yerel bir modülde kod göreli modül girintili gerekir, ancak üst düzey bir modülde kod girintili. Namespace öğelerini girintili gerekmez.

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

### <a name="formatting-object-expressions-and-interfaces"></a>Nesne ifadeleri ve arabirimler biçimlendirme

Nesne ifadeleri ve arabirimler hizalanmayacak ile aynı şekilde `member` sonra 4 alan girintili.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Boşluk ifadelerde biçimlendirme

Gereksiz boşluk önlemek F# ifadeler.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Adlandırılmış bağımsız değişkenler de olmamalıdır boşluk çevresindeki `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a>Biçimlendirme öznitelikleri

[Öznitelikleri](../language-reference/attributes.md) bir yapısı yerleştirilir:

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

### <a name="formatting-attributes-on-parameters"></a>Parametreleri biçimlendirme öznitelikleri

Öznitelikleri parametreleri yerde de olabilir. Bu durumda, aynı satırda parametre adından önce ve sonra yerleştirin:

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a>Birden çok öznitelik biçimlendirme

Bir parametre değil bir yapı için birden çok öznitelik uygulandığında, bunlar yok her satıra bir öznitelik olduğunu yerleştirilmelidir:

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

Bir parametre uygulandığında, bunlar aynı satırda olmalıdır ve ayrılmış bir `;` ayırıcı.

## <a name="formatting-literals"></a>Biçimlendirme değişmez değerleri

[F#değişmez değerler](../language-reference/literals.md) kullanarak `Literal` özniteliği öznitelik kendi satırına yerleştirin ve camelCase adlandırma kullanın:

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

Öznitelik değeri ile aynı satırda yerleştirmekten kaçının.
