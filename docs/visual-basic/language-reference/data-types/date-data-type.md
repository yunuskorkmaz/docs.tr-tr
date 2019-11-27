---
title: Date Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: 972df72874753a0f1213f3a4942468c59e3913ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344022"
---
# <a name="date-data-type-visual-basic"></a>Date Veri Türü (Visual Basic)

0001 yılının 1 Ocak ayının 9999 31 Aralık 12:00:00 'a kadar (gece yarısı), 11:59:59.9999999 PM arasında değişen tarihleri temsil eden IEEE 64-bit (8 baytlık) değerleri barındırır. Her artış, Gregoryen takvimdeki 1 Ocak yılın başından itibaren geçen sürenin 100 nanosaniye süresini temsil eder. Maksimum değer 100, 1 Ocak 10000 yılın başından önce nanosaniye 'yi temsil eder.

## <a name="remarks"></a>Açıklamalar

Tarih değerlerini, zaman değerlerini veya tarih ve saat değerlerini içermesi için `Date` veri türünü kullanın.

`Date` varsayılan değeri 1 Ocak 0001 tarihinde 0:00:00 (gece yarısı) değeridir.

<xref:Microsoft.VisualBasic.DateAndTime> sınıfından geçerli tarih ve saati alabilirsiniz.

## <a name="format-requirements"></a>Biçim gereksinimleri

`Date` değişmez değeri sayı işaretleri (`# #`) içine alınmalıdır. Tarih değerini M/d/yyyy biçiminde belirtmeniz gerekir, örneğin `#5/31/1993#`veya yyyy-aa-gg, örneğin `#1993-5-31#`. Önce yılı belirtirken eğik çizgi kullanabilirsiniz.  Bu gereksinim, yerel ayarınızı ve bilgisayarınızın tarih ve saat biçimi ayarlarını birbirinden bağımsızdır.

Bu kısıtlamanın nedeni, kodunuzun anlamını uygulamanızın çalıştırıldığı yerel ayara bağlı olarak asla değiştirmemelidir. `Date` bir `#3/4/1998#` sabit kodladığınızı ve 4 Mart 1998 ' den itibaren olduğunu varsayalım. Aa/gg/yyyy kullanan bir yerel ayarda, 3/4/1998 istediğiniz şekilde derlenir. Ancak uygulamanızı birçok ülkede/bölgede dağıttığınız varsayın. Gg/aa/yyyy kullanan bir yerel ayarda, sabit kodlanmış sabit değer 3 Nisan 1998 ' e derlenir. Yyyy/aa/gg kullanan bir yerel ayarda, değişmez değer geçersiz (1998 Nisan, 0003) ve bir derleyici hatasına neden olur.

## <a name="workarounds"></a>Geçici Çözümler

Bir `Date` sabit değerini yerel ayarınızdaki biçime veya özel bir biçime dönüştürmek için, önceden tanımlanmış veya Kullanıcı tanımlı bir tarih biçimi belirterek, <xref:Microsoft.VisualBasic.Strings.Format%2A> işlevine değişmez değer sağlayın. Aşağıdaki örnek bunu gösterir.

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

Alternatif olarak, bir tarih ve saat değerini birleştirmek için <xref:System.DateTime> yapısının aşırı yüklenmiş oluşturucularından birini kullanabilirsiniz. Aşağıdaki örnek, öğleden sonra 31 Mayıs 12:14 1993 ' i temsil eden bir değer oluşturur.

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a>Saat biçimi

Saat değerini 12 saat veya 24 saat biçiminde belirtebilirsiniz, örneğin `#1:15:30 PM#` veya `#13:15:30#`. Ancak, dakikalar veya saniyeler belirtmezseniz, har veya PM belirtmeniz gerekir.

## <a name="date-and-time-defaults"></a>Tarih ve saat Varsayılanları

Tarih/saat değişmez değerinde bir tarih eklemezseniz, Visual Basic değerin tarih bölümünü 1 Ocak 0001 olarak ayarlar. Tarih/saat değişmez değerinde bir saat eklemezseniz, Visual Basic değerin saat bölümünü günün başına, yani gece yarısı (0:00:00) olarak ayarlar.

## <a name="type-conversions"></a>Tür Dönüştürmeleri

Bir `Date` değerini `String` türüne dönüştürürseniz Visual Basic, tarihi çalışma zamanı yerel ayarı tarafından belirtilen kısa tarih biçimine göre işler ve saati çalışma zamanı yerel ayarı tarafından belirtilen saat biçimine (12 saat veya 24 saat) göre işler.

## <a name="programming-tips"></a>Programlama İpuçları

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlardaki tarih/saat türlerinin Visual Basic `Date` türüyle uyumlu olmadığını aklınızda bulundurun. Böyle bir bileşene bir tarih/saat bağımsız değişkeni geçirdiğinizden, bunu yeni Visual Basic kodunuzda `Date` yerine `Double` olarak bildirin ve <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>dönüştürme yöntemlerini kullanın.

- **Tür karakterleri.** `Date` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok. Ancak derleyici, sayıları sayı işaretleri (`# #`) içinde `Date`olarak değerlendirir.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.DateTime?displayProperty=nameWithType> yapısıdır.

## <a name="example"></a>Örnek

`Date` veri türünün bir değişkeni veya sabiti hem tarihi hem de saati tutar. Aşağıdaki örnek bunu göstermektedir.

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
