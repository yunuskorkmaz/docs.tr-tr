---
title: Birinci sınıf işlevler
description: "Birinci sınıf işlevleri hakkında bilgi edinin ve bunların F # ' ta işlevsel programlama için ne kadar önemli olduğunu öğrenin."
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810917"
---
# <a name="first-class-functions"></a>Birinci sınıf işlevler

İşlevsel programlama dillerinin özelliklerini tanımlama, işlevlerin birinci sınıf durumuna yükseltilmesinin bir özelliğidir. Diğer yerleşik türlerin değerleriyle yapabileceğin bir işlev ile yapabilecekleriniz ve bunu benzer bir ölçüde çaba ile yapabileceksiniz.

Birinci sınıf durumun tipik ölçümleri şunları içerir:

- İşlevleri tanımlayıcılara bağlayabilir miyim? Diğer bir deyişle, bunlara adlar verebilir misiniz?

- İşlevleri bir liste gibi veri yapılarında depolayabilirler mi?

- İşlev çağrısında bir işlevi bağımsız değişken olarak geçirebilir misiniz?

- İşlev çağrısından bir işlev döndürebilir misiniz?

Son iki ölçü, *daha yüksek sıralı işlemler* veya *daha yüksek sıralı işlevler*olarak bilinenleri tanımlar. Daha yüksek sıralı işlevler işlevleri bağımsız değişken olarak kabul eder ve işlev çağrılarının değeri olarak işlevleri döndürür. Bu işlemler, işlevleri eşleme işlevleri ve işlevlerinin oluşturulması gibi işlevsel programlamanın bu şekilde çalışmasını destekler.

## <a name="give-the-value-a-name"></a>Değere bir ad verin

Bir işlev birinci sınıf bir değer ise, tam sayıları, dizeleri ve diğer yerleşik türleri de belirleyebilmeniz gibi, bu değeri de yazmanız gerekir. Bu, bir tanımlayıcıyı bir değere bağlama gibi fonksiyonel programlama belgeleriyle ifade edilir. F # adları değerlere bağlamak için [ `let` bağlamaları](../language-reference/functions/let-bindings.md) kullanır: `let <identifier> = <value>` . Aşağıdaki kodda iki örnek gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

Bir işlevi kolayca kolayca adlandırın. Aşağıdaki örnek, `squareIt` `squareIt` [lambda ifadesine](../language-reference/functions/lambda-expressions-the-fun-keyword.md) tanımlayıcıyı bağlayarak adlı bir işlevi tanımlar `fun n -> n * n` . İşlevin `squareIt` tek bir parametresi vardır, `n` ve bu parametrenin karesini döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

F #, daha az yazma ile aynı sonucu elde etmek için aşağıdaki daha kısa sözdizimi sağlar.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

Genellikle izleyen örnekler, `let <function-name> = <lambda-expression>` işlevlerin bildirimi ve diğer değer türlerinin bildirimi arasındaki benzerlikleri vurgulamak için ilk stili kullanır. Ancak, tüm adlandırılmış işlevler kısa sözdizimi ile de yazılabilir. Örneklerden bazıları her iki şekilde yazılmıştır.

## <a name="store-the-value-in-a-data-structure"></a>Değeri bir veri yapısında depolayın

Birinci sınıf bir değer, bir veri yapısında depolanabilir. Aşağıdaki kod, listelerde ve tanımlama değerlerinde değerleri depolayan örnekleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

Bir kayıt düzeninde depolanan bir işlev adının aslında bir işleve göre değerlendirileceğini doğrulamak için aşağıdaki örnek, `fst` ve `snd` işleçlerini kayıt kümesinden ilk ve ikinci öğeleri ayıklamak için kullanır `funAndArgTuple` . Kayıt düzeni içindeki ilk öğe `squareIt` ve ikinci öğe `num` . Tanımlayıcı, `num` işlev için geçerli bir bağımsız değişken olan tamsayı 10 ' a bir önceki örneğe bağlanır `squareIt` . İkinci ifade, kayıt düzeni içindeki ilk öğeyi demet içindeki ikinci öğeye uygular: `squareIt num` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

Benzer şekilde, tanımlayıcı `num` ve tamsayı 10 ' da birbirinin yerine kullanılabilir, bu nedenle tanımlayıcı `squareIt` ve lambda ifadesi olabilir `fun n -> n * n` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Değeri bağımsız değişken olarak geçirme

Bir değerde bir dilde birinci sınıf durum varsa, bunu bir işleve bağımsız değişken olarak geçirebilirsiniz. Örneğin, tamsayıların ve dizelerin bağımsız değişken olarak iletilmesi yaygındır. Aşağıdaki kod, F # içinde bağımsız değişken olarak geçirilen tamsayıları ve dizeleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

İşlevlerde birinci sınıf durum varsa, bunları aynı şekilde bağımsız değişken olarak geçirebilmelisiniz. Bunun daha yüksek sıralı işlevlerin ilk özelliği olduğunu unutmayın.

Aşağıdaki örnekte, işlevinin `applyIt` iki parametresi vardır `op` `arg` . İçin bir parametresi ve işlevi için uygun bir bağımsız değişken içeren bir işlevde gönderirseniz `op` `arg` , işlevi uygulamanın sonucunu döndürür `op` `arg` . Aşağıdaki örnekte, hem işlev bağımsız değişkeni hem de tamsayı bağımsız değişkeni, adları kullanılarak aynı şekilde gönderilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

Bir işlevi başka bir işleve bağımsız değişken olarak gönderebilme özelliği, eşleme veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlamaları daha da sağlar. Örneğin, bir eşleme işlemi, bir liste içinde görüntülenen işlevler tarafından paylaşılan hesaplamayı yakalayan daha yüksek sıralı bir işlevdir, her öğe için bir şey yapın ve ardından sonuçların bir listesini döndürür. Her bir öğeyi bir tamsayılar listesinde veya her öğenin kare halinde artırmak ya da dizeler listesindeki her öğeyi büyük harfe değiştirmek isteyebilirsiniz. Hesaplamanın hataya açık olan bölümü, listede ilerleyen özyinelemeli işlemdir ve döndürülecek sonuçların bir listesini oluşturur. Bu bölüm, eşleme işlevinde yakalanır. Belirli bir uygulama için yazmanız gereken tek şey, her liste öğesine tek tek uygulamak istediğiniz işlevdir (ekleme, karelerini alıp, değişen Case). Bu işlev, önceki örnekte olduğu gibi, eşleme işlevine bağımsız değişken olarak gönderilir `squareIt` `applyIt` .

F #, [listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md)ve [diziler](../language-reference/sequences.md)dahil olmak üzere çoğu koleksiyon türü için harita yöntemleri sağlar. Aşağıdaki örnekler listeleri kullanır. Söz dizimi `List.map <the function> <the list>` şeklindedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

Daha fazla bilgi için bkz. [listeler](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Işlev çağrısından değeri döndürün

Son olarak, bir işlevde bir dilde birinci sınıf durum varsa, tamsayılar ve dizeler gibi diğer türleri döndürmeniz gibi, bunu bir işlev çağrısının değeri olarak dönebilmelisiniz.

Aşağıdaki işlev çağrıları, tamsayılar döndürür ve görüntüler.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

Aşağıdaki işlev çağrısı bir dize döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

Satır içi olarak belirtilen aşağıdaki işlev çağrısı, bir Boole değeri döndürür. Görünen değer `True` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

İşlev çağrısının değeri olarak bir işlevi döndürme özelliği, daha yüksek sıralı işlevlerin ikinci özelliğidir. Aşağıdaki örnekte, `checkFor` bir bağımsız değişken alan bir işlev `item` olarak tanımlanır ve değeri olarak yeni bir işlev döndürür. Döndürülen işlev, bağımsız değişkeni olarak bir liste alır `lst` ve içinde için arama yapar `item` `lst` . Varsa `item` , işlev döndürür `true` . Yoksa `item` , işlev döndürür `false` . Önceki bölümde olduğu gibi, aşağıdaki kod, listede arama yapmak için [List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists)bir belirtilen List işlevini kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Aşağıdaki kod, `checkFor` bir bağımsız değişkeni, bir listeyi alan ve listede 7 ' yi arayan yeni bir işlev oluşturmak için kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

Aşağıdaki örnek, `compose` iki işlev bağımsız değişkeninin bir oluşumunu döndüren bir işlevi bildirmek Için F # içindeki işlevlerin ilk sınıf durumunu kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> Daha da daha kısa bir sürüm için, "curried Işlevleri" başlıklı bölüme bakın.

Aşağıdaki kod, `compose` her ikisi de aynı türde tek bir bağımsız değişken alacak şekilde iki işlevi bağımsız değişken olarak gönderir. Dönüş değeri, iki işlev bağımsız değişkeninin bileşimi olan yeni bir işlevdir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F # iki işleç sağlar `<<` ve `>>` Bu işlev oluşturma işlevleri. Örneğin, `let squareAndDouble2 = doubleIt << squareIt` önceki örnekteki ile eşdeğerdir `let squareAndDouble = compose doubleIt squareIt` .

İşlev çağrısının değeri olarak bir işlev döndürmesinin aşağıdaki örneği, basit bir tahmin oyunu oluşturur. Bir oyun oluşturmak için, `makeGame` birinin ' de tahmin etmesini istediğiniz değeri çağırın `target` . İşlevden döndürülen değer bir `makeGame` bağımsız değişken (tahmin) alan ve tahminin doğru olup olmadığını raporlayan bir işlevdir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

Aşağıdaki kod çağırır `makeGame` , için değeri gönderiliyor `7` `target` . Tanımlayıcı, `playGame` döndürülen lambda ifadesine bağlanır. Bu nedenle, `playGame` için bir değer bağımsız değişkeni olarak alan bir işlevdir `guess` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Curried Işlevleri

Önceki bölümde yer alan örneklerin birçoğu, F # işlev bildirimlerinde örtülü *currying* özelliğinden yararlanarak daha fazla öz yazılabilir. Currying, birden fazla parametresi olan bir işlevi, her birinin tek bir parametresi olan bir dizi katıştırılmış işlevlere dönüştüren bir işlemdir. F # ' da, birden fazla parametresi olan işlevler kendiliğinden curried ' dir. Örneğin, `compose` önceki bölümden üç parametre ile aşağıdaki kısa stilde gösterildiği gibi yazılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

Ancak sonuç, içinde gösterildiği gibi, bir parametresinin bir işlevini döndüren tek bir parametre işlevi döndüren bir parametre işlevidir `compose4curried` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

Bu işleve çeşitli yollarla erişebilirsiniz. Aşağıdaki örneklerin her biri döndürür ve 18 ' i görüntüler. `compose4`Örneklerden herhangi birinde ile değiştirebilirsiniz `compose4curried` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

İşlevin daha önce olduğu gibi hala çalıştığını doğrulamak için, özgün test çalışmalarını yeniden deneyin.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> Tanımlama grupları içindeki parametreleri kapsayan currying kısıtlayabilirler. Daha fazla bilgi için bkz. [parametrelerde ve bağımsız değişkenlerde](../language-reference/parameters-and-arguments.md)"parametre desenleri".

Aşağıdaki örnek, daha kısa bir sürümünü yazmak için örtülü currying kullanır `makeGame` . Oluşturma `makeGame` ve işlevin nasıl döndürdüğü hakkında ayrıntılar `game` Bu biçimde daha az açık olur, ancak başlangıçtaki test çalışmalarını kullanarak sonucun aynı olduğunu doğrulayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

Currying hakkında daha fazla bilgi için, bkz. [işlevlerde](../language-reference/functions/index.md)"bağımsız değişkenlerin kısmi uygulaması".

## <a name="identifier-and-function-definition-are-interchangeable"></a>Tanımlayıcı ve Işlev tanımı değiştirilebilir

`num`Önceki örneklerde bulunan değişken adı 10 tamsayı olarak değerlendirilir ve bunun `num` geçerli olduğu, 10 ' un da geçerli olduğu bir işlem olmaz. Aynı değer, işlev tanımlayıcılarının ve bunların değerlerinin her yerinde geçerlidir: işlevin adının her yerde kullanılabilmesi için, bağlandığı lambda ifadesi kullanılabilir.

Aşağıdaki örnek `Boolean` adlı bir işlevi tanımlar `isNegative` ve sonra işlevin adını ve yerine işlevin tanımını kullanır. Sonraki üç örnek tüm döndürülür ve görüntülenir `False` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

Bir adım daha devam etmek için, için `applyIt` öğesine bağlanan değeri değiştirin `applyIt` .

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>İşlevler F içindeki Ilk sınıf değerlerdir\#

Önceki bölümlerde yer alan örneklerde, F # içindeki işlevlerin F # ' ta birinci sınıf değerler olması için kriterleri karşılamakta olduğu gösterilmektedir:

- Bir tanımlayıcıyı işlev tanımına bağlayabilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- Bir işlevi bir veri yapısında saklayabilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- Bir işlevi bağımsız değişken olarak geçirebilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- İşlev çağrısının değeri olarak bir işlev döndürebilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

F # hakkında daha fazla bilgi için [f # dil başvurusuna](../language-reference/index.md)bakın.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki kod, bu konudaki tüm örnekleri içerir.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Listeler](../language-reference/lists.md)
- [Tanımlama grupları](../language-reference/tuples.md)
- [İşlevler](../language-reference/functions/index.md)
- [`let` Lara](../language-reference/functions/let-bindings.md)
- [Lambda Ifadeleri: `fun` anahtar sözcüğü](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
