---
title: Ara Değerli Dizeler
ms.date: 10/31/2017
ms.openlocfilehash: d1220f3804d571f6da229dc5dfa099a22ab1478d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344320"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Enterpolasyonlu dizeler (Visual Basic Başvurusu)

Dizeleri oluşturmak için kullanılır.  Bir ara değerli dize, *enterpolasyonlu ifadeler*içeren bir şablon dizesi gibi görünür.  Bir enterpolasyonlu dize, içerdiği ilişkili ifadelerin dize gösterimleriyle yerini alan bir dize döndürür. Bu özellik Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.

Enterpolasyonlu bir dizenin bağımsız değişkenleri bir [bileşik biçim dizesinden](../../../../standard/base-types/composite-formatting.md#composite-format-string)daha kolay anlaşılır.  Örneğin, enterpolasyonlu dize

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

' {name} ' ve ' {hours: hh} ' adlı iki enterpolasyonlu ifade içeriyor. Eşdeğer bileşik biçim dizesi:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

Enterpolasyonlu bir dizenin yapısı:

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

burada:

- *alan genişliği* , alandaki karakter sayısını gösteren işaretli bir tamsayıdır. Pozitif ise, alan sağa hizalanır; negatif ise, sola hizalı.

- *Biçim-dize* , biçimlendirilen nesne türüne uygun bir biçim dizesidir. Örneğin, bir <xref:System.DateTime> değeri için, "D" veya "d" gibi [Standart Tarih ve saat biçimi dizesi](../../../../standard/base-types/standard-date-and-time-format-strings.md) olabilir.

> [!IMPORTANT]
> `$` ile dizeyi Başlatan `"` arasında boşluk olamaz. Bunun yapılması bir derleyici hatasına neden olur.

Bir dize sabit değeri kullanabileceğiniz her yerde enterpolasyonlu bir dize kullanabilirsiniz.  Enterpolasyonlu dize, enterpolasyonlu dize her çalıştırıldığında değerlendirilir. Bu, enterpolasyonlu bir dizenin tanımını ve değerlendirmesini ayırmanızı sağlar.

Bir küme ayracı ("{" veya "}"), enterpolasyonlu bir dizeye eklemek için, iki küme ayracı kullanın, "{{" veya "}}".  Daha fazla bilgi için örtük dönüşümler bölümüne bakın.

Enterpolasyonlu dize, ara değer ("), iki nokta üst üste (:) veya virgül (,) gibi, enterpolasyonlu bir dizede özel anlamı olan başka karakterler içeriyorsa, sabit metin halinde gerçekleştiklerinde kaçışlar veya şu şekilde ayrılmış bir ifadeye dahil edilmesi gerekir Bu değerler, enterpolasyonlu bir ifadeye dahil edilen dil öğelerseler parantez. Aşağıdaki örnek, sonuç dizesine dahil etmek için tırnak işaretleri çıkar ve iki nokta üst üste bir biçim dizesine kadar yorumlanmaması için `(age == 1 ? "" : "s")` ifadeyi sınırlandırmak için ayraçları kullanır.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Örtük dönüşümler

Enterpolasyonlu bir dizeden üç örtük tür dönüştürmesi vardır:

1. Enterpolasyonlu bir dizenin <xref:System.String>dönüşümü. Aşağıdaki örnek, enterpolasyonlu dize ifadeleri dize gösterimleriyle değiştirilmiş olan bir dize döndürür. Örneğin:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Bu, bir dize yorumlamasının nihai sonucudur. Çift küme ayracı ("{{" ve "}}") tüm oluşumları tek bir küme ayracına dönüştürülür.

2. Tek bir <xref:System.IFormattable> örneğinden kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza izin veren bir <xref:System.IFormattable> değişkenine bir ara değerli dizenin dönüştürülmesi. Bu, bireysel kültürler için doğru sayısal ve tarih biçimleri gibi şeyleri dahil etmek için kullanışlıdır.  Çift küme ayracı ("{{" ve "}}") tüm oluşumları, dizeyi açıkça veya dolaylı olarak <xref:System.Object.ToString> yöntemi çağırarak biçimlendirene kadar çift küme ayraçları olarak kalır.  İçerilen tüm enterpolasyon ifadeleri {0}, {1}ve benzeri olarak dönüştürülür.

   Aşağıdaki örnek, üyeleri ve enterpolasyonlu bir dizeden oluşturulan <xref:System.IFormattable> değişkeninin alan ve özellik değerlerini göstermek için yansıma kullanır. Ayrıca, <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine geçirir.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Enterpolasyonlu dize yalnızca yansıma kullanılarak incelenebileceğini unutmayın. <xref:System.Console.WriteLine(System.String)>gibi bir dize biçimlendirme yöntemine geçirilirse, biçim öğeleri çözümlenir ve sonuç dizesi döndürülür.

3. Enterpolasyonlu bir dizenin bir bileşik biçim dizesini temsil eden <xref:System.FormattableString> değişkenine dönüştürülmesi. Bileşik biçim dizesini ve bunun sonuç dizesi olarak nasıl işlediğini incelemek, örneğin bir sorgu oluşturuyorsanız ekleme saldırısından korunmanıza yardımcı olabilir. <xref:System.FormattableString> ayrıca şunları içerir:

      - <xref:System.Globalization.CultureInfo.CurrentCulture>için sonuç dizesi üreten <xref:System.FormattableString.ToString> aşırı yükleme.

      - <xref:System.Globalization.CultureInfo.InvariantCulture>için bir dize üreten <xref:System.FormattableString.Invariant%2A> yöntemi.

      - Belirtilen kültür için sonuç dizesi üreten <xref:System.FormattableString.ToString(System.IFormatProvider)> yöntemi.

    Çift küme ayracı ("{{" ve "}}") tüm oluşumları, biçimlendirene kadar çift küme ayraçları olarak kalır.  İçerilen tüm enterpolasyon ifadeleri {0}, {1}ve benzeri olarak dönüştürülür.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Visual Basic Dili Başvurusu](index.md)
