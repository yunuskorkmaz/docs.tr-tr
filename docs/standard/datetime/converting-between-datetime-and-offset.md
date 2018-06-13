---
title: DateTime ve DateTimeOffset arasında dönüştürme
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dec0e5138ecf08783f11d21cd28d7291d27ea68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578254"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime ve DateTimeOffset arasında dönüştürme

Ancak <xref:System.DateTimeOffset> yapısı sağlayan bir saat dilimi tanıma daha büyük ölçüde <xref:System.DateTime> yapısı, <xref:System.DateTime> parametreleri içindeki yöntem çağrılarının daha yaygın olarak kullanılır. Bu nedenle, dönüştürme yeteneği <xref:System.DateTimeOffset> değerler <xref:System.DateTime> değerleri ve bunun tersi de özellikle önemlidir. Bu konu, mümkün olduğunca fazla saat dilimi bilgi korur şekilde dönüştürmeler gerçekleştirme gösterir.

> [!NOTE]
> Hem <xref:System.DateTime> ve <xref:System.DateTimeOffset> saat diliminde saatleri temsil eden olduğunda türlerine sahip bazı sınırlamalar uygulanır. İle <xref:System.DateTime.Kind%2A> özelliği, <xref:System.DateTime> yalnızca Eşgüdümlü Evrensel Saat (UTC) ve sistemin yerel saat dilimini yansıtacak şekilde yapamaz. <xref:System.DateTimeOffset> bir süre UTC uzaklığı, ancak uzaklık, gerçek saat dilimi ait yansıtmaz yansıtır. Saat değerleri ve saat dilimleri için destek hakkında daha fazla ayrıntı için bkz: [seçme arasında DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>DateTimeOffset DateTime gelen dönüştürme

<xref:System.DateTimeOffset> Yapısı sağlar yapmak için iki eşdeğer şekilde <xref:System.DateTime> için <xref:System.DateTimeOffset> çoğu dönüştürmeleri için uygun olan dönüştürme:

* <xref:System.DateTimeOffset.%23ctor%2A> Yeni bir oluşturur Oluşturucusu <xref:System.DateTimeOffset> nesne temel alarak bir <xref:System.DateTime> değeri.

* Atamanızı sağlar örtük dönüşüm işleci bir <xref:System.DateTime> değeri bir <xref:System.DateTimeOffset> nesnesi.

UTC ve yerel <xref:System.DateTime> değerleri, <xref:System.DateTimeOffset.Offset%2A> elde edilen özelliğini <xref:System.DateTimeOffset> değeri doğru olarak UTC veya yerel saat dilimi konumu yansıtır. Örneğin, aşağıdaki kodu UTC zamanı eşdeğerine dönüştürür <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Bu durumda, uzaklığını `utcTime2` 00:00 değişkenidir. Benzer şekilde, aşağıdaki kodu yerel saat eşdeğerine dönüştürür <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ancak, <xref:System.DateTime> özelliği değerlerini <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, bu iki dönüştürme yöntemleri üreten bir <xref:System.DateTimeOffset> olan uzaklığı, yerel saat dilimi değeri. Bu ABD'de çalıştırılan aşağıdaki örnekte gösterilir Pasifik Standart saat dilimi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Varsa <xref:System.DateTime> değer yansıtır UTC ve yerel saat dilimi dışında bir şey, saat ve tarihi, kendisine dönüştürebilirsiniz bir <xref:System.DateTimeOffset> değer ve aşırı yüklenmiş çağırarak saat dilimi bilgilerini korumak <xref:System.DateTimeOffset.%23ctor%2A> Oluşturucusu. Örneğin, aşağıdaki örnek başlatır bir <xref:System.DateTimeOffset> Orta Standart Saati gösteren nesne.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Bu oluşturucu aşırı ikinci parametresi bir <xref:System.TimeSpan> , UTC zaman uzaklığını temsil eden nesnesi alınamıyor çağırarak <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> zaman karşılık gelen saat dilimi yöntemi. Yöntemin tek parametresi <xref:System.DateTime> dönüştürülmesi için tarih ve saati gösteren bir değer. Saat diliminin gün ışığından yararlanma saati destekliyorsa, bu parametre, belirli bir tarih ve saat için uygun uzaklığı belirlemek yöntem sağlar.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTime DateTimeOffset gelen dönüştürme

<xref:System.DateTimeOffset.DateTime%2A> Özelliği gerçekleştirmek için kullanılan en yaygın olarak <xref:System.DateTimeOffset> için <xref:System.DateTime> dönüştürme. Ancak, döndüren bir <xref:System.DateTime> özelliği değeri <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified>aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Bunun hakkında herhangi bir bilgi anlamı <xref:System.DateTimeOffset> UTC değerinin ilişkisi dönüştürme kayıp zaman <xref:System.DateTimeOffset.DateTime%2A> özelliği kullanılır. Bu etkiler <xref:System.DateTimeOffset> UTC saati ya da sistemin yerel saat için karşılık gelen değerleri <xref:System.DateTimeOffset.DateTime%2A> yapısını yansıtır bu iki saat dilimi bir yalnızca kendi <xref:System.DateTime.Kind%2A> özelliği.

Mümkün olduğunca fazla saat dilimi bilgi dönüştürülürken korumak için bir <xref:System.DateTimeOffset> için bir <xref:System.DateTime> kullanabileceğiniz değeri <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özellikleri.

### <a name="converting-a-utc-time"></a>UTC saati dönüştürme

Olduğunu belirten bir dönüştürülmüş <xref:System.DateTimeOffset.DateTime%2A> değeri UTC saati, değerini almak <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> özelliği. Bu farklı <xref:System.DateTimeOffset.DateTime%2A> iki yolla özelliği:

* Döndürdüğü bir <xref:System.DateTime> özelliği değeri <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc>.

* Varsa <xref:System.DateTimeOffset.Offset%2A> özellik değerine eşit değil <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, süresi için UTC dönüştürür.

> [!NOTE]
> Uygulamanız dönüştürülen gerektiriyorsa <xref:System.DateTime> değerleri zaman içinde kesin bir şekilde tek bir nokta tanımlamak, kullanmayı düşünmelisiniz <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> tüm işlemeye özelliği <xref:System.DateTimeOffset> için <xref:System.DateTime> dönüşümler.

Aşağıdaki kod <xref:System.DateTimeOffset.UtcDateTime%2A> dönüştürmek için özellik bir <xref:System.DateTimeOffset> olan uzaklık eşittir değeri <xref:System.TimeSpan.Zero?displayProperty=nameWithType> için bir <xref:System.DateTime> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Aşağıdaki kod <xref:System.DateTimeOffset.UtcDateTime%2A> bir saat dilimi dönüştürmesi ve tür dönüştürmeleri gerçekleştirileceği özelliği bir <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Yerel saat dönüştürme

Olduğunu belirten bir <xref:System.DateTimeOffset> değeri yerel saat temsil eder, geçirebilirsiniz <xref:System.DateTime> tarafından döndürülen değer <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> özelliğine `static` (`Shared` Visual Basic'te) <xref:System.DateTime.SpecifyKind%2A> yöntemi. Yöntemi, ilk parametre olarak geçirilen saat ve tarihi verir, ancak ayarlar <xref:System.DateTime.Kind%2A> kendi ikinci parametresi tarafından belirtilen değere özelliği. Aşağıdaki kod <xref:System.DateTime.SpecifyKind%2A> dönüştürülürken yöntemi bir <xref:System.DateTimeOffset> olan uzaklık, yerel saat dilimine karşılık gelen değer.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Aynı zamanda <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> dönüştürmek için özellik bir <xref:System.DateTimeOffset> yerel değerin <xref:System.DateTime> değeri. <xref:System.DateTime.Kind%2A> Özelliği döndürülen <xref:System.DateTime> değer <xref:System.DateTimeKind.Local>. Aşağıdaki kod <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> dönüştürülürken özelliği bir <xref:System.DateTimeOffset> olan uzaklık, yerel saat dilimine karşılık gelen değer. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Aldığınızda bir <xref:System.DateTime> kullanarak değer <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliği, özelliğin `get` erişimci ilk dönüştürür <xref:System.DateTimeOffset> değeri UTC'ye, ardından bunu yerel saate çağırarak dönüştüren <xref:System.DateTimeOffset.ToLocalTime%2A> yöntemi. Bu, arasında bir değer alabilirsiniz anlamına gelir <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> bir tür dönüştürme gerçekleştirmek aynı anda bir saat dilimi dönüştürme gerçekleştirmek için özellik. Ayrıca, yerel saat diliminin ayarlama kuralları dönüştürme gerçekleştirmede uygulanan anlamına gelir. Aşağıdaki kod kullanımını göstermektedir <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> türü ve bir saat dilimi dönüştürme gerçekleştirmek için özellik.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Genel amaçlı dönüştürme yöntemi

Aşağıdaki örnek, adlandırılmış bir yöntem tanımlar `ConvertFromDateTimeOffset` dönüştüren <xref:System.DateTimeOffset> değerler <xref:System.DateTime> değerleri. Sapması üzerinde bağlı olarak, belirler olup olmadığını <xref:System.DateTimeOffset> değeri UTC saati, yerel saat ya da başka bir zaman ve döndürülen tarih ve saat değerinin tanımlar <xref:System.DateTime.Kind%2A> özelliği uygun şekilde.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

İzleme örnek çağrıları `ConvertFromDateTimeOffset` dönüştürmek için yöntem <xref:System.DateTimeOffset> UTC saati, yerel saat ve saat ABD temsil eden değerleri Orta standart saat dilimi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Bu kod, uygulama ve onun tarih ve saat değerlerini kaynak bağlı olarak her zaman geçerli olmayabilir iki varsayımlar kullandığına dikkat edin:

* Bir tarih ve saat olan uzaklık değeri varsayar <xref:System.TimeSpan.Zero?displayProperty=nameWithType> UTC temsil eder. Aslında, UTC saati belirli bir saat dilimi, bir değildir, ancak hangi bağlantılı olarak dünyanın saat diliminde kez standartlaştırılmış zaman. Saat dilimleri ayrıca uzaklığı sahip <xref:System.TimeSpan.Zero>.

* Bu, bir tarih ve saat olan uzaklık, yerel saat dilimini eşittir yerel saat dilimini temsil ettiğini varsayar. Tarih ve saat değerleri kendi özgün saat diliminden ilişkilendirmesi olduğundan, bu durumda olmayabilir; Tarih ve saat aynı uzaklıkları başka bir saat diliminde kaynaklanan.

## <a name="see-also"></a>Ayrıca bkz.

[Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
