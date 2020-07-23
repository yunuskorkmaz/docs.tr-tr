---
title: DateTime ve DateTimeOffset arasında dönüştürme
description: .NET 'teki DateTimeOffset değerleri ile tarih saat değerleri arasında dönüştürme. DateTimeOffset yapısı, DateTime yapısından daha fazla zaman dilimi tanıma sağlar.
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
ms.openlocfilehash: 86f2c982d7f87e83102933d1de73d6e13086dc87
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924909"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime ve DateTimeOffset arasında dönüştürme

<xref:System.DateTimeOffset>Yapısı yapıdan daha fazla sayıda saat dilimi tanıma sağlasa da <xref:System.DateTime> , <xref:System.DateTime> Parametreler yöntem çağrılarında daha yaygın olarak kullanılır. Bu nedenle, <xref:System.DateTimeOffset> değerleri değerlere dönüştürebilme <xref:System.DateTime> ve tam tersi özellikle önemlidir. Bu konuda, bu dönüşümler mümkün olduğunca çok saat dilimi bilgilerini koruyan bir şekilde nasıl gerçekleştirileceği gösterilmektedir.

> [!NOTE]
> Hem <xref:System.DateTime> hem de <xref:System.DateTimeOffset> türlerinin saat dilimlerindeki zamanları temsil eden bazı sınırlamaları vardır. Özelliği ile <xref:System.DateTime.Kind%2A> <xref:System.DateTime> yalnızca Eşgüdümlü Evrensel Saat (UTC) ve sistemin yerel saat dilimini yansıtabilir. <xref:System.DateTimeOffset>saatin UTC 'den sapmasını yansıtır, ancak bu kaydırın ait olduğu gerçek saat dilimini yansıtmaz. Saat değerleri ve saat dilimleri desteğiyle ilgili ayrıntılar için bkz. [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Tarih saatten DateTimeOffset 'e dönüştürme

<xref:System.DateTimeOffset>Yapı, <xref:System.DateTime> <xref:System.DateTimeOffset> çoğu Dönüştürmelere uygun dönüştürme yapmak için iki eşdeğer yol sağlar:

- <xref:System.DateTimeOffset.%23ctor%2A> <xref:System.DateTimeOffset> Bir değere göre yeni bir nesne oluşturan Oluşturucu <xref:System.DateTime> .

- Bir nesneye değer atamanıza izin veren örtük dönüştürme işleci <xref:System.DateTime> <xref:System.DateTimeOffset> .

UTC ve yerel <xref:System.DateTime> değerler için, <xref:System.DateTimeOffset.Offset%2A> sonuçta elde edilen DEĞERIN özelliği <xref:System.DateTimeOffset> UTC veya yerel saat dilimi sapmasını doğru bir şekilde yansıtır. Örneğin, aşağıdaki kod UTC saatini eşdeğer <xref:System.DateTimeOffset> değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Bu durumda, `utcTime2` değişkeninin boşluğu 00:00 ' dir. Benzer şekilde, aşağıdaki kod yerel saati eşdeğer <xref:System.DateTimeOffset> değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ancak, <xref:System.DateTime> özelliği olan değerler için <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , bu iki dönüştürme yöntemi, <xref:System.DateTimeOffset> yerel saat diliminin bir değeri olan bir değer oluşturur. Bu, ABD Pasifik standart saat diliminde çalıştırılan aşağıdaki örnekte gösterilmiştir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Değer, <xref:System.DateTime> tarihi ve saati yerel saat dilimi veya UTC dışında bir şekilde yansıtıyor ise, bu <xref:System.DateTimeOffset> değeri bir değere dönüştürebilir ve daha fazla yüklenmiş oluşturucuyu çağırarak saat dilimi bilgilerini koruyabilirsiniz <xref:System.DateTimeOffset.%23ctor%2A> . Örneğin, aşağıdaki örnek, <xref:System.DateTimeOffset> merkezi standart saatini yansıtan bir nesnesi oluşturur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Bu Oluşturucu aşırı yüklemesinin ikinci parametresi <xref:System.TimeSpan> olan zamanın UTC 'den sapmasını temsil eden bir nesne, <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> zaman karşılık gelen saat diliminin yöntemi çağırarak alınmalıdır. Metodun tek parametresi, <xref:System.DateTime> Dönüştürülecek tarihi ve saati temsil eden değerdir. Saat dilimi yaz saati kaydetme süresini destekliyorsa, bu parametre, yöntemin bu belirli tarih ve saat için uygun sapmayı belirlemesine izin verir.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTimeOffset 'ten DateTime 'a dönüşümler

<xref:System.DateTimeOffset.DateTime%2A>Özelliği, dönüştürmek için en yaygın olarak kullanılır <xref:System.DateTimeOffset> <xref:System.DateTime> . Ancak, <xref:System.DateTime> <xref:System.DateTime.Kind%2A> Aşağıdaki örnekte gösterildiği gibi, özelliği olan bir değer döndürür <xref:System.DateTimeKind.Unspecified> .

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Bu, <xref:System.DateTimeOffset> özellik kullanıldığında DEĞERIN UTC ile olan ilişkisi ile ilgili tüm bilgilerin kaybolduğu anlamına gelir <xref:System.DateTimeOffset.DateTime%2A> . Bu <xref:System.DateTimeOffset> , <xref:System.DateTimeOffset.DateTime%2A> Yapı, özelliğinde yalnızca iki saat dilimini YANSıTTıĞıNDAN UTC saatine veya sistemin yerel saatine karşılık gelen değerleri etkiler <xref:System.DateTime.Kind%2A> .

Bir değere dönüştürürken mümkün olduğunca çok zaman dilimi bilgilerini korumak için <xref:System.DateTimeOffset> <xref:System.DateTime> <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliklerini kullanabilirsiniz.

### <a name="converting-a-utc-time"></a>UTC saatini dönüştürme

Dönüştürülmüş bir <xref:System.DateTimeOffset.DateTime%2A> DEĞERIN UTC saati olduğunu göstermek için özelliğin değerini alabilirsiniz <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> . <xref:System.DateTimeOffset.DateTime%2A>Özellikten iki şekilde farklılık gösterir:

- <xref:System.DateTime>Özelliği olan bir değer döndürür <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc> .

- <xref:System.DateTimeOffset.Offset%2A>Özellik değeri eşit değilse <xref:System.TimeSpan.Zero?displayProperty=nameWithType> , saati UTC 'ye dönüştürür.

> [!NOTE]
> Uygulamanız <xref:System.DateTime> , dönüştürülmüş değerlerin bir zamanda tek bir noktayı kesin bir şekilde belirlemesini gerektiriyorsa, <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> tüm dönüştürmeleri işlemek için özelliğini kullanmayı göz önünde bulundurmanız <xref:System.DateTimeOffset> gerekir <xref:System.DateTime> .

Aşağıdaki kod, bir değeri <xref:System.DateTimeOffset.UtcDateTime%2A> <xref:System.DateTimeOffset> değere eşit olan bir değeri dönüştürmek için özelliğini kullanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType> <xref:System.DateTime> .

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Aşağıdaki kod, bir <xref:System.DateTimeOffset.UtcDateTime%2A> değer üzerinde hem saat dilimi dönüştürmesi hem de tür dönüştürmesi gerçekleştirmek için özelliğini kullanır <xref:System.DateTimeOffset> .

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Yerel saati dönüştürme

Bir <xref:System.DateTimeOffset> değerin yerel saati temsil ettiğini göstermek için, <xref:System.DateTime> özelliği tarafından döndürülen değeri <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> `static` ( `Shared` Visual Basic) <xref:System.DateTime.SpecifyKind%2A> yöntemine geçirebilirsiniz. Yöntemi, ilk parametresi olarak kendisine geçirilen tarih ve saati döndürür, ancak <xref:System.DateTime.Kind%2A> özelliğini ikinci parametresi tarafından belirtilen değere ayarlar. Aşağıdaki kod, <xref:System.DateTime.SpecifyKind%2A> bir <xref:System.DateTimeOffset> değeri yerel saat dilimine karşılık gelen bir değer dönüştürülürken yöntemini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>Bir <xref:System.DateTimeOffset> değeri yerel bir değere dönüştürmek için özelliğini de kullanabilirsiniz <xref:System.DateTime> . <xref:System.DateTime.Kind%2A>Döndürülen <xref:System.DateTime> değerin özelliği <xref:System.DateTimeKind.Local> . Aşağıdaki kod, <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset> yerel saat dilimine karşılık gelen bir değer dönüştürülürken özelliğini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

<xref:System.DateTime>Özelliğini kullanarak bir değer aldığınızda <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> , özelliğin `get` ERIŞIMCISI önce <xref:System.DateTimeOffset> değeri UTC 'ye dönüştürür, ardından yöntemini çağırarak yerel saate dönüştürür <xref:System.DateTimeOffset.ToLocalTime%2A> . Bu <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> , bir tür dönüştürmesi gerçekleştirirken bir saat dilimi dönüştürmesi gerçekleştirmek için özelliğinden bir değer alabilmeniz anlamına gelir. Ayrıca, dönüştürme işlemi sırasında yerel saat diliminin ayarlama kurallarının uygulandığı anlamına gelir. Aşağıdaki kod, <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> hem tür hem de saat dilimi dönüştürmesi gerçekleştirmek için özelliğinin kullanımını gösterir. Örnek çıktı, Pasifik saati dilimine (ABD ve Kanada) ayarlanmış bir makine içindir. Kasım tarihi UTC-8 olan Pasifik standart saati, Haziran tarihi de UTC-7 olan gün ışığından yararlanma saatine göre yapılır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Genel amaçlı bir dönüştürme yöntemi

Aşağıdaki örnek, `ConvertFromDateTimeOffset` değerleri değerlere dönüştüren adlı bir yöntemi tanımlar <xref:System.DateTimeOffset> <xref:System.DateTime> . Bu, sapmasını temel alarak <xref:System.DateTimeOffset> DEĞERIN UTC saati, yerel saat veya başka bir zaman olduğunu belirler ve döndürülen tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğini uygun şekilde tanımlar.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Aşağıdaki örnek, `ConvertFromDateTimeOffset` <xref:System.DateTimeOffset> bir UTC zamanını, yerel saati ve ABD Orta standart saat diliminde bir saati temsil eden değerleri dönüştürmek için yöntemini çağırır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Bu kodun, uygulamaya ve Tarih ve saat değerlerinin kaynağına bağlı olarak her zaman geçerli olmayabilir:

- Bu, bir tarih ve saat değerinin, sapmasını UTC 'yi <xref:System.TimeSpan.Zero?displayProperty=nameWithType> temsil ettiğini varsayar. Aslında, UTC belirli bir saat diliminde bir zaman değildir, ancak dünyanın saat dilimlerindeki saatlerin standartlaştırılmış olduğu zamana göre belirlenir. Saat dilimleri de bir uzaklığa sahip olabilir <xref:System.TimeSpan.Zero> .

- Yerel saat dilimine eşit olan bir tarih ve saatin yerel saat dilimini temsil ettiğini varsayar. Tarih ve saat değerlerinin özgün saat dilimlerinden ilişkisi olmadığından, bu durum olmayabilir; Tarih ve saat, aynı uzaklığa sahip başka bir saat diliminde kaynaklı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
