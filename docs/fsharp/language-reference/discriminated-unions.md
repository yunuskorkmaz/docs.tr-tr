---
title: Ayrılmış Birleşimler
description: F# ayrımcı birliş nasıl kullanılacağını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400220"
---
# <a name="discriminated-unions"></a>Ayrılmış Birleşimler

Ayrımcı sendikalar, her biri farklı değerlere ve türlere sahip, adlandırılmış birkaç servis örneğinden biri olabilecek değerler için destek sağlar. Ayrımcı sendikalar heterojen veriler için yararlıdır; geçerli ve hata durumları da dahil olmak üzere özel durumlara sahip olabilecek veriler; türünde bir örnekten diğerine değişen veriler; ve küçük nesne hiyerarşileri için bir alternatif olarak. Buna ek olarak, özyinelemeli ayrımcı sendikalar ağaç veri yapılarını temsil etmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Açıklamalar

Ayrımcı sendikalar diğer dillerdeki birlik türlerine benzer, ancak farklılıklar vardır. C++'daki birleşim türünde veya Visual Basic'te bir varyant türünde olduğu gibi, değerde depolanan veriler sabit değildir; birkaç farklı seçenekten biri olabilir. Ancak, bu diğer dillerdeki birlişlerden farklı olarak, olası seçeneklerin her birine bir *servis talebi tanımlayıcısı*verilir. Servis talebi tanımlayıcıları, bu tür nesnelerin olabileceği çeşitli olası değer türlerinin adlarıdır; değerler isteğe bağlıdır. Değerler yoksa, durum numaralandırma örneğine eşdeğerdir. Değerler varsa, her değer belirtilen bir türün tek bir değeri veya aynı veya farklı türdeki birden çok alanı biraraya getiren bir tuple olabilir. Tek bir alana bir ad verebilirsiniz, ancak aynı durumda diğer alanlar adlandırılmış olsa bile ad isteğe bağlıdır.

Ayrımcı sendikalar için erişilebilirlik `public`varsayılan olarak .

Örneğin, şekil türünün aşağıdaki bildirimini göz önünde bulundurun.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Önceki kod, dikdörtgen, Daire ve Prizma olmak üzere üç durumdan herhangi birinin değerlerine sahip olabilecek ayrımcı bir birlik Şekli bildirir. Her servis talebinin farklı bir alan kümesi vardır. Dikdörtgen durumda iki adlandırılmış alanları, her `float`ikisi de türü , adları genişlik ve uzunluk var. Circle davasının sadece bir adı var, yarıçapı. Prizma durumda iki (genişlik ve yükseklik) alanları adlı üç alan vardır. Adsız alanlar anonim alanlar olarak adlandırılır.

Aşağıdaki örneklere göre adlandırılmış ve anonim alanlar için değerler sağlayarak nesneleri oluşturmak.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Bu kod, başlatmada adlandırılmış alanları kullanabileceğinizi veya bildirimdeki alanların sıralanmasına güvenebileceğinizi ve sırayla her alan için değerleri sağlayabileceğinizi gösterir. Önceki kodda `rect` kurucu çağrısı adlandırılmış alanları kullanır, ancak kurucu `circ` çağrı sıralama kullanır. Sipariş edilen alanları ve adlandırılmış alanları, inşaatta `prism`olduğu gibi karıştırabilirsiniz.

Tür, `option` F# çekirdek kitaplığında basit bir ayrımcı birleşimdir. Türü `option` aşağıdaki gibi bildirilir.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Önceki kod, türün `Option` iki servis nedeni olan ayrımlı `Some` bir `None`birleşim olduğunu belirtir ve . Servis `Some` talebi, türü tür parametresi `'a`ile temsil edilen anonim bir alandan oluşan ilişkili bir değere sahiptir. Servis `None` talebinin ilişkili bir değeri yoktur. Böylece `option` tür, bazı türde bir değere sahip veya değeri olmayan genel bir türü belirtir. Türü `Option` de daha yaygın olarak kullanılan `option`bir küçük tür takma vardır.

Vaka tanımlayıcıları, ayrımcı birlik türü için yapıcı olarak kullanılabilir. Örneğin, tür değerlerini `option` oluşturmak için aşağıdaki kod kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Örnek tanımlayıcılar desen eşleştirme ifadelerinde de kullanılır. Desen eşleştirme ifadesinde, tek tek servis talepleriyle ilişkili değerler için tanımlayıcılar sağlanır. Örneğin, aşağıdaki kodda, `x` `Some` `option` tür örneği ile ilişkili değer verilen tanımlayıcıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Desen eşleştirme ifadelerinde, ayrımcı birleşim eşleşmelerini belirtmek için adlandırılmış alanları kullanabilirsiniz. Daha önce bildirilen Şekil türü için, alanların değerlerini ayıklamak için aşağıdaki kodun gösterdiği gibi adlandırılmış alanları kullanabilirsiniz.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

Normalde, durum tanımlayıcıları sendika adı ile niteleme den önce kullanılabilir. Adın her zaman birliğin adı ile nitelikli olmasını istiyorsanız, Birleşim türü tanımına [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) özniteliğini uygulayabilirsiniz.

### <a name="unwrapping-discriminated-unions"></a>Ayrımcı Sendikaların Ambalajını Açma

F# Ayrımcı Sendikalar genellikle tek bir türü sarma için etki alanı modelleme kullanılır. Desen eşleştirme yoluyla da temel değeri ayıklamak kolaydır. Tek bir servis talebi için eşeşleştirme ifadesi kullanmanız gerekmez:

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

Aşağıdaki örnek bunu göstermektedir:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Desen eşleştirmede doğrudan işlev parametrelerine de izin verilir, böylece tek bir servis talebinin paketlemesine orada da izin verebilirsiniz:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Struct Ayrımcı Sendikalar

Ayrıca, Ayrımcı Birliş'leri yapı olarak temsil edebilirsiniz.  Bu öznitelik `[<Struct>]` ile yapılır.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Bunlar referans türleri değil, değer türleri olduğundan, başvuru ayrımı yapan birbiriyle karşılaştırıldığında ek hususlar vardır:

1. Bunlar değer türleri olarak kopyalanır ve değer türü semantiği vardır.
2. Çok harfli yapı lı Ayrımcılık Birliği ile özyinelemeli bir tür tanımı kullanamazsınız.
3. Çok harfli yapı Ayrımlı Birlik için benzersiz örnek adları sağlamanız gerekir.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Nesne Hiyerarşileri Yerine Ayrımcı Birliş Kullanma

Küçük nesne hiyerarşisine daha basit bir alternatif olarak genellikle ayrımcı bir birleşim kullanabilirsiniz. Örneğin, daire, kare ve benzeri türleri `Shape` türemiş bir taban sınıf yerine aşağıdaki ayrımcı birleşim kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Nesne yönelimli bir uygulamada kullanacağınız gibi, bir alanı veya çevreyi hesaplamak için sanal bir yöntem yerine, bu miktarları hesaplamak için dalla eşleşen deseni uygun formüllerle kullanabilirsiniz. Aşağıdaki örnekte, şekle bağlı olarak alanı hesaplamak için farklı formüller kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Ağaç Veri Yapıları için Ayrımcı Birliş Kullanma

Ayrımcı sendikalar özyinelemeli olabilir, bu da birliğin kendisinin bir veya daha fazla vaka türüne dahil edilebildiği anlamına gelir. Özyinelemeli ayrımcı birliş, programlama dillerinde ifadeleri modellemek için kullanılan ağaç yapıları oluşturmak için kullanılabilir. Aşağıdaki kodda, ikili ağaç veri yapısı oluşturmak için özyinelemeli bir ayrımcılık birliği kullanılır. Birleşim, `Node`tamsayı değeri ve sol ve sağ alt ağaçları olan bir düğüm `Tip`olan ve ağacı sonlandıran iki durumdan oluşur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Önceki kodda `resultSumTree` 10 değeri vardır. Aşağıdaki resimde ağaç yapısı `myTree`.

![myTree için ağaç yapısını gösteren diyagram.](../media/discriminated-unions/tree-structure-mytree.png)

Ağaçtaki düğümler heterojen sayılsa, ayrımcı sendikalar iyi çalışır. Aşağıdaki kodda, tür, `Expression` sayıların ve değişkenlerin eklenmesini ve çoğalmasını destekleyen basit bir programlama dilinde bir ifadenin soyut sözdizimi ağacını temsil eder. Bazı birleşim durumları özyinelemeli değildir ve sayılar`Number`( )`Variable`veya değişkenleri ( ) temsil eder. Diğer durumlarda özyinelemeli ve operands `Multiply`da ifadeler olduğu işlemleri temsil eder.`Add` İşlev `Evaluate` sözdizimi ağacını özyinelemeli olarak işlemek için bir eşleşme ifadesi kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Bu kod yürütüldüğünde, `result` değeri 5'tir.

## <a name="members"></a>Üyeler

Ayrımcılık yapılan sendikalarda üye tanımlamak mümkündür. Aşağıdaki örnek, bir özelliğin nasıl tanımlanacağını ve arabirimi nasıl uygulayacağını gösterir:

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a>Ortak öznitelikler

Aşağıdaki öznitelikler genellikle ayrımcı sendikalarda görülür:

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
