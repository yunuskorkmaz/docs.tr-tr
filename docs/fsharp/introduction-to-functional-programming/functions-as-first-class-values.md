---
title: İlk Sınıf Değerleri Olarak İşlevler (F#)
description: 'İşlevler F # programlama dilinin birinci sınıf durumuna nasıl yükseltilir öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 45b65ab2454a592d38c80fd367e7243635614727
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586902"
---
# <a name="functions-as-first-class-values"></a>İlk Sınıf Değerleri Olarak İşlevler

Bir tanımlama işlevsel programlama dilleri, birinci sınıf durum işlevlerin özelliğidir. Bir işlev ile ne olursa olsun, diğer yerleşik türlerin değerlerle yapın ve bunu karşılaştırılabilir düzeyde çaba yapabilmek yapmak.

Birinci sınıf durumunu tipik ölçüler şunları içerir:

- İşlev tanımlayıcıları için bağlayabilirsiniz? Diğer bir deyişle, bunları adlar verebilir misiniz?

- Bir liste gibi veri yapıları işlevlerde depolayabilir miyim?

- Bir işlev çağrısında bağımsız değişken olarak bir işlev geçirebilirsiniz?

- Bir işlev çağrısında bir işlev iade edebilir miyim?

Son iki ölçü olarak bilinen ne tanımlamak *daha yüksek sıralı işlemler* veya *daha yüksek sıralı işlev*. Daha yüksek sıralı işlev, işlev bağımsız değişkenleri olarak kabul edin ve İşlevler işlev çağrılarının değeri olarak döndürür. Bu işlemleri gibi kavramanızı işlevleri ve işlevlerin oluşturulması eşleme olarak işlevsel programlama desteği.

## <a name="give-the-value-a-name"></a>Değer bir ad verin

Birinci sınıf bir değer bir işlev ise tam sayılar, dizeler ve diğer yerleşik türler yalnızca ad verebilirsiniz, bunu adlandırın mümkün olması gerekir. Bu tanımlayıcının bağlama için bir değer olarak fonksiyonel programlama belgeleri olarak adlandırılır. F # kullandığı [ `let` bağlamaları](../language-reference/functions/let-bindings.md) değerlere adları bağlamak için: `let <identifier> = <value>`. Aşağıdaki kod, iki örnek gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Bir işlev gibi kolayca yeniden adlandırabilirsiniz. Aşağıdaki örnek adlı bir işlev tanımlar `squareIt` tanımlayıcı bağlayarak `squareIt` için [lambda ifadesi](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. İşlev `squareIt` bir parametresi vardır `n`, ve bu parametre karesini döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F # aşağıdakileri sağlar daha az yazarak ile aynı sonucu elde etmek için daha kısa bir söz dizimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

İlk stili, genellikle aşağıdaki örneklerde kullanın `let <function-name> = <lambda-expression>`işlevlerin bildirimini ve diğer değer türleri bildirimi arasındaki benzerlikler vurgulamak için. Bununla birlikte, adlandırılan işlevlerin kısa sözdizimi ile yazılabilir. Bazı örnekler, her iki yolla da yazılır.

## <a name="store-the-value-in-a-data-structure"></a>Bir veri yapısı değer Store

Birinci sınıf bir değer veri yapısı içinde depolanabilir. Aşağıdaki kod, listeler ve dizilerde değerler depolayan örnekleri gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Bir grup içinde depolanmış bir işlev adı, bir işleve aslında değerlendirildiğini doğrulamak için aşağıdaki örnekte `fst` ve `snd` işleçleri tanımlama grubundan birinci ve ikinci öğeleri ayıklanacak `funAndArgTuple`. Dizideki ilk öğe `squareIt` ve ikinci öğe `num`. Tanımlayıcı `num` tamsayıya 10, geçerli bir bağımsız değişken için bir önceki örnekte bağlı `squareIt` işlevi. İkinci ifade düzenindeki ikinci öğe dizideki ilk öğe uygular: `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Benzer şekilde, tanımlayıcı olarak yalnızca `num` ve tamsayı 10 kullanılabileceğinden, bu nedenle tanımlayıcısı için `squareIt` ve lambda ifadesi `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Değeri bağımsız değişken olarak geçirin

Değer bir dilde birinci sınıf bir durum varsa, bir işleve bağımsız değişken olarak geçirebilirsiniz. Örneğin, tamsayılar ve dizelerin bağımsız değişken olarak geçirmek için yaygındır. Aşağıdaki kod, tamsayı ve F # bağımsız değişken olarak geçirilen dizeler gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

İşlevler, birinci sınıf bir durum varsa, bunları bağımsız değişken olarak aynı şekilde geçirebilmek için olmalıdır. Bu daha yüksek sıralı işlev ilk özelliği olduğunu unutmayın.

Aşağıdaki örnekte, işlev `applyIt` iki parametreye sahip `op` ve `arg`. Bir parametre için olan bir işlev gönderme `op` ve uygun bir bağımsız değişken işleve `arg`, işlevin sonucu döndürür `op` için `arg`. Aşağıdaki örnekte, işlev bağımsız değişkeni hem tamsayı bağımsız değişkeni aynı şekilde, adları kullanılarak gönderilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

Bir işlev, başka bir işleve bağımsız değişken olarak gönderme olanağı, map veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlama vurgular. Bir harita, örneğin, bir listeyi gözden geçirip, her öğe için bir şey yapın ve ardından sonuçların listesini döndürür işlevleri tarafından paylaşılan hesaplama yakalayan bir yüksek sıralı işlev işlemdir. Tamsayı, listedeki her öğe artırmak veya her öğe kare veya dizelerinin listesini her öğe büyük harfe değiştirmek isteyebilirsiniz. Hesaplama hataya parçası listesi üzerinden yinelenen işlemidir ve döndürülecek sonuçları bir liste oluşturur. Bu bölüm, eşleme işlevinde yakalanır. Belirli bir uygulama için yazmanız şey, tek tek her liste öğesine uygulamak istediğiniz işlevi (ekleyerek, karesini, değiştirme). İşlevi gibi bir eşleme işlevi için bağımsız değişken olarak gönderilir `squareIt` gönderilen `applyIt` önceki örnekte.

F # dahil olmak üzere çoğu koleksiyon türü için eşleme yöntemlerini sağlar [listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md), ve [dizileri](../language-reference/sequences.md). Aşağıdaki örnekler listeleri kullanın. Söz dizimi `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Daha fazla bilgi için [listeler](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Bir işlev çağrısında dönüş değeri

Bir işlev bir dilde birinci sınıf bir durum varsa, tamsayılar ve dizelerin gibi diğer türleri, iade yalnızca son olarak, bir işlev çağrısı, değeri olarak geri olması gerekir.

Aşağıdaki işlev çağrıları, tamsayı döndüren ve bunları görüntüler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

Aşağıdaki işlev çağrısı, bir dize döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

Aşağıdaki işlev çağrısı, satır içi olarak bildirilen bir Boole değeri döndürür. Görüntülenen değer `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

İşlev dönüş değeri olarak bir işlev çağrısı olanağı, daha yüksek sıralı işlev ikinci özelliğidir. Aşağıdaki örnekte, `checkFor` tek bir bağımsız değişken alan bir işlev olarak tanımlanır `item`ve yeni bir işlev değeri olarak döndürür. Döndürülen işlevi, bağımsız olarak bir liste alır `lst`ve arar `item` içinde `lst`. Varsa `item` işlevi döndürür, varsa `true`. Varsa `item` işlevi döndürür yoksa `false`. Önceki bölümde gösterildiği gibi aşağıdaki kod, sağlanan liste işlevini kullanır. [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), listesinde arama yapın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Aşağıdaki kod `checkFor` listesinde bir bağımsız değişken listesini ve 7 arar alan yeni bir işlev oluşturmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

Aşağıdaki örnekte birinci sınıf işlevler durumunu F # bir işlevi bildirmek için kullanır `compose`, iki işlev bağımsız değişkenleri bir bileşimini döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]

>[!NOTE]
Daha kısa bir sürüm için aşağıdaki "Curried İşlevler" bölümüne bakın

Aşağıdaki kod iki işlev için bağımsız değişken olarak gönderir. `compose`hem aynı türde tek bir bağımsız değişken almakta olan. İki işlev bağımsız değişkenlerinin bir birleşimi olan yeni bir işlev dönüş değeridir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]

>[!NOTE]
F # sağlayan iki işleç `<<` ve `>>`, İşlevler oluşturun. Örneğin, `let squareAndDouble2 = doubleIt << squareIt` eşdeğerdir `let squareAndDouble = compose doubleIt squareIt` önceki örnekte.

Bir işlev çağrısı değeri olarak bir işlev döndürme aşağıdaki örnek, basit bir tahmin etme oyunu oluşturur. Oyun oluşturmak için arama `makeGame` değeriyle birinin tahmin etmesini istediğiniz için gönderilen `target`. İşlev dönüş değeri `makeGame` bir bağımsız değişken (tahmin) alır ve tahmin doğru olup olmadığını bildirir, bir işlevdir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

Aşağıdaki kod çağrıları `makeGame`, değerini göndererek `7` için `target`. Tanımlayıcı `playGame` döndürülen lambda ifadesi ile ilişkili. Bu nedenle, `playGame` değeri bağımsız değişken olarak alan için bir işlev, `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Curried işlevleri

Önceki bölümde yer alan örnekler birçoğu daha kısaca örtük avantajlarından yararlanarak yazılabilir *currying* F # işlev bildirimleri içinde. Currying her biri tek bir parametreye sahip bir dizi katıştırılmış İşlevler, birden fazla parametresi olan bir işlev dönüştüren bir işlemdir. F # içinde birden fazla parametreye sahip işlevler kendiliğinden curried haldedir. Örneğin, `compose` üç parametrelerle aşağıdaki kısa stili gösterildiği gibi önceki bölümden yazılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

Ancak, sonuç bir gösterildiği gibi bir işlevi sırayla bir parametrenin başka bir işlev döndürür. bir parametre olarak döndüren bir parametrenin işlevidir `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

Bu işlev, çeşitli şekillerde erişebilirsiniz. Her biri aşağıdaki örnekler verir ve 18 görüntüler. Değiştirebilirsiniz `compose4` ile `compose4curried` herhangi birinde örnekler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Önce yaptığınız gibi işlev hala çalışır durumda olduğunu doğrulamak için özgün test çalışmalarını yeniden deneyin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]

>[!NOTE]
Parametreleri de tanımlama gruplarına kapsayan tarafından currying kısıtlayabilirsiniz. Daha fazla bilgi için bkz: "Parametre desenleri" [parametreler ve bağımsız değişkenler](../language-reference/parameters-and-arguments.md).

Kullanan daha kısa bir sürümünü yazmanıza aşağıdaki örnek örtük currying `makeGame`. Nasıl ayrıntılarını `makeGame` oluşturur ve döndürür `game` işlevi bu biçimde daha az açık, ancak sonuç aynı olduğunu özgün test çalışmalarını kullanarak doğrulayabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Currying hakkında daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevleri](../language-reference/functions/index.md).

## <a name="identifier-and-function-definition-are-interchangeable"></a>Tanımlayıcı ve işlev tanımı birbirinin yerine kullanılabilir.

Değişken adı `num` önceki örnekleri, tamsayı 10 değerlendirir ve süpriz olduğundan, nerede `num` olan geçerli 10 de geçerlidir. İşlev tanımlayıcıları ve bunların değerlerini true aynıdır: bağlı lambda ifadesi işlevin adını kullanılabilir, her yerde kullanılabilir.

Aşağıdaki örnekte tanımlayan bir `Boolean` çağrılan işlev `isNegative`ve işlevin adını hem de işlev tanımı birbirinin yerine kullanılır. Sonraki üç örnekler tüm geri dönün ve görüntüleme `False`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Bir adım ileri taşımak için değeri yerine, `applyIt` için bağlı `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>İşlevler F birinci sınıf değerler\#

Önceki bölümlerde örneklerde, F # işlevleri ilk sınıf değerleri olarak F # olan ölçütlerini sağladığını göstermektedir:

- Tanımlayıcının bir işlev tanımı bağlayabilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Veri yapısı içinde bir işlev depolayabilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Bir işlev bağımsız değişken olarak geçirebilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Bir işlev bir işlev çağrısı değeri olarak döndürebilir.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

F # hakkında daha fazla bilgi için bkz. [F # dili başvurusu](../language-reference/index.md).

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki kod bu konunun tüm örnekleri içerir.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Listeler](../language-reference/lists.md)
- [Demetler](../language-reference/tuples.md)
- [İşlevler](../language-reference/functions/index.md)
- [`let` Bağlamaları](../language-reference/functions/let-bindings.md)
- [Lambda ifadeleri: `fun` anahtar sözcüğü](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
