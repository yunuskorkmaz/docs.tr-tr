---
title: Genel Türler
description: Kod tekrarlamadan farklı F# türlerle çalışacak kod yazmanızı sağlayan genel işlevleri ve türleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 5d6e57762095e44836425f90d21a6c1dc71edaaa
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666700"
---
# <a name="generics"></a>Genel Türler

F#işlev değerleri, Yöntemler, Özellikler ve sınıflar, kayıtlar ve ayırt edici birleşimler gibi toplama türleri *genel*olabilir. Genel yapılar, genellikle genel yapının kullanıcısı tarafından sağlanan en az bir tür parametresi içerir. Genel işlevler ve türler, her tür için kodu tekrarlamadan çeşitli türlerle birlikte çalışarak kod yazmanızı sağlar. Kodunuzun genel olması F#, genellikle kodunuzun tür çıkarımı ve otomatik Genelleştirme mekanizmaları tarafından genel olarak açıkça çıkarsandığı için, kodunuzun genel hale getirilmesi basit olabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a>Açıklamalar

Açık bir genel işlevin veya türün bildirimi, tür parametrelerinin belirtimi (ve kullanımı) dışında, işlev veya tür adından sonra açılı ayraçlar olarak genel olmayan bir işlev veya türden çok benzer.

Bildirimler genellikle dolaylı olarak geneldir. Bir işlev veya tür oluşturmak için kullanılan her parametrenin türünü tam olarak belirtmezseniz, derleyici her bir parametre, değer ve değişkenin türünü yazdığınız koddan çıkarmaya çalışır. Daha fazla bilgi için bkz. [tür çıkarımı](../type-inference.md). Tür veya işlevinizin kodu başka türlü parametre türlerini sınırlandırmadığından, işlev veya tür örtülü olarak geneldir. Bu işlem *Otomatik Genelleştirme*olarak adlandırılır. Otomatik Genelleştirme üzerinde bazı sınırlar vardır. Örneğin, F# derleyici genel bir yapının türlerini çıkarsanamıyor, derleyici *değer kısıtlaması*adlı bir kısıtlamaya başvuran bir hata bildirir. Bu durumda bazı tür ek açıklamalarını eklemeniz gerekebilir. Otomatik Genelleştirme ve değer kısıtlaması hakkında daha fazla bilgi ve sorunu gidermek için kodunuzun nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [Otomatik Genelleştirme](automatic-generalization.md).

Önceki sözdiziminde, *tür parametreleri* , her biri tek tırnak işaretiyle başlayan ve isteğe bağlı olarak, bu tür için kullanılabilecek türleri daha fazla sınırlayan bir kısıtlama yan tümcesi içeren, virgülle ayrılmış parametrelerin bir listesidir. parametresinin. Çeşitli türlerdeki kısıtlama yan tümcelerinin sözdizimi ve kısıtlamalar hakkında diğer bilgiler için bkz. [kısıtlamalar](constraints.md).

Söz diziminde *tür tanımı* genel olmayan bir türün tür tanımıyla aynıdır. Bir sınıf türü için Oluşturucu `as` parametrelerini, isteğe bağlı bir yan tümceyi, eşittir sembolünü, kayıt alanlarını `inherit` , yan tümcesini, ayrılmış `let` bir Union için seçimleri, ve `do` bağlamaları, üye tanımlarını içerir ve genel olmayan tür tanımında izin verilen başka bir şey.

Diğer sözdizimi öğeleri, genel olmayan işlevler ve türler için olanlarla aynıdır. Örneğin, *nesne tanımlayıcısı* kapsayan nesnenin kendisini temsil eden bir tanıtıcıdır.

Özellikler, alanlar ve oluşturucular kapsayan türden daha genel olamaz. Ayrıca, modüldeki değerler genel olamaz.

## <a name="implicitly-generic-constructs"></a>Örtük genel yapılar

F# Derleyici kodunuzda türleri kodaldığında, genel olarak genel olabilecek tüm işlevleri otomatik olarak değerlendirir. Parametre türü gibi açıkça bir tür belirtirseniz, otomatik genelleştirmeyi engelleyebilirsiniz.

Aşağıdaki kod örneğinde, `makeList` , veya parametreleri açıkça genel olarak bildirildiği halde, geneldir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

İşlevin imzası olarak algılanır `'a -> 'a -> 'a list`. Bu örnekte `a` ve `b` aynı türe sahip olacak şekilde algılanır olduğunu unutmayın. Bunun nedeni, bir listeye birlikte dahil edilmeleri ve bir listenin tüm öğeleri aynı türde olmalıdır.

Ayrıca bir parametre türünün genel bir tür parametresi olduğunu göstermek için bir tür ek açıklamasında tek tırnak işareti sözdizimini kullanarak bir işlevi genel hale getirebilirsiniz. Aşağıdaki kodda `function1` , parametreleri tür parametreleri olarak bu şekilde bildirildiği için geneldir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Açık genel yapılar

Ayrıca, tür parametrelerini açılı ayraçlar (`<type-parameter>`) içinde açıkça bildirerek bir işlevi genel hale getirebilirsiniz. Aşağıdaki kod bunu göstermektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Genel yapıları kullanma

Genel işlevleri veya yöntemleri kullandığınızda, tür bağımsız değişkenlerini belirtmeniz gerekmez. Derleyici, uygun tür bağımsız değişkenlerini çıkarması için tür çıkarımı kullanır. Hala bir belirsizlik varsa, birden fazla tür bağımsız değişkenini virgülle ayırarak, açılı ayraç içinde tür bağımsız değişkenleri sağlayabilirsiniz.

Aşağıdaki kod, önceki bölümlerde tanımlanan işlevlerin kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

> [!NOTE]
> Ada göre genel bir türe başvurmanın iki yolu vardır. Örneğin, `list<int>` ve `int list` tek bir tür bağımsız değişkenine `int`sahip genel bir türe `list` başvurmak için iki yol vardır. İkinci form, genel olarak gibi F# `list` `option`yalnızca yerleşik türler ile kullanılır. Birden çok tür bağımsız değişkeni varsa, normalde söz dizimini `Dictionary<int, string>` kullanırsınız, ancak sözdizimini `(int, string) Dictionary`de kullanabilirsiniz.

## <a name="wildcards-as-type-arguments"></a>Tür bağımsız değişkenleri olarak joker karakterler

Derleyici tarafından bir tür bağımsız değişkeninin çıkarsanın belirtmek için, adlandırılmış tür bağımsız değişkeni yerine alt çizgi veya joker karakter sembolünü`_`() kullanabilirsiniz. Bu, aşağıdaki kodda gösterilmiştir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Genel türlerde ve Işlevlerde kısıtlamalar

Genel tür veya işlev tanımında, yalnızca genel tür parametresinde kullanılabilir olan bilinen yapıları kullanabilirsiniz. Bu, derleme zamanında işlev ve yöntem çağrılarının doğrulanmasını etkinleştirmek için gereklidir. Tür parametrelerinizi açıkça bildirirseniz, derleyiciye belirli yöntemlerin ve işlevlerin kullanılabildiğini bildirmek için genel bir tür parametresine açık bir kısıtlama uygulayabilirsiniz. Ancak, F# derleyicinin genel parametre türlerinizi çıkarması için izin verirseniz, sizin için uygun kısıtlamaları saptacaktır. Daha fazla bilgi için bkz. [kısıtlamalar](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Statik Olarak Çözümlenmiş Tür Parametreleri

F# Programlarda kullanılabilecek iki tür parametre vardır. İlki, önceki bölümlerde açıklanan türün genel tür parametreleridir. Bu ilk tür parametresi, Visual Basic ve C#gibi dillerde kullanılan genel tür parametrelerine eşdeğerdir. Başka türde bir tür parametresi öğesine F# özeldir ve statik olarak çözümlenen bir *tür parametresi*olarak adlandırılır. Bu yapılar hakkında daha fazla bilgi için bkz. [statik çözümlenen tür parametreleri](statically-resolved-type-parameters.md).

## <a name="examples"></a>Örnekler

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil Başvurusu](../index.md)
- [Türler](../fsharp-types.md)
- [Statik Olarak Çözümlenmiş Tür Parametreleri](statically-resolved-type-parameters.md)
- [Genel Türler](../../../standard/generics/index.md)
- [Otomatik Genelleştirme](automatic-generalization.md)
- [Kısıtlamalar](constraints.md)
