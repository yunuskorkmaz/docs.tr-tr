---
title: Derleyici Yönergeleri
description: Hakkında bilgi edinin F# dil önişlemci yönergeleri, koşullu derleme yönergeleri, satır yönergeleri ve derleyici yönergeleri.
ms.date: 12/10/2018
ms.openlocfilehash: 2b62fb930a3b0c55103d6b0edbe20ae056ba86bd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645505"
---
# <a name="compiler-directives"></a>Derleyici Yönergeleri

Bu konuda işlemci yönergeleri ve derleyici yönergeleri açıklar.

## <a name="preprocessor-directives"></a>Ön işlemci Yönergeleri

Önişlemci yönergesi # sembolü ile önek ve bir satırda kendiliğinden görünür. Bu, derleyici önce çalışır önişlemci tarafından yorumlanır.

Aşağıdaki tablo, kullanılabilen önişlemci yönergeleri listeler F#.

|Yönergesi|Açıklama|
|---------|-----------|
|`#if` *Sembol*|Koşullu derlemeyi destekler. Kod bölümünde sonra `#if` dahil ise *sembol* tanımlanır. Simgenin ayrıca ile negatif `!`.|
|`#else`|Koşullu derlemeyi destekler. Sembol önceki kullandıysanız içerecek şekilde kodun bir bölümünü işaretler `#if` tanımlı değil.|
|`#endif`|Koşullu derlemeyi destekler. Koşullu bir kod bölümünün sonuna işaret eder.|
|`#`[satır] *int*,<br/>`#`[satır] *int* *dize*,<br/>`#`[satır] *int* *verbatim dizesi*|Hata ayıklama için orijinal kaynak kodu satır ve dosya adı belirtir. Bu özellik Oluştur araçlar için sağlanan F# kaynak kodu.|
|`#nowarn` *warningcode*|Derleyici Uyarısı veya uyarıları devre dışı bırakır. Bir uyarıyı devre dışı bırakmak için numarasını derleme çıktısından bulun ve tırnak işaretleri içine alın. "FS" ön ekini atlayın. Aynı satırda birden çok uyarı numaralarını devre dışı bırakmak için her bir sayının tırnak işaretleri içine alın ve her bir dizenin bir boşlukla ayırın. Örneğin:

`#nowarn "9" "40"`

Uyarı devre dışı bırakma etkisini yönergesi önünde dosyasının bölümlerini dahil olmak üzere tüm dosyayı uygular. |

## <a name="conditional-compilation-directives"></a>Koşullu derleme yönergeleri

Bu yönergeler biri tarafından devre dışı kod, Visual Studio Kod Düzenleyicisi'nde soluk görünür.

> [!NOTE]
> Diğer dillerde olduğu gibi koşullu derleme yönergeleri davranışı aynı değildir. Örneğin, Boolean ifadeler sembolleri içeren kullanamazsınız ve `true` ve `false` özel bir anlamı yoktur. Kullandığınız sembolleri `if` yönergesi komut satırı veya proje ayarlarında tanımlanmalıdır; hiçbir `define` önişlemci yönergesi.

Aşağıdaki kod kullanışını `#if`, `#else`, ve `#endif` yönergeleri. Bu örnekte, kod tanımı iki sürümünü içeren `function1`. Zaman `VERSION1` kullanılarak tanımlanmış [-define derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kod arasında `#if` yönergesi ve `#else` yönergesi etkinleştirilir. Aksi takdirde, kod arasında `#else` ve `#endif` etkinleştirilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Var olan hiçbir `#define` önişlemci yönergesi F#. Tarafından kullanılan sembollerini tanımlamak için derleyici seçeneği veya proje ayarlarını kullanmanız gerekir `#if` yönergesi.

Koşullu derleme yönergeleri yuvalanabilir. Girinti önişlemci yönergeleri için önemli değildir.

Ayrıca bir simgeyle negate `!`. Bir şey yalnızca bu örnekte, bir dizenin değerdir _değil_ hata ayıklama:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Satır yönergeleri

Oluşturma sırasında derleyici hataları bildirir F# satır başvuru ile kod numaraları her bir hata oluştuğu. Bu satır numaraları için bir dosyanın ilk satırı 1 konumunda başlatın. Ancak, oluşturuyorsanız, F# kaynak kodunuzdan oluşturulan kodun satır numaralarını başka bir aracı olmayan genellikle ilgi, çünkü oluşturulan hataları F# kod büyük olasılıkla başka bir kaynaktan ortaya çıkar. `#line` Yönergesi oluşturma araçları yazarları için bir yol sağlar F# kaynak kodu, sayılar ve kaynak dosyalarını orijinal satıra hakkında bilgi için oluşturulan geçirmek için F# kod.

Kullanırken `#line` yönerge, dosya adları tırnak içine alınmalıdır. Sürece verbatim belirteci (`@`) gerekir kaçış ters eğik çizgi karakterleri iki ters eğik çizgi karakterleri yerine bunları yolu kullanmak için kullanarak dize önünde görünür. Geçerli satırı belirteçleri aşağıda verilmiştir. Bu örneklerde, varsayımında özgün dosya `Script1` sonuçları bir otomatik olarak oluşturulan içinde F# aracı ile çalışır ve bu yönergeleri konumunda kod satırı 25 dosyasındakibazıbelirteçlerioluşturulduğuzamankoddosyası`Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Bu belirteçler belirtmek F# bu konumda oluşturulan kod satırına yakın veya bu bazı yapıları türetilen `25` içinde `Script1`.

## <a name="compiler-directives"></a>Derleyici Yönergeleri

Derleyici yönergeleri, önişlemci yönergeleri # işareti ile ön eki, ancak önişlemci tarafından yorumlanmasını yerine, bunlar derleyici yorumlar ve işlem yapmak için kalan benzerler.

Aşağıdaki tabloda kullanılabilir derleyici yönergesi F#.

|Yönergesi|Açıklama|
|---------|-----------|
|`#light` ["on"&#124;"kapalı"]|Etkinleştirir veya diğer ML sürümleriyle uyumluluk için basit söz dizimi devre dışı bırakır. Varsayılan olarak, basit söz dizimi etkinleştirilir. Ayrıntılı sözdizimi her zaman etkindir. Bu nedenle, hem basit söz dizimi hem de ayrıntılı söz dizimini kullanabilirsiniz. Yönergenin `#light` kendisi tarafından değerine eşdeğer olan `#light "on"`. Belirtirseniz `#light "off"`, tüm dil yapıları için ayrıntılı sözdizimini kullanmanız gerekir. Söz dizimi için belgelerinde F# basit söz dizimi kullandığınız varsayılarak da sunulur. Daha fazla bilgi için [ayrıntılı sözdizimi](verbose-syntax.md).|

(Fsi.exe) yorumlayıcısını yeniden oluşturulmak yönergeleri için bkz. [etkileşimli programlama F# ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Derleyici Seçenekleri](compiler-options.md)
