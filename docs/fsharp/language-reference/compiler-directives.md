---
title: Derleyici Yönergeleri
description: 'F # dil Önişlemci yönergeleri, koşullu derleme yönergeleri, hat yönergeleri ve derleyici yönergeleri hakkında bilgi edinin.'
ms.date: 12/10/2018
f1_keywords:
- '#endif_FS'
ms.openlocfilehash: aee307eb7bccc8d91b5162f3f43db3b806b761d0
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855380"
---
# <a name="compiler-directives"></a>Derleyici Yönergeleri

Bu konu, işlemci yönergelerini ve derleyici yönergelerini açıklamaktadır.

## <a name="preprocessor-directives"></a>Ön işlemci Yönergeleri

Önişlemci yönergesine # simgesiyle ön eki eklenir ve tek başına bir satırda görüntülenir. Derleyicinin kendisinden önce çalışan Önişlemci tarafından yorumlanır.

Aşağıdaki tabloda, F # ' da kullanılabilen Önişlemci yönergeleri listelenmiştir.

|Deki|Açıklama|
|---------|-----------|
|`#if` * simgesi*|Koşullu derlemeyi destekler. `#if` *Sembol* tanımlanmışsa, öğesinden sonra gelen kod. Sembol Ayrıca ile de olabilir `!` .|
|`#else`|Koşullu derlemeyi destekler. Öncekiyle birlikte kullanılan sembol tanımlanmazsa, kodun bir bölümünü içerecek şekilde işaretler `#if` .|
|`#endif`|Koşullu derlemeyi destekler. Kodun koşullu bölümünün sonunu işaretler.|
|`#`satırı *int*,<br/>`#`satırı *int* *dize*,<br/>`#`satırı *tamsayı* *harfine dize*|Hata ayıklama için özgün kaynak kodu satırını ve dosya adını gösterir. Bu özellik, F # kaynak kodu üreten araçlar için sağlanır.|
|`#nowarn`*uyarı kodu*|Bir derleyici uyarısını veya uyarılarını devre dışı bırakır. Bir uyarıyı devre dışı bırakmak için, derleyici çıktısından numarasını bulun ve tırnak işaretleri içine ekleyin. "FS" önekini atlayın. Aynı satırda birden çok uyarı numarasını devre dışı bırakmak için, her sayıyı tırnak içine alın ve her dizeyi bir boşluk ile ayırın. Örnek:

`#nowarn "9" "40"`

Bir uyarının devre dışı bırakılması etkisi, dosyanın yönergeden önce gelen kısımları da dahil olmak üzere tüm dosya için geçerlidir. |

## <a name="conditional-compilation-directives"></a>Koşullu derleme yönergeleri

Bu yönergelerden biri tarafından devre dışı bırakılan kod Visual Studio Code düzenleyicide soluk görünür.

> [!NOTE]
> Koşullu derleme yönergelerinin davranışı, diğer dillerdeki gibi değildir. Örneğin, sembolleri içeren Boole deyimlerini kullanamaz ve `true` `false` özel bir anlamı yoktur. Yönergede kullandığınız semboller `if` komut satırı veya proje ayarlarında tanımlanmalıdır; hiçbir `define` Önişlemci yönergesi yoktur.

Aşağıdaki kod,, ve yönergelerinin kullanımını gösterir `#if` `#else` `#endif` . Bu örnekte, kod, tanımının iki sürümünü içerir `function1` . `VERSION1` [-Define derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)kullanılarak tanımlandığında, `#if` yönergesi ve yönergesi arasındaki kod `#else` etkinleştirilir. Aksi halde, ve arasındaki `#else` kod `#endif` etkinleştirilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

`#define`F # içinde bir ön işlemci yönergesi yok. Yönergesi tarafından kullanılan sembolleri tanımlamak için derleyici seçeneğini veya proje ayarlarını kullanmanız gerekir `#if` .

Koşullu derleme yönergeleri iç içe olabilir. Girintileme, Önişlemci yönergeleri için önemli değildir.

Ayrıca, simgesiyle bir simge de ekleyebilirsiniz `!` . Bu örnekte, bir dizenin değeri _yalnızca hata ayıklama olmadığında bir_ şeydir:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Çizgi yönergeleri

Derlerken, derleyici, her hatanın gerçekleştiği satır numaralarına başvurarak F # kodundaki hataları raporlar. Bu satır numaraları, bir dosyanın ilk satırı için 1 ' den başlar. Ancak, başka bir araçtan F # kaynak kodu oluşturuyorsanız, oluşturulan koddaki satır numaraları genellikle ilgilenmez, çünkü oluşturulan F # kodundaki hatalar başka bir kaynaktan büyük olasılıkla ortaya çıkar. `#line`Yönergesi, oluşturulan f # koduna orijinal satır numaraları ve kaynak dosyaları hakkında bilgi geçirmek Için F # kaynak kodu üreten araç yazarları için bir yol sağlar.

`#line`Yönergesini kullandığınızda dosya adlarının tırnak içine alınması gerekir. Tam belirteç ( `@` ) dizenin önünde görünüp görüntülenmediği takdirde, yolda kullanabilmek için ters eğik çizgi karakterlerinden birini yerine iki ters eğik çizgi kullanarak kaçış yapmanız gerekir. Aşağıdakiler geçerli çizgi belirteçleridir. Bu örneklerde, özgün dosyanın `Script1` bir araç aracılığıyla çalıştırıldığında otomatik olarak oluşturulan bir F # kod dosyası ile sonuçlandığını ve bu yönergelerin konumundaki kodun dosyadaki 25. satırda bazı belirteçlerden oluşturulduğunu varsayın `Script1` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Bu belirteçler, bu konumda oluşturulan F # kodunun, içinde veya yakınında bazı yapılardan türetilmediğini belirtir `25` `Script1` .

## <a name="compiler-directives"></a>Derleyici Yönergeleri

Derleyici yönergeleri, bir # işaretiyle ön eki olduklarından, ancak Önişlemci 'nin yorumlanması yerine, derleyicinin yorumlanması ve üzerinde işlem yapması nedeniyle, Önişlemci yönergelerine benzer.

Aşağıdaki tabloda, F # ' da kullanılabilen derleyici yönergesi listelenmektedir.

|Deki|Açıklama|
|---------|-----------|
|`#light`["on" &#124; "kapalı"]|Diğer ML sürümleriyle uyumluluk için hafif söz dizimini etkinleştirilir veya devre dışı bırakır. Varsayılan olarak, hafif sözdizimi etkindir. Verbose sözdizimi her zaman etkindir. Bu nedenle, hem basit söz dizimi hem de ayrıntılı sözdizimini kullanabilirsiniz. `#light`Tek başına yönerge öğesine eşdeğerdir `#light "on"` . Belirtirseniz `#light "off"` , tüm dil yapıları için ayrıntılı sözdizimi kullanmanız gerekir. F # belgelerinde sözdizimi, hafif sözdizimi kullandığınızı varsayımıyla sunulur. Daha fazla bilgi için bkz. [ayrıntılı sözdizimi](verbose-syntax.md).|

Yorumlayıcı (fsi.exe) yönergeleri için bkz. [F # Ile etkileşimli programlama](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Derleyici seçenekleri](compiler-options.md)
