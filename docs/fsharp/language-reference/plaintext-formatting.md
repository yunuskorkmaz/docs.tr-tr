---
title: Düz Metin Biçimlendirmesi
description: 'F # uygulamalarında ve betiklerinizde printf ve diğer düz metin biçimlendirmesini nasıl kullanacağınızı öğrenin.'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063789"
---
# <a name="plain-text-formatting"></a>Düz metin biçimlendirme

F #,,, `printf` `printfn` ve ilgili işlevleri kullanılarak düz metnin tür denetimli biçimlendirmesini destekler `sprintf` .
Örneğin,

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

çıktıyı verir

```fsharp
Hello world, 2 + 2 is 4
```

F # yapılandırılmış değerlerin düz metin olarak biçimlendirilmesini de sağlar.
Örneğin, çıktıyı matris benzeri bir görünüm olarak biçimlendiren aşağıdaki örneği göz önünde bulundurun.

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

`%A`Biçimlendirme dizelerinde biçimi kullandığınızda yapılandırılmış düz metin biçimlendirmesi etkinleştirilir `printf` .
Ayrıca, çıktının ek bilgi içerdiği ve ek olarak özelleştirilebilen F # Interactive 'teki değerlerin çıktısı biçimlendirilirken de etkinleştirilir.
Düz metin biçimlendirme Ayrıca, `x.ToString()` hata ayıklama, günlüğe kaydetme ve diğer araç oluşturma ile ilgili olarak oluşan, F # UNION ve kayıt değerleri üzerinde yapılan çağrılar aracılığıyla da Observable ' dır.

## <a name="checking-of-printf-format-strings"></a>`printf`Biçimlendirme dizeleri denetleniyor

`printf`Biçim dizesindeki printf biçim belirticileriyle eşleşmeyen bir bağımsız değişkenle bir biçimlendirme işlevi kullanılıyorsa, derleme zamanı hatası bildirilir.  Örneğin,

```fsharp
sprintf "Hello %s" (2+2)
```

çıktıyı verir

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

Teknik olarak, `printf` ve diğer ilgili işlevleri kullanırken, F # derleyicisindeki özel bir kural, biçim dizesi olarak geçirilen dize değişmez değerini denetler ve sonraki bağımsız değişkenlerin, kullanılan biçim belirticileriyle eşleşecek şekilde doğru türde olmasını sağlar.

## <a name="format-specifiers-for-printf"></a>İçin biçim belirticileri`printf`

Biçimlerin biçim belirtimleri `printf` `%` biçimi gösteren işaretçilerle dizelerdir. Biçim yer tutucuları `%[flags][width][.precision][type]` , türün şu şekilde yorumlanması durumunda oluşur:

| Biçim belirteci   | Tür (ler)        | Açıklamalar                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | bool      | Veya olarak biçimlendirilir `true``false`                |
| `%s`               | string    | Kaçışsız içerikleri olarak biçimlendirilir         |
| `%c`               | char      | Karakter sabiti olarak biçimlendirilir  |
| `%d`, `%i`         | temel bir tamsayı türü | Temel tamsayı türü imzalanmışsa, bir ondalık tamsayı olarak biçimlendirilir, imzalandı |
| `%u`               | temel bir tamsayı türü | İşaretsiz ondalık tamsayı olarak biçimlendirilir   |
| `%x`, `%X`         | temel bir tamsayı türü | İşaretsiz onaltılık sayı (sırasıyla onaltılık basamaklar için a-f veya A-F) olarak biçimlendirilir  |
|  `%o`              | temel bir tamsayı türü | İşaretsiz sekizlik sayı olarak biçimlendirilir |
| `%e`, `%E`         | temel kayan nokta türü | `[-]d.dddde[sign]ddd`D 'nin tek bir ondalık basamak olduğu, yani gggg bir veya daha fazla ondalık basamak, DDD ise yalnızca üç ondalık basamak ve oturum açma `+` ya da`-` |
| `%f`               | temel kayan nokta türü | `[-]dddd.dddd` `dddd` Bir veya daha fazla ondalık basamak olmak üzere, forma sahip imzalı bir değer olarak biçimlendirilir. Ondalık noktadan önceki basamak sayısı sayının büyüklüğüne ve ondalık ayırıcıdan sonraki basamak sayısı, istenen duyarlığa bağlıdır. |
| `%g`, `%G` | temel kayan nokta türü |  `%f` `%e` Belirtilen değer ve duyarlık için daha küçük olduğu için, veya biçiminde yazdırılmış bir imzalı değer olarak kullanılarak biçimlendirilir. |
| `%M` | bir `System.Decimal` değer  |    `"G"`Biçim belirleyicisi kullanılarak biçimlendirilir`System.Decimal.ToString(format)` |
| `%O` | herhangi bir değer  |   Nesnesi kutulama yaparak ve metodunu çağırarak biçimlendirilir `System.Object.ToString()` |
| `%A` | herhangi bir değer  |   Varsayılan düzen ayarlarıyla [yapılandırılmış düz metin biçimlendirme](plaintext-formatting.md) kullanılarak biçimlendirildi |
| `%a` | herhangi bir değer  |   İki bağımsız değişken gerektirir: bir bağlam parametresini ve değeri kabul eden bir biçimlendirme işlevi ve yazdırılacak belirli değer |
| `%t` | herhangi bir değer  |   Bir bağımsız değişken gerektirir: bir bağlam parametresini kabul eden veya uygun metni döndüren bir biçimlendirme işlevi |
| `%%` | (yok)  |   Bağımsız değişken gerektirmez ve bir salt yüzde işareti yazdırır:`%` |

Temel tamsayı türleri `byte` ( `System.Byte` ), ( `sbyte` ) `System.SByte` , `int16` () `System.Int16` , `uint16` ( `System.UInt16` ), `int32` `System.Int32` `uint32` `System.UInt32` `int64` `System.Int64` `uint64` `System.UInt64` `nativeint` `System.IntPtr` `unativeint` `System.UIntPtr` (), (), ve ().
Temel kayan nokta türleri `float` ( `System.Double` ) ve `float32` ( `System.Single` ).

İsteğe bağlı genişlik, sonucun en az genişliğini gösteren bir tamsayıdır. Örneğin, `%6d` bir tamsayı yazdırır, en az altı karakteri dolduracak şekilde boşluk ile önek olarak. Width ise `*` , karşılık gelen genişliği belirtmek için fazladan bir tamsayı bağımsız değişkeni alınır.

Geçerli bayraklar şunlardır:

| Bayrak   | Etki        | Açıklamalar                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | Gerekli genişliği oluşturmak için boşluk yerine sıfır ekleyin |    |
| `-` |  Sonucu belirtilen genişlik içinde Sola Yasla |   |
| `+`  | `+`Sayı pozitifse ( `-` negatifler için bir işareti eşlemek için) bir karakter ekleyin |   |
| boşluk karakteri | Sayı pozitif ise (örneğin, negatifler için '-' işaretini eşlemek için) fazladan bir boşluk ekleyin |

Printf `#` bayrağı geçersiz ve kullanılıyorsa bir derleme zamanı hatası bildirilir.

Değerler, sabit kültür kullanılarak biçimlendirilir. Kültür ayarları, `printf` ve biçimlendirme sonuçlarının etkilenmediği durumlar dışında biçimlendirme ile ilgisiz `%O` değildir `%A` . Daha fazla bilgi için bkz. [yapılandırılmış düz metin biçimlendirmesi](plaintext-formatting.md).

## <a name="a-formatting"></a>`%A`biçime

`%A`Biçim Belirleyicisi, verileri insanlarca okunabilir bir şekilde biçimlendirmek için kullanılır ve ayrıca tanılama bilgilerini raporlamak için yararlı olabilir.

### <a name="primitive-values"></a>İlkel değerler

Belirteci kullanarak düz metin biçimlendirilirken `%A` , F # sayısal değerleri, soneki ve sabit kültürüyle biçimlendirilir. Kayan nokta değerleri, kayan nokta duyarlılığı 10 ' un kullanılarak biçimlendirilir. Örneğin,

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

üretmez

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

`%A`Tanımlayıcı kullanılırken dizeler, tırnak işaretleri kullanılarak biçimlendirilir. Kaçış kodları eklenmez ve bunun yerine ham karakterler yazdırılır. Örneğin,

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

üretmez

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a>.NET değerleri

Tanımlayıcı kullanılarak düz metin biçimlendirilirken `%A` , F # .NET nesneleri, `x.ToString()` ve tarafından verilen varsayılan .NET ayarları kullanılarak biçimlendirilir `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` .  Örneğin,

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

üretmez

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a>Yapılandırılmış değerler

Belirteci kullanarak düz metin biçimlendirilirken `%A` , blok girintileme F # listeleri ve tanımlama grupları için kullanılır. Bu, önceki örnekte gösterilmiştir.
Birden çok boyutlu diziler de dahil olmak üzere dizilerin yapısı da kullanılır.  Tek boyutlu diziler sözdizimi ile gösterilir `[| ... |]` . Örneğin,

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

üretmez

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

Varsayılan yazdırma genişliği 80 ' dir.  Bu genişlik, biçim tanımlayıcıda bir yazdırma genişliği kullanılarak özelleştirilebilir. Örneğin,

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

üretmez

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

0 yazdırma genişliğini belirtmek, hiçbir yazdırma genişliği kullanılmazsa sonuç olarak sonuçlanır. Çıktıda gömülü dizelerin satır sonları içermesi dışında, tek satırlık bir metin oluşur.  Örneğin:

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

üretmez

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

İçinde gösterilen dizi () değerleri için 4 derinlik sınırı kullanılır `IEnumerable` `seq { ...}` . Liste ve dizi değerleri için 100 derinlik sınırı kullanılır.
Örneğin,

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

üretmez

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

Blok girintileme, ortak kayıt ve birleşim değerlerinin yapısı için de kullanılır. Örneğin,

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

üretmez

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

Kullanılıyorsa `%+A` , kayıt ve birleşimlerin özel yapısı da yansıma kullanılarak da ortaya kaydedilir. Örneğin:

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

üretmez

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a>Büyük, döngüsel veya derin iç içe geçmiş değerler

Büyük yapılandırılmış değerler 10000 genel nesne düğümü sayısı üst sınırına biçimlendirilir.
Derin iç içe geçmiş değerler 100 derinliğine biçimlendirilir.  Her iki durumda da `...` çıktının bir kısmını almak için kullanılır.  Örneğin,

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

bazı parçalar olmadan büyük bir çıkış üretir:

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

Döngü, nesne grafiklerde algılanır ve `...` döngülerin algılandığı yerlerde kullanılır. Örneğin:

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

üretmez

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a>Lazy, null ve işlev değerleri

`Value is not created`Değer henüz değerlendirilmemişse, yavaş değerler veya eşit metin olarak yazdırılır.

`null`Değer statik türünün, `null` izin verilen bir temsil olduğu bir birleşim türü olarak belirlenmediği sürece null değerler yazdırılır.

F # işlev değerleri, dahili olarak oluşturulan kapanış adı olarak yazdırılır (örneğin,) `<fun:it@43-7>` .

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a>Düz metin biçimlendirmesini özelleştirme`StructuredFormatDisplay`

`%A`Tanımlayıcı kullanılırken, `StructuredFormatDisplay` tür bildirimlerinde özniteliği varlığını dikkate alır.  Bu, bir değeri göstermek için yedek metin ve özellik belirtmek için kullanılabilir. Örnek:

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

üretmez

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a>Düz metin biçimlendirmesini geçersiz kılarak özelleştirin`ToString`

Varsayılan uygulama, `ToString` F # programlamasında Observable ' dır. Genellikle, varsayılan sonuçlar programcı ile ilgili bilgi görüntüsü veya Kullanıcı çıktısında kullanım için uygun değildir ve sonuç olarak varsayılan uygulamayı geçersiz kılmak yaygın bir işlemdir.  

Varsayılan olarak, F # kayıt ve birleşim türleri tarafından `ToString` kullanılan bir uygulamayla uygulamasını geçersiz kılar `sprintf "%+A"` .  Örneğin,

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

üretmez

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

Sınıf türleri için, varsayılan bir uygulama `ToString` sağlanmaz ve .net varsayılanı kullanılır ve bu da türün adını bildirir. Örneğin,

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

üretmez

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

İçin bir geçersiz kılma eklemek `ToString` daha iyi biçimlendirme sağlayabilir.

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

üretmez

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a>Yapılandırılmış yazdırma F# Etkileşimli

F# Etkileşimli ( `dotnet fsi` ), değerleri raporlamak için yapılandırılmış düz metin biçimlendirmesinin genişletilmiş bir sürümünü kullanır ve ek özelleştirme sağlar. Daha fazla bilgi için bkz. [F# Etkileşimli](fsharp-interactive-options.md).

## <a name="customize-debug-displays"></a>Hata ayıklama ekranları Özelleştir

.NET için hata ayıklayıcılar, ve gibi özniteliklerin kullanımına saygı `DebuggerDisplay` `DebuggerTypeProxy` gösterir ve bu, hata ayıklayıcı İnceleme penceresinde nesnelerin yapılandırılmış görüntüsünü etkiler.
F # derleyicisi ayırt edici birleşim ve kayıt türleri için bu öznitelikleri otomatik olarak oluşturdu, ancak sınıf, arabirim veya yapı türleri değil.

Bu öznitelikler F # düz metin biçimlendirmesinde yok sayılır, ancak F # türlerinde hata ayıklarken ekranları geliştirmek için bu yöntemleri uygulamak yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Dizeler](strings.md)
- [Kayıtlar](records.md)
- [Ayrılmış Birleşimler](discriminated-unions.md)
- [F# Etkileşimli](fsharp-interactive-options.md)
