---
title: Kod Biçimlendirme Yönergeleri (F#)
description: 'F # programlama okunabilirlik, estetik, standartlaştırma ve derleme dili için kod girintileme biçimlendirme yönergeleri öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 5bb1f9958a21beb795f9174e44f24c7194453fc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564836"
---
# <a name="code-formatting-guidelines"></a>Kod Biçimlendirme Yönergeleri

Bu konuda kod girintileme yönergeleri F # için özetlenmektedir. F # dili satır sonu ve girinti duyarlı olduğundan, bu yalnızca bir okunabilirlik sorunu, estetik sorunu veya kodunuzu doğru biçimde biçimlendirmek için kodlama Standartlaştırma sorun değil. Kodunuzun doğru şekilde derlenmesi için için doğru biçimlendirmeniz gerekir.


## <a name="general-rules-for-indentation"></a>Girinti genel kuralları
Girinti gerekli olduğunda, boşluk, sekme değil kullanmanız gerekir. En az bir alan gereklidir. Kuruluşunuz için girinti kullanmak için alanları sayısını belirtmek için kodlama standartları oluşturabilir; girinti oluştuğu her düzeyde girinti üç veya dört boşluklardan tipiktir. Kuruluşunuzun girinti standartları seçeneklerini değiştirerek eşleştirmek için Visual Studio yapılandırabilirsiniz `Options` kullanılabilir iletişim kutusu `Tools` menüsü. İçinde `Text Editor` düğümünü genişletin `F#` ve ardından `Tabs`. Kullanılabilir seçenekler açıklaması için bkz: [seçenekler, metin düzenleyici, tüm diller, sekmeler](https://msdn.microsoft.com/library/7sffa753.aspx).

Genel olarak, derleyici, kodunuzu ayrıştırırken geçerli iç içe geçme düzeyini gösteren bir iç yığın tutar. Kod girintili, yeni bir iç içe geçme düzeyini oluşturulan veya bu dahili yığına gönderilir. Bir yapı sona erdiğinde düzeyi Sil'i. Girinti düzeyi sonuna işaret eder ve iç yığın pop yollarından olmakla birlikte, belirli belirteçleri de, aşağıdaki gibi Sil'i için düzeyinin neden `end` anahtar sözcüğü veya bir kapanış ayracı veya parantez.

İşlev tanımı kod bir tür tanımı gibi bir çok satırlı yapısında `try...with` yapı ve döngü yapıları, gerekir girintili yapı açılış satır göre. Girintili ilk satırı sütun konumu sonraki kod için aynı yapı oluşturur. Girinti düzeyi adlı bir *bağlamı*. Sütun konumu olarak adlandırılır, en az bir sütun ayarlar bir *offside satır*, aynı bağlamda olan sonraki kod satırı için. Bir kod satırı karşılaşıldığında, bu yerleşik sütun konumu daha az girintili, derleyici bağlamı sona erdi ve, şimdi ileri düzeyde, önceki bağlamda kodlama olduğunu varsayar. Terim *offside* içinde bir kod satırı tetikleyen bir yapı sonuna onu yetecek kadar girinti uygulanmamış olduğundan koşulu tanımlamak için kullanılır. Diğer bir deyişle, bir offside satırı solundaki offside kodudur. Doğru girintili kodda, offside kural yapıları sonuna ayırmak için yararlanın. Girinti yanlış kullanırsanız, offside bir koşul bir uyarı verecek derleyici neden olabilir veya yanlış kodunuzu yorumu için yol açabilir.

Offside satırları şu şekilde belirlenir.


- Bir `=` belirteci ile ilişkili bir `let` offside bir sonra ilk belirteci sütun satırında tanıtır `=` oturum.


- İçinde bir `if...then...else` ifade, sonra ilk belirteci sütun konumunu `then` anahtar sözcüğü veya `else` anahtar sözcüğü bir offside satırı tanıtır.


- İçinde bir `try...with` ifadesi, sonra ilk belirteci `try` offside satır tanıtır.


- İçinde bir `match` ifadesi, sonra ilk belirteci `with` ve her sonra ilk belirteci `->` offside satırları tanıtır.


- Birinci belirtecin sonra `with` bir türü uzantısı offside satır tanıtır.


- Birinci belirtecin veya sonra bir açılış ayracı veya parantez `begin` anahtar sözcüğü, offside satır tanıtır.


- Anahtar sözcükler ilk karakteri `let`, `if`, ve `module` offside satırları tanıtır.


Aşağıdaki kod örnekleri girinti kuralları gösterilmektedir. Burada, yazdırma deyimleri uygun bağlamıyla ilişkilendirilecek girinti kullanır. Girinti kaydırır her zaman, bağlam Sil'i ve önceki bağlamına döndürür. Bu nedenle, bir alan her bir yineleme sonunda yazdırılır; "Bitti!" yalnızca bir kez offside girinti döngü parçası olmadığını çünkü yazdırılır. "En üst düzey bağlamı" dizesi yazdırma işlevi bir parçası değil. İşlevi çağrılmadan önce bu nedenle, ilk olarak, statik başlatma sırasında yazdırılan.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

Çıktı aşağıdaki gibidir:

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

Uzun satırları böldüğünüzde, satır devamlılığı erişebileceğinizden kapsayan yapı girintili gerekir. Örneğin, işlev bağımsız değişkenleri işlevi adının ilk karakteri erişebileceğinizden aşağıdaki kodda gösterildiği gibi girintili gerekir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

Sonraki bölümde açıklandığı gibi bu kurallar için özel durumlar vardır.


## <a name="indentation-in-modules"></a>Modüllerdeki girinti
Bir yerel modül kodda modülü göre girintili gerekir, ancak üst düzey bir modül kodda girintili olması gerekmez. Namespace öğeleri girintili gerekmez.

Aşağıdaki kod örnekleri bu gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

Daha fazla bilgi için bkz: [modülleri](modules.md).


## <a name="exceptions-to-the-basic-indentation-rules"></a>Temel girinti kurallar için özel durumlar
Genel, önceki bölümde açıklandığı gibi çok satırlı yapıları kodda yapı ilk satırının girinti göre girintili gerekir ve ilk offside satır oluştuğunda yapı sonuna tarafından belirlenen kuralıdır. Bazı oluşturur, gibi bağlamları son olduğunda hakkında kural için bir özel `try...with` ifadesi `if...then...else` ifadesi ve kullanımını `and` karşılıklı özyinelemeli işlevler veya türleri bildirme sözdizimine sahip birden fazla bölümü. Sonraki bölümleri gibi girinti `then` ve `else` içinde bir `if...then...else` aynı ifade belirteciyle düzeyi, ifade başlayan, ancak içerik için bir son belirten yerine, aynı bağlamın'in sonraki bölümüne temsil eder. Bu nedenle, bir `if...then...else` ifade aşağıdaki kod örneğinde olduğu gibi yazılabilir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

Özel durumun offside Kuralın yalnızca geçerli `then` ve `else` anahtar sözcükler. Bu nedenle, girinti hata olmasa da `then` ve `else` satır kod girinti Ayrıca, başarısız bir `then` bloğu bir uyarı üretir. Bu kod aşağıdaki satırları gösterilmiştir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

Kodu için bir `else` bloğu, ek bir özel kural uygular. Önceki örnekte uyarı yalnızca kodda oluşur `then` kodda yer almayan blok `else` bloğu. Bu, çeşitli koşullarını işlevinin başında kodu olabilir. işlev için kalan zorlamadan denetler kod yazmanıza olanak sağlayan bir `else` girintili blok,. Bu nedenle, bir uyarı üretmeden aşağıdaki yazabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

Önceki satıra iç işleçler için olduğu gibi kadar bir satır girintili değil yükleyen bağlamları bitiş kural için başka bir özel `+` ve `|>`. İç işleçleri ile başlayan satırlar başlamak için verilen `(1 + oplength)` sütunları bağlamı için bir son tetikleme olmadan normal konumuna önce burada `oplength` işleci olun karakter sayısı. Bu ilk belirteci önceki satırla hizalamak için işleçten sonra neden olur.

Örneğin, aşağıdaki kodda, `+` simgesi izin verilir önceki satıra'den küçük girintili iki sütun olmalıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

İç içe geçme düzeyini daha yüksek olduğunda girinti genellikle artırsa içinde derleyici girinti daha düşük bir sütun konumu sıfırlamanıza olanak tanır birkaç yapıları vardır.

Sütun konumu sıfırlamanız izin yapıları aşağıdaki gibidir:


- Anonim işlevler gövdesi. Aşağıdaki kodda yazdırma ifade sol uzağına sütun konumu başlar `fun` anahtar sözcüğü. Ancak, satır önceki girinti düzeyi başlangıcı sol sütununda başlamamalıdır (diğer bir deyişle, sol tarafındaki `L` içinde `List`).
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- Parantez tarafından ya da içine yapıları `begin` ve `end` içinde bir `then` veya `else` , engelleme bir `if...then...else` ifadesi, sağlanan girinti sütun konumu az `if` anahtar sözcüğü. Bu özel bir kodlama stilde izin veren bir açma ayracı veya `begin` sonra satırının sonunda kullanılan `then` veya `else`.


- Modüller, sınıflar, arabirimler ve virgülle ayrılan yapıları gövdeleri `begin...end`, `{...}`, `class...end`, veya `interface...end`. Bu içinde açma anahtar sözcüğü tür tanımı tür adı ile aynı satırda açılış anahtar sözcüğü erişebileceğinizden girintili olması için tüm gövdesini zorlamadan olabilen bir stil sağlar.
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)
