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
ms.openlocfilehash: 2ed9ca7337e40b5520ddbfc92925c5bedb45f701
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289284"
---
# <a name="standard-timespan-format-strings"></a>Standart TimeSpan biçim dizeleri

Standart <xref:System.TimeSpan> Biçim dizesi, <xref:System.TimeSpan> biçimlendirme işleminden kaynaklanan bir değerin metin temsilini tanımlamak için tek bir biçim belirticisi kullanır. Boşluk da dahil olmak üzere birden fazla karakter içeren herhangi bir biçim dizesi, özel biçim dizesi olarak yorumlanır <xref:System.TimeSpan> . Daha fazla bilgi için bkz. [Özel TimeSpan Biçim dizeleri](custom-timespan-format-strings.md) .  
  
 Değerlerin dize temsilleri, <xref:System.TimeSpan> yönteminin aşırı yüklemelerinin <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yanı sıra, gibi bileşik biçimlendirmeyi destekleyen yöntemlere göre oluşturulur <xref:System.String.Format%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [biçimlendirme türleri](formatting-types.md) ve [Bileşik biçimlendirme](composite-formatting.md). Aşağıdaki örnek biçimlendirme işlemlerinde standart biçim dizelerinin kullanımını gösterir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standart <xref:System.TimeSpan> Biçim dizeleri, ve yöntemleri tarafından, <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> ayrıştırma işlemleri için gereken giriş dizeleri biçimini tanımlamak için de kullanılır. (Ayrıştırma bir değerin dize temsilini bu değere dönüştürür.) Aşağıdaki örnek, ayrıştırma işlemlerinde standart biçim dizelerinin kullanımını gösterir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
Aşağıdaki tabloda standart zaman aralığı biçim belirticileri listelenmektedir.  
  
|Biçim belirteci|Name|Description|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|,|Sabit (Sabit) biçim|Bu tanımlayıcı kültüre duyarlı değildir. Formu alır `[-][d'.']hh':'mm':'ss['.'fffffff]` .<br /><br /> ("T" ve "T" biçim dizeleri aynı sonuçları üretir.)<br /><br /> Daha fazla bilgi: [sabit ("c") Biçim belirleyicisi](#the-constant-c-format-specifier).|`TimeSpan.Zero`-> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)`-> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)`-> 3.17:25:30.5000000|  
|"g"|Genel kısa biçim|Bu belirtici yalnızca gerekli olanları verir. Kültüre duyarlıdır ve formu alır `[-][d':']h':'mm':'ss[.FFFFFFF]` .<br /><br /> Daha fazla bilgi: [genel kısa ("g") Biçim belirleyicisi](#the-general-short-g-format-specifier).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`-> 1:3: 16:50, 5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3: 16:50599 (fr-FR)|  
|"G"|Genel uzun biçim|Bu belirtici her zaman gün ve yedi kesirli basamak verir. Kültüre duyarlıdır ve formu alır `[-]d':'hh':'mm':'ss.fffffff` .<br /><br /> Daha fazla bilgi: [genel uzun ("G") Biçim belirleyicisi](#the-general-long-g-format-specifier).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (en-US)<br /><br /> `New TimeSpan(18, 30, 0)`-> 0:18:30:00, 0000000 (fr-FR)|  

## <a name="the-constant-c-format-specifier"></a>Sabit ("c") Biçim belirleyicisi  
 "C" biçim belirticisi aşağıdaki biçimde bir değerin dize gösterimini döndürür <xref:System.TimeSpan> :  
  
 [-] [*d*.] *SS*:*dd*:*SS*[.* fffffff*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Nokta (.) ve iki nokta (:) değişmez simgeler. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Description|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten isteğe bağlı bir eksi işareti.|  
|*TID*|Önünde sıfır olmayan, isteğe bağlı gün sayısı.|  
|*ss*|"00" ile "23" arasında değişen saat sayısı.|  
|*d*|"00" ile "59" arasında değişen dakika sayısı.|  
|*ss*|"0" ile "59" arasında değişen saniye sayısı.|  
|*fffffff*|Saniyenin isteğe bağlı kesirli kısmı.  Değeri "0000001" (bir Tick veya saniyenin 1 10-milimetre Onth) arasında "9999999" (9.999.999 10-milionon saniyenin veya bir saniyeden daha az bir değer) arasında değişebilir.|  
  
 "G" ve "G" biçim Belirticilerinin aksine, "c" Biçim belirleyicisi kültüre duyarlı değildir. Bu, sabit bir değerin dize gösterimini üretir <xref:System.TimeSpan> ve .NET Framework 4 ' den önce .NET Framework önceki tüm sürümleri için ortaktır. "c" varsayılan <xref:System.TimeSpan> biçim dizesidir; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi "c" biçim dizesini kullanarak bir zaman aralığı değeri biçimlendirir.  
  
> [!NOTE]
> <xref:System.TimeSpan>Ayrıca "c" standart biçim dizesiyle aynı davranış ile özdeş olan "t" ve "T" standart biçim dizelerini de destekler.  
  
 Aşağıdaki örnek iki <xref:System.TimeSpan> nesneyi örneklemektedir, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, <xref:System.TimeSpan> "c" biçim belirticisini kullanarak değeri göstermek için bileşik biçimlendirme kullanır.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  

## <a name="the-general-short-g-format-specifier"></a>Genel kısa ("g") Biçim belirleyicisi  
 "G" <xref:System.TimeSpan> biçim belirticisi, <xref:System.TimeSpan> yalnızca gerekli öğeleri ekleyerek bir küçük biçimdeki değerin dize gösterimini döndürür. Aşağıdaki biçimdedir:  
  
 [-] [*d*:] *h*:*mm*:*SS*[.* FFFFFFF*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. İki nokta (:) sabit bir simgedir. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Description|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten isteğe bağlı bir eksi işareti.|  
|*TID*|Önünde sıfır olmayan, isteğe bağlı gün sayısı.|  
|*olsun*|"0" ile "23" arasında, önünde sıfır olmadan değişen saat sayısı.|  
|*d*|"00" ile "59" arasında değişen dakika sayısı..|  
|*ss*|"00" ile "59" arasında değişen saniye sayısı..|  
|*.*|Kesirli saniye ayırıcısı. <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>Kullanıcı geçersiz kılmaları olmadan belirtilen kültürün özelliğine eşdeğerdir.|  
|*FFFFFFF*|Kesirli saniyeler. Olabildiğince az basamak görüntülenir.|  
  
 "G" biçim belirticisi gibi, "g" biçim belirticisi yerelleştirilmiştir. Kesirli saniye ayırıcısı, geçerli kültürü veya belirtilen kültürün özelliğini temel alır <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> .  
  
 Aşağıdaki örnek iki <xref:System.TimeSpan> nesneyi örneklemektedir, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, <xref:System.TimeSpan> "g" biçim belirticisini kullanarak değeri göstermek için bileşik biçimlendirme kullanır. Ayrıca, <xref:System.TimeSpan> geçerli sistem kültürünün (Bu örnekte, İngilizce-Birleşik Devletler veya en-US) ve Fransızca-Fransa (fr-fr) kültürüne ait biçimlendirme kurallarını kullanarak değeri biçimlendirir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  

## <a name="the-general-long-g-format-specifier"></a>Genel uzun ("G") Biçim belirleyicisi  
 "G" <xref:System.TimeSpan> biçim belirticisi, bir değerin dize gösterimini, <xref:System.TimeSpan> her zaman hem gün hem de kesirli saniyeleri içeren uzun bir biçimde döndürür. "G" standart biçim belirticisinden elde edilen dize aşağıdaki biçimdedir:  
  
 [-] *d*:*SS*:*dd*:*SS*. *fffffff*  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. İki nokta (:) sabit bir simgedir. Aşağıdaki tabloda kalan öğeler açıklanmaktadır.  
  
|Öğe|Description|  
|-------------|-----------------|  
|*-*|Negatif bir zaman aralığını belirten isteğe bağlı bir eksi işareti.|  
|*TID*|Önünde sıfır olmayan gün sayısı.|  
|*ss*|"00" ile "23" arasında değişen saat sayısı.|  
|*d*|"00" ile "59" arasında değişen dakika sayısı.|  
|*ss*|"00" ile "59" arasında değişen saniye sayısı.|  
|*.*|Kesirli saniye ayırıcısı. <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>Kullanıcı geçersiz kılmaları olmadan belirtilen kültürün özelliğine eşdeğerdir.|  
|*fffffff*|Kesirli saniyeler.|  
  
 "G" biçim belirticisi gibi, "g" biçim belirticisi yerelleştirilmiştir. Kesirli saniye ayırıcısı, geçerli kültürü veya belirtilen kültürün özelliğini temel alır <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> .  
  
 Aşağıdaki örnek iki <xref:System.TimeSpan> nesneyi örneklemektedir, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, <xref:System.TimeSpan> "G" biçim belirticisini kullanarak değeri göstermek için bileşik biçimlendirme kullanır. Ayrıca, <xref:System.TimeSpan> geçerli sistem kültürünün (Bu örnekte, İngilizce-Birleşik Devletler veya en-US) ve Fransızca-Fransa (fr-fr) kültürüne ait biçimlendirme kurallarını kullanarak değeri biçimlendirir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
- [Özel TimeSpan Biçim dizeleri](custom-timespan-format-strings.md)
- [Dizeleri Ayrıştırma](parsing-strings.md)
