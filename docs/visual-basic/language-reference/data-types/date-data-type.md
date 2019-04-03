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
ms.openlocfilehash: 42a36351ad70bc16b6cad63450ee5fcb3ed4f1ef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821386"
---
# <a name="date-data-type-visual-basic"></a>Date Veri Türü (Visual Basic)
IEEE 64-bit (8 bayt) 12:00: 00'da (gece yarısı), 1 Ocak 0001-31 Aralık 9999 yılın yılın arasında değişen tarihleri ve saatleri temsil eden bir değer PM 11:59:59.9999999 tutar. Her artış, Gregoryen takvimindeki 1 yılının 1 Ocak başından beri geçen 100 nanosaniyelik geçen süreyi temsil eder. En yüksek değer 100 nanosaniyelik 10000 yılın 1 Ocak, başlamadan önce temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım `Date` tarih değerleri, saat değerleri veya tarih ve saat değerlerini içeren bir veri türü.  
  
 Varsayılan değer olan `Date` 0:00:00 (gece yarısı) 1 Ocak 0001.  
  
 Geçerli tarih ve saat alabilirsiniz <xref:Microsoft.VisualBasic.DateAndTime> sınıfı.  
  
## <a name="format-requirements"></a>Biçim gereksinimlerini  
 İçine almalısınız bir `Date` sayı işaretleri içindeki sabit değeri (`# #`). Örneğin a/yyyy biçiminde tarih değeri belirtmelisiniz `#5/31/1993#`, ya da yyyy-aa-gg, örneğin `#1993-5-31#`. Yılın ilk belirtirken, eğik çizgi kullanabilirsiniz.  Bu gereksinim, bölgeniz ve bilgisayarınızın tarih ve saat biçimi ayarlarını bağımsızdır.  
  
 Bu kısıtlamanın nedeni anlamı kodunuzu, uygulamanızın çalıştığı yerel ayara bağlı olarak hiçbir zaman değiştirmelisiniz ' dir. Sabit kodlu varsayalım bir `Date` , değişmez değer `#3/4/1998#` ve ortalama 4 Mart 1998'de istediğiniz. İstediğiniz gibi aa/gg/yyyy kullanan bir yerel ayarda 3/4/1998'de derler. Ancak birçok ülkede uygulamanızı dağıtabilmeniz varsayalım. Gg/aa/yyyy kullanan bir yerel ayarında, sabit kodlanmış değişmez değeri 3 Nisan 1998 derlenir. Değişmez değer yyyy/aa/gg kullanan bir yerel ayarında geçersiz olur (Nisan 1998 ' 0003) ve bir derleyici hatasına neden olabilir.  
  
## <a name="workarounds"></a>Geçici Çözümler  
 Dönüştürülecek bir `Date` bölgeniz biçimi veya özel bir biçim için değişmez değerin değişmez değer sağlamanız <xref:Microsoft.VisualBasic.Strings.Format%2A> işlevi, bir ya da önceden tanımlı veya kullanıcı tanımlı tarih biçimini belirleme. Aşağıdaki örnekte bu gösterir.  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 Alternatif olarak, aşırı yüklü oluşturucular birini kullanabilirsiniz <xref:System.DateTime> bir tarih ve saat değerini derlemek için yapısı. Aşağıdaki örnek, 12:14 öğleden sonra 31 Mayıs 1993 temsil etmek için bir değer oluşturur.  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a>Saat biçimi  
 Örneğin 12 saat veya 24 saat biçiminde saat değeri belirtebilirsiniz `#1:15:30 PM#` veya `#13:15:30#`. Ancak, dakika veya saniye belirtmezseniz, AM veya PM belirtmeniz gerekir.  
  
## <a name="date-and-time-defaults"></a>Tarih ve saat Varsayılanları  
 Bir tarihi bir tarih/saat değişmez değer eklemezseniz, Visual Basic değerinin tarih bölümünü 1 Ocak, 0001 ayarlar. Bir süre içinde bir tarih değişmez eklemezseniz, Visual Basic değerinin saat bölümünü diğer bir deyişle, gece yarısı güne başlamak için ayarlar. (0: 00:00).  
  
## <a name="type-conversions"></a>Tür Dönüştürmeleri  
 Dönüştürürseniz, bir `Date` değerini `String` türü, Visual Basic çalışma zamanı tarafından belirtilen kısa tarih biçimini göre tarih oluşturur ve tarafından belirlenen süre saat biçimini (12 saat veya 24 saat) göre işler çalışma zamanı yerel ayar.  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
-   **Birlikte çalışabilirlik değerlendirmeleri.** Örnek otomasyon ve COM nesneleri için .NET Framework için yazılmaz bileşenleriyle arabirim, tarih/saat türleri diğer ortamlarda unutmayın Visual Basic ile uyumlu değil `Date` türü. Bir tarih/saat değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Double` yerine `Date` , yeni bir Visual Basic kod ve dönüştürme yöntemleri kullanın <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.  
  
-   **Tür karakterleri.** `Date` değişmez değer türü karakteri ya da tanımlayıcı türü karakteri var. Ancak derleyici değişmez değerleri sayı işaretleri alınmış işler (`# #`) olarak `Date`.  
  
-   **Çerçeve türü.** .NET Framework içinde karşılık gelen türü <xref:System.DateTime?displayProperty=nameWithType> yapısı.  
  
## <a name="example"></a>Örnek  
 Bir değişken veya sabiti `Date` tarih ve saat veri türü tutar. Aşağıdaki örnek bunu göstermektedir.  
  
```  
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
