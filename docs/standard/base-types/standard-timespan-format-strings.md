---
title: "Standart TimeSpan Biçim Dizeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02dd73cd7f8f6be07b298e6fb1aac2b4759d21bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="standard-timespan-format-strings"></a>Standart TimeSpan Biçim Dizeleri
<a name="Top"></a>Standart bir <xref:System.TimeSpan> biçim dizesi metin gösterimini tanımlamak için bir tek biçim belirticisi kullanan bir <xref:System.TimeSpan> bir biçimlendirme işleminin sonuçları değeri. Beyaz alan dahil olmak üzere birden fazla karakter içeriyor herhangi bir biçim dizesini özel olarak yorumlanır <xref:System.TimeSpan> biçim dizesi. Daha fazla bilgi için bkz: [özel TimeSpan biçim dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md) .  
  
 Dize gösterimlerini <xref:System.TimeSpan> değerleri aşırı yapılan çağrılar tarafından üretilen <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType> yöntemini de olarak bileşik gibi biçimlendirme, destek yöntemlerle <xref:System.String.Format%2A?displayProperty=nameWithType>. Daha fazla bilgi için bkz: [biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md) ve [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md). Aşağıdaki örnek işlemleri biçimlendirmesindeki standart biçim dizeleri kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 Standart <xref:System.TimeSpan> biçim dizeleri tarafından da kullanılır <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> ve <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> ilişkin gerekli biçime tanımlamak için yöntemleri giriş işlemleri ayrıştırması dizeleri. (Ayrıştırma değeri dize gösterimini bu değerine dönüştürür.) Aşağıdaki örnek işlemleri ayrıştırılırken standart biçim dizeleri kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a>Aşağıdaki tabloda standart zaman aralığı biçim belirticileri listeler.  
  
|Biçim belirteci|Ad|Açıklama|Örnekler|  
|----------------------|----------|-----------------|--------------|  
|"c"|Sabit (sabit) biçimi|Bu belirleyici kültüre duyarlı değil. Formundadır `[-][d’.’]hh’:’mm’:’ss[‘.’fffffff]`.<br /><br /> ("T" ve "T" biçim dizeleri aynı sonucu verir.)<br /><br /> Daha fazla bilgi: [sabit ("c") biçim belirticisi](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Genel kısa biçimi|Bu tanımlayıcı, yalnızca gerekli olanla çıkarır. Kültüre duyarlı olduğundan ve formundadır `[-][d’:’]h’:’mm’:’ss[.FFFFFFF]`.<br /><br /> Daha fazla bilgi: [genel kısa ("g") biçim belirticisi](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)`-> 1:3:16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)`1:3:16:50, 5 (fr-FR) -><br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`-> 1:3:16:50.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)`1:3:16:50, 599 (fr-FR) ->|  
|"G"|Genel uzun biçimi|Bu tanımlayıcı her zaman gün ve yedi kesir basamakları çıkarır. Kültüre duyarlı olduğundan ve formundadır `[-]d’:’hh’:’mm’:’ss.fffffff`.<br /><br /> Daha fazla bilgi: [genel uzun ("G") biçim belirticisi](#GeneralLong).|`New TimeSpan(18, 30, 0)`-> 0:18:30:00.0000000 (en-US)<br /><br /> `New TimeSpan(18, 30, 0)`0:18:30:00, 0000000 (fr-FR) ->|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>Sabit ("c") biçim belirticisi  
 "C" biçim belirteci dize gösterimini döndürür bir <xref:System.TimeSpan> değeri aşağıdaki biçimde:  
  
 [-] [*d*.] *hh*:*mm*:*ss*[. *fffffff*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Nokta (.) ve iki nokta üst üste (:) değişmez değer simgelerdir. Aşağıdaki tabloda kalan öğelerini açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Bir eksi zaman aralığı gösteren bir isteğe bağlı eksi işareti.|  
|*d*|İsteğe bağlı gün sayısı, hiçbir baştaki sıfırlarla.|  
|*ss*|"00"-"23" aralıkları saat sayısı.|  
|*mm*|"00"-"59" aralıkları dakika sayısı.|  
|*ss*|"0" "59" aralıkları saniye sayısı.|  
|*fffffff*|İsteğe bağlı kesirli kısmı ikinci bir.  "9999999" değerini "0000001 biçim önekini" (bir değer veya bir on-millionth bir saniye) aralığında değişebilir (9,999,999 on milyonda bir saniye veya daha az bir değer ikinci).|  
  
 "G" ve "G" biçim belirticileri aksine, "c" biçim belirteci kültüre duyarlı değil. Dize gösterimini üreten bir <xref:System.TimeSpan> değişmez ve önce .NET Framework'ün tüm önceki sürümler için ortak olan değer [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. "c" varsayılan değerdir <xref:System.TimeSpan> biçim dizesi; <xref:System.TimeSpan.ToString?displayProperty=nameWithType> yöntemi "c" biçim dizesi kullanarak bir zaman aralığı değeri biçimlendirir.  
  
> [!NOTE]
>  <xref:System.TimeSpan>Ayrıca "t" ve "c" standart biçim dizesine davranışını özdeş "T" standart biçim dizeleri destekler.  
  
 Aşağıdaki örnekte iki başlatır <xref:System.TimeSpan> nesneleri, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, bileşik biçimlendirme görüntülemek için kullandığı <xref:System.TimeSpan> "c" biçim belirteci kullanarak değeri.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Tablo dön](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>Genel kısa ("g") biçim belirticisi  
 "g" <xref:System.TimeSpan> biçim belirticisi dize gösterimini döndürür bir <xref:System.TimeSpan> yalnızca gerekli olan öğeler de dahil olmak üzere tarafından compact formda değeri. Aşağıdaki biçime sahiptir:  
  
 [-] [*d*:]*h*:*mm*:*ss*[. *FFFFFFF*]  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Noktalı virgül (;) sabit bir simge ' dir. Aşağıdaki tabloda kalan öğelerini açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Bir eksi zaman aralığı gösteren bir isteğe bağlı eksi işareti.|  
|*d*|İsteğe bağlı gün sayısı, hiçbir baştaki sıfırlarla.|  
|*h*|"0"-"23" hiçbir baştaki sıfırlarla aralıkları saat sayısı.|  
|*mm*|Hangi "00"-"59" aralıkları dakika sayısını...|  
|*ss*|"00"-"59" aralıkları saniye sayısı...|  
|*.*|Kesirli saniye ayırıcı. Belirtilen kültür için 's eşdeğerdir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kullanıcı olmadan özelliğini geçersiz kılar.|  
|*FFFFFFF*|Kesirli saniye sayısı. Mümkün olduğunca az basamaklar görüntülenir.|  
  
 "G" biçim belirticisi gibi "g" biçim belirticisi yerelleştirilmiştir. Kesirli saniye ayırıcı geçerli kültürü veya belirtilen kültürün dayanarak <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliği.  
  
 Aşağıdaki örnekte iki başlatır <xref:System.TimeSpan> nesneleri, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, bileşik biçimlendirme görüntülemek için kullandığı <xref:System.TimeSpan> "g" biçim belirteci kullanarak değeri. Ayrıca, biçimleri <xref:System.TimeSpan> (Bu, bu durumda, İngilizce - ABD veya en-US) geçerli sistem kültürü ve Fransızca - Fransa (fr-FR) kültür biçimlendirme kuralları kullanarak değeri.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Tablo dön](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>Genel uzun süre ("G") biçim belirticisi  
 "G" <xref:System.TimeSpan> biçim belirticisi dize gösterimini döndürür bir <xref:System.TimeSpan> gün ve Kesirli saniye her zaman içeren uzun bir form değeri. "G" standart biçim belirticisi sonuçları dize aşağıdaki biçime sahiptir:  
  
 [-] *d*:*hh*:*mm*:*ss*. *fffffff*  
  
 Köşeli ayraçlar ([ve]) içindeki öğeler isteğe bağlıdır. Noktalı virgül (;) sabit bir simge ' dir. Aşağıdaki tabloda kalan öğelerini açıklar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|*-*|Bir eksi zaman aralığı gösteren bir isteğe bağlı eksi işareti.|  
|*d*|Hiçbir baştaki sıfırlarla gün sayısı.|  
|*ss*|"00"-"23" aralıkları saat sayısı.|  
|*mm*|"00"-"59" aralıkları dakika sayısı.|  
|*ss*|"00"-"59" aralıkları saniye sayısı.|  
|*.*|Kesirli saniye ayırıcı. Belirtilen kültür için 's eşdeğerdir <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> kullanıcı olmadan özelliğini geçersiz kılar.|  
|*fffffff*|Kesirli saniye sayısı.|  
  
 "G" biçim belirticisi gibi "g" biçim belirticisi yerelleştirilmiştir. Kesirli saniye ayırıcı geçerli kültürü veya belirtilen kültürün dayanarak <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> özelliği.  
  
 Aşağıdaki örnekte iki başlatır <xref:System.TimeSpan> nesneleri, aritmetik işlemler gerçekleştirmek için bunları kullanır ve sonucu görüntüler. Her durumda, bileşik biçimlendirme görüntülemek için kullandığı <xref:System.TimeSpan> "G" biçim belirteci kullanarak değeri. Ayrıca, biçimleri <xref:System.TimeSpan> (Bu, bu durumda, İngilizce - ABD veya en-US) geçerli sistem kültürü ve Fransızca - Fransa (fr-FR) kültür biçimlendirme kuralları kullanarak değeri.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Tablo dön](#Top)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 [Özel TimeSpan Biçim Dizeleri](../../../docs/standard/base-types/custom-timespan-format-strings.md)  
 [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
