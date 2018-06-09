---
title: 'F # kod biçimlendirme yönergeleri'
description: 'F # kod biçimlendirme yönergeleri hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 6c8e4059fd4bf1e7450118a6df02609217c4f4db
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231519"
---
# <a name="f-code-formatting-guidelines"></a>F # kod biçimlendirme yönergeleri

Bu makalede, F # kodunuzun böylece kodunuzu biçimlendirme için yönergeler sunar:

* Genel olarak daha okunabilir görüntülenebilir
* Visual Studio Araçları ve diğer düzenleyicileri biçimlendirme tarafından uygulanan kurallarına uygun değil
* Başka bir kod çevrimiçi benzer

Bu yönergelere dayalı [F # biçimlendirme kuralları kapsamlı bir kılavuz](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) tarafından [Anh Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Girinti için genel kurallar

F # önemli boşluk varsayılan olarak kullanır. Aşağıdaki yönergeler bu uygulayabilir bazı zorluklar juggle nasıl konusunda yönergeler sağlamak için tasarlanmıştır.

### <a name="using-spaces"></a>Alanları kullanma

Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir. En az bir alan gereklidir. Kuruluşunuz için girinti kullanmak için alanları sayısını belirtmek için kodlama standartları oluşturabilir; girinti girinti oluştuğu her düzeyde iki, üç veya dört boşluklardan tipiktir.

**Girinti başına 4 boşluk öneririz.**

Bu, programların girinti öznel bir konudur belirtti. Çeşitlemeler edilir, ancak takip etmeniz gerekir ilk kural *girinti tutarlılığını*. Girinti, genel olarak kabul edilen bir stil seçin ve temelinizde sistematik olarak kullanın.

## <a name="formatting-blank-lines"></a>Boş satırlar biçimlendirme

* Ayrı en üst düzey işlevi ve sınıf tanımları iki boş satırlar.
* Yöntem tanımlarını bir sınıf içinde tek bir boş çizgi ile ayrılır.
* Ek boş satırlar (tutumlu) ilgili işlevleri grupları ayırmak için kullanılabilir. Boş satırlar ilgili one-liners (örneğin, sahte uygulamaları kümesi) arasında bir grup atlanabilir.
* Boş satırlar işlevlerde, gerektiğinde, mantıksal bölümleri belirtmek için kullanın.

## <a name="formatting-comments"></a>Açıklamalar Biçimlendirme

Genellikle birden çok çift eğik çizgi açıklamaları ML stil bloğu açıklamaları tercih edilir.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Satır içi açıklamalar ilk harfini büyük.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Adlandırma kuralları

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Sınıf bağlı, ifade bağlı ve desen ilişkili değerleri ve işlevleri için camelCase kullanın

Yaygın bir durumdur ve yerel değişkenleri olarak veya desen eşleşmeleri ve işlev tanımları camelCase tüm adları için kabul edilen F # stili bağlanır.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Sınıflardaki yerel olarak bağlı işlevleri de camelCase kullanmanız gerekir.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Modül bağlı ortak işlevleri için camelCase kullanın

Bir modül bağlı işlevi genel API'si bir parçası olduğunda, camelCase kullanmanız gerekir:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>İç ve özel modülü sınır değerleri ve işlevleri için camelCase kullanın

CamelCase aşağıdakiler de dahil olmak üzere özel modülü sınır değerleri için kullanın:

* Komut dosyalarında geçici işlevler

* Bir modül veya türü iç uygulamasını yapmak değerleri

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>CamelCase parametrelerini kullanın

Tüm parametreleri camelCase .NET adlandırma kurallarına uygun olarak kullanmanız gerekir.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Modüller için PascalCase kullanın

Tüm modülleri (üst düzey, iç, özel, iç içe geçmiş) PascalCase kullanmanız gerekir.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Tür bildirimleri, üyeleri ve etiketler için PascalCase kullanın

Sınıflar, arabirimler, yapılar, numaralandırmalar, temsilciler, kaydeder ve ayrılmış birleşimler tüm ile PascalCase adlı olmalıdır. Üye türleri ve kaydeder ve ayrılmış birleşimler için etiketleri içinde ayrıca PascalCase kullanmanız gerekir.

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

Ad alanları, özel durumlar, olaylar ve proje /`.dll` adları PascalCase de kullanmalıdır. Yalnızca bu diğer .NET dilleri gelen tüketicilere daha doğal eşitleyerek tüketim yapar, ayrıca karşılaşma olasılığı olan .NET adlandırma kuralları ile tutarlı olur.

### <a name="avoid-underscores-in-names"></a>Alt çizgi adlarında kaçının

Tarihsel olarak, bazı F # kitaplıkları adları alt çizgi kullandınız. Kısmen .NET adlandırma kuralları ile çakışıyor çünkü ancak bu artık yaygın olarak, kabul edilir. Bu, bazı F # programcıları alt çizgi yoğun, kısmen geçmiş nedenlerle kullanın ve dayanıklılık ve saygı önemlidir da belirtti. Ancak, bunu kullanıp kullanmayacağınızı hakkında seçmesini başkaları tarafından stili genellikle yanıtlamadığı unutmayın.

Yerel, alt çizgi yaygın olduğu bileşenleriyle birlikte özel bazı durumlar içerir.

### <a name="use-standard-f-operators"></a>Standart F # işleçleri kullanın

Aşağıdaki işleçleri F # standart Kitaplığı'nda tanımlanır ve eşdeğerleri tanımlama yerine kullanılmalıdır. Kodunu daha okunabilir ve kullanılan deyimsel hale eğilimlidir gibi bu işleçlere kullanılması önerilir. Arka plan OCaml veya diğer işlevsel programlama dili geliştiricilere farklı deyimleri alışkın olabilir. Aşağıdaki liste, önerilen F # işleçleri özetler.

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Genel türler için önek söz dizimini kullanın (`Foo<T>`) sonek sözdizimi yerine (`T Foo`)

F # genel türleri adlandırma hem sonek ML stili devralır (örneğin, `int list`) yanı sıra .NET stili önek (örneğin, `list<int>`). Dört belirli türleri dışında .NET stili tercih eder:

1. F # listeleri, sonek formu kullanın: `int list` yerine `list<int>`.
2. F # seçenekleri için sonek formu kullanın: `int option` yerine `option<int>`.
3. F # diziler için söz dizimi adı kullanmak `int[]` yerine `int array` veya `array<int>`.
4. Başvuru hücreleri için kullanmak `int ref` yerine `ref<int>` veya `Ref<int>`.

Diğer tüm türleri için önek formu kullanın.

## <a name="formatting-discriminated-union-declarations"></a>Ayrılmış birleşim bildirimleri biçimlendirme

Girinti `|` 4 boşluk tarafından türü tanımında:

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

Örneklenen ayrılmış birden çok satıra yayılmış ayrılmış birleşimler içerdiği veri girinti ile yeni bir kapsam vermeniz gerekir:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

Kapatma parantezi de yeni bir satıra olabilir:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a>Diziler biçimlendirme

Parantez içine alınmış bir tanımlama grubu örneklemesi olmalıdır ve sınırlandırma virgül içinde tek bir boşlukla örneğin gelmelidir: `(1, 2)`, `(x, y, z)`.

Diziler desen eşleştirme içinde parantez atlamak için yaygın olarak kabul edilen bir özel durumdur:

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a>Kayıtları biçimlendirme

Kısa kayıtları tek bir çizgi yazılabilir:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Uzun kayıtları yeni satırlar için etiketleri kullanmanız gerekir:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Aynı satır ve yeni bir satıra kapatma belirteci açma belirteci yerleştirerek de uygundur:

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

Aynı kuralları dizisi ve liste öğeleri için geçerlidir.

## <a name="formatting-lists-and-arrays"></a>Biçimlendirme listeler ve diziler

Yazma `x :: l` boşluk ile `::` işleci (`::` bu nedenle boşluklarla çevrelenmiş bir iç işleci) ve `[1; 2; 3]` (`;` bu nedenle bir boşluk bırakarak bir sınırlayıcı).

Her zaman iki farklı küme parantezi benzeri işleç arasındaki en az bir boşluk kullanın. Örneğin, arasında boşluk bırakmak bir `[` ve `{`.

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

Kayıtları gibi listeler ve birden çok satıra yayılmış bölme diziler benzer bir kural izleyin:

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

Koşulları girinti onları oluşturan ifadeler boyutlarına bağlıdır. Varsa `cond`, `e1` ve `e2` küçük, yalnızca bunları tek satıra yazın:

```fsharp
if cond then e1 else e2
```

Varsa `e1` ve `cond` küçük, ancak `e2` büyük:

```fsharp
if cond then e1
else
    e2
```

Varsa `e1` ve `cond` büyük ve `e2` küçük:

```fsharp
if cond then
    e1
else e2
```

Tüm ifadeler büyükse:

```fsharp
if cond then
    e1
else
    e2
```

Birden çok koşulları ile `elif` ve `else` aynı kapsamda girintili `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Desen eşleştirme yapıları

Kullanım bir `|` her bir eşleşme yan tümcesinin hiçbir girinti ile. İfade kısaysa, her alt aynı zamanda basit ise tek bir satır kullanmayı seçebilirsiniz.

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

Sağ ok eşleşen kalıbı tarafındaki ifade çok büyükse, taşıyabilir girintili bir adımda aşağıdaki satırı `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Desen ile başlayan anonim işlevlerin eşleşen `function`, genellikle çok girinti değil. Örneğin, aşağıdaki gibi bir kapsam girintileme uygundur:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Desen eşleştirme tarafından tanımlanan işlevlerinde `let` veya `let rec` girintili 4 boşluk, başlattıktan sonra olmalıdır `let`olsa bile `function` anahtar sözcüğü kullanılır:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Oklar hizalama önermiyoruz.

## <a name="formatting-trywith-expressions"></a>Biçimlendirme try / ifadelerle

Desen eşleştirme özel durum türüne girintili aynı düzeyde `with`.

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

Genel olarak, çoğu işlevi parametresi uygulama aynı çizgi üzerinde gerçekleştirilir.

Yeni bir satıra bir işlev parametreleri uygulamak isterseniz, bunları bir kapsam tarafından girinti.

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

Aynı yönergeleri işlevi bağımsız değişken olarak lambda ifadeleri için geçerlidir. Lambda ifadesi, gövde gövdesi başka bir satır varsa bir kapsam tarafından girintili

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

Ancak, bir lambda ifadesi gövdesi birden fazla satır ise, onu ayrı bir işlevdeki Finansman göz önünde bulundurun yerine tek bir bağımsız değişken olarak bir işleve uygulanan bir çok satırlı yapısı sahip.

### <a name="formatting-infix-operators"></a>Biçimlendirme iç işleçleri

Alanları ayrı işleçleriyle. Bu kural belirgin istisnaları `!` ve `.` işleçler.

İç ifadeleri serisi aynı sütunda Tamam üzeresiniz:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Ardışık Düzen operatörleri biçimlendirme

Ardışık Düzen `|>` işleçleri çalışması üzerinde ifadeleri altında gitmesini.

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

Bir yerel modül kodda modülü göre girintili gerekir, ancak üst düzey bir modül kodda girintili. Namespace öğeleri girintili gerekmez.

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

Nesne ifadeleri ve arabirimler hizalı ile aynı şekilde `member` sonra 4 boşluk girintili.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a>İfadelerde boşluk biçimlendirme

F # ifadelerde yabancı boşluk kaçının.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Adlandırılmış bağımsız değişkenler de olmamalıdır alanını çevreleyen `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
