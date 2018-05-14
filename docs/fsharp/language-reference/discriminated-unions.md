---
title: Ayrılmış Birleşimler (F#)
description: 'F # kullanmayı öğrenin birleşimler.'
ms.date: 05/16/2016
ms.openlocfilehash: 617c659e26df52819a98294bcbfa081ab82fed03
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2018
---
# <a name="discriminated-unions"></a>Ayrılmış Birleşimler

Ayrılmış birleşimler, bir dizi adlandırılmış durumlarda, büyük olasılıkla her farklı değerler ve türlerle biri olabilir değerler için destek sağlar. Ayrılmış birleşimler heterojen veriler için kullanışlı; Geçerli dahil olmak üzere özel durumlar ve hata durumları olabilir veri; bir örnek bir türden diğerine değişen verileri; ve küçük nesne Hiyerarşiler için alternatif olarak. Ayrıca, özyinelemeli ayrılmış birleşimler ağaç veri yapıları temsil etmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a>Açıklamalar
Ayrılmış birleşimler diğer dillerde birleşim türlerini benzer ancak bazı farklılıklar vardır. Olarak bir birleşim türü c++ veya Visual Basic değişken türü değerinde depolanan verileri Düzeltilmemiş; Bu seçeneklerden biri veya birkaçı farklı olabilir. Bu diğer dillerdeki birleşimler, Bununla birlikte, her bir olası seçenek verilir bir *servis talebi tanımlayıcısı*. Bu tür nesneler olabilir değerleri çeşitli olası türleri için adları büyük/küçük harfe tanımlayıcılardır; değerleri isteğe bağlıdır. Değerler mevcut değilse, bir numaralandırma durumu eşdeğer bir durumdur. Değerleri varsa, her değer ya da belirtilen bir tür ya da aynı veya farklı türdeki birden çok alan toplayan bir tanımlama grubu tek bir değer olabilir. Tek bir alanı bir ad verin, ancak diğer alanlar aynı durumda adlı olsa bile isteğe bağlı adıdır.

Ayrılmış birleşimler için erişilebilirlik varsayılanları `public`.

Örneğin, bir şekil türü aşağıdaki bildirimi göz önünde bulundurun.

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

Önceki kod ayrılmış birleşim herhangi üç durumda değerlere sahip olabilir şekli bildirir: dikdörtgen, daire ve Prizma. Her durumda, farklı bir alan kümesi vardır. Durumda olması adlı iki dikdörtgen alanları, her iki tür `float`, adları genişlik ve uzunluk sahip. Yalnızca bir adlandırılmış alan daire durumda olması RADIUS. Üç alanları Prizma durumu olan alanları adlı iki hangi (genişlik ve yükseklik). Adlandırılmamış alanları anonim alanlar olarak adlandırılır.

Aşağıdaki örnekler göre adlandırılmış ve anonim alanların değerlerini sağlayarak nesneleri oluşturur.

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

Bu kod başlatma adlandırılmış alanları ya da kullanabilirsiniz, veya sırasını bildiriminde alanlarının kullanır ve yalnızca değerleri için her bir alan sırayla belirtin gösterir. İçin oluşturucu çağrısı `rect` önceki kodda adlandırılmış alanlar, ancak Oluşturucusu çağrısı için kullandığı `circ` sıralama kullanır. Sıralı alanları karıştırabilirsiniz ve yapımı olduğu gibi alanları adlı `prism`.

`option` Basit bir ayrılmış birleşim F # core kitaplık içinde türüdür. `option` Türü gibi bildirilmedi.

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

Önceki kod belirleyen türü `Option` iki durumda sahip ayrılmış bir birleşimdir `Some` ve `None`. `Some` Durumu, türü tür parametresi tarafından gösterilen bir anonim alanından oluşur ilişkili bir değere sahip `'a`. `None` Durumda olması ilişkili değer. Bu nedenle `option` ya da bazı türü veya herhangi bir değer değerine sahip genel bir tür türünü belirtir. Türü `Option` ayrıca bir küçük harf türü diğer adı olan `option`, yani daha sık kullanılan.

Servis talebi tanımlayıcıları oluşturucular ayrılmış birleşim türü için kullanılabilir. Örneğin, aşağıdaki kod değerlerini oluşturmak için kullanılan `option` türü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

Servis talebi tanımlayıcıları da eşleşen modelinde kullanılır. İfade ile eşleşen bir deseni tanımlayıcıları tek tek durumları ile ilişkili değerleri için sağlanır. Örneğin, aşağıdaki kodda, `x` tanımlayıcısı ile ilişkili değer verilen `Some` durumu `option` türü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

Eşleşen desende adlandırılmış alanlar ayrılmış birleşim eşleşmeleri belirtmek için kullanabilirsiniz. Alanların değerlerini ayıklamak için aşağıdaki kodda gösterildiği gibi daha önce bildirildi Şekil türü için adlandırılmış alanlar kullanabilirsiniz.

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

Normalde, servis talebi tanımlayıcıları UNION adıyla niteleme olmadan kullanılabilir. Her zaman UNION adıyla nitelendirilmesi adı istiyorsanız uygulayabilirsiniz [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliğin birleşim türü tanımı.

### <a name="unwrapping-discriminated-unions"></a>Açma ayrılmış birleşimler

F # ayrılmış birleşimler genellikle etki alanı-modelleme tek bir türü kaydırma için kullanılır. Desen eşleştirme de aracılığıyla alttaki değerini ayıklayın kolaydır. Bir eşleşme ifadesi için tek bir kasada kullanmanız gerekmez:
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

Aşağıdaki örnekte bu gösterir:

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a>Yapı birleşimler

F # 4.1 ile başlayarak, ayrılmış birleşimler yapılar da gösterebilir.  Bu gerçekleştirilir `[<Struct>]` özniteliği.

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

Bu değer türleri ve başvuru türlerini değil çünkü vardır ek başvuru ile karşılaştırıldığında konuları ayrılmış birleşimler:

1. Bunlar, değer türleri kopyalanır ve değer türü anlamları vardır.
2. Bir özyinelemeli tür tanımı multicase yapı Discriminated birleşimi ile kullanamazsınız.
3. Multicase yapı Discriminated birleşimi benzersiz servis talebi adlar sağlamanız gerekir.

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a>Ayrılmış birleşimler yerine nesne hiyerarşileri kullanma
Küçük nesne hiyerarşisi daha basit bir alternatif olarak, ayrılmış bir birleşim genellikle kullanabilirsiniz. Örneğin, aşağıdaki ayrılmış birleşim yerine kullanılabilecek bir `Shape` temel daire, türlerinde türetilmiş kare, vb. sınıfı.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

Bunun yerine bir alanı veya çevre hesaplamak için sanal yöntemi gibi nesne yönelimli uygulama kullanır, bu miktarlar işlem için uygun formüller dala eşleşen kalıbı kullanabilirsiniz. Aşağıdaki örnekte, farklı formüller şekli bağlı olarak alan hesaplamak için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

Çıktı aşağıdaki gibidir:

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a>Ayrılmış birleşimler ağaç veri yapıları için kullanma
Ayrılmış birleşimler birleşim türünde bir veya daha fazla örneklerinin eklenebilir anlamı özyinelemeli olabilir. Özyinelemeli ayrılmış birleşimler programlama dilleri, model ifadeleri için kullanılan ağaç yapıları oluşturmak için kullanılabilir. Aşağıdaki kodda bir özyinelemeli ayrılmış birleşim bir ikili ağacı veri yapısı oluşturmak için kullanılır. İki örneklerini UNION oluşur `Node`, bir tamsayı değeri ve sol ve sağ alt ağaçta, bir düğümü olduğu ve `Tip`, ağaç sonlandırır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

Önceki kod `resultSumTree` 10 değerine sahiptir. Aşağıdaki çizim için ağaç yapısını gösterir `myTree`.

![MyTree için ağaç yapısı](../media/TreeStructureDiagram.png)

Ayrılmış birleşimler ağacında düğümlerin heterojen iyi çalışır. Aşağıdaki kodda, türü `Expression` eklenmesini destekler basit bir programlama dili ifade soyut söz dizimi ağaç ve çarpma numaraları ve değişkenlerin temsil eder. Birleşim durumları bazıları özyinelemeli olmayan ve her iki sayılar temsil eder (`Number`) veya değişkenleri (`Variable`). Diğer durumlarda özyinelemeli ve işlemleri temsil eder (`Add` ve `Multiply`), işlenen ifadeler de nerede. `Evaluate` İşlevi bir eşleşme ifadesi özyinelemeli olarak işlem sözdizimi ağacı için kullanır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

Bu kod, ne zaman yürütülür, değeri `result` 5'tir.

## <a name="common-attributes"></a>Ortak Öznitelikler

Aşağıdaki öznitelikler içinde ayrılmış birleşimler sık görülür:

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* `[Struct]` (F # 4.1 ve üzeri)

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)
