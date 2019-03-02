---
title: C#İfadeleri - Turu C# dil
description: ifadeleri ve işlenenleri işleçleri olan yapı taşları C# dil
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 682f98d51bf4eb3c1641297972afb86956e06d3e
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212098"
---
# <a name="expressions"></a>İfadeler

*İfadeleri* oluşturulan *işlenenler* ve *işleçleri*. İfade işleçleri işlenenlere uygulamak için hangi işlemleri gösterir. İşleçler örnekler `+`, `-`, `*`, `/`, ve `new`. Değişmez değerler, alanlar, yerel değişkenleri ve ifadeleri işlenenler örnekleridir.

Bir ifade birden çok işleç içeren *öncelik* işleçleri tek tek işleçler değerlendirilme sırası denetler. Örneğin, ifade `x + y * z` değerlendirmesinde `x + (y * z)` çünkü `*` işleci daha yüksek önceliğe sahip `+` işleci.

Bir işlenen aynı önceliğe sahip iki işleç arasında gerçekleştiğinde *ilişkilendirilebilirliği* operatörleri işlemleri gerçekleştirilir sırasını denetler:

*   Atama işleçleri hariç tüm ikili işleçler şunlardır *ilişkilendirilebilir*, yani işlemler soldan sağa doğru gerçekleştirilir. Örneğin, `x + y + z` değerlendirmesinde `(x + y) + z`.
*   Atama işleçleri ve koşullu işleç (`?:`) olan *sağla ilişkilendirilebilir*, sağdan sola işlemler gerçekleştirilir anlamına gelir. Örneğin, `x = y = z` değerlendirmesinde `x = (y = z)`.

Öncelik ve ilişkisellik parantez kullanılarak denetlenebilir. Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve ardından sonuca ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonucu çarpan `z`.

Çoğu işleçleri olabilir *aşırı*. İşleç aşırı yüklemesi, aşağıdakilerden birini veya her iki işlenen kullanıcı tanımlı sınıf veya yapı türü olduğu işlemlerinde belirtilmesi için kullanıcı tanımlı işleç uygulamalarına izin verir.

Aşağıdaki özetler C#'s işleçlerini, en düşük yüksekten öncelik sırasına işleci kategorileri listeleme. Aynı kategoride işleçleri eşit önceliğe sahiptir. Her kategori altında bu ifade türünün açıklaması ile birlikte bu kategorideki ifadeleri listesidir.

* Birincil
    - `x.m`: Üye erişimi
    - `x(...)`: Yöntem ve temsilci çağırma
    - `x[...]`: Dizi ve dizinleyici erişimi
    - `x++`: Artırım sonrası
    - `x--`: Azaltım sonrası
    - `new T(...)`: Nesne ve temsilci oluşturma
    - `new T(...){...}`: Başlatıcı ile nesne oluşturma
    - `new {...}`:  Anonim nesne Başlatıcı
    - `new T[...]`: Dizi oluşturma
    - `typeof(T)`: Elde <xref:System.Type> nesnesi `T`
    - `checked(x)`: İşaretli bağlamında ifade değerlendirme
    - `unchecked(x)`: İşaretlenmemiş bağlamında ifade değerlendirme
    - `default(T)`: Türünün varsayılan değerini alın `T`
    - `delegate {...}`: Anonim işlevi (anonim yöntemi)
* Birli
    - `+x`: Kimlik
    - `-x`: Olumsuzlama
    - `!x`: Mantıksal olumsuzlama
    - `~x`: Bitwise olumsuzlama
    - `++x`: Artırım öncesi
    - `--x`: Azaltım öncesi
    - `(T)x`: Açıkça dönüştürmek `x` yazmak için `T`
    - `await x`: Zaman uyumsuz olarak bekleyin `x` tamamlamak için
* Çarpma
    - `x * y`: Çarpma
    - `x / y`: Bölme
    - `x % y`: Kalan
* Eklenebilir
    - `x + y`: Toplama, dize bitiştirme, temsilci birleşimi
    - `x – y`: Çıkarma, temsilci kaldırma
* Shift
    - `x << y`: Sola kaydırma
    - `x >> y`: Sağa kaydırma
* İlişkisel ve tür testi
    - `x < y`: Küçüktür
    - `x > y`: Büyüktür
    - `x <= y`: Küçük veya eşittir
    - `x >= y`: Büyük veya eşittir
    - `x is T`: Dönüş `true` varsa `x` olduğu bir `T`, `false` Aksi takdirde
    - `x as T`: Dönüş `x` olarak yazılan `T`, veya `null` varsa `x` değil bir `T`
* Eşitlik
    - `x == y`: Eşittir
    - `x != y`: Eşit değildir
* Mantıksal VE
    - `x & y`: Tamsayı bitwise ve, boolean mantıksal ve
* Mantıksal XOR
    - `x ^ y`: Tamsayı bitwise XOR, Boolean mantıksal XOR
* Mantıksal VEYA
    - `x | y`: Tamsayı bitwise VEYA, boolean mantıksal VEYA
* Koşullu VE
    - `x && y`: Değerlendirilen `y` yalnızca `x` değil `false`
* Koşullu VEYA
    - `x || y`: Değerlendirilen `y` yalnızca `x` değil `true`
* Null birleşim
    - `x ?? y`: Değerlendiren `y` varsa `x` için null `x` Aksi takdirde
* Koşullu
    - `x ? y : z`: Değerlendirir `y` varsa `x` olduğu `true`, `z` varsa `x` olduğu `false`
* Atama ve anonim işlev
    - `x = y`: Atama
    - `x op= y`: Bileşik atama; desteklenen işleçler şunlardır:
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: Anonim işlevi (lambda ifadesi)

> [!div class="step-by-step"]
> [Önceki](types-and-variables.md)
> [İleri](statements.md)