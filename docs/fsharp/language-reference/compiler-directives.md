---
title: Derleyici Yönergeleri
description: Dil ön F# işlemci yönergeleri, koşullu derleme yönergeleri, hat yönergeleri ve derleyici yönergeleri hakkında bilgi edinin.
ms.date: 12/10/2018
ms.openlocfilehash: 16db2efb2fee2c2c5e94aa98eb0a13183a4e0e0b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630406"
---
# <a name="compiler-directives"></a>Derleyici Yönergeleri

Bu konu, işlemci yönergelerini ve derleyici yönergelerini açıklamaktadır.

## <a name="preprocessor-directives"></a>Ön işlemci Yönergeleri

Önişlemci yönergesine # simgesiyle ön eki eklenir ve tek başına bir satırda görüntülenir. Derleyicinin kendisinden önce çalışan Önişlemci tarafından yorumlanır.

Aşağıdaki tabloda, ' de F#kullanılabilen Önişlemci yönergeleri listelenmiştir.

|Yönergesi|Açıklama|
|---------|-----------|
|`#if`*sembol*|Koşullu derlemeyi destekler. `#if` *Sembol* tanımlanmışsa, öğesinden sonra gelen kod. Sembol Ayrıca ile `!`de olabilir.|
|`#else`|Koşullu derlemeyi destekler. Öncekiyle `#if` birlikte kullanılan sembol tanımlanmazsa, kodun bir bölümünü içerecek şekilde işaretler.|
|`#endif`|Koşullu derlemeyi destekler. Kodun koşullu bölümünün sonunu işaretler.|
|`#`satırı *int*,<br/>`#`satırı *int* *dize*,<br/>`#`satırı *int* *Tam dize*|Hata ayıklama için özgün kaynak kodu satırını ve dosya adını gösterir. Bu özellik, kaynak kodu üreten F# araçlar için sağlanır.|
|`#nowarn`*uyarı kodu*|Bir derleyici uyarısını veya uyarılarını devre dışı bırakır. Bir uyarıyı devre dışı bırakmak için, derleyici çıktısından numarasını bulun ve tırnak işaretleri içine ekleyin. "FS" önekini atlayın. Aynı satırda birden çok uyarı numarasını devre dışı bırakmak için, her sayıyı tırnak içine alın ve her dizeyi bir boşluk ile ayırın. Örneğin:

`#nowarn "9" "40"`

Bir uyarının devre dışı bırakılması etkisi, dosyanın yönergeden önce gelen kısımları da dahil olmak üzere tüm dosya için geçerlidir. |

## <a name="conditional-compilation-directives"></a>Koşullu derleme yönergeleri

Bu yönergelerden biri tarafından devre dışı bırakılan kod Visual Studio Code düzenleyicide soluk görünür.

> [!NOTE]
> Koşullu derleme yönergelerinin davranışı, diğer dillerdeki gibi değildir. Örneğin, sembolleri `true` `false` içeren Boole deyimlerini kullanamaz ve özel bir anlamı yoktur. `if` Yönergede kullandığınız semboller komut satırı veya proje ayarlarında tanımlanmalıdır; hiçbir `define` Önişlemci yönergesi yoktur.

Aşağıdaki kod `#if`, `#else`, ve `#endif` yönergelerinin kullanımını gösterir. Bu örnekte, kod, tanımının `function1`iki sürümünü içerir. -Define [derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)kullanılarak tanımlandığında, `#if` yönergesi ve `#else` yönergesi arasındaki kod etkinleştirilir. `VERSION1` Aksi halde, ve `#else` `#endif` arasındaki kod etkinleştirilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

' De F#bir ön işlemciyönergesiyoktur.`#define` `#if` Yönergesi tarafından kullanılan sembolleri tanımlamak için derleyici seçeneğini veya proje ayarlarını kullanmanız gerekir.

Koşullu derleme yönergeleri iç içe olabilir. Girintileme, Önişlemci yönergeleri için önemli değildir.

Ayrıca, simgesiyle bir simge `!`de ekleyebilirsiniz. Bu örnekte, bir dizenin değeri _yalnızca hata ayıklama_ olmadığında bir şeydir:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Çizgi yönergeleri

Derlerken derleyici, her hatanın gerçekleştiği satır numaralarına F# başvurarak koddaki hataları raporlar. Bu satır numaraları, bir dosyanın ilk satırı için 1 ' den başlar. Ancak, başka bir araçtan F# kaynak kodu oluşturuyorsanız oluşturulan koddaki satır numaraları genellikle ilgilenmez, çünkü oluşturulan F# koddaki hatalar büyük olasılıkla başka bir kaynaktan ortaya çıkar. Yönergesi, oluşturulan F# koda özgün satır numaraları ve kaynak dosyaları hakkında F# bilgi geçirmek için kaynak kodu üreten araç yazarları için bir yol sağlar. `#line`

`#line` Yönergesini kullandığınızda dosya adlarının tırnak içine alınması gerekir. Tam belirteç (`@`) dizenin önünde görünüp görüntülenmediği takdirde, yolda kullanabilmek için ters eğik çizgi karakterlerinden birini yerine iki ters eğik çizgi kullanarak kaçış yapmanız gerekir. Aşağıdakiler geçerli çizgi belirteçleridir. Bu örneklerde, özgün dosyanın `Script1` bir araç aracılığıyla çalıştırıldığında otomatik olarak oluşturulan F# bir kod dosyası ile sonuçlandığını ve bu yönergelerin konumundaki kodun dosyadaki `Script1`25.satırdakibazıbelirteçlerdenoluşturulduğunuvarsayın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Bu belirteçler, bu konumda F# oluşturulan kodun, `25` içinde `Script1`veya yakınında bazı yapılardan türetilmediğini belirtir.

## <a name="compiler-directives"></a>Derleyici Yönergeleri

Derleyici yönergeleri, bir # işaretiyle ön eki olduklarından, ancak Önişlemci 'nin yorumlanması yerine, derleyicinin yorumlanması ve üzerinde işlem yapması nedeniyle, Önişlemci yönergelerine benzer.

Aşağıdaki tabloda ' de F#kullanılabilen derleyici yönergesi listelenmektedir.

|Yönergesi|Açıklama|
|---------|-----------|
|`#light`[""&#124;"kapalı"]|Diğer ML sürümleriyle uyumluluk için hafif söz dizimini etkinleştirilir veya devre dışı bırakır. Varsayılan olarak, hafif sözdizimi etkindir. Verbose sözdizimi her zaman etkindir. Bu nedenle, hem basit söz dizimi hem de ayrıntılı sözdizimini kullanabilirsiniz. Tek başına `#light` yönerge öğesine `#light "on"`eşdeğerdir. Belirtirseniz `#light "off"`, tüm dil yapıları için ayrıntılı sözdizimi kullanmanız gerekir. İçin F# belgelerindeki sözdizimi, hafif sözdizimi kullandığınızı varsayımıyla sunulur. Daha fazla bilgi için bkz. [ayrıntılı sözdizimi](verbose-syntax.md).|

Yorumlayıcı (fsi. exe) yönergeleri için bkz. [etkileşimli programlama F# ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Derleyici Seçenekleri](compiler-options.md)
