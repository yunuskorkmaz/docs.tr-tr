---
title: "İlk Sınıf Değerleri Olarak İşlevler (F#)"
description: "F # programlama dili birinci sınıf durumuna işlevleri nasıl yükseltilir öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a>İlk Sınıf Değerleri Olarak İşlevler

Bir tanımlama işlevsel programlama dilleri, birinci sınıf durumuna işlevlerin özelliğidir. Bir işlev ne olursa olsun, diğer yerleşik türleri değerlerle yapın ve karşılaştırılabilir çaba işlevle yapabilmek yapmak olması gerekir.

İlk sınıf durumu tipik önlemleri şunları içerir:

- İşlev tanımlayıcıları için bağlayabilirsiniz? Diğer bir deyişle, bunları adları verebilirsiniz?

- Bir liste gibi veri yapılarını işlevlerde depolayabilir miyim?

- Bir işlev çağrısı bir bağımsız değişken olarak bir işlev geçirebilirsiniz?

- Bir işlev çağrısında bir işlev dönebilir miyim?

Son iki önlem ne olarak da bilinir tanımlar *daha yüksek sıralı işlemleri* veya *daha yüksek sıralı işlevler*. Daha yüksek sıralı işlevler işlevleri bağımsız değişkenler olarak kabul edin ve işlevleri işlev çağrılarını değeri olarak döndürür. Bu işlemler programlamanınnın işlevler ve işlevlerin oluşturulması eşleme olarak işlevsel programlama desteği.


## <a name="give-the-value-a-name"></a>Değer bir ad verin

Bir işlev birinci sınıf bir değerse yalnızca tamsayı, dizeler ve diğer yerleşik türleri adlandırabilirsiniz, ad mümkün olması gerekir. Bu tanımlayıcı bir değere bağlama olarak işlevsel programlama belgeleri olarak adlandırılır. F # kullanan [ `let` bağlamaları](../language-reference/functions/let-bindings.md) adlarını değerlere bağlamak için: `let <identifier> = <value>`. Aşağıdaki kod iki örnek gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

Bir işlev gibi kolayca adı verebilirsiniz. Aşağıdaki örnek adlı bir işlev tanımlar `squareIt` tanımlayıcısı bağlayarak `squareIt` için [lambda ifadesi](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`. İşlev `squareIt` parametresinin, `n`, ve o parametrenin karesini döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

F # aşağıdakileri sağlar daha az yazarak ile aynı sonucu elde etmek için daha az sözdizimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

İlk stili, çoğunlukla izleyin örnekleri kullanmak `let <function-name> = <lambda-expression>`işlevlerin ve bildirimi diğer türlerin değerleri arasındaki benzerlikler vurgulamak için. Ancak, tüm adlandırılmış işlevler kısa sözdizimi ile yazılabilir. Bazı örnekler, her iki yolla da yazılır.


## <a name="store-the-value-in-a-data-structure"></a>Bir veri yapısında değerini depolama

İlk sınıf değeri veri yapısı içinde depolanabilir. Aşağıdaki kod, listeler ve diziler değerlerini depolamak örnekler gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

Bir tanımlama grubu içinde depolanan bir işlev adı bir işleve aslında değerlendirildiğini doğrulamak için aşağıdaki örnekte kullanır `fst` ve `snd` tanımlama grubundan birinci ve ikinci öğeleri ayıklamak için işleçleri `funAndArgTuple`. Tanımlama grubundaki ilk öğe `squareIt` ve ikinci öğedir `num`. Tanımlayıcı `num` tamsayı 10 ' geçerli bir bağımsız değişken için bir önceki örnekte bağlı `squareIt` işlevi. İkinci ifade dizideki ikinci öğe dizideki ilk öğe uygulandığı: `squareIt num`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

Benzer şekilde, tanımlayıcı olarak yalnızca `num` ve tamsayı 10 birbirinin yerine kullanıldığında, bu nedenle tanımlayıcısı için `squareIt` ve lambda ifadesi `fun n -> n * n`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a>Değer bağımsız değişken olarak geçirin

Bir değeri bir dilde birinci sınıf durumu varsa bir işleve bağımsız değişken olarak geçirebilirsiniz. Örneğin, tamsayıları ve dizeleri bağımsız değişken olarak geçirmek yaygındır. Aşağıdaki kod tamsayılar ve F # bağımsız değişken olarak geçirilen dizelere gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

İşlevler birinci sınıf durumu varsa, bunları bağımsız değişken olarak aynı şekilde geçirebilmek için olması gerekir. Bu daha yüksek sıralı işlevlerin ilk özelliği olduğunu unutmayın.

Aşağıdaki örnekte, işlev `applyIt` iki parametreye sahip `op` ve `arg`. Bir parametre için olan bir işlev gönderme `op` ve işlevi için uygun bir bağımsız değişken `arg`, işlevi uygulanıyor sonucunu döndürür `op` için `arg`. Aşağıdaki örnekte, işlev bağımsız değişkeni ve tamsayı bağımsız değişkeni aynı şekilde adları kullanılarak gönderilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

Bir işlevin başka bir işleve bağımsız değişken olarak gönderme olanağı map veya filtre işlemleri gibi işlevsel programlama dillerinde ortak soyutlamalar vurgular. Map işlemi, örneğin, bir listeyi gözden geçirip, her öğe için bir şeyler ve sonuçları listesinin döndürülmesi işlevler tarafından paylaşılan hesaplamaları yakalayan bir daha yüksek sıralı işlevdir. Tamsayı, listesi her bir öğesinde Artır veya her öğenin karesini veya dizelerinin listesini her bir öğesinde büyük harfe değiştirmek isteyebilirsiniz. Hesaplamanın hataya yatkın bölümü listesi kullanılarak bu adımları özyinelemeli işlemdir ve sonuçları döndürmek için bir liste oluşturur. Bu bölümü eşleme işlevinde yakalanır. Belirli bir uygulama için yazılması gereken tek şey, her liste öğesi için ayrı ayrı uygulamak istediğiniz işlevi (ekleme, karesini, durum değiştirme). İşlev gibi eşleme işleve bağımsız değişken olarak gönderilir `squareIt` gönderilir `applyIt` önceki örnekte.

F # dahil olmak üzere çoğu koleksiyon türü için map yöntemlerini sağlar [listeler](../language-reference/lists.md), [diziler](../language-reference/arrays.md), ve [sıraları](../language-reference/sequences.md). Aşağıdaki örnekler listelerini kullanın. Sözdizimi `List.map <the function> <the list>`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

Daha fazla bilgi için bkz: [listeler](../language-reference/lists.md).

## <a name="return-the-value-from-a-function-call"></a>Bir işlev çağrısının dönüş değeri

Bir işlev bir dilde birinci sınıf durumu varsa, yalnızca tamsayı ve dizeler gibi diğer türleri dönüş son olarak, bir işlev çağrısı değeri olarak iade etme olanağınız olması gerekir.

Aşağıdaki işlev çağrıları tamsayılar döner ve bunları görüntüler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

Aşağıdaki işlev çağrısı bir dize döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

Satır içi tanımlanmış aşağıdaki işlev çağrısı bir Boole değeri döndürür. Görüntülenen değer `True`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

Bir işlev çağrısı değeri olarak bir işlev döndürme özelliği, daha yüksek sıralı işlevler ikinci özelliğidir. Aşağıdaki örnekte, `checkFor` tek bir bağımsız değişken bir işlevi olarak tanımlanan `item`ve yeni bir işlev değeri olarak döndürür. Döndürülen işlev, bağımsız değişkeni olarak bir liste alır `lst`ve arar `item` içinde `lst`. Varsa `item` işlevi döndürür, varsa `true`. Varsa `item` işlevi döndürür, yok `false`. Önceki bölümde olduğu gibi aşağıdaki kod sağlanan liste işlevini kullanır [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), listeyi aramak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

Aşağıdaki kod `checkFor` bir bağımsız değişken, bir listesi ve 7 arar listede geçen yeni bir işlev oluşturmak için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

Aşağıdaki örnek işlevleri birinci sınıf durumunu F #'de, bir işlev bildirmek için kullanır `compose`, ve iki işlevi bağımsız değişkeninin birleşimini döndürür.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
Daha kısa bir sürüm için aşağıdaki "Curried işlevleri" bölümüne bakın


Aşağıdaki kod iki işlev bağımsız değişkenleri olarak gönderir. `compose`, her iki aynı türde tek bir bağımsız değişken almakta olan. Dönüş değerini iki işlev bağımsız değişkenleri oluşan bir bileşimdir yeni bir işlevdir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
F # iki işleç sağlar, `<<` ve `>>`, işlevleri oluşturun. Örneğin, `let squareAndDouble2 = doubleIt << squareIt` eşdeğerdir `let squareAndDouble = compose doubleIt squareIt` önceki örnekte.

Bir işlev çağrısı değeri olarak bir işlev döndürme aşağıdaki örnekte basit bir oyun tahmin etme oluşturur. Oyun oluşturmak için arama `makeGame` değeriyle birinin tahmin etmesini istediğiniz için gönderilen `target`. İşlev dönüş değerini `makeGame` , bir bağımsız değişken (tahmin) ve tahmin doğru olup olmadığını bildiren bir işlevdir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

Aşağıdaki kod çağrıları `makeGame`, değerini göndererek `7` için `target`. Tanımlayıcı `playGame` döndürülen lambda ifadesi ile ilişkili. Bu nedenle, `playGame` bağımsız değişken olarak bir değer götüren bir işlevi olduğunu `guess`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a>Curried işlevleri

Birçok önceki bölümdeki örnek daha az ama öz örtük yararlanarak yazılabilir *currying* F # işlevi bildirimlerden. Currying her birinin tek bir parametre olan bir dizi katıştırılmış işlevlere içine birden fazla parametre olan bir işlev dönüştüren bir işlemdir. F #'ta birden fazla parametre olan işlevler kendiliğinden curried haldedir. Örneğin, `compose` aşağıdaki kısa stili üç parametre ile gösterildiği gibi önceki bölümden yazılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

Ancak, sonuç gösterildiği gibi bir işlevi sırayla bir parametresinin başka bir işlev döndürür bir parametre olarak döndüren bir parametrenin bir işlevi olduğunu `compose4curried`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

Bu işlev, çeşitli şekillerde erişebilir. Aşağıdaki örnekler her döndürür ve 18 görüntüler. Değiştirebileceğiniz `compose4` ile `compose4curried` herhangi bir örnek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

Önce yaptığınız gibi işlev hala çalıştığını doğrulamak için özgün test çalışmaları yeniden deneyin.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
Diziler parametrelerini kapsayan tarafından currying kısıtlayabilirsiniz. Daha fazla bilgi için bkz: "Parametre desenleri" [parametreler ve bağımsız değişkenler](../language-reference/parameters-and-arguments.md).

Daha kısa bir sürümünü yazmak için örtülü currying aşağıdaki örnekte kullanır `makeGame`. Nasıl ayrıntılarını `makeGame` oluşturur ve döndürür `game` işlevi bu biçimde daha az açık, ancak sonuç aynı olduğunu özgün test çalışmalarını kullanarak doğrulayabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

Currying hakkında daha fazla bilgi için bkz: "Değişkenlerin kısmi uygulaması" [işlevler](../language-reference/functions/index.md).


## <a name="identifier-and-function-definition-are-interchangeable"></a>Tanımlayıcı ve işlev tanımı birbirinin yerine kullanılabilir.
Değişken adı `num` önceki örnekler tamsayı 10 değerlendirir ve hiçbir beklenmedik biçimde olduğundan bu where `num` olan geçerli 10 de geçerlidir. İşlev tanımlayıcıları ve bunların değerleri doğru aynıdır: işlevin adını kullanılabilir, herhangi bir yere bağlı lambda ifadesi kullanılabilir.

Aşağıdaki örnek tanımlayan bir `Boolean` adlı işlevi `isNegative`, işlevin adını ve işlevinin tanımı birbirinin yerine kullanır. Sonraki üç örnekler tüm döner ve görüntüler `False`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

Daha ayrıntılı bir adım öteye için değer yerine, `applyIt` için bağlı `applyIt`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a>İlk sınıf değerleri olarak F # işlevlerdir #

Önceki bölümlerde örnekler F # işlevleri F # ilk sınıf değerleri olan ölçütlerini sağladığını göstermektedir:

- Bir işlev tanımı için bir tanımlayıcı bağlayabilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- Veri yapısı içinde bir işlev depolayabilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- Bir işlev bağımsız değişken olarak geçirebilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- Bir işlev çağrısı değeri olarak bir işlev geri dönebilirsiniz.
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

F # hakkında daha fazla bilgi için bkz: [F # dili başvurusu](../language-reference/index.md).

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki kod, bu konudaki tüm örnekleri içerir.

### <a name="code"></a>Kod

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.

[Listeler](../language-reference/lists.md)

[Diziler](../language-reference/tuples.md)

[İşlevler](../language-reference/functions/index.md)

[`let`Bağlamaları](../language-reference/functions/let-bindings.md)

[Lambda ifadeleri: `fun` anahtar sözcüğü](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
