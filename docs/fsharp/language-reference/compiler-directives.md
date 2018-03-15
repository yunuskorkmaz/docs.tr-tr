---
title: "Derleyici Yönergeleri (F#)"
description: "F # dili önişlemci yönergeleri, koşullu derleme yönergeleri, satır yönergeleri ve derleyici yönergeleri hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 93aef07a-6747-4ce4-a10f-a05168978af6
ms.openlocfilehash: c7ec056f407f3af34528205a5abb1cdef7d43fef
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="compiler-directives"></a>Derleyici Yönergeleri

Bu konu, işlemci yönergeleri ve derleyici yönergeleri açıklar.


## <a name="preprocessor-directives"></a>Ön işlemci Yönergeleri
Önişlemci yönergesi # simgesiyle konduğundan ve tek başına bir satıra görünür. Derleyici önce çalışır önişlemci olarak yorumlanır.

F #'da kullanılabilir önişlemci yönergeleri aşağıdaki tabloda listelenmektedir.


|Yönergesi|Açıklama|
|---------|-----------|
|`#if` *Simgesi*|Koşullu derleme destekler. Sonra bölümdeki kod `#if` dahil ise *simgesi* tanımlanır.|
|`#else`|Koşullu derleme destekler. Simgenin önceki ile kullanılan eklenecek kodun bir bölümünü işaretler `#if` tanımlı değil.|
|`#endif`|Koşullu derleme destekler. Koşullu bölümün kodun sonunu işaretler.|
|`#`[satır] *int*,<br/>`#`[satır] *int* *dize*,<br/>`#`[satır] *int* *dize verbatim*|Hata ayıklama için orijinal kaynak kodu satır ve dosya adı gösterir. Bu özellik, F # kaynak kodu oluşturmak için araçları sağlanır.|
|`#nowarn` *warningcode*|Derleyici Uyarısı veya uyarıları devre dışı bırakır. Bir uyarı devre dışı bırakmak için kendi Derleyici çıktısı numarasından bulun ve tırnak işaretleri içine alın. "FS" öneki atlayın. Aynı satıra birden çok uyarı numaralarını devre dışı bırakmak için her numarası tırnak işaretleri içine alın ve her dize boşlukla ayırın. Örneğin:

`#nowarn "9" "40"`


Bir uyarı devre dışı bırakma etkisini yönergesi koyun dosyanın bölümlerini de dahil olmak üzere tüm dosya için geçerlidir. |

## <a name="conditional-compilation-directives"></a>Koşullu derleme yönergeleri
Bu yönergeleri biri tarafından devre dışı bırakıldıktan kod Visual StudioCode Düzenleyicisi'nde devre dışı görünüyorsa.


>[!NOTE] 
Diğer dillerde olduğundan koşullu derleme yönergeleri davranışını aynı değil. Örneğin, sembolleri içeren Boolean ifadeler kullanamazsınız ve `true` ve `false` özel bir anlamı yoktur. Kullandığınız simgeleri `if` proje ayarları veya komut satırı tarafından yönergesi tanımlanmalıdır; hiçbir `define` önişlemci yönergesi.


Aşağıdaki kod kullanımını göstermektedir `#if`, `#else`, ve `#endif` yönergeleri. Bu örnekte, iki sürümü tanımını kodunu içerir `function1`. Zaman `VERSION1` kullanılarak tanımlanmış [-define derleyici seçeneği](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kod arasında `#if` yönergesi ve `#else` yönergesi etkinleştirilir. Aksi takdirde, kod arasında `#else` ve `#endif` etkinleştirilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Var olan hiçbir `#define` F # önişlemci yönergesi. Tarafından kullanılan simgeler tanımlamak için derleyici seçeneği veya proje ayarları kullanmalısınız `#if` yönergesi.

Koşullu derleme yönergeleri iç içe. Girinti önişlemci yönergeleri için önemli değildir.


## <a name="line-directives"></a>Satır yönergeleri
Oluştururken, derleyici hataları F # kodunda her bir hata oluştuğu satır numaralarını başvurarak bildirir. Bu satır numaraları 1 dosyasındaki ilk satırı için başlangıç. Başka bir aracından F # kaynak kodu oluşturma, başka bir kaynaktan oluşturulan F # kodunda en olası hatalar ortaya ancak, oluşturulan kodda satır numaralarını genellikle ilgi, değildir. `#line` Yönergesi özgün satırı hakkında bilgi oluşturulan F # kodu için sayı ve kaynak dosyaları geçirmek için F # kaynak kodu oluşturma araçları yazarları için bir yol sağlar.

Kullandığınızda `#line` yönerge, dosya adları tırnak içine alınmalıdır. Sürece verbatim belirteci (`@`) gerekir kaçış ters eğik çizgi karakterlerini iki ters eğik çizgi karakterleri yerine yolu kullanmak için kullanarak dize önünde görüntülenir. Geçerli satır belirteçleri verilmiştir. Bu örneklerde, varsayımında özgün dosya `Script1` bir aracı çalışır ve bu yönergeleri konumda kod satırı 25 dosyasındaki bazı belirteçleri oluşturulur, bir otomatik olarak oluşturulan F # kod dosyasında sonuçları `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Bu belirteçler bazı yapıları veya satır yakın bu konumda oluşturulan F # kodu türetilmiş belirtmek `25` içinde `Script1`.


## <a name="compiler-directives"></a>Derleyici Yönergeleri
Derleyici yönergeleri önişlemci yönergeleri, çünkü bir # işareti önek ancak önişlemci tarafından yorumlanmak yerine, bunlar yorumlamak ve hareket derleyici için kalan benzer.

Aşağıdaki tabloda, F #'da kullanılabilir derleyici yönergesi listeler.


|Yönergesi|Açıklama|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Etkinleştirir veya diğer ML sürümleri ile uyumluluk için basit sözdizimi devre dışı bırakır. Varsayılan olarak, basit sözdizimi etkindir. Ayrıntılı sözdizimi her zaman etkindir. Bu nedenle, basit sözdizimi ve ayrıntılı sözdizimi kullanabilirsiniz. Yönergesi `#light` tek başına eşdeğer olan `#light "on"`. Belirtirseniz `#light "off"`, tüm dil yapıları için ayrıntılı sözdizimi kullanmanız gerekir. F # belgeleri sözdiziminde basit sözdizimi kullanmakta olduğunuz varsayılarak da sunulur. Daha fazla bilgi için bkz: [ayrıntılı sözdizimi](verbose-syntax.md).|
Yorumlayıcı (fsi.exe) yönergeleri için bkz: [etkileşimli programlama F # ile](../tutorials/fsharp-interactive/index.md).


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Derleyici Seçenekleri](compiler-options.md)

