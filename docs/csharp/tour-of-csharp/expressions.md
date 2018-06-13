---
title: C# ifadeleri - C# dili turu
description: 'C# dili yapı taşlarını şunlardır: ifadeleri, işlenen ve işleçler'
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 8fa1c5d0464644b26eb457bca8ecaf007c288f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352311"
---
# <a name="expressions"></a>İfadeler

*İfadeleri* gelen oluşturulan *işlenenler* ve *işleçleri*. İfade işleçleri işlenenlerine uygulamak için hangi işlemleri gösterir. İşleçler örneklerindendir `+`, `-`, `*`, `/`, ve `new`. Değişmez değerler, alanlar, yerel değişkenleri ve ifadeler işlenenler örneklerindendir.

Bir ifade birden çok işleç içerdiğinde *öncelik* işleçleri tek tek işleçleri değerlendirilir sırasını denetler. Örneğin, ifade `x + y * z` olarak değerlendirilir `x + (y * z)` çünkü `*` daha yüksek önceliğe sahip `+` işleci.

İşleneni aynı önceliğe sahip iki işleç arasında oluştuğunda *birleşim* operatörleri işlemler gerçekleştirilir sırasını denetler:

*   Atama işleçleri hariç tüm ikili işleçler şunlardır: *sola ilişkilendirilebilir*, işlemler soldan sağa gerçekleştirilir anlamına gelir. Örneğin, `x + y + z` olarak değerlendirilir `(x + y) + z`.
*   Atama işleçleri ve koşullu işleç (`?:`) olan *sağa ilişkilendirilebilir*, işlemler arasında sağdan sola gerçekleştirilir anlamına gelir. Örneğin, `x = y = z` olarak değerlendirilir `x = (y = z)`.

Öncelik ve birleşim parantez kullanılarak denetlenebilir. Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve sonucu ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonuç olarak çoğaltır `z`.

Çoğu işleçleri olabilir *aşırı*. İşleç aşırı yüklemesi, birini veya her ikisini işlenen kullanıcı tanımlı sınıfta veya yapı türü nerede işlemleri için belirtilmesi için kullanıcı tanımlı işleci uygulamaları izin verir.

Yüksekten en düşüğe öncelik sırasına işleci kategorilerini liste C# ' ın işleçleri, aşağıda özetlenmiştir. Aynı kategoride operatörleri eşit önceliğe sahiptir. Her kategori altında bu ifade türünün açıklaması yanı sıra bu kategorideki ifadeleri listesidir.

* birincil
    - `x.m`: Üye erişimi
    - `x(...)`: Yöntemi ve temsilci çağırma
    - `x[...]`: Dizi ve dizin oluşturucu erişim
    - `x++`: Sonrası artırma
    - `x--`: Sonrası azaltma
    - `new T(...)`: Nesne ve temsilci oluşturma
    - `new T(...){...}`: Başlatıcısı ile nesne oluşturma
    - `new {...}`: Anonim nesne Başlatıcı
    - `new T[...]`: Dizi oluşturma
    - `typeof(T)`: Elde <xref:System.Type> nesnesi `T`
    - `checked(x)`: Checked bağlamda ifade değerlendirme
    - `unchecked(x)`: Denetlenmeyen bağlamda ifade değerlendirme
    - `default(T)`: Türü varsayılan değerini edinme `T`
    - `delegate {...}`: Anonim işlevi (anonim yöntemi)
* Birli
    - `+x`: Kimlik
    - `-x`: Değilleme
    - `!x`: Mantıksal olumsuzlaştırma
    - `~x`: Bit tabanlı değil işlecini
    - `++x`: Ön artırma
    - `--x`: Ön azaltma
    - `(T)x`: Açıkça dönüştürme `x` yazmak için `T`
    - `await x`: Zaman uyumsuz olarak bekleyin `x` tamamlamak için
* Çarpma
    - `x * y`: Çarpma
    - `x / y`: Bölme
    - `x % y`: Kalan
* ADDITIVE
    - `x + y`: Eklenmesi, dize birleştirme, temsilci birleşimi
    - `x – y`: Çıkarma, temsilci kaldırma
* Kaydırma
    - `x << y`: Shift sol
    - `x >> y`: Sağa kaydırma
* İlişkisel ve türü test etme
    - `x < y`: Küçüktür
    - `x > y`: Büyüktür
    - `x <= y`: Küçüktür veya eşittir
    - `x >= y`: Büyüktür veya eşittir
    - `x is T`: Dönüş `true` varsa `x` olan bir `T`, `false` Aksi takdirde
    - `x as T`: Dönüş `x` olarak yazılan `T`, veya `null` varsa `x` değil bir `T`
* Eşitlik
    - `x == y`: Eşit
    - `x != y`: Eşit değil
* Mantıksal VE
    - `x & y`: Tamsayı Bitsel ve, Boole mantıksal ve
* Mantıksal XOR
    - `x ^ y`: Bit düzeyinde XOR tamsayı, boolean mantıksal XOR
* Mantıksal VEYA
    - `x | y`: Tamsayı Bitsel veya boolean mantıksal OR
* Koşullu VE
    - `x && y`: Hesaplar `y` yalnızca `x` değil `false`
* Koşullu VEYA
    - `x || y`: Hesaplar `y` yalnızca `x` değil `true`
* Null birleşim
    - `x ?? y`: Değerlendiren `y` varsa `x` için null `x` Aksi takdirde
* Koşullu
    - `x ? y : z`: Hesaplar `y` varsa `x` olan `true`, `z` varsa `x` olduğu `false`
* Atama veya anonim işlevi
    - `x = y`: Atama
    - `x op= y`: Bileşik atama; desteklenen işleçler şunlardır:
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: Anonim işlevi (lambda ifadesi)

>[!div class="step-by-step"]
[Önceki](types-and-variables.md)
[sonraki](statements.md)
