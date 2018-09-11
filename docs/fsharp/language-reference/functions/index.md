---
title: İşlevler (F#)
description: 'F # ve nasıl F # ortak fonksiyonel programlama yapılarını destekler işlevleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 717eba7e69398048d229173e07ccc376797171bb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262171"
---
# <a name="functions"></a>İşlevler

Tüm programlama dillerinde program yürütmenin temel birimi işlevlerdir. F # işlevi bir ada sahip diğer dillerde olduğu gibi parametreleri ve sınav zamanı bağımsız değişkenleri olabilir ve bir gövdeye sahip. F # ayrıca değerlere işlevler değerlendirmesini gibi fonksiyonel programlama yapıları adlandırılmamış işlevler ifadelerde örtülü bir tanım kısmi yoluyla işlevlerin yeni işlevleri ve curried işlevleri oluşturmak üzere işlevlerin oluşturulması kullanılmasını destekler işlev bağımsız değişkenleri uygulama.

İşlevleri kullanarak tanımladığınız `let` anahtar sözcüğü veya işlev özyinelemeli ise `let rec` anahtar sözcüğü birleşimi.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Açıklamalar

*İşlevi adı* işlevi temsil eden bir tanımlayıcıdır. *Parametre-listesi* boşluklarla ayırarak art arda gelen parametreleri oluşur. Parametreler bölümünde açıklandığı gibi her parametre için açık bir tür belirtebilirsiniz. Belirli bir bağımsız değişken türü belirtmezseniz derleyici işlev gövdesi türünü çıkarsamak çalışır. *İşlev gövdesi* bir ifade içerir. İşlev gövdesi yapar genellikle dönüş değeri son bir ifadede sizin ifadeler bir dizi oluşan bileşik bir ifade deyimidir. *Dönüş türü* bir tür tarafından sonuna bir virgül ve isteğe bağlıdır. Derleyici, dönüş değeri türünü açıkça belirtmezseniz son deyim dönüş türünden belirler.

Basit bir işlev tanımı şuna benzer:

```fsharp
let f x = x + 1
```

Önceki örnekte, işlev adıdır `f`, bağımsız değişken `x`, türüne sahip `int`, işlev gövdesidir `x + 1`, ve dönüş değeri türünde `int`.

İşlevleri işaretlenebilir `inline`. Hakkında bilgi için `inline`, bkz: [satır içi işlevleri](../functions/inline-functions.md).

## <a name="scope"></a>Kapsam

Hiçbir modül kapsamı dışında kapsam düzeyinde, bir değer veya işlev adı yeniden kullanmak için bir hata değil. Daha sonra bildirilen ad, bir adı yeniden kullanırsanız, daha önce bildirilen ad gölgeliyor. Ancak, Modül içindeki en üst düzey kapsamında adları benzersiz olmalıdır. Örneğin, aşağıdaki kodu, modül kapsamda göründüğünde, ancak bir işlev içinde görünür olmayan bir hata oluşturur:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ancak, aşağıdaki kod kapsamı herhangi bir düzeyde kabul edilebilir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Parametreler

İşlev adından sonra parametrelerinin adları listelenmektedir. Aşağıdaki örnekte gösterildiği gibi bir parametrenin türünü belirtebilirsiniz:

```fsharp
let f (x : int) = x + 1
```

Bir tür belirtirseniz, parametre adı ve adından virgül ile ayrılır. Parametre türü, tür parametresi için atlarsanız, derleyici tarafından algılanır. Örneğin, aşağıdaki işlev tanımında, bağımsız değişken `x` türünde olmasını çıkarılan `int` 1 türünde olduğu için `int`.

```fsharp
let f x = x + 1
```

Ancak, derleyici işlev olarak genel yap dener. Örneğin, aşağıdaki kod dikkat edin:

```fsharp
let f x = (x, x)
```

İşlevi, herhangi bir türde bir bağımsız değişkeninden bir tanımlama grubu oluşturur. Türü belirtilmediğinden işlevi herhangi bir bağımsız değişken türü ile kullanılabilir. Daha fazla bilgi için [otomatik Genelleştirme](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>İşlev Gövdeleri

Bir işlev gövdesinin yerel değişkenlerin ve işlevlerin tanımlarını içerebilir. Bu değişkenlerin ve işlevlerin dışında ancak geçerli işlevin gövdesinde kapsamına dahildir. Basit sözdizimi seçeneği etkin olduğunda, aşağıdaki örnekte gösterildiği gibi bir tanımı bir işlev gövdesinde olduğunu belirtmek için Girintileme kullanmanız gerekir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Daha fazla bilgi için [kod biçimlendirme yönergeleri](../code-formatting-guidelines.md) ve [ayrıntılı sözdizimi](../verbose-syntax.md).

## <a name="return-values"></a>Dönüş Değerleri

Derleyici dönüş değeri ve türü belirlemek için bir işlev gövdesinde son ifade kullanır. Derleyicinin önceki ifadelerden son ifadesinden türü çıkarsayabilir. İşlevde `cylinderVolume`türünü önceki bölümde gösterildiği `pi` değişmez değer türünden belirlenir `3.14159` olmasını `float`. Derleyici türünü kullanan `pi` ifadenin türü belirlenemiyor `h * pi * r * r` olmasını `float`. Bu nedenle, işlevin genel dönüş türü olan `float`.

Dönüş değeri açıkça belirtmek için bir kod aşağıdaki gibi yazın:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Derleyici kod yukarıda yazıldığı gibi geçerli **float** parametre türleri de uygulamak istediyseniz, tüm işlevin; aşağıdaki kodu kullanın:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>İşlev Çağırma

İşlevler, işlev adının ardından bir boşluk ve boşluklarla ayırarak sonra herhangi bir bağımsız değişkeni belirterek çağırın. Örneğin, işlev çağrısı için **cylinderVolume** ve sonucu değerine atama **sesi**, aşağıdaki kodu yazın:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Bağımsız Değişkenlerin Kısmi Uygulanması

Belirtilen bağımsız değişkenler sayısından daha az sağlarsanız, kalan bağımsız değişken bekler, yeni bir işlev oluşturun. Bu yöntem bağımsız değişkenleri işleme olarak adlandırılır *currying* ve F # gibi fonksiyonel programlama dillerinin bir özelliğidir. Örneğin, kanal iki boyutlarıyla çalıştığınız düşünün: bir yarıçapını varsa **2.0** ve başka bir sahip **3.0**. Kanal hacmi gibi belirlemek işlevleri oluşturabilirsiniz:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Ardından, iki farklı boyutlardaki kanal çeşitli uzunluklarına gerektiği gibi ek bağımsız değişken sağlayın:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Özyinelemeli İşlevler

*Özyinelemeli işlevler* kendisini çağıran işlev. Belirttiğiniz gerektirdikleri **rec** anahtar sözcüğü aşağıdaki **izin** anahtar sözcüğü. Herhangi bir işlev çağrısındaki çağırma işlevinin gövdesi içinde özyinelemeli işlevini çağırın. Aşağıdaki özyinelemeli işlev hesaplar *n*<sup>th</sup> Fibonacci sayı. Fibonacci sayı dizisi antiquity bu yana bilinen ve art arda gelen her bir sayının sıradaki önceki iki sayının toplamı olduğu bir dizidir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Bazı özyinelemeli işlevler program yığın taşması veya bunları dikkatli ve biriktiricileri ve devamlılıklar kullanımı gibi özel teknikleri farkındalıkta yazdığınız değil, verimsiz gerçekleştirin.

## <a name="function-values"></a>İşlev Değerleri

F #'ta tüm işlevleri değerler olarak kabul edilir; olarak aslında, bilinen *işlev değerleri*. İşlevleri değerler olduğundan, diğer işlevlere veya diğer bağlamlarda bağımsız değişkenler olarak değerleri kullanıldığı kullanılabilirler. Bir işlev değeri bağımsız değişken olarak alan bir işlev örneği aşağıdadır:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Bir işlevi değer türü kullanarak belirttiğiniz `->` belirteci. Bu belirteç sol tarafındaki bağımsız değişkenin türü ve sağ tarafta dönüş değeridir. Önceki örnekte, `apply1` bir işlev alır bir işlev, `transform` bir bağımsız değişken olarak nerede `transform` tamsayı alır ve başka bir tamsayı döndüren bir işlev değil. Aşağıdaki kod nasıl kullanılacağını gösterir `apply1`:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Değerini `result` önceki kod çalıştırıldıktan sonra 101 olacaktır.

Birden çok bağımsız değişkeni tarafından art arda ayrılan `->` belirteçleri, aşağıdaki örnekte gösterildiği gibi:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Sonuç 200'dür.

## <a name="lambda-expressions"></a>Lambda İfadeleri

A *lambda ifadesi* adlandırılmamış bir işlevdir. Önceki örneklerde işlevleri adlı tanımlamak yerine **artışı** ve **mul**, lambda ifadeleri şu şekilde kullanabilirsiniz:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Lambda ifadeleri kullanarak tanımladığınız `fun` anahtar sözcüğü. Bir lambda ifadesi yerine tek bir işlev tanımı benzer `=` belirteç `->` belirteci bağımsız değişken listesi işlevi gövdesinden ayırmak için kullanılır. Bir normal işlev tanımı gibi bağımsız değişken türleri çıkarılan veya açıkça belirtilen ve lambda ifadesinin dönüş türü, son ifadesinin gövdesinde türünden algılanır. Daha fazla bilgi için [Lambda ifadeleri: `fun` anahtar sözcüğü](../functions/lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>İşlev Bileşimi ve Ardışık Düzen Oluşturma

F # işlevleri diğer işlevleri oluşabilir. İki işlev bileşimi **işlev1** ve **function2** uygulamayı temsil eden başka bir işlev, **işlev1** uygulamayıveardından**function2**:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

202 sonucudur.

Ardışık Düzen art arda işlemlerin olarak birbirine zincirlenmiş için işlev çağrılarını etkinleştirir. Şu şekilde çalışır ardışık düzen oluşturma:

```fsharp
let result = 100 |> function1 |> function2
```

Sonuç, 202 tekrar edilir.

Birleştirme işleçleri iki işlevler ve bir işlev döndürür. aksine, ardışık düzen operatörleri, bir işlev ve bağımsız değişken alır ve bir değer döndürür. Aşağıdaki kod örneği, kullanım ve işlev imzası farklılıkları göstererek işlem hattı ve birleştirme işleçleri arasındaki farkı gösterir.

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

Bir tür ancak değil işlevler yöntemlerinin aşırı yüklenebilir. Daha fazla bilgi için [yöntemleri](../members/methods.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Değerler](../values/index.md)
- [F# Dili Başvurusu](../index.md)
