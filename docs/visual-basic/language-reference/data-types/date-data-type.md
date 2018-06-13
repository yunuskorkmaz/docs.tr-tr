---
title: Date Veri Türü (Visual Basic)
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
ms.openlocfilehash: b7827206d6e145b559d9716df5ec4a98ac4ea0b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591826"
---
# <a name="date-data-type-visual-basic"></a>Date Veri Türü (Visual Basic)
1 Ocak 0001-31 Aralık 9999 yılın yılın arasında değişen tarih ve saat 12:00: 00'da (gece yarısı) temsil eden IEEE 64-bit (8-bayt) değerleri PM 11:59:59.9999999 tutar. Her artış başlayarak Gregoryen takvim 1 yılının 1 Ocak 100 nanosaniye geçen süreyi temsil eder. En yüksek değer 100 nanosaniye başlangıcından 10000 yılın 1 Ocak önce temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Date` veri türü tarih değerleri, saat değerleri veya tarih ve saat değerlerini içerir.  
  
 Varsayılan değer olan `Date` 0:1 Ocak 0001 00:00 (gece yarısı).  
  
 Geçerli tarih ve saati alabilirsiniz <xref:Microsoft.VisualBasic.DateAndTime> sınıfı.  
  
## <a name="format-requirements"></a>Biçim gereksinimleri  
 İçine almalısınız bir `Date` sayı işaretleri içinde değişmez değer (`# #`). Örneğin g/yyyy biçiminde tarih değeri belirtmelisiniz `#5/31/1993#`, veya yyyy-aa-gg, örneğin `#1993-5-31#`. Yılın ilk belirtirken, eğik çizgi kullanabilirsiniz.  Bu gereksinim, bölgeniz ve bilgisayarınızın tarih ve saat biçim ayarları bağımsızdır.  
  
 Bu kısıtlama kodunuzu anlamı, uygulamanızın çalıştığı yerel ayara bağlı olarak hiçbir zaman değiştirmeniz gerektiğini nedeni. Sabit kodlu varsayalım bir `Date` , değişmez değer `#3/4/1998#` ve 4 Mart 1998 anlama kendisine planlıyorsunuz. Düşündüğünüz olarak aa/gg/yyyy kullanan bir yerel ayarda 4/3/1998 derler. Ancak birçok ülkede uygulamanızı dağıtmak varsayalım. Aa/gg/yyyy kullanan bir yerel ayarda, sabit kodlanmış değişmez değeri 3 Nisan 1998 için derleme. Yyyy/aa/gg kullanan bir yerel ayarda değişmez değeri geçersiz olur (Nisan 1998, 0003) ve bir derleyici hatasına neden olabilir.  
  
## <a name="workarounds"></a>Geçici Çözümler  
 Dönüştürülecek bir `Date` bölgeniz biçimi veya özel bir biçim değişmez değeri sağlamak için sabit <xref:Microsoft.VisualBasic.Strings.Format%2A> işlevi, önceden tanımlanmış veya kullanıcı tanımlı tarih biçimini belirleme. Aşağıdaki örnekte bu gösterir.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Alternatif olarak aşırı yüklü oluşturucular birini kullanabilirsiniz <xref:System.DateTime> yapısı bir tarih ve saat değeri birleştirin. Aşağıdaki örnekte, 12:14 öğleden sonra en 31 May 1993 temsil etmek için bir değer oluşturur.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>Saat biçimi  
 Örneğin bir saat 12 veya 24 saat biçiminde saat değeri belirtebilirsiniz `#1:15:30 PM#` veya `#13:15:30#`. Ancak, dakika veya saniye belirtmezseniz AM veya PM belirtmeniz gerekir.  
  
## <a name="date-and-time-defaults"></a>Tarih ve saat Varsayılanları  
 Bir tarih bir tarih/saat değişmez değer içermiyorsa, Visual Basic değerinin tarih bölümünü 1 Ocak, 0001 ayarlar. Bir tarih/saat sabit bir zaman dahil, Visual Basic değerinin saat bölümünü başka bir deyişle, gece yarısı gün başına ayarlar. (0: 00:00).  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  
 Dönüştürürseniz, bir `Date` değeri `String` türü, Visual Basic çalışma zamanı yerel ayarı tarafından belirtilen kısa tarih biçimine göre tarihi işler ve tarafından belirtilen süre (saat 12 veya 24 saat) saat biçimi göre işler çalışma zamanı yerel ayar.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Birlikte çalışma hakkında dikkat edilecek noktalar** Örnek otomasyon veya COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, diğer ortamlarda türleri tarih unutmayın Visual Basic ile uyumlu olmadığında `Date` türü. Bu tür bir bileşen için bir tarih/saat değişkeni geçirilirse olarak bildirme `Double` yerine `Date` yeni Visual Basic kod ve dönüştürme yöntemleri kullanma <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Karakterleri yazın.** `Date` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri içeriyor. Ancak, derleyici içinde sayı işaretleri arasına değişmez değerleri kabul eder (`# #`) olarak `Date`.  
  
-   **Framework türü.** .NET Framework'teki karşılık gelen tür <xref:System.DateTime?displayProperty=nameWithType> yapısı.  
  
## <a name="example"></a>Örnek  
 Bir değişken veya sabiti `Date` veri türü tarih ve saati içerir. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Standart Tarih ve Saat Biçim Dizeleri](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [Özel Tarih ve Saat Biçim Dizeleri](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
