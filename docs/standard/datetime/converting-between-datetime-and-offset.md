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
ms.openlocfilehash: 830e3e6e98be2eaaff2af6c0bdac650732833ab7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864433"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime ve DateTimeOffset arasında dönüştürme

Rağmen <xref:System.DateTimeOffset> yapısı sağlar bir saat dilimini Tanıma ' büyük ölçüde <xref:System.DateTime> yapısı, <xref:System.DateTime> parametreleri yöntem çağrılarında daha yaygın olarak kullanılır. Bu nedenle, dönüştürme yeteneği <xref:System.DateTimeOffset> değerler <xref:System.DateTime> değerleri ve tersi özellikle önemlidir. Bu konu, mümkün olduğunca saat dilimi bilgilerini koruyan bir şekilde dönüştürmeler gerçekleştirmek nasıl gösterir.

> [!NOTE]
> Hem <xref:System.DateTime> ve <xref:System.DateTimeOffset> türleri saat diliminde saatleri temsil eden, bazı sınırlamalar sahiptir. İle kendi <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTime> yalnızca Eşgüdümlü Evrensel Saat (UTC) ve sistemin yerel saat dilimi yansıtacak şekilde yapamaz. <xref:System.DateTimeOffset> bir süre UTC ile olan uzaklığı, ancak gerçek saat dilimi uzaklığı, ait yansıtmaz yansıtır. Saat değerleri ve saat dilimleri için destek hakkında daha fazla ayrıntı için bkz: [seçme arasında DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>DateTimeOffset ilk tarih-saat dönüştürme

<xref:System.DateTimeOffset> Yapısı gerçekleştirmek için iki eşdeğer yöntemleri sağlayan <xref:System.DateTime> için <xref:System.DateTimeOffset> çoğu dönüştürmeleri için uygun olan dönüştürme:

* <xref:System.DateTimeOffset.%23ctor%2A> Oluşturan yeni bir oluşturucu <xref:System.DateTimeOffset> nesnesini temel alan bir <xref:System.DateTime> değeri.

* Atayabilirsiniz örtülü dönüştürme işlecine bir <xref:System.DateTime> değerini bir <xref:System.DateTimeOffset> nesne.

UTC ve yerel <xref:System.DateTime> değerleri <xref:System.DateTimeOffset.Offset%2A> ortaya çıkan özellik <xref:System.DateTimeOffset> değeri UTC veya yerel saat dilimi farkı doğru olarak yansıtır. Örneğin, aşağıdaki kod bir UTC saati eşdeğerine dönüştürür <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Bu durumda, uzaklığı `utcTime2` 00:00 değişkendir. Benzer şekilde, aşağıdaki kod bir yerel saat eşdeğerine dönüştürür <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ancak, <xref:System.DateTime> ayarlanmış değerleri <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, bu iki dönüştürme yöntemleri bir <xref:System.DateTimeOffset> olan uzaklığı, yerel saat dilimi değeri. Bu ABD bölgesinde çalıştırılan aşağıdaki örnekte gösterilmiştir Pasifik Standart saat dilimi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Varsa <xref:System.DateTime> tarih ve UTC ve yerel saat dilimi dışında bir şey saat değeri yansıtır, kendisine dönüştürebilirsiniz bir <xref:System.DateTimeOffset> değeri ve aşırı yüklenmiş çağırarak saat dilimi bilgilerini korumak <xref:System.DateTimeOffset.%23ctor%2A> Oluşturucusu. Örneğin, aşağıdaki örnekte örnekleyen bir <xref:System.DateTimeOffset> merkezi standart saat gösteren nesne.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Bu oluşturucu aşırı yüklemesi, ikinci parametresi bir <xref:System.TimeSpan> zaman uzaklığını UTC biçiminden temsil eden nesne çağrılarak alınabilir <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> yöntemi zaman karşılık gelen saat dilimi. Tek parametresi yöntemin <xref:System.DateTime> dönüştürülecek tarih ve saati gösteren bir değer. Gün ışığından yararlanma saat dilimi destekliyorsa, bu parametre, belirli bir tarih ve saat için uygun uzaklık belirlemek yöntem sağlar.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTime DateTimeOffset öğesinden dönüştürme

<xref:System.DateTimeOffset.DateTime%2A> Özelliği gerçekleştirmek için kullanılan en yaygın olarak <xref:System.DateTimeOffset> için <xref:System.DateTime> dönüştürme. Ancak, döndürür bir <xref:System.DateTime> ayarlanmış değer <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified>, aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Bunun hakkında herhangi bir bilgi anlamı <xref:System.DateTimeOffset> değerinin ilişki UTC'ye dönüştürme kayıp olduğunda <xref:System.DateTimeOffset.DateTime%2A> özelliği kullanılır. Bu etkiler <xref:System.DateTimeOffset> çünkü UTC saati veya sistemin yerel saate karşılık gelen değerleri <xref:System.DateTimeOffset.DateTime%2A> yapısını yansıtan bu iki saat dilimindeki bir yalnızca kendi <xref:System.DateTime.Kind%2A> özelliği.

Dönüştürülürken mümkün olduğunca fazla saat dilimi bilgilerini korumak için bir <xref:System.DateTimeOffset> için bir <xref:System.DateTime> kullanabileceğiniz değeri <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özellikleri.

### <a name="converting-a-utc-time"></a>UTC saati dönüştürme

Belirtmek için bir dönüştürülmüş <xref:System.DateTimeOffset.DateTime%2A> değeri UTC saati, değerini alabilir <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> özelliği. Bu farklıdır <xref:System.DateTimeOffset.DateTime%2A> iki yolla özelliği:

* Döndürür bir <xref:System.DateTime> ayarlanmış değer <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc>.

* Varsa <xref:System.DateTimeOffset.Offset%2A> özellik değeri eşit değil <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, saat UTC'ye dönüştürür.

> [!NOTE]
> Dönüştürülen uygulamanız gerekiyorsa <xref:System.DateTime> değerlerini zaman içinde kesin bir şekilde tek bir nokta tanımlamak, kullanmayı düşünmelisiniz <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> tüm özellik <xref:System.DateTimeOffset> için <xref:System.DateTime> dönüştürme.

Aşağıdaki kod <xref:System.DateTimeOffset.UtcDateTime%2A> dönüştürmek için özellik bir <xref:System.DateTimeOffset> eşit olan uzaklık değeri <xref:System.TimeSpan.Zero?displayProperty=nameWithType> için bir <xref:System.DateTime> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Aşağıdaki kod <xref:System.DateTimeOffset.UtcDateTime%2A> özelliği üzerinde bir saat dilimi dönüştürmesi hem bir tür dönüştürmesi gerçekleştirmek için bir <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Yerel saat dönüştürme

Belirtmek için bir <xref:System.DateTimeOffset> değer yerel saat temsil eder, geçirebilirsiniz <xref:System.DateTime> tarafından döndürülen değer <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> özelliğini `static` (`Shared` Visual Basic'te) <xref:System.DateTime.SpecifyKind%2A> yöntemi. Yöntemi, tarih ve saat, birinci parametre olarak geçirilen döndürür, ancak ayarlar <xref:System.DateTime.Kind%2A> , ikinci parametre tarafından belirtilen değere özelliği. Aşağıdaki kod <xref:System.DateTime.SpecifyKind%2A> dönüştürülürken yöntemi bir <xref:System.DateTimeOffset> olan uzaklığı, yerel saat dilimi karşılık gelen bir değer.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Ayrıca <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> dönüştürmek için özellik bir <xref:System.DateTimeOffset> yerel değer <xref:System.DateTime> değeri. <xref:System.DateTime.Kind%2A> Özelliği döndürülen <xref:System.DateTime> değer <xref:System.DateTimeKind.Local>. Aşağıdaki kod <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> dönüştürülürken özelliği bir <xref:System.DateTimeOffset> olan uzaklığı, yerel saat dilimi karşılık gelen bir değer. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Aldığınızda bir <xref:System.DateTime> kullanarak değer <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özellik, özelliğin `get` erişimci ilk dönüştürür <xref:System.DateTimeOffset> değerini UTC'ye, ardından bunu yerel saat olarak çağırarak dönüştüren <xref:System.DateTimeOffset.ToLocalTime%2A> yöntemi. Yani arasında bir değer alabilir <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> bir tür dönüştürmesi gerçekleştirmek aynı anda bir saat dilimi dönüştürmesi gerçekleştirmek için özellik. Ayrıca, yerel saat diliminin ayarlama kuralları dönüşüm gerçekleştirme içinde uygulanan anlamına gelir. Aşağıdaki kod kullanışını <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> hem bir türü hem de saat dilimi dönüştürmesi gerçekleştirmek için özellik.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Bir genel amaçlı bir dönüştürme yöntemi

Aşağıdaki örnek adlı bir yöntem tanımlar `ConvertFromDateTimeOffset` dönüştüren <xref:System.DateTimeOffset> değerler <xref:System.DateTime> değerleri. Üzerinde uzaklığı bağlı olarak, belirler olmadığını <xref:System.DateTimeOffset> değeri UTC saati, yerel saat ya da başka bir zaman ve döndürülen tarih ve saat değerinin tanımlar <xref:System.DateTime.Kind%2A> özelliği uygun şekilde.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

İzleme örneği çağrıları `ConvertFromDateTimeOffset` yöntemini <xref:System.DateTimeOffset> UTC saati, yerel saat ve ABD'deki bir süre temsil değerleri Merkezi standart saat dilimi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Bu kod, uygulama ve onun tarih ve saat değerlerini kaynağına bağlı olarak her zaman geçerli olmayabilir iki varsayımlar kullandığına dikkat edin:

* Bir tarih ve saat olan uzaklık değeri varsayar <xref:System.TimeSpan.Zero?displayProperty=nameWithType> UTC temsil eder. Aslında, UTC saati, belirli bir saat dilimini değildir, ancak saatler dünyanın saat diliminde olduğu ile ilgili olarak standart saati. Saat dilimi uzaklığı de sahip olabilir <xref:System.TimeSpan.Zero>.

* Bu, bir tarih ve saat olan uzaklığı yerel saat dilimi eşit yerel saat dilimini temsil edildiğini varsayar. Tarih ve saat değerlerini kendi özgün saat diliminden noktanızla ilişkisi olduğundan, bu durumda olmayabilir; Tarih ve saat aynı uzaklığı olan başka bir saat dilimindeki kaynaklanan.

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
