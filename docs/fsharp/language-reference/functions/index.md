---
title: İşlevler (F#)
description: 'F # ve nasıl F # ortak işlevsel programlama yapılarını destekler işlevleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: c96dddb07ca671a9e823fb25f6f6c3788fe32fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566411"
---
# <a name="functions"></a>İşlevler

Temel birim herhangi bir programlama dili program yürütme işlevlerdir. Diğer diller olduğu gibi bir F # işlevi bir ada sahip, parametreler ve bağımsız değişkenler Al olabilir ve gövde sahiptir. F # ayrıca değerleri olarak işlevler değerlendirmesini gibi işlevsel programlama yapıları adlandırılmamış işlevler ifadelerde, yeni işlevler, curried işlevleri ve kısmi yapmamanız işlevlerin örtük tanımı oluşturmak için işlevlerin oluşturulması kullanılmasını destekler işlev bağımsız değişkenleri uygulama.

İşlevleri kullanarak tanımladığınız `let` anahtar sözcüğü veya işlev özyinelemeli ise `let rec` anahtar sözcüğü birleşimi.


## <a name="syntax"></a>Sözdizimi

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Açıklamalar
*İşlev adı* işlevi temsil eden bir tanımlayıcıdır. *Parametre listesi* boşluklarla ayırarak art arda parametreleri oluşur. Parametreler bölümünde açıklandığı gibi her parametre için bir açık tür belirtebilirsiniz. Belirli bir bağımsız değişken türü belirtmezseniz, derleyici işlev gövdesi türünden Infer dener. *İşlev gövdesi* bir ifadenin oluşur. İşlev gövdesi yapan genellikle dönen değer son bir ifadede culminate ifadeleri sayısı oluşan bileşik bir ifade ifadesidir. *Dönüş türü* türüne göre üste ve isteğe bağlıdır. Dönüş değeri türünü açıkça belirtmezseniz derleyici son deyim dönüş türü belirler.

Basit işlev tanımı aşağıdakine benzer:

```fsharp
let f x = x + 1
```

Önceki örnekte işlevi adıdır `f`, bağımsız değişken `x`, türüne sahip `int`, işlev gövdesi `x + 1`, ve dönüş değeri türü `int`.

İşlevler işaretlenir `inline`. Hakkında bilgi için `inline`, bkz: [satır içi işlevler](../functions/inline-functions.md).


## <a name="scope"></a>Kapsam
Tüm modül kapsamı dışında kapsam düzeyinde, bir değer veya işlev adı yeniden kullanmak için bir hata değildir. Bir ad yeniden kullanırsanız, daha sonra bildirilen ad daha önce bildirilen ad shadows. Ancak, bir modüldeki en üst düzey kapsamında adlarının benzersiz olması gerekir. Örneğin, aşağıdaki kod modülü kapsamda göründüğünde, ancak bir işlev içinde görüntülendiğinde değil, bir hata üretir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ancak herhangi bir kapsam düzeyinde aşağıdaki kodu kabul edilebilir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]
    
#### <a name="parameters"></a>Parametreler
Parametre adları sonra işlevi adı listelenir. Aşağıdaki örnekte gösterildiği gibi bir parametrenin türünü belirtebilirsiniz:

```fsharp
let f (x : int) = x + 1
```

Bir tür belirtirseniz, parametrenin adı izler ve adından virgülle ayrılmış. Parametresinin türü atlarsanız, parametre türü derleyici tarafından algılanır. Örneğin, aşağıdaki işlev tanımında, bağımsız değişkeni `x` türünde olması olayla `int` 1 türünde olduğundan `int`.

```fsharp
let f x = x + 1
```

Ancak, derleyici işlevi olabildiğince genel kurmayı dener. Örneğin, aşağıdaki kodu not edin:

```fsharp
let f x = (x, x)
```

İşlev herhangi bir türde bir bağımsız değişkende bir tanımlama grubu oluşturur. Türü belirtilmediğinden, bu işlev ile herhangi bir bağımsız değişken türü kullanılır. Daha fazla bilgi için bkz: [otomatik Genelleştirme](../generics/automatic-generalization.md).


## <a name="function-bodies"></a>İşlev Gövdeleri
İşlev gövdesi, yerel değişkenleri ve işlevleri tanımları içerebilir. Bu tür değişkenleri ve işlevleri gövdesi geçerli işlevi dışında bu kapsamda ' dir. Basit sözdizimi seçeneği etkin olduğunda, aşağıdaki örnekte gösterildiği gibi bir tanımı bir işlev gövdesine olduğunu belirtmek için girinti kullanmanız gerekir:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Daha fazla bilgi için bkz: [kod biçimlendirme yönergeleri](../code-formatting-guidelines.md) ve [ayrıntılı sözdizimi](../verbose-syntax.md).


## <a name="return-values"></a>Dönüş Değerleri
Derleyici son deyim dönüş değeri ve türü belirlemek için bir işlev gövdesine kullanır. Derleyici önceki ifadeleri son ifadesinden türünü Infer. İşlevinde `cylinderVolume`türünü önceki bölümde gösterilen `pi` sabit türünden belirlenir `3.14159` olmasını `float`. Derleyici türünü kullanan `pi` ifade türünü belirlemek için `h * pi * r * r` olmasını `float`. Bu nedenle, işlevinin genel dönüş türü olan `float`.

Dönüş değeri açıkça belirtmek için bir kod aşağıdaki gibi yazın:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Kod yukarıda yazıldığı şekilde derleyici geçerlidir **float** de parametre türleri uygulamak ortalama, tüm işleve; aşağıdaki kodu kullanın:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>İşlev Çağırma
İşlev adı bir boşluk bırakarak ve boşluklarla ayırarak sonra herhangi bir bağımsız değişken belirterek işlevlerini çağırın. Örneğin, bir işlevi çağırmak için **cylinderVolume** ve sonuç değeri atayın **sesi**, aşağıdaki kodu yazın:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Bağımsız Değişkenlerin Kısmi Uygulanması
Belirtilen bağımsız değişkenler sayısından az sağlarsanız, kalan bağımsız değişkenleri bekler yeni bir işlev oluşturun. Bu yöntem bağımsız değişkenleri işleme olarak adlandırılır *currying* ve F # işlevsel programlama dilleri özelliğidir. Örneğin, iki kanal boyutlarıyla çalıştığınız varsayalım: bir yarıçapı varsa **2.0** ve diğer bir yarıçapı sahip **3.0**. Kanal hacmi gibi belirlemek işlevleri oluşturabilirsiniz:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Ardından, çeşitli iki farklı boyutlarda kanal uzunluk için gerektiğinde ek bağımsız değişken sağlayın:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]
    
## <a name="recursive-functions"></a>Özyinelemeli İşlevler
*Özyinelemeli işlevler* kendisini çağıran işlev. Bunlar, belirttiğiniz gerektirir **rec** anahtar sözcüğünü aşağıdaki **izin** anahtar sözcüğü. Hiçbir işlev çağrısı çağırma işlevinin gövdesi içinde özyinelemeli işlevinden çağırır. Aşağıdaki özyinelemeli işlev hesaplar *n*th Fibonacci numarası. Fibonacci numarası dizisi antiquity bu yana bilinen ve her ardışık sayı dizisinin önceki iki sayı toplamı olacak bir dizidir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Bazı özyinelemeli işlevler program yığın taşması olabilir ya da bunları Bakım ve accumulators ve devamlılıklar kullanımı gibi özel teknikleri hakkında farkındalık ile yazdığınız değil inefficiently gerçekleştirin.


## <a name="function-values"></a>İşlev Değerleri
F #'ta tüm işlevleri değerleri olarak kabul edilir; olarak aslında, bilinen *işlev değerleri*. İşlevleri değerleri olduğundan, bunlar diğer işlevleri veya diğer bağlamlarda bağımsız değişken değerleri kullanıldığı kullanılabilir. Bağımsız değişken olarak bir işlev değer isteyen bir işlevi örneği aşağıdadır:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Kullanarak bir işlev değer türü belirtmek `->` belirteci. Bu belirteç sol tarafındaki bağımsız değişken türü, ve sağ tarafta dönüş değeri. Önceki örnekte, `apply1` bir işlev alır bir işlevi olduğunu `transform` bir bağımsız değişken olarak burada `transform` tamsayı alan ve başka bir tamsayı döndüren bir işlev değil. Aşağıdaki kodu nasıl kullanılacağını gösterir `apply1`:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Değeri `result` önceki kod çalıştıktan sonra 101 olacaktır.

Birden çok bağımsız değişkenleri art arda tarafından ayrılmış olan `->` belirteçler, aşağıdaki örnekte gösterildiği gibi:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

200 sonucudur.


## <a name="lambda-expressions"></a>Lambda İfadeleri
A *lambda ifadesi* adlandırılmamış bir işlevdir. Önceki örneklerde işlevleri adlı tanımlama yerine **artırma** ve **mul**, lambda ifadeleri şu şekilde kullanabilirsiniz:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Lambda ifadeleri kullanarak tanımladığınız `fun` anahtar sözcüğü. Lambda ifadesi, yerine dışında bir işlev tanımı benzer `=` belirteç, `->` belirteci bağımsız değişken listesi işlevi gövdesinden ayırmak için kullanılır. Normal işlev tanımı olduğu gibi bağımsız değişken türleri yapılandırılacağını veya açıkça belirtilen ve lambda ifadesi dönüş türü gövdesi son ifadesinde tür çıkarımı yapılan. Daha fazla bilgi için bkz: [Lambda ifadeleri: `fun` anahtar sözcüğü](../functions/lambda-expressions-the-fun-keyword.md).


## <a name="function-composition-and-pipelining"></a>İşlev Bileşimi ve Ardışık Düzen Oluşturma
F # işlevleri diğer işlevleri birleştirilebilir. İki işlevlerin oluşturulması **function1** ve **function2** , uygulamanın gösteren başka bir işlevi olan **function1** Uygulamaveardından**function2**:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

202 sonucudur.

Art arda işlemleri olarak birbirine zincirlenmesi için ardışık düzen etkinleştirir işlevi çağırır. Works gibi ardışık düzen oluşturma:

```fsharp
let result = 100 |> function1 |> function2
```

Yeniden 202 sonucudur.

Birleşim operatörleri iki işlevleri alır ve bir işlev döndürür; Bunun aksine, ardışık düzen operatörleri bir işlev ve bağımsız değişken alır ve bir değer döndürür. Aşağıdaki kod örneğinde işlevi imzalar ve kullanım farklılıkları göstererek ardışık düzen ve birleşim işleçleri arasındaki farkı gösterir.

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
Bir tür ancak değil işlevleri yöntemlerini aşırı yüklenebilir. Daha fazla bilgi için bkz: [yöntemleri](../members/methods.md).


## <a name="see-also"></a>Ayrıca Bkz.
[Değerler](../values/index.md)

[F# Dili Başvurusu](../index.md)
