---
title: Genel Türler (F#)
description: 'F # genel işlevler ve çeşitli türleri kod yinelenen olmadan çalışan kod yazmanıza olanak sağlayan türleri kullanmayı öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a9f2e2ee-bcb1-4ce3-8531-850aa183040f
ms.openlocfilehash: e7a5712fddf4d372d1ada86927f50e394a59a410
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="generics"></a>Genel Türler

F # işlevi değerleri, yöntemler, özellikler ve sınıflar gibi toplama türleri kaydeder ve ayrılmış birleşimler olabilir *genel*. Genel yapılar genellikle genel yapı kullanıcı tarafından sağlanan en az bir tür parametresi içerir. Genel işlevler ve türleri, kodu her türü için yinelenen olmadan çeşitli türleri ile çalışır kod yazmanıza olanak sağlar. Genellikle, kodunuzu örtük olarak genel olarak derleyicinin tür çıkarımı ve otomatik Genelleştirme mekanizmaları tarafından algılanır için kodunuzu genel yapılması F #'ta basit olabilir.


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
Bir açıkça genel işlevi ya da türü bildirimi genel olmayan işlevi veya tür parametrelerinde köşeli işlevi veya tür adından sonra belirtimi (ve kullanım) dışında türü benzer.

Bildirimleri genellikle örtük olarak geneldir. Tam olarak bir işlevi veya türü oluşturmak için kullanılan her parametrenin türü belirtmezseniz, derleyici her parametre, değer ve değişken yazdığınız kodun türünü Infer dener. Daha fazla bilgi için bkz: [tür çıkarımı](../type-inference.md). Kod türünü veya işlevi için parametre türlerini aksi kısıtlamaz, işlev veya türü örtük olarak genel olur. Bu işlem adlı *otomatik Genelleştirme*. Otomatik Genelleştirme üzerinde bazı sınırlamalar vardır. Örneğin, F # derleyici genel bir yapı için türlerini anlamak kaydedemediği derleyici adlı bir kısıtlama başvuran bir hata bildirir *değer kısıtlaması*. Bu durumda, bazı tür ek açıklamaları eklemek zorunda kalabilirsiniz. Otomatik Genelleştirme ve değer kısıtlama ve sorunu gidermek için kodunuzu değiştirme hakkında daha fazla bilgi için bkz: [otomatik Genelleştirme](automatic-generalization.md).

Önceki sözdiziminde *tür parametreleri* her biri daha fazla ne türleri olabilir sınırlayan isteğe bağlı olarak bir kısıtlama yan tümcesi ile tek tırnak işareti ile başlayan bir virgülle ayrılmış listesi bilinmeyen türleri temsil eden parametreleri Bu tür parametresi için kullanılabilir. Sözdizimi kısıtlaması yan tümceleri çeşitli türleri ve kısıtlamalar hakkında diğer bilgi için bkz: [kısıtlamaları](constraints.md).

*Tür tanımı* sözdiziminde genel olmayan bir tür için tür tanımı ile aynıdır. İsteğe bağlı bir sınıf türü için Oluşturucusu parametreleri içeren `as` yan tümcesi, eşit simgesi, kayıt alanları `inherit` yan tümcesi, ayrılmış bir birleşim seçenekleri `let` ve `do` bağlamaları, üye tanımları ve başka bir şey genel olmayan tür tanımında izin verilir.

Bir söz dizimi öğeleri genel olmayan işlevleri ve türler için aynıdır. Örneğin, *nesne tanımlayıcısı* içeren nesneyi temsil eden bir tanımlayıcıdır.

Özellikler, alanlar ve oluşturucular kendilerini kapsayan türle daha fazla genel olamaz. Ayrıca, bir modül değerlerde genel olamaz.


## <a name="implicitly-generic-constructs"></a>Örtük olarak genel yapılar
F # derleyici kodunuzu türlerinde oluşturur, genel olarak genel herhangi bir işlev otomatik olarak algılar. Bir tür parametre türü gibi açıkça belirtirseniz otomatik Genelleştirme engeller.

Aşağıdaki kod örneğinde, `makeList` rağmen ne parametreleri açıkça olarak genel bildirilir geneldir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

İşlev imzası olmasını çıkarımı yapılan `'a -> 'a -> 'a list`. Unutmayın `a` ve `b` Bu örnekte, aynı türe sahip algılanır. Bu listedeki birlikte bulunur ve listesini tüm öğeleri aynı türde olmalıdır çünkü.

Ayrıca bir işlev parametre türü bir genel tür parametresi olduğunu belirtmek için bir tür açıklama içinde tek tırnak işareti sözdizimini kullanarak genel yapabilirsiniz. Aşağıdaki kodda, `function1` türü parametreleri olarak bildirilen parametreleri bu şekilde, çünkü geneldir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]
    
## <a name="explicitly-generic-constructs"></a>Açıkça genel yapılar
Ayrıca bir işlev türü parametrelerinin köşeli ayraç içinde açıkça bildirerek genel yapabilirsiniz (`<type-parameter>`). Aşağıdaki kod bunu göstermektedir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]
    
## <a name="using-generic-constructs"></a>Genel kullanarak oluşturur
Genel işlevler veya yöntemler kullandığınızda, tür bağımsız değişkenleri belirtmek sahip olmayabilir. Derleyici tür çıkarımı uygun tür bağımsız değişkenleri anlamak için kullanır. Hala bir belirsizlik ise, tür bağımsız değişkenleri köşeli parantez içinde birden çok tür bağımsız değişkenleri virgül ile ayırarak sağlayabilir.

Aşağıdaki kod önceki bölümlerde tanımlanan işlevler kullanımını gösterir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]
    
>[!NOTE]
Genel bir tür adıyla başvurmak için iki yolu vardır. Örneğin, `list<int>` ve `int list` genel bir tür başvurmak iki şekilde yapabilirsiniz `list` tek tür bağımsız değişkeni olan `int`. İkinci form işleme, genel yalnızca yerleşik F # türleri ile aşağıdaki gibi kullanılır `list` ve `option`. Birden çok tür bağımsız değişkeni varsa, söz dizimi normalde kullandığınız `Dictionary<int, string>` sözdizimini de kullanabilirsiniz, ancak `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Tür bağımsız değişkenleri olarak joker karakterler
Tür bağımsız değişkeni derleyici tarafından çıkarılmamalıdır belirtmek için alt çizgi veya joker karakter sembolünü kullanabilirsiniz (`_`), adlandırılmış tür bağımsız değişkeni yerine. Bu aşağıdaki kodda gösterilir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]
    
## <a name="constraints-in-generic-types-and-functions"></a>Genel türler ve İşlevler kısıtlamaları
Genel tür veya işlev tanımı genel tür parametresi kullanılabilir olması için bilinen yapıları kullanabilirsiniz. Bu işlev ve yöntem çağrıları doğrulama derleme zamanında etkinleştirmek için gereklidir. Tür parametreleri açıkça bildirirseniz derleyici belirli yöntemler ve işlevleri kullanılabilir olduğunu bildirmek için genel tür parametresi açık bir kısıtlaması uygulayabilirsiniz. Genel parametre türleri anlamak F # derleyici izin verirseniz, ancak bunu uygun kısıtlamaları sizin için belirler. Daha fazla bilgi için bkz: [kısıtlamaları](constraints.md).


## <a name="statically-resolved-type-parameters"></a>Statik Olarak Çözümlenmiş Tür Parametreleri
F # programlarında kullanılabilir tür parametreleri iki tür vardır. Genel tür parametreleri önceki bölümlerde açıklanan tür ilk var. Tür parametresi ilk bu tür, Visual Basic ve C# gibi dillerde kullanılan genel tür parametreleri eşdeğerdir. Tür parametresi başka bir tür F # için özel ve olarak adlandırılır bir *statik olarak çözümlenmiş tür parametresi*. Bu yapılar hakkında daha fazla bilgi için bkz: [statik olarak çözümlenmiş tür parametreleri](statically-resolved-type-parameters.md).


## <a name="examples"></a>Örnekler
[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[Dil Başvurusu](../index.md)

[Türler](../fsharp-types.md)

[Statik olarak çözümlenmiş tür parametreleri](statically-resolved-type-parameters.md)

[.NET Framework'te genel türler](~/docs/standard/generics/index.md)

[Otomatik Genelleştirme](automatic-generalization.md)

[Kısıtlamaları](constraints.md)
