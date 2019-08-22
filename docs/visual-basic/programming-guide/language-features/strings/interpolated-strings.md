---
title: Enterpolasyonlu dizeler (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: b9dd055154c86da370a984a465ed412f1fd9908c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666946"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Enterpolasyonlu dizeler (Visual Basic Başvurusu)

Dizeleri oluşturmak için kullanılır.  Bir ara değerli dize, *enterpolasyonlu ifadeler*içeren bir şablon dizesi gibi görünür.  Bir enterpolasyonlu dize, içerdiği ilişkili ifadelerin dize gösterimleriyle yerini alan bir dize döndürür. Bu özellik Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.

Enterpolasyonlu bir dizenin bağımsız değişkenleri bir [bileşik biçim dizesinden](../../../../standard/base-types/composite-formatting.md#composite-format-string)daha kolay anlaşılır.  Örneğin, enterpolasyonlu dize

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

' {name} ' ve ' {hours: hh} ' adlı iki enterpolasyonlu ifade içeriyor. Eşdeğer bileşik biçim dizesi:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

Enterpolasyonlu bir dizenin yapısı:

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

burada:

- *alan genişliği* , alandaki karakter sayısını gösteren işaretli bir tamsayıdır. Pozitif ise, alan sağa hizalanır; negatif ise, sola hizalı.

- *Biçim-dize* , biçimlendirilen nesne türüne uygun bir biçim dizesidir. Örneğin, bir <xref:System.DateTime> değer için, "d" veya "d" gibi [Standart Tarih ve saat biçimi dizesi](../../../../standard/base-types/standard-date-and-time-format-strings.md) olabilir.

> [!IMPORTANT]
> `$` Ve arasındadizeBaşlatanboşlukolamaz.`"` Bunun yapılması bir derleyici hatasına neden olur.

Bir dize sabit değeri kullanabileceğiniz her yerde enterpolasyonlu bir dize kullanabilirsiniz.  Enterpolasyonlu dize, enterpolasyonlu dize her çalıştırıldığında değerlendirilir. Bu, enterpolasyonlu bir dizenin tanımını ve değerlendirmesini ayırmanızı sağlar.

Bir küme ayracı ("{" veya "}"), enterpolasyonlu bir dizeye eklemek için, iki küme ayracı kullanın, "{{" veya "}}".  Daha fazla bilgi için örtük dönüşümler bölümüne bakın.

Enterpolasyonlu dize, ara değer ("), iki nokta üst üste (:) veya virgül (,) gibi, enterpolasyonlu bir dizede özel anlamı olan başka karakterler içeriyorsa, sabit metin halinde gerçekleştiklerinde kaçışlar veya şu şekilde ayrılmış bir ifadeye dahil edilmesi gerekir Bu değerler, enterpolasyonlu bir ifadeye dahil edilen dil öğelerseler parantez. Aşağıdaki örnek, sonuç dizesine dahil etmek için tırnak işaretleri çıkar ve iki nokta üst üste bir biçim dizesine kadar yorumlanmaması için `(age == 1 ? "" : "s")` ifadeyi sınırlandırmak için ayraçları kullanır.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Örtük dönüşümler

Enterpolasyonlu bir dizeden üç örtük tür dönüştürmesi vardır:

1. Enterpolasyonlu bir <xref:System.String>dizenin öğesine dönüştürülmesi. Aşağıdaki örnek, enterpolasyonlu dize ifadeleri dize gösterimleriyle değiştirilmiş olan bir dize döndürür. Örneğin:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Bu, bir dize yorumlamasının nihai sonucudur. Çift küme ayracı ("{{" ve "}}") tüm oluşumları tek bir küme ayracına dönüştürülür.

2. <xref:System.IFormattable> Tek<xref:System.IFormattable> bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza izin veren bir değişkene, enterpolasyonlu bir dizenin dönüştürülmesi. Bu, bireysel kültürler için doğru sayısal ve tarih biçimleri gibi şeyleri dahil etmek için kullanışlıdır.  Çift küme ayracı ("{{" ve "}}") tüm oluşumları, <xref:System.Object.ToString> yöntemi açıkça veya örtük olarak çağırarak, dizeyi biçimlendirene kadar çift küme ayraçları olarak kalır.  İçerilen tüm enterpolasyon ifadeleri {0}, {1}, vb. olarak dönüştürülür.

   Aşağıdaki örnek, öğeleri ve enterpolasyonlu bir dizeden oluşturulan bir <xref:System.IFormattable> değişkenin alan ve özellik değerlerini göstermek için yansıma kullanır. Ayrıca, <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine geçirir.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Enterpolasyonlu dize yalnızca yansıma kullanılarak incelenebileceğini unutmayın. Bir dize biçimlendirme yöntemine (örneğin <xref:System.Console.WriteLine(System.String)>,) geçirilirse, biçim öğeleri çözümlenir ve sonuç dizesi döndürülür.

3. Enterpolasyonlu bir dizenin bileşik <xref:System.FormattableString> biçim dizesini temsil eden bir değişkene dönüştürülmesi. Bileşik biçim dizesini ve bunun sonuç dizesi olarak nasıl işlediğini incelemek, örneğin bir sorgu oluşturuyorsanız ekleme saldırısından korunmanıza yardımcı olabilir. <xref:System.FormattableString> Ayrıca şunları içerir:

      - İçin sonuç dizesi üreten bir <xref:System.FormattableString.ToString> aşırı yükleme. <xref:System.Globalization.CultureInfo.CurrentCulture>

      - İçin bir dize üreten bir <xref:System.FormattableString.Invariant%2A> yöntem. <xref:System.Globalization.CultureInfo.InvariantCulture>

      - Belirtilen <xref:System.FormattableString.ToString(System.IFormatProvider)> kültür için sonuç dizesi üreten bir yöntem.

    Çift küme ayracı ("{{" ve "}}") tüm oluşumları, biçimlendirene kadar çift küme ayraçları olarak kalır.  İçerilen tüm enterpolasyon ifadeleri {0}, {1}, vb. olarak dönüştürülür.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Visual Basic Dili Başvurusu](index.md)
