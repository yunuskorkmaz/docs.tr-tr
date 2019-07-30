---
title: Birinci sınıf işlevler
description: Birinci sınıf işlevler ve ' de F#fonksiyonel programlama için nasıl önemli oldukları hakkında bilgi edinin.
ms.date: 10/29/2018
ms.openlocfilehash: 4681d32abd59cc4aade6f4cb2d062e7888bcfbbc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629720"
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

Bir işlev birinci sınıf bir değer ise, tam sayıları, dizeleri ve diğer yerleşik türleri de belirleyebilmeniz gibi, bu değeri de yazmanız gerekir. Bu, bir tanımlayıcıyı bir değere bağlama gibi fonksiyonel programlama belgeleriyle ifade edilir. F#adları değerlere bağlamak için [ `let` bağlamaları](../language-reference/functions/let-bindings.md) kullanır:. `let <identifier> = <value>` Aşağıdaki kodda iki örnek gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

Bir işlevi kolayca kolayca adlandırın. Aşağıdaki örnek, `squareIt` [lambda ifadesine](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`tanımlayıcıyı `squareIt` bağlayarak adlı bir işlevi tanımlar. İşlevin `squareIt` tek bir `n`parametresi vardır, ve bu parametrenin karesini döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

F#daha az yazma ile aynı sonucu elde etmek için aşağıdaki daha kısa sözdizimi sağlar.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

Genellikle izleyen örnekler, işlevlerin bildirimi ve diğer değer türlerinin `let <function-name> = <lambda-expression>`bildirimi arasındaki benzerlikleri vurgulamak için ilk stili kullanır. Ancak, tüm adlandırılmış işlevler kısa sözdizimi ile de yazılabilir. Örneklerden bazıları her iki şekilde yazılmıştır.

## <a name="store-the-value-in-a-data-structure"></a>Değeri bir veri yapısında depolayın

Birinci sınıf bir değer, bir veri yapısında depolanabilir. Aşağıdaki kod, listelerde ve tanımlama değerlerinde değerleri depolayan örnekleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

Bir kayıt düzeninde depolanan bir işlev adının aslında bir işleve göre değerlendirileceğini doğrulamak için aşağıdaki örnek, `fst` ve `snd` işleçlerini kayıt `funAndArgTuple`kümesinden ilk ve ikinci öğeleri ayıklamak için kullanır. Kayıt düzeni `squareIt` içindeki ilk öğe ve ikinci `num`öğe. Tanımlayıcı `num` , `squareIt` işlev için geçerli bir bağımsız değişken olan tamsayı 10 ' a bir önceki örneğe bağlanır. İkinci ifade, kayıt düzeni içindeki ilk öğeyi demet içindeki ikinci öğeye uygular: `squareIt num`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

Benzer şekilde, tanımlayıcı `num` ve tamsayı 10 ' da birbirinin yerine kullanılabilir, bu nedenle tanımlayıcı `squareIt` ve lambda ifadesi `fun n -> n * n`olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a>Değeri bağımsız değişken olarak geçirme

Bir değerde bir dilde birinci sınıf durum varsa, bunu bir işleve bağımsız değişken olarak geçirebilirsiniz. Örneğin, tamsayıların ve dizelerin bağımsız değişken olarak iletilmesi yaygındır. Aşağıdaki kod, içinde F#bağımsız değişken olarak geçirilen tamsayıları ve dizeleri gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

İşlevlerde birinci sınıf durum varsa, bunları aynı şekilde bağımsız değişken olarak geçirebilmelisiniz. Bunun daha yüksek sıralı işlevlerin ilk özelliği olduğunu unutmayın.

Aşağıdaki örnekte, işlevinin `applyIt` iki `op` parametresi `arg`vardır. İçin `op` bir parametresi ve `arg`işlevi için uygun bir bağımsız değişken içeren bir işlevde gönderirseniz, işlevi uygulamanın `op` `arg`sonucunu döndürür. Aşağıdaki örnekte, hem işlev bağımsız değişkeni hem de tamsayı bağımsız değişkeni, adları kullanılarak aynı şekilde gönderilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

Bir işlevi başka bir işleve bağımsız değişken olarak gönderebilme özelliği, eşleme veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlamaları daha da sağlar. Örneğin, bir eşleme işlemi, bir liste içinde görüntülenen işlevler tarafından paylaşılan hesaplamayı yakalayan daha yüksek sıralı bir işlevdir, her öğe için bir şey yapın ve ardından sonuçların bir listesini döndürür. Her bir öğeyi bir tamsayılar listesinde veya her öğenin kare halinde artırmak ya da dizeler listesindeki her öğeyi büyük harfe değiştirmek isteyebilirsiniz. Hesaplamanın hataya açık olan bölümü, listede ilerleyen özyinelemeli işlemdir ve döndürülecek sonuçların bir listesini oluşturur. Bu bölüm, eşleme işlevinde yakalanır. Belirli bir uygulama için yazmanız gereken tek şey, her liste öğesine tek tek uygulamak istediğiniz işlevdir (ekleme, karelerini alıp, değişen Case). Bu işlev, önceki örnekte olduğu gibi `squareIt` `applyIt` , eşleme işlevine bağımsız değişken olarak gönderilir.

F#[listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md)ve [diziler](../language-reference/sequences.md)dahil olmak üzere çoğu koleksiyon türü için eşleme yöntemleri sağlar. Aşağıdaki örnekler listeleri kullanır. Söz dizimi `List.map <the function> <the list>`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

Daha fazla bilgi için bkz. [listeler](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Işlev çağrısından değeri döndürün

Son olarak, bir işlevde bir dilde birinci sınıf durum varsa, tamsayılar ve dizeler gibi diğer türleri döndürmeniz gibi, bunu bir işlev çağrısının değeri olarak dönebilmelisiniz.

Aşağıdaki işlev çağrıları, tamsayılar döndürür ve görüntüler.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

Aşağıdaki işlev çağrısı bir dize döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

Satır içi olarak belirtilen aşağıdaki işlev çağrısı, bir Boole değeri döndürür. Görünen `True`değer.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

İşlev çağrısının değeri olarak bir işlevi döndürme özelliği, daha yüksek sıralı işlevlerin ikinci özelliğidir. Aşağıdaki örnekte, `checkFor` bir `item`bağımsız değişken alan bir işlev olarak tanımlanır ve değeri olarak yeni bir işlev döndürür. Döndürülen işlev, bağımsız değişkeni `lst`olarak bir liste alır ve içinde `lst`için `item` arama yapar. Varsa `item` , işlev döndürür `true`. Yoksa, işlev döndürür `false`. `item` Önceki bölümde olduğu gibi, aşağıdaki kod, listede arama yapmak için [List. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)bir belirtilen List işlevini kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Aşağıdaki kod, bir `checkFor` bağımsız değişkeni, bir listeyi alan ve listede 7 ' yi arayan yeni bir işlev oluşturmak için kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

Aşağıdaki örnek, iki işlev bağımsız değişkeninin bir oluşumunu döndüren bir işlevi F# `compose`bildirmek için içindeki işlevlerin ilk sınıf durumunu kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> Daha da daha kısa bir sürüm için, "curried Işlevleri" başlıklı bölüme bakın.

Aşağıdaki kod, her ikisi de aynı türde tek `compose`bir bağımsız değişken alacak şekilde iki işlevi bağımsız değişken olarak gönderir. Dönüş değeri, iki işlev bağımsız değişkeninin bileşimi olan yeni bir işlevdir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> F#iki işleç `<<` ve `>>`, bu işlev oluşturma işlevleri sağlar. Örneğin, `let squareAndDouble2 = doubleIt << squareIt` önceki örnekteki ile `let squareAndDouble = compose doubleIt squareIt` eşdeğerdir.

İşlev çağrısının değeri olarak bir işlev döndürmesinin aşağıdaki örneği, basit bir tahmin oyunu oluşturur. Bir oyun oluşturmak için, birinin `makeGame` `target`' de tahmin etmesini istediğiniz değeri çağırın. İşlevden `makeGame` döndürülen değer bir bağımsız değişken (tahmin) alan ve tahminin doğru olup olmadığını raporlayan bir işlevdir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

Aşağıdaki kod çağırır `makeGame`, için `target`değeri `7` gönderiliyor. Tanımlayıcı `playGame` , döndürülen lambda ifadesine bağlanır. Bu nedenle `playGame` , için `guess`bir değer bağımsız değişkeni olarak alan bir işlevdir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a>Curried Işlevleri

Önceki bölümde yer alan örneklerin birçoğu, F# işlev bildirimlerinde örtülü *currying* özelliğinden yararlanarak daha fazla öz yazılabilir. Currying, birden fazla parametresi olan bir işlevi, her birinin tek bir parametresi olan bir dizi katıştırılmış işlevlere dönüştüren bir işlemdir. ' F#De, birden fazla parametresi olan işlevler doğal olarak curried ' dir. Örneğin, `compose` önceki bölümden üç parametre ile aşağıdaki kısa stilde gösterildiği gibi yazılabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

Ancak sonuç, içinde `compose4curried`gösterildiği gibi, bir parametresinin bir işlevini döndüren tek bir parametre işlevi döndüren bir parametre işlevidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

Bu işleve çeşitli yollarla erişebilirsiniz. Aşağıdaki örneklerin her biri döndürür ve 18 ' i görüntüler. Örneklerden herhangi birinde `compose4curried`iledeğiştirebilirsiniz . `compose4`

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

İşlevin daha önce olduğu gibi hala çalıştığını doğrulamak için, özgün test çalışmalarını yeniden deneyin.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> Tanımlama grupları içindeki parametreleri kapsayan currying kısıtlayabilirler. Daha fazla bilgi için bkz. [parametrelerde ve bağımsız değişkenlerde](../language-reference/parameters-and-arguments.md)"parametre desenleri".

Aşağıdaki örnek, daha kısa bir sürümünü `makeGame`yazmak için örtülü currying kullanır. Oluşturma ve `game` işlevin nasıl `makeGame` döndürdüğü hakkında ayrıntılar bu biçimde daha az açık olur, ancak başlangıçtaki test çalışmalarını kullanarak sonucun aynı olduğunu doğrulayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

Currying hakkında daha fazla bilgi için, bkz. [işlevlerde](../language-reference/functions/index.md)"bağımsız değişkenlerin kısmi uygulaması".

## <a name="identifier-and-function-definition-are-interchangeable"></a>Tanımlayıcı ve Işlev tanımı değiştirilebilir

Önceki örneklerde bulunan `num` değişken adı 10 tamsayı olarak değerlendirilir ve bunun geçerli olduğu, 10 ' un da geçerli olduğu `num` bir işlem olmaz. Aynı değer, işlev tanımlayıcılarının ve bunların değerlerinin her yerinde geçerlidir: işlevin adının her yerde kullanılabilmesi için, bağlandığı lambda ifadesi kullanılabilir.

Aşağıdaki örnek adlı `Boolean` `isNegative`bir işlevi tanımlar ve sonra işlevin adını ve yerine işlevin tanımını kullanır. Sonraki üç örnek tüm döndürülür ve görüntülenir `False`.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

Bir adım daha devam etmek için, için `applyIt` `applyIt`öğesine bağlanan değeri değiştirin.

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>İşlevler F içindeki Ilk sınıf değerlerdir\#

Önceki bölümlerde yer alan örnekler, ' F# F#deki ilk sınıf değerleri olan ölçütü karşılamakta olan işlevleri göstermektedir:

- Bir tanımlayıcıyı işlev tanımına bağlayabilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- Bir işlevi bir veri yapısında saklayabilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- Bir işlevi bağımsız değişken olarak geçirebilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- İşlev çağrısının değeri olarak bir işlev döndürebilirsiniz.
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

Hakkında F#daha fazla bilgi için bkz. [ F# dil başvurusu](../language-reference/index.md).

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki kod, bu konudaki tüm örnekleri içerir.

### <a name="code"></a>Kod

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Listeler](../language-reference/lists.md)
- [Demetler](../language-reference/tuples.md)
- [İşlevler](../language-reference/functions/index.md)
- [`let`Lara](../language-reference/functions/let-bindings.md)
- [Lambda Ifadeleri: `fun` Anahtar Sözcüğü](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
