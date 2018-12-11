---
title: Genel Türler (F#)
description: Nasıl kullanacağınızı öğrenin F# genel işlevler ve çeşitli türleri ile kod yinelenen olmadan çalışan kod yazmanızı sağlayan tür.
ms.date: 05/16/2016
ms.openlocfilehash: 7eae69bc0286bff4997c6399c7417bde119c2204
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147011"
---
# <a name="generics"></a>Genel Türler

F#işlev değerleri, yöntemler, özellikler ve sınıflar gibi toplama türleri kaydeder ve ayrılmış birleşimler olabilir *genel*. Genel yapılar genellikle genel yapısı, kullanıcı tarafından sağlanan en az bir tür parametresi içerir. Genel işlevler ve türleri çeşitli türleri ile kod her türü için yinelenen olmadan çalışan kod yazmanıza olanak sağlar. Kodunuzu genel yapma, basit olabilir F#, genellikle kodunuzu örtük olarak genel olarak derleyicinin tür çıkarımı ve otomatik Genelleştirme düzenekleri tarafından algılanır.

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

Bir açık genel işlev veya tür bildirimi genel olmayan işlev veya tür, işlev veya tür adından sonra köşeli parantez içinde tür parametreleri belirtimi (ve kullanım) dışında benzer.

Bildirimleri genellikle örtük olarak geneldir. Tam olarak bir işlev veya türü oluşturmak için kullanılan her parametresinin türü belirtmezseniz derleyici her parametre, değer ve değişkeni yazdığınız kodun türünü çıkarsamak çalışır. Daha fazla bilgi için [tür çıkarımı](../type-inference.md). Kod tür veya işlev için parametre türlerini aksi kısıtlamaz, işlev veya türü örtük olarak genel olur. Bu işlem adlı *otomatik Genelleştirme*. Otomatik Genelleştirme üzerinde bazı limitler mevcuttur. Örneğin, varsa F# derleyici, genel bir yapı için türlerini çıkarması oluşturamıyor, derleyici adlı bir kısıtlamaya başvuran hata raporları *değer kısıtlaması*. Bu durumda, bazı tür ek açıklamaları eklemeniz gerekebilir. Otomatik Genelleştirme ve değer kısıtlama ve sorunu çözmek için kodunuzu değiştirme hakkında daha fazla bilgi için bkz. [otomatik Genelleştirme](automatic-generalization.md).

Önceki sözdiziminde, *tür parametreleri* ne tür olabilir. daha fazla sınırlayan isteğe bağlı olarak bir kısıtlama yan tümcesi ile tek tırnak işareti ile başlayan her biri bir virgülle ayrılmış listesi bilinmeyen türleri temsil eden parametreleri Bu tür parametresi için kullanılabilir. Kısıtlama yan tümceleri çeşitli türleri ve kısıtlamalar hakkında diğer bilgiler için sözdizimi için bkz [kısıtlamaları](constraints.md).

*Tür tanımı* sözdiziminde genel olmayan bir tür için tür tanımı ile aynıdır. İsteğe bağlı bir sınıf türü için Oluşturucu parametreleri içeren `as` yan tümcesi, eşit sembol, kayıt alanlarını `inherit` yan tümcesi, ayrılmış bir birleşim seçenekleri `let` ve `do` bağlamaları, üye tanımları ve diğer her şey genel olmayan tür tanımında izin verilir.

Diğer sözdizimi öğeleri genel olmayan işlevleri ve türleri için aynıdır. Örneğin, *nesne tanımlayıcısı* içeren nesneyi temsil eden bir tanımlayıcıdır.

Özellikler, alanlar ve oluşturucular daha kapsayan türdeki genel olamaz. Ayrıca, değerleri bir modülde genel olamaz.

## <a name="implicitly-generic-constructs"></a>Örtük olarak genel yapılar

Zaman F# derleyici, kodunuzdaki türleri algılar, otomatik olarak genel genel herhangi bir işlev değerlendirir. Bir tür gibi bir parametre türü, açıkça belirtirseniz otomatik Genelleştirme engeller.

Aşağıdaki kod örneğinde, `makeList` olsa da ne parametrelerini açıkça genel olarak bildirilen geneldir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

İşlev imzası olmasını algılanır `'a -> 'a -> 'a list`. Unutmayın `a` ve `b` Bu örnekte, aynı türe sahip için algılanır. Bunlar bir listede birlikte eklenir ve tüm öğeleri aynı türde olmalıdır çünkü budur.

Ayrıca bir işlev bir parametre türü bir genel tür parametresi olduğunu belirtmek için bir tür ek açıklaması içinde tek tırnak işareti sözdizimi kullanılarak genel yapabilirsiniz. Aşağıdaki kodda, `function1` türü parametreleri olarak bu şekilde, parametrelerini bildirilen için geneldir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Açıkça genel yapılar

Ayrıca bir işlevi köşeli parantez içinde tür parametrelerinden biri açıkça bildirerek genel yapabilirsiniz (`<type-parameter>`). Aşağıdaki kod bunu göstermektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Genel oluşturur

Genel işlevleri veya yöntemleri kullandığınızda, tür bağımsız değişkenlerini belirtmek olmayabilir. Derleyicinin tür çıkarımı uygun tür bağımsız değişkenlerini çıkarsamak için kullanır. Hala bir belirsizlik ise, tür bağımsız değişkenleri köşeli parantez içinde birden çok tür bağımsız değişkenleri virgülle ayırarak sağlayabilirsiniz.

Aşağıdaki kod, önceki bölümde tanımlanan işlevlerin kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

> [!NOTE]
> Ada göre bir genel türe başvurmak amacıyla iki yolu vardır. Örneğin, `list<int>` ve `int list` genel bir türe başvurmak için kullanabileceğiniz iki yöntemdir `list` tek tür bağımsız değişkeni olan `int`. İkinci form genel yalnızca yerleşik ile kullanılan F# gibi türleri `list` ve `option`. Birden çok tür bağımsız değişkeni varsa, söz dizimi normalde kullandığınız `Dictionary<int, string>` söz dizimi de kullanabilirsiniz, ancak `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Joker karakter tür bağımsız değişkenleri olarak

Tür bağımsız değişkeni derleyici tarafından çıkarılmamalıdır belirtmek için alt çizgi veya joker karakter sembolünü kullanabilirsiniz (`_`), yerine adlandırılmış tür bağımsız değişkeni. Bu aşağıdaki kod gösterilmektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Sınırlamalar genel türler ve İşlevler

Genel tür veya işlev tanımı, genel tür parametresinde kullanılabilir olduğu bilinen yapıları kullanabilirsiniz. Bu, derleme zamanında işlevi ve yöntem çağrılarının doğrulamayı etkinleştirmek için gereklidir. Kendi tür parametreleri açıkça bildirirseniz, derleyici belirli yöntemleri ve işlevleri mevcut olduğunu bildirmek için bir genel tür parametresi açık bir kısıtlaması uygulayabilirsiniz. Ancak, izin verirseniz F# derleyici, genel parametre türlerini çıkarması sizin için uygun kısıtlamaları belirler. Daha fazla bilgi için [kısıtlamaları](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Statik Olarak Çözümlenmiş Tür Parametreleri

İki tür kullanılabilir tür parametrelerinin F# programlar. İlk tür önceki bölümlerde açıklanan genel tür parametreleri olan. Tür parametresini ilk bu tür, Visual Basic ve C# gibi dillerde kullanılan genel tür parametreleri eşdeğerdir. Başka bir tür parametresi tür özeldir F# ve şeklinde adlandırılan bir *statik olarak çözümlenmiş tür parametresi*. Bu yapılar hakkında daha fazla bilgi için bkz. [statik olarak çözümlenmiş tür Parametreleri'nde](statically-resolved-type-parameters.md).

## <a name="examples"></a>Örnekler

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil Başvurusu](../index.md)
- [Türler](../fsharp-types.md)
- [Statik Olarak Çözümlenmiş Tür Parametreleri](statically-resolved-type-parameters.md)
- [.NET Framework'teki genel türler](~/docs/standard/generics/index.md)
- [Otomatik Genelleştirme](automatic-generalization.md)
- [Kısıtlamalar](constraints.md)
