---
title: Standart TimeSpan biçim dizeleri
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
ms.openlocfilehash: ec06edc16829c6d4caf8c760922aac1471e365c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75346624"
---
# <a name="standard-timespan-format-strings"></a>Standart TimeSpan biçim dizeleri

Standart <xref:System.TimeSpan> biçim dizesi, biçimlendirme işleminden kaynaklanan bir <xref:System.TimeSpan> değerin metin gösterimini tanımlamak için tek bir biçim belirtici kullanır. Beyaz boşluk da dahil olmak üzere birden fazla karakter içeren herhangi <xref:System.TimeSpan> bir biçim dizesi, özel biçim dizesi olarak yorumlanır. Daha fazla bilgi için [Bkz. Özel TimeSpan biçim dizeleri.](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
  
 <xref:System.TimeSpan> Değerlerin dize gösterimleri, <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yöntemin aşırı yüklerine yapılan çağrılar ve <xref:System.String.Format%2A?displayProperty=nameWithType>bileşik biçimlendirmeyi destekleyen yöntemlerle üretilir. Daha fazla bilgi için [bkz.](../../../docs/standard/base-types/formatting-types.md) [Composite Formatting](../../../docs/standard/base-types/composite-formatting.md) Aşağıdaki örnekte, biçimlendirme işlemlerinde standart biçim dizeleri kullanımı gösterilmektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standart <xref:System.TimeSpan> biçim dizeleri, ayrışma işlemleri için giriş dizeleri gerekli biçimini tanımlamak için <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemler tarafından da kullanılır. (Ayrıştırma, bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnekte, ayrıştma işlemlerinde standart biçim dizeleri kullanımı gösterilmektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
Aşağıdaki tabloda standart zaman aralığı biçimi belirteciler listelenmektedir.  
  
|Biçim belirteci|Adı|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|"c"|Sabit (değişmez) biçim|Bu belirtim kültüre duyarlı değildir. Bu formu `[-][d'.']hh':'mm':'ss['.'fffffff]`alır.<br /><br /> ("t" ve "T" biçimdizelleri aynı sonuçları üretir.)<br /><br /> Daha fazla bilgi: [Sabit ("c") Biçim Belirtici](#the-constant-c-format-specifier).|`TimeSpan.Zero`-> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)`-> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)`-> 3.17:25:30.5000000|  
|"g"|Genel kısa biçim|Bu belirtim yalnızca gereken çıktıları belirtir. Kültüre duyarlıdır ve şeklini `[-][d':']h':'mm':'ss[.FFFFFFF]`alır.<br /><br /> Daha fazla bilgi: [Genel Kısa ("g") Biçim Belirtici](#the-general-short-g-format-specifier).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50.5 (tr-ABD)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50,5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50.599 (tr-ABD)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50,599 (fr-FR)|  
|"G"|Genel uzun biçim|Bu belirtim her zaman gün ve yedi kesirli basamak çıkar. Kültüre duyarlıdır ve şeklini `[-]d':'hh':'mm':'ss.fffffff`alır.<br /><br /> Daha fazla bilgi: [Genel Uzun ("G") Biçim Belirtici](#the-general-long-g-format-specifier).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (tr-ABD)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00,0000000 (fr-FR)|  

## <a name="the-constant-c-format-specifier"></a>Sabit ("c") Biçim Belirtici  
 "c" biçimi belirtimi aşağıdaki formda bir <xref:System.TimeSpan> değerin dize temsilini döndürür:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[.* fffffff*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Dönem (.) ve kolon (:) gerçek sembollerdir. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif zaman aralığını gösteren isteğe bağlı negatif işaret.|  
|*D*|Önde gelen sıfırlar olmadan isteğe bağlı gün sayısı.|  
|*Hh*|"00" ile "23" arasında değişen saat sayısı.|  
|*Mm*|"00" ile "59" arasında değişen dakika sayısı.|  
|*Ss*|"0" ile "59" arasında değişen saniye sayısı.|  
|*fffffff*|Saniyenin isteğe bağlı kesirli kısmı.  Değeri "0000001" (bir kene veya saniyenin on milyonda biri) ile "99999999" (saniyenin on milyonda biri veya bir saniyedaha az kene) arasında değişebilir.|  
  
 "g" ve "G" biçimi belirticilerinden farklı olarak, "c" biçim belirtici kültüre duyarlı değildir. Değişmez ve .NET <xref:System.TimeSpan> Framework 4'ten önce .NET Framework'ün önceki tüm sürümlerinde ortak olan bir değerin dize temsilini üretir. "c" varsayılan <xref:System.TimeSpan> biçim dizesidir; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntem "c" biçimi dizesini kullanarak bir zaman aralığı değerini biçimlendirür.  
  
> [!NOTE]
> <xref:System.TimeSpan>ayrıca davranış olarak "c" standart biçim dizesinde aynı olan "t" ve "T" standart biçim dizelerini de destekler.  
  
 Aşağıdaki örnek, iki <xref:System.TimeSpan> nesneyi anında kullanır, aritmetik işlemler gerçekleştirmek için kullanır ve sonucu görüntüler. Her durumda, "c" biçim belirticisini kullanarak <xref:System.TimeSpan> değeri görüntülemek için bileşik biçimlendirme kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  

## <a name="the-general-short-g-format-specifier"></a>Genel Kısa ("g") Biçim Belirtici  
 "g" <xref:System.TimeSpan> biçimi belirtimi, yalnızca gerekli <xref:System.TimeSpan> öğeleri ekleyerek bir değerin dize temsilini kompakt bir biçimde döndürür. Aşağıdaki formu vardır:  
  
 [-] [*d*:] *h*:*mm*:*ss*[.* FFFFFFF*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Kolon (:) gerçek bir semboldür. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif zaman aralığını gösteren isteğe bağlı negatif işaret.|  
|*D*|Önde gelen sıfırlar olmadan isteğe bağlı gün sayısı.|  
|*H*|"0" ile "23" arasında değişen ve önde gelen sıfırlar bulunmayan saat sayısı.|  
|*Mm*|"00" ile "59" arasında değişen dakika sayısı...|  
|*Ss*|"00" ile "59" arasında değişen saniye sayısı...|  
|*.*|Kesirli saniye ayırıcı. Kullanıcı geçersiz kılmadan belirtilen <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kültürün özelliğine eşdeğerdir.|  
|*FFFFFFF*|Kesirli saniyeler. Mümkün olduğunca az basamak görüntülenir.|  
  
 "G" biçimi belirtici gibi, "g" biçimi belirtimi yerelleştirilmiştir. Onun kesirli saniye ayırıcı geçerli kültür veya belirli <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> bir kültürün özelliği ne dayanır.  
  
 Aşağıdaki örnek, iki <xref:System.TimeSpan> nesneyi anında kullanır, aritmetik işlemler gerçekleştirmek için kullanır ve sonucu görüntüler. Her durumda, "g" biçimlendirme <xref:System.TimeSpan> belirtici sini kullanarak değeri görüntülemek için bileşik biçimlendirme kullanır. Buna ek olarak, <xref:System.TimeSpan> geçerli sistem kültürünün biçimlendirme kurallarını (bu durumda İngilizce - Amerika Birleşik Devletleri veya en-ABD) ve Fransızca - Fransa (fr-FR) kültürünü kullanarak değeri biçimlendirmektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  

## <a name="the-general-long-g-format-specifier"></a>Genel Uzun ("G") Biçim Belirtici  
 "G" <xref:System.TimeSpan> biçim belirtici her zaman gün <xref:System.TimeSpan> ve kesirli saniye içeren uzun bir biçimde bir değerin dize gösterimi döndürür. "G" standart biçim belirticisinden çıkan dize aşağıdaki forma sahiptir:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Kolon (:) gerçek bir semboldür. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif zaman aralığını gösteren isteğe bağlı negatif işaret.|  
|*D*|Önde gelen sıfırlar olmayan gün sayısı.|  
|*Hh*|"00" ile "23" arasında değişen saat sayısı.|  
|*Mm*|"00" ile "59" arasında değişen dakika sayısı.|  
|*Ss*|"00" ile "59" arasında değişen saniye sayısı.|  
|*.*|Kesirli saniye ayırıcı. Kullanıcı geçersiz kılmadan belirtilen <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kültürün özelliğine eşdeğerdir.|  
|*fffffff*|Kesirli saniyeler.|  
  
 "G" biçimi belirtici gibi, "g" biçimi belirtimi yerelleştirilmiştir. Onun kesirli saniye ayırıcı geçerli kültür veya belirli <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> bir kültürün özelliği ne dayanır.  
  
 Aşağıdaki örnek, iki <xref:System.TimeSpan> nesneyi anında kullanır, aritmetik işlemler gerçekleştirmek için kullanır ve sonucu görüntüler. Her durumda, "G" biçimlendirme <xref:System.TimeSpan> belirtici sini kullanarak değeri görüntülemek için bileşik biçimlendirme kullanır. Buna ek olarak, <xref:System.TimeSpan> geçerli sistem kültürünün biçimlendirme kurallarını (bu durumda İngilizce - Amerika Birleşik Devletleri veya en-ABD) ve Fransızca - Fransa (fr-FR) kültürünü kullanarak değeri biçimlendirmektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
