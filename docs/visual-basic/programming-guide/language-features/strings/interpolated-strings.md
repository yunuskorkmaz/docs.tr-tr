---
title: Enterpolasyonlu dizeler
ms.date: 10/31/2017
ms.openlocfilehash: c427b48ce58a59ff3878f24f1989db6ac8c8239a
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805284"
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

- *Biçim-dize* , biçimlendirilen nesne türüne uygun bir biçim dizesidir. Örneğin, bir değer için <xref:System.DateTime> , "d" veya "d" gibi [Standart Tarih ve saat biçimi dizesi](../../../../standard/base-types/standard-date-and-time-format-strings.md) olabilir.

> [!IMPORTANT]
> `$`Ve arasında `"` dize Başlatan boşluk olamaz. Bunun yapılması bir derleyici hatasına neden olur.

Bir dize sabit değeri kullanabileceğiniz her yerde enterpolasyonlu bir dize kullanabilirsiniz.  Enterpolasyonlu dize, enterpolasyonlu dize her çalıştırıldığında değerlendirilir. Bu, enterpolasyonlu bir dizenin tanımını ve değerlendirmesini ayırmanızı sağlar.

Bir küme ayracı ("{" veya "}"), enterpolasyonlu bir dizeye eklemek için, iki küme ayracı kullanın, "{{" veya "}}".  Daha fazla bilgi için örtük dönüşümler bölümüne bakın.

Enterpolasyonlu dize, ara değer ("), iki nokta üst üste (:) veya virgül (,) gibi, enterpolasyonlu bir dizede özel anlamı olan başka karakterler içeriyorsa, sabit metin halinde gerçekleştiklerinde kaçışlar veya enterpolasyonlu bir ifadeye dahil edilen bir ifadeye dahil edilmesi gerekir. Aşağıdaki örnek, sonuç dizesine dahil etmek için tırnak işaretleri çıkar:

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Örtük dönüştürmeler

Enterpolasyonlu bir dizeden üç örtük tür dönüştürmesi vardır:

1. Enterpolasyonlu bir dizenin öğesine dönüştürülmesi <xref:System.String> . Aşağıdaki örnek, enterpolasyonlu dize ifadeleri dize gösterimleriyle değiştirilmiş olan bir dize döndürür. Örnek:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Bu, bir dize yorumlamasının nihai sonucudur. Çift küme ayracı ("{{" ve "}}") tüm oluşumları tek bir küme ayracına dönüştürülür.

2. <xref:System.IFormattable>Tek bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza izin veren bir değişkene, enterpolasyonlu bir dizenin dönüştürülmesi <xref:System.IFormattable> . Bu, bireysel kültürler için doğru sayısal ve tarih biçimleri gibi şeyleri dahil etmek için kullanışlıdır.  Çift küme ayracı ("{{" ve "}}") tüm oluşumları, yöntemi açıkça veya örtük olarak çağırarak, dizeyi biçimlendirene kadar çift küme ayraçları olarak kalır <xref:System.Object.ToString> .  İçerilen tüm enterpolasyon ifadeleri {0} ,, vb. olarak dönüştürülür {1} .

   Aşağıdaki örnek, öğeleri ve <xref:System.IFormattable> enterpolasyonlu bir dizeden oluşturulan bir değişkenin alan ve özellik değerlerini göstermek için yansıma kullanır. Ayrıca, <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine geçirir.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Enterpolasyonlu dize yalnızca yansıma kullanılarak incelenebileceğini unutmayın. Bir dize biçimlendirme yöntemine (örneğin,) geçirilirse <xref:System.Console.WriteLine(System.String)> , biçim öğeleri çözümlenir ve sonuç dizesi döndürülür.

3. Enterpolasyonlu bir dizenin <xref:System.FormattableString> bileşik biçim dizesini temsil eden bir değişkene dönüştürülmesi. Bileşik biçim dizesini ve bunun sonuç dizesi olarak nasıl işlediğini incelemek, örneğin bir sorgu oluşturuyorsanız ekleme saldırısından korunmanıza yardımcı olabilir. <xref:System.FormattableString>Ayrıca şunları içerir:

      - <xref:System.FormattableString.ToString>İçin sonuç dizesi üreten bir aşırı yükleme <xref:System.Globalization.CultureInfo.CurrentCulture> .

      - <xref:System.FormattableString.Invariant%2A>İçin bir dize üreten bir yöntem <xref:System.Globalization.CultureInfo.InvariantCulture> .

      - <xref:System.FormattableString.ToString(System.IFormatProvider)>Belirtilen kültür için sonuç dizesi üreten bir yöntem.

    Çift küme ayracı ("{{" ve "}}") tüm oluşumları, biçimlendirene kadar çift küme ayraçları olarak kalır.  İçerilen tüm enterpolasyon ifadeleri {0} ,, vb. olarak dönüştürülür {1} .

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Visual Basic dil başvurusu](index.md)
