---
title: Ayrılmış Birleşimler
description: Nasıl kullanacağınızı öğrenin F# ayrılmış birleşimler.
ms.date: 05/16/2016
ms.openlocfilehash: 9d3f423d068df1c43791919b0d71ca82304ae85e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821432"
---
# <a name="discriminated-unions"></a>Ayrılmış Birleşimler

Ayrılmış birleşimler, bir dizi adlandırılmış durumlarda, büyük olasılıkla her biri farklı değerde ve türde herhangi birini değerler için destek sağlar. Ayrılmış birleşimler heterojen veriler için kullanışlı; Geçerli dahil olmak üzere, özel durumlar ve hata durumları veri; bir örneği bir türden diğerine değişen verileri; ve küçük nesne hiyerarşileri için alternatif olarak. Ayrıca, özyinelemeli ayırt edici birleşimler ağaç veri yapılarını temsil etmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a>Açıklamalar

Ayrılmış birleşimler, diğer dillerdeki birleşim türleriyle benzerdir, ancak bazı farklılıklar vardır. Olarak C++ içindeki birleşim türünde veya Visual Basic içindeki değişken türünde değerde depolanan veriler sabit; ayrı ayrı birkaç seçenekten biri olabilir. Diğer bu dillerdeki birleşimlerden farklı olarak, Bununla birlikte, olası seçeneklerin her biri verilir bir *durum tanımlayıcı*. Durum tanımlayıcıları, bu tür nesneler olabilir değerleri çeşitli olası türleri adlarıdır; İsteğe bağlı değerler. Değerler mevcut değilse, böyle bir numaralandırma vakasına eşdeğerdir. Değerler varsa her değer ya da belirtilen bir türün ya da aynı ya da farklı türlerin birden çok alanını toplayan bir tanımlama grubu tek bir değer olabilir. Ayrı ayrı alanlara bir ad verebilirsiniz ancak aynı durumdaki diğer alanlar adlandırılmış olsa dahi, isteğe bağlı adıdır.

Ayrılmış birleşimler için erişilebilirlik varsayılanları `public`.

Örneğin, bir şekil türünün aşağıdaki bildirimini düşünün.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Yukarıdaki kod, ayrılmış bir birleşim herhangi birinin üç durum değerleri olan şekil bildirir: Dikdörtgen, daire ve Prizma. Her durumda, farklı bir alan kümesi vardır. Dikdörtgenin çalışması sahip iki adlı alanları, iki tür `float`, genişlik ve uzunluk adlarına sahip. Circle durumu yalnızca bir adlandırılmış alana sahiptir RADIUS. Prism durumunun üç alanı vardır alanları adlı iki hangi (genişlik ve yükseklik). Adlandırılmamış anonim alan olarak adlandırılır.

Aşağıdaki örnekler göre adlandırılmış ve anonim alanlar için değerleri sağlayarak nesneleri oluşturmak.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Bu kod, başlatma işlemindeki adlandırılmış alanları kullanabilirsiniz, veya bildirimdeki alanların sıralamasını üzerinde kullanır ve her alan için değerleri'yalnızca sırayla sağlayın gösterir. İçin oluşturucu çağrısı `rect` önceki kod içinde adlandırılmış alanları, ancak için oluşturucu çağrısı kullanır `circ` sıralamayı kullanır. Sıralı alanları karıştırabilirsiniz ve alanları, oluşumunu olduğu gibi adlı `prism`.

`option` Türüdür, basit bir birleşimdir F# çekirdek kitaplığı. `option` Türü gibi bildirilir.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Önceki kod belirten türü `Option` iki duruma sahip ayrılmış bir birleşim olduğunu `Some` ve `None`. `Some` Çalışması türü tür parametresi ile temsil edilir bir anonim alan içeren ilişkili değeri var `'a`. `None` Çalışması ilişkili değere sahip. Bu nedenle `option` türü veya tür veya değer değeri olan bir genel tür belirtir. Türü `Option` ayrıca bir küçük harf tür diğer adı olan `option`, yani daha sık kullanılan.

Durum tanımlayıcıları, ayrılmış birleşim türü için oluşturucu kullanılabilir. Örneğin, aşağıdaki kod değerler oluşturmak için kullanılan `option` türü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Durum tanımlayıcıları da Desen eşleştirme ifadelerinde kullanılır. Bir desen eşleme ifadesinde tanımlayıcılar tek tek durumlarla ilişkili değerler için sağlanır. Örneğin, aşağıdaki kodda, `x` tanımlayıcısı ile ilişkili değer verilen `Some` durumu `option` türü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Desen eşleştirme ifadelerinde, ayrılmış birleşim eşleşmelerini belirtmek için adlandırılmış alanları kullanabilirsiniz. Alanların değerlerini ayıklamak için aşağıdaki kodda gösterildiği gibi daha önceden bildirilen Şekil türü için adlandırılmış alanları kullanabilirsiniz.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Normalde, büyük/küçük harf tanımlayıcıları, birleşim adıyla nitelemeden kullanılabilir. Her zaman için birleşim adıyla nitelendirilmesi adını isterseniz uygulayabilirsiniz [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliğini birleşim türü tanımına.

### <a name="unwrapping-discriminated-unions"></a>Açma ayrılmış birleşimler

İçinde F# ayırt edici birleşimler sık kullanılan etki alanı modelleme, tek bir tür sarmalama için. Temeldeki değeri de desen eşleştirme aracılığıyla ayıklamak kolay bir işlemdir. Bir eşleme ifadesi için tek bir kasada kullanmanız gerekmez:

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

Aşağıdaki örnek bunu gösterir:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

Burada tek bir kasada sarmalamadan çıkarma için desen eşleştirme doğrudan işlev parametrelerinde da izin verilir:

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a>Ayrılmış birleşimler yapısı

İle başlayarak F# 4.1, ayırt edici birleşimler yapı birimleri olarak da temsil edebilir.  Bunun `[<Struct>]` özniteliği.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Bu değer türleri ve başvuru türleri değil çünkü vardır ek konuları başvuru ile karşılaştırıldığında ayırt edici birleşimler:

1. Bunlar, değer türleri kopyalanır ve değer türü anlamları vardır.
2. Bir özyinelemeli tür tanımı Discriminated birleşim multicase yapı ile kullanamazsınız.
3. Multicase yapı Discriminated birleşim büyük/küçük harf benzersiz adlar sağlamanız gerekir.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Nesne hiyerarşileri yerine ayrılmış birleşimler kullanma

Küçük nesne hiyerarşisi için basit bir alternatif olarak, ayrılmış bir birleşim genellikle kullanabilirsiniz. Örneğin, aşağıdaki ayrılmış bileşim yerine kullanılabilecek bir `Shape` temel türleri daire, türetilmiş kare vb. sınıfı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Bunun yerine bir alan veya çevre hesaplamak için sanal bir yöntem, nesne yönelimli bir uygulamada kullanmanız gerekir, bu miktarları hesaplamak için uygun formüllere eşleşen kalıbı kullanabilirsiniz. Aşağıdaki örnekte, şekile bağlı olarak alan hesaplamak için farklı formüller kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Çıktı aşağıdaki şekilde olacaktır:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Ayrılmış birleşimler ağaç veri yapıları için kullanma

Ayrılmış birleşimler, yani birleşim kendi başına bir veya daha fazla türünü eklenebilir, özyinelemeli olabilir. Özyinelemeli ayrılmış birleşimler, programlama dillerindeki ifadeleri için kullanılan ağaç yapıları oluşturmak için kullanılabilir. Aşağıdaki kodda bir özyinelemeli ayrılmış birleşim bir ikili ağaç veri yapısı oluşturmak için kullanılır. Birleşim iki durumdan oluşur `Node`, bir tamsayı değeri ile sol ve sağ alt ağaçlara sahip bir düğüm ve `Tip`, ve ağacı sonlandıran.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Önceki kodda, `resultSumTree` 10 değerine sahiptir. Ağaç yapısı için aşağıdaki çizimde `myTree`.

![MyTree için ağaç yapısı gösteren diyagram.](../media/discriminated-unions/tree-structure-mytree.png)

Ayrılmış birleşimler Ağaçtaki düğümler heterojen iyi çalışır. Aşağıdaki kodda, türü `Expression` toplanmasını ve çarpılmasını sayıların ve değişkenlerin destekler basit bir programlama dili, bir ifadenin soyut sözdizimi ağacını temsil eder. Bazı birleşim durumları özyinelemeli değildir ve sayıları temsil eder (`Number`) veya değişkenler (`Variable`). Diğer durumlarda özyinelemelidir ve işlemleri temsil etmekte (`Add` ve `Multiply`), işlenenlerin de ifadeleri olduğu. `Evaluate` İşlevi sözdizimi ağacını yinelemeli olarak işlemek için bir eşleme ifadesi kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Bu kod zaman yürütülür, değerini `result` 5'tir.

## <a name="common-attributes"></a>Ortak Öznitelikler

Aşağıdaki öznitelikler de ayrılmış birleşimler yaygın olarak görülür:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]`

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)