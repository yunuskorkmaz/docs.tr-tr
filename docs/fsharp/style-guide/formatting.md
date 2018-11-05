---
title: Biçimlendirme yönergelerine F# kodu
description: F# kod biçimlendirme yönergeleri hakkında bilgi edinin.
ms.date: 05/14/2018
ms.openlocfilehash: 0d7d2d1771710db55bf990f3a06079b2aec48fd7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858011"
---
# <a name="f-code-formatting-guidelines"></a>Biçimlendirme yönergelerine F# kodu

Bu makalede, F# kodu böylece, kodunuzu biçimlendirme için yönergeler sunar:

* Genel olarak daha okunaklı görüntülenebilir
* Visual Studio Araçları ve diğer düzenleyiciler biçimlendirme tarafından uygulanan kuralları uygun olan
* Benzer şekilde diğer kod çevrimiçi

Bu kılavuzu temel alan [F# biçimlendirme kuralları kapsamlı bir kılavuz](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) tarafından [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Girinti için genel kurallar

F# önemli boşluk varsayılan olarak kullanır. Aşağıdaki yönergeleri Bu getirebilir bazı zorluklar juggle nasıl dair yönergeler sağlamak üzere tasarlanmıştır.

### <a name="using-spaces"></a>Alanları kullanma

Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir. En az bir alan gereklidir. Kuruluşunuz için Girintileme kullanmak için boşluk sayısını belirtmek için kodlama standartları oluşturabilirsiniz. girinti girinti oluştuğu her düzeyde iki, üç veya dört boşluk tipiktir.

**Girinti başına 4 alan öneririz.**

Bu, programların girinti öznel bir konudur belirtti. Değişimleri Tamam, ancak izlemeniz gereken ilk kural *girinti tutarlılığını*. Genel olarak kabul edilen bir girinti stilini seçin ve kod temelinizde sistematik olarak kullanın.

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

Genel ve yerel değişkenler olarak veya desen ve işlev tanımları camelCase tüm adlar için kabul edilen F# stili bağlanır.

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

Tarihsel olarak, bazı F# kitaplıkları adları alt çizgi kullandınız. Kısmen, .NET adlandırma kuralları ile çakışıyor çünkü ancak bu artık yaygın olarak, kabul edilir. Bu, bazı F# programcıları alt çizgi yoğun, kısmen geçmiş nedenlerle kullanın ve dayanıklılık ve saygı önemlidir da belirtti. Ancak, bir seçeneğiniz mi kullanılacağını hakkında başkaları tarafından stili genellikle yanıtlamadığı unutmayın.

Bazı özel durumlar, alt çizgi yaygın olduğu yerel bileşenleriyle birlikte içerir.

### <a name="use-standard-f-operators"></a>Standart F# işleçleri kullanma

Aşağıdaki işleçleri, F# standart kitaplıkta tanımlanan ve eşdeğerleri tanımlamak yerine kullanılmalıdır. Bu kod daha okunabilir ve kullanılan deyimsel bir hale gelir gibi bu işleçleri kullanarak önerilir. Arka plan OCaml veya işlev başka bir programlama dilinde geliştiricilere, farklı deyimleri için alışkın olabilir. Aşağıdaki listede, önerilen F# işleçleri özetlenmektedir.

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

F# genel türleri adlandırma iki sonek ML stili devralır (örneğin, `int list`) öneki .NET stili yanı sıra (örneğin, `list<int>`). .NET stili dört belirli tür dışında tercih et:

1. F# listeleri için sonek biçimi kullanın: `int list` yerine `list<int>`.
2. F# seçenekleri için sonek biçimi kullanın: `int option` yerine `option<int>`.
3. F# diziler için söz dizimi adı kullanmak `int[]` yerine `int array` veya `array<int>`.
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

Aynı satırda ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek de ince olmakla birlikte kullanmanız gerektiğini unutmayın [ayrıntılı sözdizimi](../language-reference/verbose-syntax.md) üyelerini tanımlamak için ( `with` anahtar sözcüğü):

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address: string
    City: string
    Zip: string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
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

Aynı satırda ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek da uygundur:

```fsharp
let rainbow = {
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
```

Bu kuralların listesi ve dizi öğeleri için geçerlidir.

## <a name="formatting-lists-and-arrays"></a>Biçimlendirme listeler ve diziler

Yazma `x :: l` etrafındaki boşlukları ile `::` işleci (`::` dolayısıyla boşluklarla çevrili bir içtakı işleci) ve `[1; 2; 3]` (`;` dolayısıyla ardından bir boşluk, bir sınırlayıcıdır).

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

Kayıtlar gibi listeler ve birden çok satırda bölme diziler benzer bir kural uygulayın:

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

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
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
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
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Boşluk ifadelerde biçimlendirme

F# ifadelerini fazlalık bölünemez boşluğu kaçının.

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
