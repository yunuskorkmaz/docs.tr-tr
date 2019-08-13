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
ms.openlocfilehash: 3e67861a32d5863e4c1b4d9b147c507c1bb54c39
ms.sourcegitcommit: 46c68557bf6395f0ab9915f7558f2faae0097695
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2019
ms.locfileid: "66491102"
---
# <a name="standard-timespan-format-strings"></a>Standart TimeSpan Biçim Dizeleri
<a name="Top"></a>Standart <xref:System.TimeSpan> biçim dizesi, biçimlendirme işleminden kaynaklanan bir <xref:System.TimeSpan> değerin metin temsilini tanımlamak için tek bir biçim belirticisi kullanır. Boşluk da dahil olmak üzere birden fazla karakter içeren herhangi bir biçim dizesi, özel <xref:System.TimeSpan> biçim dizesi olarak yorumlanır. Daha fazla bilgi için bkz. [Özel TimeSpan Biçim dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 <xref:System.TimeSpan> Değerlerin dize temsilleri, <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yönteminin aşırı yüklemelerinin yanı sıra, gibi <xref:System.String.Format%2A?displayProperty=nameWithType>bileşik biçimlendirmeyi destekleyen yöntemlere göre oluşturulur. Daha fazla bilgi için bkz. [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md) ve [Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md). Aşağıdaki örnek biçimlendirme işlemlerinde standart biçim dizelerinin kullanımını gösterir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standart <xref:System.TimeSpan> biçim dizeleri, ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> yöntemleri tarafından, <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ayrıştırma işlemleri için gereken giriş dizeleri biçimini tanımlamak için de kullanılır. (Ayrıştırma bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnek, ayrıştırma işlemlerinde standart biçim dizelerinin kullanımını gösterir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a>Aşağıdaki tabloda standart zaman aralığı biçim belirticileri listelenmektedir.  
  
|Biçim belirteci|Ad|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|,|Sabit (Sabit) biçim|Bu tanımlayıcı kültüre duyarlı değildir. Formu `[-][d'.']hh':'mm':'ss['.'fffffff]`alır.<br /><br /> ("T" ve "T" biçim dizeleri aynı sonuçları üretir.)<br /><br /> Daha fazla bilgi: [Sabit ("c") Biçim belirleyicisi](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Genel kısa biçim|Bu belirtici yalnızca gerekli olanları verir. Kültüre duyarlıdır ve formu `[-][d':']h':'mm':'ss[.FFFFFFF]`alır.<br /><br /> Daha fazla bilgi: [Genel kısa ("g") Biçim belirleyicisi](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50599 (fr-FR)|  
|"G"|Genel uzun biçim|Bu belirtici her zaman gün ve yedi kesirli basamak verir. Kültüre duyarlıdır ve formu `[-]d':'hh':'mm':'ss.fffffff`alır.<br /><br /> Daha fazla bilgi: [Genel uzun ("G") Biçim belirleyicisi](#GeneralLong).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (en-US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00, 0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Sabit ("c") Biçim belirleyicisi  
 "C" biçim belirticisi aşağıdaki biçimde bir <xref:System.TimeSpan> değerin dize gösterimini döndürür:  
  
 [-] [*d*.] *SS*:*dd*:*SS*[. *fffffff*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Nokta (.) ve iki nokta (:) değişmez simgeler. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten isteğe bağlı bir eksi işareti.|  
|*d*|Önünde sıfır olmayan, isteğe bağlı gün sayısı.|  
|*hh*|"00" ile "23" arasında değişen saat sayısı.|  
|*d*|"00" ile "59" arasında değişen dakika sayısı.|  
|*ss*|"0" ile "59" arasında değişen saniye sayısı.|  
|*fffffff*|Saniyenin isteğe bağlı kesirli kısmı.  Değeri "0000001" (bir Tick veya saniyenin 1 10-milimetre Onth) arasında "9999999" (9.999.999 10-milionon saniyenin veya bir saniyeden daha az bir değer) arasında değişebilir.|  
  
 "G" ve "G" biçim Belirticilerinin aksine, "c" Biçim belirleyicisi kültüre duyarlı değildir. Bu, sabit bir <xref:System.TimeSpan> değerin dize gösterimini üretir ve .NET Framework 4 ' den önce .NET Framework önceki tüm sürümleri için ortaktır. "c" varsayılan <xref:System.TimeSpan> biçim dizesidir <xref:System.TimeSpan.ToString?displayProperty=nameWithType> ; yöntemi "c" biçim dizesini kullanarak bir zaman aralığı değeri biçimlendirir.  
  
> [!NOTE]
>  <xref:System.TimeSpan>Ayrıca "c" standart biçim dizesiyle aynı davranış ile özdeş olan "t" ve "T" standart biçim dizelerini de destekler.  
  
 Aşağıdaki örnek iki <xref:System.TimeSpan> nesneyi örneklemektedir, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, "c" biçim belirticisini kullanarak <xref:System.TimeSpan> değeri göstermek için bileşik biçimlendirme kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Tabloya dön](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Genel kısa ("g") Biçim belirleyicisi  
 "G" <xref:System.TimeSpan> biçim belirticisi, yalnızca gerekli öğeleri ekleyerek bir küçük <xref:System.TimeSpan> biçimdeki değerin dize gösterimini döndürür. Aşağıdaki biçimdedir:  
  
 [-] [*d*:] *h*:*mm*:*SS*[. *FFFFFFF*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. İki nokta (:) sabit bir simgedir. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten isteğe bağlı bir eksi işareti.|  
|*d*|Önünde sıfır olmayan, isteğe bağlı gün sayısı.|  
|*h*|"0" ile "23" arasında, önünde sıfır olmadan değişen saat sayısı.|  
|*d*|"00" ile "59" arasında değişen dakika sayısı..|  
|*ss*|"00" ile "59" arasında değişen saniye sayısı..|  
|*.*|Kesirli saniye ayırıcısı. Kullanıcı geçersiz kılmaları olmadan belirtilen kültürün <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliğine eşdeğerdir.|  
|*FFFFFFF*|Kesirli saniyeler. Olabildiğince az basamak görüntülenir.|  
  
 "G" biçim belirticisi gibi, "g" biçim belirticisi yerelleştirilmiştir. Kesirli saniye ayırıcısı, geçerli kültürü veya belirtilen kültürün <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliğini temel alır.  
  
 Aşağıdaki örnek iki <xref:System.TimeSpan> nesneyi örneklemektedir, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, "g" biçim belirticisini kullanarak <xref:System.TimeSpan> değeri göstermek için bileşik biçimlendirme kullanır. Ayrıca, geçerli sistem kültürünün <xref:System.TimeSpan> (Bu örnekte, İngilizce-Birleşik Devletler veya en-US) ve Fransızca-Fransa (fr-fr) kültürüne ait biçimlendirme kurallarını kullanarak değeri biçimlendirir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Tabloya dön](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Genel uzun ("G") Biçim belirleyicisi  
 "G" <xref:System.TimeSpan> biçim belirticisi, bir <xref:System.TimeSpan> değerin dize gösterimini, her zaman hem gün hem de kesirli saniyeleri içeren uzun bir biçimde döndürür. "G" standart biçim belirticisinden elde edilen dize aşağıdaki biçimdedir:  
  
 [-] *d*:*SS*:*dd*:*SS*. *fffffff*  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. İki nokta (:) sabit bir simgedir. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten isteğe bağlı bir eksi işareti.|  
|*d*|Önünde sıfır olmayan gün sayısı.|  
|*hh*|"00" ile "23" arasında değişen saat sayısı.|  
|*d*|"00" ile "59" arasında değişen dakika sayısı.|  
|*ss*|"00" ile "59" arasında değişen saniye sayısı.|  
|*.*|Kesirli saniye ayırıcısı. Kullanıcı geçersiz kılmaları olmadan belirtilen kültürün <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliğine eşdeğerdir.|  
|*fffffff*|Kesirli saniyeler.|  
  
 "G" biçim belirticisi gibi, "g" biçim belirticisi yerelleştirilmiştir. Kesirli saniye ayırıcısı, geçerli kültürü veya belirtilen kültürün <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliğini temel alır.  
  
 Aşağıdaki örnek iki <xref:System.TimeSpan> nesneyi örneklemektedir, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, "G" biçim belirticisini kullanarak <xref:System.TimeSpan> değeri göstermek için bileşik biçimlendirme kullanır. Ayrıca, geçerli sistem kültürünün <xref:System.TimeSpan> (Bu örnekte, İngilizce-Birleşik Devletler veya en-US) ve Fransızca-Fransa (fr-fr) kültürüne ait biçimlendirme kurallarını kullanarak değeri biçimlendirir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Tabloya dön](#Top)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
