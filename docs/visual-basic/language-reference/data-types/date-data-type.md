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
ms.openlocfilehash: 46c25e14db56d4cc3c6d59ec7649b37c35676e2e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387432"
---
# <a name="date-data-type-visual-basic"></a>Date Veri Türü (Visual Basic)

0001 yılının 1 Ocak ayının 9999 31 Aralık 12:00:00 'a kadar (gece yarısı), 11:59:59.9999999 PM arasında değişen tarihleri temsil eden IEEE 64-bit (8 baytlık) değerleri barındırır. Her artış, Gregoryen takvimdeki 1 Ocak yılın başından itibaren geçen sürenin 100 nanosaniye süresini temsil eder. Maksimum değer 100, 1 Ocak 10000 yılın başından önce nanosaniye 'yi temsil eder.

## <a name="remarks"></a>Açıklamalar

`Date`Tarih değerlerini, zaman değerlerini veya tarih ve saat değerlerini içermesi için veri türünü kullanın.

`Date`1 Ocak 0001 tarihinde varsayılan değer 0:00:00 ' dir (gece yarısı).

Geçerli tarih ve saati <xref:Microsoft.VisualBasic.DateAndTime> sınıftan alabilirsiniz.

## <a name="format-requirements"></a>Biçim gereksinimleri

Bir `Date` sabit değeri sayı işaretleri () içine almalısınız `# #` . Tarih değerini M/d/yyyy biçiminde belirtmeniz gerekir, örneğin `#5/31/1993#` veya yyyy-aa-gg gibi `#1993-5-31#` . Önce yılı belirtirken eğik çizgi kullanabilirsiniz.  Bu gereksinim, yerel ayarınızı ve bilgisayarınızın tarih ve saat biçimi ayarlarını birbirinden bağımsızdır.

Bu kısıtlamanın nedeni, kodunuzun anlamını uygulamanızın çalıştırıldığı yerel ayara bağlı olarak asla değiştirmemelidir. Bir sabit `Date` değer `#3/4/1998#` kodladığınızı ve 4 Mart 1998 ' den itibaren olduğunu varsayalım. Aa/gg/yyyy kullanan bir yerel ayarda, 3/4/1998 istediğiniz şekilde derlenir. Ancak uygulamanızı birçok ülkede/bölgede dağıttığınız varsayın. Gg/aa/yyyy kullanan bir yerel ayarda, sabit kodlanmış sabit değer 3 Nisan 1998 ' e derlenir. Yyyy/aa/gg kullanan bir yerel ayarda, değişmez değer geçersiz (1998 Nisan, 0003) ve bir derleyici hatasına neden olur.

## <a name="workarounds"></a>Geçici Çözümler

Bir `Date` sabit değeri yerel ayarınızdaki biçime veya özel bir biçime dönüştürmek için, <xref:Microsoft.VisualBasic.Strings.Format%2A> önceden tanımlanmış veya Kullanıcı tanımlı bir tarih biçimini belirterek, işleve değişmez değeri sağlayın. Aşağıdaki örnek bunu gösterir.

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

Alternatif olarak, <xref:System.DateTime> bir tarih ve saat değerini birleştirmek için yapının aşırı yüklenmiş oluşturucularından birini de kullanabilirsiniz. Aşağıdaki örnek, öğleden sonra 31 Mayıs 12:14 1993 ' i temsil eden bir değer oluşturur.

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a>Saat biçimi

Saat değerini 12 saat veya 24 saat biçiminde belirtebilirsiniz, örneğin `#1:15:30 PM#` veya `#13:15:30#` . Ancak, dakikalar veya saniyeler belirtmezseniz, har veya PM belirtmeniz gerekir.

## <a name="date-and-time-defaults"></a>Tarih ve saat Varsayılanları

Tarih/saat değişmez değerinde bir tarih eklemezseniz, Visual Basic değerin tarih bölümünü 1 Ocak 0001 olarak ayarlar. Tarih/saat değişmez değerinde bir saat eklemezseniz, Visual Basic değerin saat bölümünü günün başına, yani gece yarısı (0:00:00) olarak ayarlar.

## <a name="type-conversions"></a>Tür Dönüştürmeleri

Bir `Date` değeri `String` türüne dönüştürürseniz Visual Basic, tarihi çalışma zamanı yerel ayarı tarafından belirtilen kısa tarih biçimine göre işler ve saati çalışma zamanı yerel ayarı tarafından belirtilen saat biçimine (12 saat veya 24 saat) göre işler.

## <a name="programming-tips"></a>Programlama İpuçları

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlardaki tarih/saat türlerinin Visual Basic türüyle uyumlu olmadığını aklınızda bulundurun `Date` . Böyle bir bileşene bir tarih/saat bağımsız değişkeni geçirdiğinizden, bunu `Double` yeni Visual Basic kodunuzda değil olarak bildirin `Date` ve dönüştürme yöntemlerini <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve kullanın <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType> .

- **Tür karakterleri.** `Date`değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok. Ancak derleyici, sayıları sayı işaretleri () içinde olarak değerlendirir `# #` `Date` .

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.DateTime?displayProperty=nameWithType> yapısıdır.

## <a name="example"></a>Örnek

Veri türünün bir değişkeni veya sabiti `Date` hem tarih hem de saati tutar. Aşağıdaki örnek bunu göstermektedir.

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime?displayProperty=nameWithType>
- [Veri türleri](index.md)
- [Standart Tarih ve saat biçim dizeleri](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [Özel tarih ve saat biçim dizeleri](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
