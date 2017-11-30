---
title: "Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri"
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>Nasıl yapılır: Gidiş Dönüş Tarih ve Saat Değerleri
Birçok uygulamada, tarih ve saat değeri tek bir nokta zaman içinde kesin bir şekilde tanımlamak için tasarlanmıştır. Bu konuda kaydetme ve geri yükleme gösterilmektedir bir <xref:System.DateTime> değeri, bir <xref:System.DateTimeOffset> değer ve zaman içeren bir tarih ve saat değeri böylece aynı anda kaydedilen değer olarak geri yüklenen değer tanımlayan bilgileri bölge.  
  
### <a name="to-round-trip-a-datetime-value"></a>Bir DateTime değerini gidiş dönüşlü hale getirmek için  
  
1.  Dönüştürme <xref:System.DateTime> çağırarak kendi dize gösterimi değerine <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirticisi yöntemiyle.  
  
2.  Dize gösterimini Kaydet <xref:System.DateTime> değer bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.  
  
3.  Temsil eden dize almak <xref:System.DateTime> değeri.  
  
4.  Çağrı <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve geçişi <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.  
  
 Aşağıdaki örnek gösterilmektedir gidiş nasıl bir <xref:System.DateTime> değeri.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Zaman gidiş bir <xref:System.DateTime> değeri, bu teknik başarıyla her yerel ve evrensel zaman zaman korur. Örneğin, bir yerel varsa <xref:System.DateTime> değeri ABD sisteminde kaydedilir Pasifik Standart saat dilimi ve ABD sisteminde geri Orta standart saat dilimi, geri yüklenen tarih ve saat iki saat dilimi arasındaki zaman farkı yansıtır özgün zamandan sonra iki saat olacaktır. Ancak, bu teknik için mutlaka tam doğru değildir kez belirtilmemiş. Tüm <xref:System.DateTime> özelliği değerlerini <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified> iseler yerel saat olarak kabul edilir. Bu durumda, değilse <xref:System.DateTime> başarıyla doğru noktası zamanında belirtmez. Bu sınırlamaya geçici çözümü sıkı bir tarih ve saat değeri kayıt için kendi saat dilimi ile eşleştiği ve geri yükleme işlemi kullanmaktır.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Bir DateTimeOffset değerini gidiş dönüşlü hale getirmek için  
  
1.  Dönüştürme <xref:System.DateTimeOffset> çağırarak kendi dize gösterimi değerine <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> "o" biçim belirticisi yöntemiyle.  
  
2.  Dize gösterimini Kaydet <xref:System.DateTimeOffset> değer bir dosyaya veya bir işlem, uygulama etki alanı veya makine sınırı arasında geçirin.  
  
3.  Temsil eden dize almak <xref:System.DateTimeOffset> değeri.  
  
4.  Çağrı <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> yöntemi ve geçişi <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> değeri olarak `styles` parametresi.  
  
 Aşağıdaki örnek gösterilmektedir gidiş nasıl bir <xref:System.DateTimeOffset> değeri.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Bu yöntem her zaman kesin bir şekilde tanımlayan bir <xref:System.DateTimeOffset> değeri zaman içinde tek bir nokta olarak. Değer daha sonra Eşgüdümlü Evrensel Saat (UTC) çağırarak dönüştürülebilir <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> yöntemi veya dönüştürülebilir belirli bir saat dilimi zamanında çağırarak <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> veya <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi. Bu teknik önemli sınırlandırılmasıdır tarihidir ve üzerinde gerçekleştirildiğinde aritmetik, zaman bir <xref:System.DateTimeOffset> belirli bir saat diliminde saati gösteren bir değer değil, saat diliminin doğru sonuçlar oluşturabilir. Bunun nedeni, zaman bir <xref:System.DateTimeOffset> değeri örneği, kendi saat diliminden ilişkisi. Bu nedenle, tarih ve saat hesaplamaları gerçekleştirdiğinizde, saat diliminin ayarlama kuralları artık uygulanabilir. Bir tarih ve saat değeri ile kendi eşlik eden saat dilimi içeren özel bir tür tanımlayarak bu soruna geçici çözüm bulabilirsiniz.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Bir tarih ve saat değerini kendi saat dilimiyle gidiş dönüşlü hale getirmek için  
  
1.  Bir sınıf veya yapı iki alanlarla tanımlayın. İlk alanı bir <xref:System.DateTime> veya <xref:System.DateTimeOffset> nesne ve ikinci bir <xref:System.TimeZoneInfo> nesnesi. Aşağıdaki örnek, bu tür bir türün basit bir sürümüdür.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Sınıfı işaretlemek <xref:System.SerializableAttribute> özniteliği.  
  
3.  Kullanarak nesne seri hale <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> yöntemi.  
  
4.  Nesnesini kullanarak geri <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> yöntemi.  
  
5.  Atama (C# ') veya (Visual Basic'te) için uygun türde bir nesne seri durumdan çıkarılmış Nesne Dönüştür.  
  
 Aşağıdaki örnek, nasıl tarih ve saat ve saat dilimi bilgilerini depolar gidiş nesneyi gösterilmektedir.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Bu teknik her zaman belirsizliğe her ikisi de önce ve sonra kaydedilmiş ve geri, sağlanan birleşik tarih ve saat ve saat dilimi nesne uyarlamasını tarih değeri ile eşitlenmemiş hale gelmesine izin vermez zaman doğru noktası yansıtması gerekir saat dilimi değeri.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnekler gerektirir:  
  
-   Şu ad alanlarından C# ile içe aktarılacağını `using` deyimleri veya [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` deyimleri:  
  
    -   <xref:System>(C# yalnızca).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   System.Core.dll referansı.  
  
-   Her örnek, dışındaki kod `DateInTimeZone` sınıfı, bir sınıf veya Visual Basic modülü dahil, yöntemleri Sarmalanan ve çağrılır `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme işlemlerini gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçme](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
