---
title: İşlevler
description: İçindeki F# işlevleri hakkında bilgi edinin ve F# ortak fonksiyonel programlama yapılarını nasıl destekler.
ms.date: 05/16/2016
ms.openlocfilehash: 6f65ce692169b71abe8d2eff7ef07b66975d478b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630707"
---
# <a name="functions"></a>İşlevler

İşlevler, herhangi bir programlama dilinde program yürütmenin temel birimidir. Diğer dillerde olduğu gibi, bir F# işlevin adı vardır, parametreleri olabilir ve bağımsız değişkenler alabilir ve bir gövdeye sahip olabilir. F#Ayrıca, işlevleri değer olarak davranma, ifadelerde adlandırılmamış işlevleri kullanma, yeni işlevler, curried işlevleri ve kısmi olarak işlevlerin örtük tanımına göre işlev oluşturma gibi işlev programlama yapılarını destekler. işlev bağımsız değişkenlerinin uygulaması.

İşlevleri `let` anahtar sözcüğünü kullanarak tanımlarsınız veya işlev özyinelemeli `let rec` ise anahtar sözcük birleşimi.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Açıklamalar

*İşlev adı* , işlevini temsil eden bir tanıtıcıdır. *Parametre-listesi* , boşluklarla ayrılmış ardışık parametrelerden oluşur. Parametreler bölümünde açıklandığı gibi her bir parametre için açık bir tür belirtebilirsiniz. Belirli bir bağımsız değişken türü belirtmezseniz, derleyici türü işlev gövdesinden çıkarması için çalışır. *İşlev gövdesi* bir ifadeden oluşur. İşlev gövdesini oluşturan ifade, genellikle dönüş değeri olan bir son ifadede yer alan bir dizi ifadeden oluşan bir bileşik ifadedir. *Dönüş türü* , ardından bir tür ve isteğe bağlıdır. Dönüş değerinin türünü açıkça belirtmezseniz, derleyici son ifadeden dönüş türünü belirler.

Basit bir işlev tanımı aşağıdakine benzer:

```fsharp
let f x = x + 1
```

Önceki örnekte, `f`işlev adı, türü `int`, işlev gövdesi `x + 1`ve dönüş değeri `x`tür `int`olan bağımsız değişkendir.

İşlevler işaretlenebilir `inline`. Hakkında `inline`bilgi için bkz. [satır içi işlevler](../functions/inline-functions.md).

## <a name="scope"></a>Kapsam

Modül kapsamı dışında herhangi bir kapsam düzeyinde bir değer veya işlev adını yeniden kullanmak bir hata değildir. Bir adı yeniden kullanırsanız daha sonra belirtilen ad daha önce belirtilen adı gölgeliyor. Ancak, modüldeki en üst düzey kapsamda adların benzersiz olması gerekir. Örneğin, aşağıdaki kod modül kapsamında göründüğünde bir hata üretir, ancak bir işlev içinde göründüğünde değil:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ancak aşağıdaki kod herhangi bir kapsam düzeyinde kabul edilebilir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Parametreler

Parametrelerin adları, işlev adından sonra listelenir. Bir parametre için aşağıdaki örnekte gösterildiği gibi bir tür belirtebilirsiniz:

```fsharp
let f (x : int) = x + 1
```

Bir tür belirtirseniz, parametrenin adını izler ve iki nokta üst üste ile birbirinden ayrılır. Parametresinin türünü atlarsanız, parametre türü derleyici tarafından algılanır. Örneğin, aşağıdaki işlev tanımında, 1 türünde `x` `int`olduğu için bağımsız değişken türü `int` olarak algılanır.

```fsharp
let f x = x + 1
```

Ancak derleyici, işlevi mümkün olduğunca genel olarak yapmayı dener. Örneğin, aşağıdaki koda göz önünde yer verilmiştir:

```fsharp
let f x = (x, x)
```

İşlevi herhangi bir türden bağımsız değişkenden bir tanımlama grubu oluşturur. Tür belirtilmediğinden, işlev herhangi bir bağımsız değişken türüyle kullanılabilir. Daha fazla bilgi için bkz. [Otomatik Genelleştirme](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>İşlev Gövdeleri

Bir işlev gövdesi, yerel değişkenlerin ve işlevlerin tanımlarını içerebilir. Bu tür değişkenler ve işlevler, geçerli işlevin gövdesinde kapsam içinde ve dışında değil. Hafif sözdizimi seçeneğini etkinleştirdiğinizde, aşağıdaki örnekte gösterildiği gibi bir tanımın bir işlev gövdesinde olduğunu göstermek için girinti kullanmanız gerekir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Daha fazla bilgi için bkz. [kod biçimlendirme yönergeleri](../code-formatting-guidelines.md) ve [ayrıntılı sözdizimi](../verbose-syntax.md).

## <a name="return-values"></a>Dönüş Değerleri

Derleyici, dönüş değerini ve türünü belirleyebilmek için bir işlev gövdesinde son ifadeyi kullanır. Derleyici, önceki ifadelerden son ifadenin türünü çıkarmayabilir. Önceki bölümde gösterilen `cylinderVolume`işlevinde, `pi` türü, sabit değer `3.14159` türünden olacak `float`şekilde belirlenir. Derleyici, kullanılacak `pi` `h * pi * r * r` ifadenin`float`türünü öğrenmek için türünü kullanır. Bu nedenle, işlevinin genel dönüş türü ' dir `float`.

Dönüş değerini açık olarak belirtmek için, kodu aşağıdaki gibi yazın:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Kod yukarıda yazıldığı için, derleyici tüm işleve **float** uygular; parametresi parametre türlerine de uygulamak için aşağıdaki kodu kullanın:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>İşlev Çağırma

İşlev adını ve ardından boşluk ile ayrılmış bağımsız değişkenleri belirterek işlevleri çağırabilirsiniz. Örneğin, **silindir Dervolume** işlevini çağırmak ve sonucu değer **Ses**'e atamak için aşağıdaki kodu yazarsınız:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Bağımsız Değişkenlerin Kısmi Uygulanması

Belirtilen sayıda bağımsız değişkene daha az bir değer sağlarsanız, kalan bağımsız değişkenleri bekleyen yeni bir işlev oluşturursunuz. Bu bağımsız değişken işleme yöntemi, gibi F#işlevsel programlama dillerinin bir özelliğidir ve olarak adlandırılır. Örneğin, iki kanal boyutu ile çalıştığınızı varsayalım: biri **2,0** radius ve diğeri ise **3,0**yarıçapı vardır. Aşağıdaki gibi kanal hacmini tespit eden işlevler oluşturabilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Daha sonra, iki farklı boyuttan oluşan çeşitli uzunluklar için gereken ek bağımsız değişkeni sağlamanız gerekir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Özyinelemeli İşlevler

*Özyinelemeli işlevler* kendilerini çağıran işlevlerdir. **Let** anahtar sözcüğünü takip eden **REC** anahtar sözcüğünü belirtmenizi gerektirir. Herhangi bir işlev çağrısını çağırırın olduğu gibi, işlev gövdesinin içinden özyinelemeli işlevi çağırın. Aşağıdaki özyinelemeli işlev *n*<sup>.</sup> fibonaccı numarasını hesaplar. Fibonaccı numara sırası, Antiquity 'in bilindiği ve ardışık her sayının dizideki önceki iki sayının toplamı olduğu bir sıralamadır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Bazı Özyinelemeli işlevler program yığınını taşımayabilir veya işlevindeki biriktiricileri ve devamlılık kullanımı gibi özel tekniklerin farkında olmak üzere, bunları dikkatli bir şekilde yazmayabilir.

## <a name="function-values"></a>İşlev Değerleri

' F#De, tüm işlevler değer olarak değerlendirilir; Aslında, *işlev değerleri*olarak bilinir. İşlevler değerler olduğundan, diğer işlevlerde veya değerlerin kullanıldığı diğer bağlamlarda bağımsız değişkenler olarak kullanılabilirler. Bağımsız değişken olarak bir işlev değeri alan bir işlev örneği aşağıda verilmiştir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

`->` Belirteç kullanarak bir işlev değerinin türünü belirtirsiniz. Bu belirtecin sol tarafında, bağımsız değişkenin türü ve sağ tarafta ise dönüş değeri bulunur. Önceki örnekte, `apply1` bir işlevi `transform` bağımsız değişken `transform` olarak alan ve bir tamsayı alan ve başka bir tamsayı döndüren bir işlevdir. Aşağıdaki kod, nasıl `apply1`kullanılacağını gösterir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Değeri `result` , önceki kod çalıştıktan sonra 101 olacaktır.

Aşağıdaki örnekte gösterildiği gibi, birden `->` çok bağımsız değişken birbirini izleyen belirteçlerle ayrılır:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Sonuç 200 ' dir.

## <a name="lambda-expressions"></a>Lambda İfadeleri

*Lambda ifadesi* adlandırılmamış bir işlevdir. Önceki örneklerde, adlandırılmış işlevleri **artırma** ve **MUL**tanımlamak yerine Lambda ifadelerini aşağıdaki şekilde kullanabilirsiniz:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Lambda ifadelerini, `fun` anahtar sözcüğünü kullanarak tanımlarsınız. Lambda ifadesi bir işlev tanımına benzer, `=` belirteç `->` yerine belirtecin bağımsız değişken listesini işlev gövdesinden ayırmak için kullanılır. Normal bir işlev tanımında olduğu gibi, bağımsız değişken türleri açıkça çıkarsanamıyor veya belirlenebilir ve lambda ifadesinin dönüş türü, gövdedeki son ifadenin türünden çıkarsanamıyor. Daha fazla bilgi için bkz [. Lambda ifadeleri: `fun` Anahtar sözcüğü](../functions/lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>İşlev Bileşimi ve Ardışık Düzen Oluşturma

İçindeki F# işlevler diğer işlevlerden oluşabilir. İki işlev **işlev1** ve **function2** bileşimi, **işlev1** uygulamasının **function2**uygulamasını temsil eden başka bir işlevdir:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Sonuç 202 ' dir.

Ardışık düzen oluşturma, işlev çağrılarının ardışık işlemler olarak birlikte zincirde olmasını sağlar. Ardışık düzen oluşturma aşağıdaki gibi çalışmaktadır:

```fsharp
let result = 100 |> function1 |> function2
```

Sonuç yeniden 202 ' dir.

Kompozisyon işleçleri iki işlev alır ve bir işlev döndürür; Buna karşılık, işlem hattı işleçleri bir işlevi ve bir bağımsız değişkeni alır ve bir değer döndürür. Aşağıdaki kod örneği, işlev imzalarındaki ve kullanımındaki farklılıkları göstererek işlem hattı ve bileşim işleçleri arasındaki farkı gösterir.

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a>Aşırı Yükleme İşlevleri

Bir türün yöntemlerini aşırı yükleyebilirsiniz ancak işlevleri kullanamazsınız. Daha fazla bilgi için bkz. [Yöntemler](../members/methods.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Değerler](../values/index.md)
- [F# Dili Başvurusu](../index.md)
