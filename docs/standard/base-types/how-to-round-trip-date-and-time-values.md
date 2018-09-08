---
title: 'Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b16d135449cad8ed489a8a3e21db326be0fae0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193269"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri
Birçok uygulamada, bir tarih ve saat değerini, tek bir nokta zaman içinde kesin bir şekilde tanımlamak için tasarlanmıştır. Bu konuda, kaydetme ve geri yükleme işlemi gösterilmektedir bir <xref:System.DateTime> değeri bir <xref:System.DateTimeOffset> değer ve bir tarih ve saat değeri zaman ile kaydedilen değer aynı zamanda geri yüklenen değeri tanımlar, böylece bilgi bölge.  
  
### <a name="to-round-trip-a-datetime-value"></a>Bir DateTime değerini gidiş dönüşlü hale getirmek için  
  
1.  Dönüştürme <xref:System.DateTime> çağırarak dize gösterimine değerine <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirteci ile yöntemi.  
  
2.  Dize gösterimini kaydedin <xref:System.DateTime> değeri bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.  
  
3.  Temsil eden dizeyi almak <xref:System.DateTime> değeri.  
  
4.  Çağrı <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.  
  
 Aşağıdaki örnekte gösterilmiştir gidiş dönüşlü hale getirmek için nasıl bir <xref:System.DateTime> değeri.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Zaman gidiş dönüşü bir <xref:System.DateTime> değeri, bu tekniği başarıyla yerel ve evrensel sürekli süreyle korur. Örneğin, bir yerel <xref:System.DateTime> değeri ABD'deki bir sistemde kaydedildi Pasifik Standart saat dilimi ve ABD'deki bir sistemde geri Merkezi standart saat dilimi, geri yüklenen tarih ve saat iki saat dilimlerini arasındaki zaman farkı yansıtır özgün saatinden sonraki iki saat olacaktır. Ancak, bu tekniği için doğru olmak zorunda değildir kez belirtilmemiş. Tüm <xref:System.DateTime> ayarlanmış değerleri <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified> yerel zamanlar oldukları gibi değerlendirilir. Bu durumda değilse <xref:System.DateTime> başarıyla doğru noktası sürede belirtmez. Bu sınırlamaya geçici çözümü, sıkı bir şekilde bir tarih ve saat değerini kendi saat dilimiyle kaydetme birleştirin ve geri yükleme işlemi oluşturmaktır.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için  
  
1.  Dönüştürme <xref:System.DateTimeOffset> çağırarak dize gösterimine değerine <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirteci ile yöntemi.  
  
2.  Dize gösterimini kaydedin <xref:System.DateTimeOffset> değeri bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.  
  
3.  Temsil eden dizeyi almak <xref:System.DateTimeOffset> değeri.  
  
4.  Çağrı <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.  
  
 Aşağıdaki örnekte gösterilmiştir gidiş dönüşlü hale getirmek için nasıl bir <xref:System.DateTimeOffset> değeri.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Bu yöntem her zaman kesin bir şekilde tanımlayan bir <xref:System.DateTimeOffset> zaman içinde tek bir nokta olarak değeri. Değer daha sonra Eşgüdümlü Evrensel Saat (UTC) çağırarak dönüştürülebilir <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi veya dönüştürülebilir belirli bir saat dilimindeki saati çağırarak <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> veya <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi. Bu tekniğe ilişkin önemli sınırlama tarihtir ve gerçekleştirilen, zaman, aritmetik bir <xref:System.DateTimeOffset> belirli bir saat dilimindeki saati gösteren bir değer değil, saat dilimi için doğru sonuçlar oluşturabilir. Bunun sebebi, bir <xref:System.DateTimeOffset> değer örneği, kendi saat diliminden noktanızla ilişkisi silinir. Bu nedenle, tarih ve saat hesaplamaları gerçekleştirdiğinizde, saat diliminin ayarlama kuralları artık uygulanabilir. Bu sorunu geçici olarak bir tarih ve saat değeri ve kendi eşlik eden saat dilimi içeren özel bir tür tanımlayarak çalışabilir.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için  
  
1.  Bir sınıf ya da iki alan bir yapı tanımlar. İlk alanı bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesne ve ikinci bir <xref:System.TimeZoneInfo> nesne. Aşağıdaki örnekte, böyle bir türü basit bir sürümüdür.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Sınıf ile işaretle <xref:System.SerializableAttribute> özniteliği.  
  
3.  Nesnesi kullanarak serileştirme <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> yöntemi.  
  
4.  Nesnesini kullanarak geri <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> yöntemi.  
  
5.  Atama (C# ') veya (Visual Basic'te) seri durumdan çıkarılmış nesne uygun türde bir nesneye dönüştürür.  
  
 Aşağıdaki örnek nasıl tarih ve saat ve saat dilimi bilgilerini depolayan bir nesne gidiş dönüş için gösterir.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Bu teknik, doğru hem önce ve sonra kaydedilip geri, sağlanan uygulama birleştirilmiş tarih ve saat ve saat dilimi nesnenin tarih değeri ile eşitlenmemiş hale izin vermiyor zaman noktası her zaman kesin bir şekilde yansıtmalıdır saat dilimi değeri.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği gerektirir:  
  
-   Aşağıdaki ad alanlarını C# ile içe aktarılacağını `using` ifadelerini veya Visual Basic `Imports` ifadeleri:  
  
    -   <xref:System> (Yalnızca C#).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Bir System.Core.dll başvurusu.  
  
-   Her örnek, dışındaki kod `DateInTimeZone` sınıfı, bir sınıf veya Visual Basic module'u içinde bulunan yöntemlerdeki sarmalanmış ve çağrılır `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md)  
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
