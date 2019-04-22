---
title: Standart TimeSpan Biçim Dizeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, standard time interval
- format strings
- standard time interval format strings
- standard format strings, time intervals
- format specifiers, time intervals
- time intervals [.NET Framework], formatting
- time [.NET Framework], formatting
- formatting [.NET Framework], time
- standard TimeSpan format strings
- formatting [.NET Framework], time intervals
ms.assetid: 9f6c95eb-63ae-4dcc-9c32-f81985c75794
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf7424c8aa2ae816340f6fa641e5c79a56ae0dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834133"
---
# <a name="standard-timespan-format-strings"></a>Standart TimeSpan Biçim Dizeleri
<a name="Top"></a> Standart <xref:System.TimeSpan> biçim dizesi metin temsilini tanımlamak için bir tek biçim belirticisi kullanan bir <xref:System.TimeSpan> bir biçimlendirme işleminden kaynaklanan değeri. Beyaz boşluk da dahil olmak üzere birden fazla karakter içeren herhangi bir biçim dizesi, özel olarak yorumlanır <xref:System.TimeSpan> biçimlendirme dizesi. Daha fazla bilgi için [Custom TimeSpan Format Strings](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Dize temsillerini <xref:System.TimeSpan> değerleri aşırı yüküne yapılan çağrılar tarafından üretilmektedir <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yöntemi de gibi yöntemlerle bileşik, aşağıdakiler gibi biçimlendirme desteği <xref:System.String.Format%2A?displayProperty=nameWithType>. Daha fazla bilgi için [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md) ve [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md). Aşağıdaki örnek, standart biçim dizeleri, biçimlendirme işlemleri, kullanımını gösterir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standart <xref:System.TimeSpan> biçim dizeleri tarafından da kullanılır <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> istenilen biçime tanımlamak için yöntemleri ayrıştırma işlemlerinde dizelerini giriş. (Ayrıştırma bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnek, standart biçim dizeleri ayrıştırma işlemlerinde, kullanımını gösterir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a> Aşağıdaki tablo standart zaman aralığı biçim belirticisi listeler.  
  
|Biçim belirteci|Ad|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|"c"|(Sabit) sabit biçim|Bu tanımlayıcının kültüre duyarlı değildir. Şu biçimi alır `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> ("T" ve "T" biçim dizeleri aynı sonucu verir.)<br /><br /> Daha fazla bilgi: [Sabit ("c") Biçim belirleyicisi](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Genel kısa biçim|Bu tanımlayıcının, yalnızca gerekli öğeleri çıkarır. Kültüre duyarlıdır ve biçimini alır `[-][d':']h':'mm':'ss[.FFFFFFF]`.<br /><br /> Daha fazla bilgi: [Genel kısa ("g") Biçim belirleyicisi](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)` 1:3:16:50.5 (en-US) -><br /><br /> `New TimeSpan(1, 3, 16, 50, 500)` 1:3:16:50, 5 (fr-FR) -><br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` 1:3:16:50.599 (en-US) -><br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` 1:3:16:50, 599 (fr-FR) ->|  
|"G"|Genel uzun biçimde|Bu tanımlayıcının her zaman gün ve yedi kesirli basamaklar çıkarır. Kültüre duyarlıdır ve biçimini alır `[-]d':'hh':'mm':'ss.fffffff`.<br /><br /> Daha fazla bilgi: [Genel uzun ("G") Biçim belirleyicisi](#GeneralLong).|`New TimeSpan(18, 30, 0)` 0:18:30:00.0000000 (en-US) -><br /><br /> `New TimeSpan(18, 30, 0)` 0:18:30:00, 0000000 (fr-FR) ->|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Sabit ("c") Biçim belirleyicisi  
 "C" biçim belirticisi dize gösterimini döndürür. bir <xref:System.TimeSpan> aşağıdaki formda değeri:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[. *fffffff*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Nokta (.) ve iki nokta üst üste (:) değişmez değer simgelerdir. Aşağıdaki tabloda, kalan öğeleri açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten bir isteğe bağlı eksi işareti.|  
|*d*|Gün önünde sıfır olmadan isteğe bağlı sayısı.|  
|*hh*|"00", "23" aralıkları saat sayısı.|  
|*aa*|"00"-"59" aralıkları dakika sayısı.|  
|*ss*|"0", "59" aralıkları saniye sayısı.|  
|*fffffff*|İkinci bir isteğe bağlı kesirli bölümü.  Değerini "9999999" için "0000001 biçim önekini" (bir değer çizgisi veya saniyede bir on milyon) değişebilir (9,999,999 on milyonda birini veya daha az bir değer çizgisi ikinci).|  
  
 "C" biçim belirtici "g" ve "G" biçim belirticisi aksine, kültüre duyarlı değil. Dize gösterimini üreten bir <xref:System.TimeSpan> önce .NET Framework'ün tüm önceki sürümleri için ortak olan ve olmayan sabit değer [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. "c", varsayılan <xref:System.TimeSpan> biçimlendirme dizesi; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi, "c" biçim dizesini kullanarak bir zaman aralığı değeri biçimlendirir.  
  
> [!NOTE]
>  <xref:System.TimeSpan> "t" ve "c" standart biçim dizesine davranışı özdeş "T" standart biçim dizeleri de destekler.  
  
 Aşağıdaki örnek iki başlatır <xref:System.TimeSpan> nesneleri, aritmetik işlemleri gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, bileşik biçimlendirme görüntülemek için kullandığı <xref:System.TimeSpan> "c" biçim belirticisi kullanılarak değeri.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Tabloya dön](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Genel kısa ("g") Biçim belirleyicisi  
 "g" <xref:System.TimeSpan> biçim belirleyici dize gösterimini döndürür bir <xref:System.TimeSpan> gerekli olan öğeler ekleyerek tutması değeri. Bunu, aşağıdaki biçime sahiptir:  
  
 [-] [*d*:]*h*:*mm*:*ss*[. *FFFFFFF*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. İki nokta üst üste (:) değişmez bir semboldür. Aşağıdaki tabloda, kalan öğeleri açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten bir isteğe bağlı eksi işareti.|  
|*d*|Gün önünde sıfır olmadan isteğe bağlı sayısı.|  
|*h*|Baştaki sıfırlar yok ile "23" için "0" aralıkları saat sayısı.|  
|*aa*|"00"-"59" aralıkları sayısı dakika...|  
|*ss*|"00"-"59" aralıkları saniye sayısı...|  
|*.*|Kesirli saniye ayırıcı. Belirtilen kültüre ait eşdeğerdir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kullanıcı olmadan özelliğini geçersiz kılar.|  
|*FFFFFFF*|Kesirli saniye. Mümkün olduğunca az basamaklar görüntülenir.|  
  
 "G" Biçim belirleyicisi gibi "g" biçim belirticisi yerelleştirilmiş. Kesirli saniye ayırıcı, geçerli kültür ya da belirtilen kültürün tabanlı <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliği.  
  
 Aşağıdaki örnek iki başlatır <xref:System.TimeSpan> nesneleri, aritmetik işlemleri gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, bileşik biçimlendirme görüntülemek için kullandığı <xref:System.TimeSpan> "g" biçim belirticisi kullanılarak değeri. Ayrıca, biçimleri <xref:System.TimeSpan> geçerli sistem kültürü (Bu, bu durumda, İngilizce - Birleşik Devletler veya en-US) ve Fransızca - Fransa (fr-FR) kültür biçimlendirme kurallarını kullanarak değeri.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Tabloya dön](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Genel uzun ("G") Biçim belirleyicisi  
 "G" <xref:System.TimeSpan> biçim belirleyici dize gösterimini döndürür bir <xref:System.TimeSpan> gün hem Kesirli saniye her zaman içeren uzun bir form değeri. "G" standart biçim tanımlayıcısı sonuç dizesi aşağıdaki biçime sahiptir:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. İki nokta üst üste (:) değişmez bir semboldür. Aşağıdaki tabloda, kalan öğeleri açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten bir isteğe bağlı eksi işareti.|  
|*d*|Baştaki sıfırlar yok gün sayısı.|  
|*hh*|"00", "23" aralıkları saat sayısı.|  
|*aa*|"00"-"59" aralıkları dakika sayısı.|  
|*ss*|"00"-"59" aralıkları saniye sayısı.|  
|*.*|Kesirli saniye ayırıcı. Belirtilen kültüre ait eşdeğerdir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kullanıcı olmadan özelliğini geçersiz kılar.|  
|*fffffff*|Kesirli saniye.|  
  
 "G" Biçim belirleyicisi gibi "g" biçim belirticisi yerelleştirilmiş. Kesirli saniye ayırıcı, geçerli kültür ya da belirtilen kültürün tabanlı <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliği.  
  
 Aşağıdaki örnek iki başlatır <xref:System.TimeSpan> nesneleri, aritmetik işlemleri gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, bileşik biçimlendirme görüntülemek için kullandığı <xref:System.TimeSpan> "G" biçim belirticisi kullanılarak değeri. Ayrıca, biçimleri <xref:System.TimeSpan> geçerli sistem kültürü (Bu, bu durumda, İngilizce - Birleşik Devletler veya en-US) ve Fransızca - Fransa (fr-FR) kültür biçimlendirme kurallarını kullanarak değeri.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Tabloya dön](#Top)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
