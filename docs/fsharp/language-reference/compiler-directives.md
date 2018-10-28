---
title: Derleyici Yönergeleri (F#)
description: 'F # dil önişlemci yönergeleri, koşullu derleme yönergeleri, satır yönergeleri ve derleyici yönergeleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 5ac375ac5acd0609a6556f9e0481d169df827c98
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181374"
---
# <a name="compiler-directives"></a>Derleyici Yönergeleri

Bu konuda işlemci yönergeleri ve derleyici yönergeleri açıklar.

## <a name="preprocessor-directives"></a>Ön işlemci Yönergeleri

Önişlemci yönergesi # sembolü ile önek ve bir satırda kendiliğinden görünür. Bu, derleyici önce çalışır önişlemci tarafından yorumlanır.

Aşağıdaki tabloda, F #'ta kullanılabilir olan önişlemci yönergeleri listeler.

|Yönergesi|Açıklama|
|---------|-----------|
|`#if` *Sembol*|Koşullu derlemeyi destekler. Kod bölümünde sonra `#if` dahil ise *sembol* tanımlanır.|
|`#else`|Koşullu derlemeyi destekler. Sembol önceki kullandıysanız içerecek şekilde kodun bir bölümünü işaretler `#if` tanımlı değil.|
|`#endif`|Koşullu derlemeyi destekler. Koşullu bir kod bölümünün sonuna işaret eder.|
|`#`[satır] *int*,<br/>`#`[satır] *int* *dize*,<br/>`#`[satır] *int* *verbatim dizesi*|Hata ayıklama için orijinal kaynak kodu satır ve dosya adı belirtir. Bu özellik için F # kaynak kodu oluşturma araçları sağlanmaz.|
|`#nowarn` *warningcode*|Derleyici Uyarısı veya uyarıları devre dışı bırakır. Bir uyarıyı devre dışı bırakmak için numarasını derleme çıktısından bulun ve tırnak işaretleri içine alın. "FS" ön ekini atlayın. Aynı satırda birden çok uyarı numaralarını devre dışı bırakmak için her bir sayının tırnak işaretleri içine alın ve her bir dizenin bir boşlukla ayırın. Örneğin:

`#nowarn "9" "40"`

Uyarı devre dışı bırakma etkisini yönergesi önünde dosyasının bölümlerini dahil olmak üzere tüm dosyayı uygular. |

## <a name="conditional-compilation-directives"></a>Koşullu derleme yönergeleri

Bu yönergeler biri tarafından devre dışı kod, Visual Studio Kod Düzenleyicisi'nde soluk görünür.

>[!NOTE]
Diğer dillerde olduğu gibi koşullu derleme yönergeleri davranışı aynı değildir. Örneğin, Boolean ifadeler sembolleri içeren kullanamazsınız ve `true` ve `false` özel bir anlamı yoktur. Kullandığınız sembolleri `if` yönergesi komut satırı veya proje ayarlarında tanımlanmalıdır; hiçbir `define` önişlemci yönergesi.

Aşağıdaki kod kullanışını `#if`, `#else`, ve `#endif` yönergeleri. Bu örnekte, kod tanımı iki sürümünü içeren `function1`. Zaman `VERSION1` kullanılarak tanımlanmış [-define derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kod arasında `#if` yönergesi ve `#else` yönergesi etkinleştirilir. Aksi takdirde, kod arasında `#else` ve `#endif` etkinleştirilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Var olan hiçbir `#define` F # önişlemci yönergesi. Tarafından kullanılan sembollerini tanımlamak için derleyici seçeneği veya proje ayarlarını kullanmanız gerekir `#if` yönergesi.

Koşullu derleme yönergeleri yuvalanabilir. Girinti önişlemci yönergeleri için önemli değildir.

## <a name="line-directives"></a>Satır yönergeleri

Oluştururken, derleyici her hatanın gerçekleştiği satır numaralarını başvurarak F # kodu hatalarını bildirir. Bu satır numaraları için bir dosyanın ilk satırı 1 konumunda başlatın. Başka bir aracı F # kaynak kodu üretiyorsanız, başka bir kaynaktan oluşturulan F # kodu en olası hataları ortaya ancak, oluşturulan kodda satır numaraları genellikle, ilgi değildir. `#line` Yönergesi, oluşturulan F # kodu numaraları ve kaynak dosyalarını orijinal satıra hakkında bilgi geçirilecek F # kaynak kodu oluşturma araçları yazarları için bir yol sağlar.

Kullanırken `#line` yönerge, dosya adları tırnak içine alınmalıdır. Sürece verbatim belirteci (`@`) gerekir kaçış ters eğik çizgi karakterleri iki ters eğik çizgi karakterleri yerine bunları yolu kullanmak için kullanarak dize önünde görünür. Geçerli satırı belirteçleri aşağıda verilmiştir. Bu örneklerde, varsayımında özgün dosya `Script1` sonuçları bir otomatik olarak oluşturulan F # kod dosyası içinde bir aracı ile çalışır ve bu yönergeleri konumunda kod satırı 25 dosyasındaki bazı belirteçleri oluşturulduğu zaman `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Bu konumda oluşturulan F # kodu bazı yapıları veya satır yakın türetilir bu belirteçleri belirtmek `25` içinde `Script1`.

## <a name="compiler-directives"></a>Derleyici Yönergeleri

Derleyici yönergeleri, önişlemci yönergeleri # işareti ile ön eki, ancak önişlemci tarafından yorumlanmasını yerine, bunlar derleyici yorumlar ve işlem yapmak için kalan benzerler.

Aşağıdaki tabloda, F #'ta da kullanılabilir derleyici yönergesi listeler.

|Yönergesi|Açıklama|
|---------|-----------|
|`#light` ["on"&#124;"kapalı"]|Etkinleştirir veya diğer ML sürümleriyle uyumluluk için basit söz dizimi devre dışı bırakır. Varsayılan olarak, basit söz dizimi etkinleştirilir. Ayrıntılı sözdizimi her zaman etkindir. Bu nedenle, hem basit söz dizimi hem de ayrıntılı söz dizimini kullanabilirsiniz. Yönergenin `#light` kendisi tarafından değerine eşdeğer olan `#light "on"`. Belirtirseniz `#light "off"`, tüm dil yapıları için ayrıntılı sözdizimini kullanmanız gerekir. F # için belge sözdiziminde basit söz dizimi kullandığınız varsayılarak da sunulur. Daha fazla bilgi için [ayrıntılı sözdizimi](verbose-syntax.md).|
(Fsi.exe) yorumlayıcısını yeniden oluşturulmak yönergeleri için bkz. [ile F # Etkileşimli programlama](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Derleyici Seçenekleri](compiler-options.md)
