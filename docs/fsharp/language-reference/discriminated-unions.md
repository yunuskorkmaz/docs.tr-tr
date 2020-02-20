---
title: Ayrılmış Birleşimler
description: Ayırt edici birleşimler kullanmayı F# öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452649"
---
# <a name="discriminated-unions"></a>Ayrılmış Birleşimler

Ayırt edici birleşimler, büyük olasılıkla her biri farklı değer ve türlere sahip olabilecek bir dizi adlandırılmış durum olabilen değerler için destek sağlar. Ayırt edici birleşimler heterojen veriler için yararlıdır; geçerli ve hata durumları dahil olmak üzere özel durumları olan veriler; tür olarak bir örnekten diğerine değişen veriler; küçük nesne hiyerarşileri için alternatif olarak. Ayrıca, yinelemeli ayırt edici birleşimler ağaç veri yapılarını temsil etmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Açıklamalar

Ayırt edici birleşimler diğer dillerdeki birleşim türlerine benzerdir, ancak farklılık vardır. İçindeki C++ bir birleşim türü veya Visual Basic değişken türünde olduğu gibi, değerde depolanan veriler düzeltilmez; Bu çeşitli seçeneklerden biri olabilir. Ancak, bu diğer dillerdeki birleşimlerin aksine, olası seçeneklerin her birine bir *Case tanımlayıcısı*verilir. Büyük/küçük harf tanımlayıcıları, bu türdeki nesnelerin olabilecek çeşitli olası değer türlerinin adlarıdır; değerler isteğe bağlıdır. Değerler yoksa, büyük/küçük harf bir numaralandırma durumuna eşdeğerdir. Değerler mevcutsa, her değer belirtilen türde tek bir değer veya aynı ya da farklı türlerin birden fazla alanını toplayan bir tanımlama grubu olabilir. Tek bir alana bir ad verebilirsiniz, ancak aynı durumda diğer alanlar adlandırılmış olsa bile ad isteğe bağlıdır.

Ayrılmış birleşimler için erişilebilirlik varsayılan olarak `public`.

Örneğin, bir şekil türünün Aşağıdaki bildirimini göz önünde bulundurun.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Yukarıdaki kod, ayırt edici bir birleşim şekli bildirir ve bu üç durumda herhangi bir değere sahip olabilir: dikdörtgen, daire ve Prizm. Her durumda farklı bir alan kümesi vardır. Dikdörtgen durumunun genişliği ve uzunluğu `float`her ikisi de olan iki adlandırılmış alana sahiptir. Daire durumunun yalnızca bir tane adlandırılmış alanı Radius vardır. Prronizme durumu üç alana sahiptir, ikisi de (genişlik ve yükseklik) olarak adlandırılır. Adlandırılmamış alanlara anonim alanlar denir.

Aşağıdaki örneklere göre adlandırılmış ve anonim alanlar için değerler sağlayarak nesneler oluşturursunuz.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Bu kod, başlatma içindeki adlandırılmış alanları kullanabilir ya da bildirimdeki alanların sıralamasını temel alabilir ve yalnızca her bir alan için değerleri de sağlayabilirsiniz. Önceki kodda `rect` için Oluşturucu çağrısı, adlandırılmış alanları kullanır, ancak `circ` Oluşturucu çağrısı sıralamayı kullanır. Sıralı alanları ve adlandırılmış alanları, `prism`yapıında karıştırabilirsiniz.

`option` türü, F# çekirdek kitaplığındaki basit bir ayırt edici birleşimdir. `option` türü aşağıdaki şekilde bildirilmiştir.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Önceki kod, tür `Option`, iki durum `Some` ve `None`olan ayrılmış bir birleşim olduğunu belirtir. `Some` durumda, türü parametre `'a`ile temsil edilen bir anonim alandan oluşan ilişkili bir değer vardır. `None` durumunun ilişkili bir değeri yok. Bu nedenle `option` türü, bir veya değeri olmayan bir değere sahip olan genel bir türü belirtir. `Option` Ayrıca, daha yaygın olarak kullanılan `option`küçük harfli tür diğer adına sahiptir.

Büyük/küçük harf tanımlayıcıları, ayırt edici birleşim türü için oluşturucular olarak kullanılabilir. Örneğin, aşağıdaki kod `option` türünün değerlerini oluşturmak için kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Büyük/küçük harf tanımlayıcıları aynı zamanda desenler eşleştirme ifadelerinde de kullanılır. Bir model eşleştirme ifadesinde, tanımlayıcılar, bireysel durumlar ile ilişkili değerler için sağlanır. Örneğin, aşağıdaki kodda `x`, `option` türünün `Some` durumuyla ilişkili değer verilen tanıtıcıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Desenler eşleştirme ifadelerinde, ayırt edici birleşim eşleşmelerini belirtmek için adlandırılmış alanları kullanabilirsiniz. Daha önce tanımlanan şekil türü için, alanların değerlerini ayıklamak üzere aşağıdaki kodda gösterildiği gibi, adlandırılmış alanları kullanabilirsiniz.

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

Genellikle, büyük/küçük harf tanımlayıcıları birleşim adıyla nitelemeden kullanılabilir. Adın her zaman birleşimin adı ile nitelenmiş olmasını istiyorsanız, [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) özniteliğini birleşim türü tanımına uygulayabilirsiniz.

### <a name="unwrapping-discriminated-unions"></a>Ayrılmış birleşimler sarmalama

F# Ayırt edici birleşimler, genellikle tek bir tür sarmalama için etki alanı modellemesinde kullanılır. Temel alınan değeri, aynı zamanda kalıp eşleştirme aracılığıyla ayıklamak çok kolaydır. Tek bir durum için eşleşme ifadesi kullanmanız gerekmez:

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

Aşağıdaki örnek şunu gösterir:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Ayrıca, doğrudan işlev parametrelerinde de model eşleştirmeye izin verilir, bu nedenle tek bir büyük/küçük harf sarmasını geri alabilirsiniz:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Yapı ayırt edici birleşimler

Ayırt edici birleşimleri yapı olarak da temsil edebilirsiniz.  Bu, `[<Struct>]` özniteliğiyle yapılır.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Bunlar değer türleri ve başvuru türleri olduklarından, başvuru ayrılmış birleşimlerle karşılaştırıldığında ek hususlar vardır:

1. Değer türleri olarak kopyalanırlar ve değer türü semantiği vardır.
2. Bir özyinelemeli tür tanımını, Multicase yapısına ayrılmış birleşim ile kullanamazsınız.
3. Çok büyük harf yapısına ayrılmış bir birleşim için benzersiz bir durum adı sağlamanız gerekir.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Nesne hiyerarşileri yerine ayrılmış birleşimler kullanma

Ayrılmış bir birleşimi genellikle küçük bir nesne hiyerarşisinin daha basit bir alternatifi olarak kullanabilirsiniz. Örneğin, aşağıdaki ayrılmış birleşim, daire, kare ve benzeri türetilmiş türler içeren `Shape` temel sınıf yerine kullanılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Bir alanı veya birimi hesaplamak için bir sanal yöntem yerine, nesne odaklı bir uygulamada kullandığınız gibi, bu miktarları hesaplamak için uygun formüllere dalla bir şekilde eşleşen model eşleştirmeyi kullanabilirsiniz. Aşağıdaki örnekte, şekle bağlı olarak alanı hesaplamak için farklı formüller kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Ağaç veri yapıları için ayrılmış birleşimler kullanma

Ayırt edici birleşimler özyinelemeli olabilir; yani birleşim bir veya daha fazla durum türüne dahil edilebilir. Yinelemeli ayırt edici birleşimler, programlama dillerinde ifadeleri modellemek için kullanılan ağaç yapıları oluşturmak için kullanılabilir. Aşağıdaki kodda, bir ikili ağaç veri yapısı oluşturmak için özyinelemeli bir ayırt edici birleşim kullanılır. Birleşim iki durumlardan oluşur, bir tamsayı değeri ve sol ve sağ alt ağaçlar içeren bir düğüm ve ağacı sonlandıran `Tip``Node`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Önceki kodda `resultSumTree` 10 değerine sahiptir. Aşağıdaki çizim `myTree`için ağaç yapısını gösterir.

![MyTree için ağaç yapısını gösteren diyagram.](../media/discriminated-unions/tree-structure-mytree.png)

Ağaç içindeki düğümler heterojen ise, ayırt edici birleşimler iyi çalışır. Aşağıdaki kodda tür `Expression`, sayıların ve değişkenlerin eklenmesi ve çarpumu destekleyen basit bir programlama dilindeki ifadenin soyut sözdizimi ağacını temsil eder. Birleşim çalışmalarından bazıları özyinelemeli değildir ve sayıları (`Number`) veya değişkenleri (`Variable`) temsil eder. Diğer durumlar özyinelemeli olarak işlenir ve işlenen işlemleri (`Add` ve `Multiply`) temsil eder; burada işlenenler de deyimlerdir. `Evaluate` işlevi, sözdizimi ağacını yinelemeli olarak işlemek için bir Match ifadesi kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Bu kod yürütüldüğünde `result` değeri 5 ' tir.

## <a name="members"></a>Üyeler

Ayrılmış birleşimlerde Üyeler tanımlamak mümkündür. Aşağıdaki örnek, bir özelliğin nasıl tanımlanacağını ve bir arabirimin nasıl uygulanacağını gösterir:

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

Aşağıdaki öznitelikler yaygın olarak ayrılmış birleşimlerde görülür:

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
