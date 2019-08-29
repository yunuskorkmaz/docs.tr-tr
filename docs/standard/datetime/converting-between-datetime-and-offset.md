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
ms.openlocfilehash: eb91ed8edd0c5cd3cb1d051157596f311718195d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107058"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime ve DateTimeOffset arasında dönüştürme

Yapısı yapıdan daha fazla sayıda saat dilimi tanıma <xref:System.DateTime> sağlasa da, parametreler yöntem çağrılarında daha yaygın olarak kullanılır. <xref:System.DateTime> <xref:System.DateTimeOffset> Bu nedenle, <xref:System.DateTimeOffset> <xref:System.DateTime> değerleri değerlere dönüştürebilme ve tam tersi özellikle önemlidir. Bu konuda, bu dönüşümler mümkün olduğunca çok saat dilimi bilgilerini koruyan bir şekilde nasıl gerçekleştirileceği gösterilmektedir.

> [!NOTE]
> <xref:System.DateTime> Hem<xref:System.DateTimeOffset> hem de türlerinin saat dilimlerindeki zamanları temsil eden bazı sınırlamaları vardır. <xref:System.DateTime.Kind%2A> ÖzelliğiileyalnızcaEşgüdümlüEvrenselSaat(UTC)vesisteminyerel<xref:System.DateTime> saat dilimini yansıtabilir. <xref:System.DateTimeOffset>saatin UTC 'den sapmasını yansıtır, ancak bu kaydırın ait olduğu gerçek saat dilimini yansıtmaz. Saat değerleri ve saat dilimleri desteğiyle ilgili ayrıntılar için bkz. [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Tarih saatten DateTimeOffset 'e dönüştürme

Yapı <xref:System.DateTimeOffset> , çoğu Dönüştürmelere uygun <xref:System.DateTimeOffset> dönüştürme yapmak <xref:System.DateTime> için iki eşdeğer yol sağlar:

- <xref:System.DateTimeOffset> Bir <xref:System.DateTimeOffset.%23ctor%2A> değeregöreyenibir<xref:System.DateTime> nesne oluşturan Oluşturucu.

- <xref:System.DateTime> Bir<xref:System.DateTimeOffset> nesneye değer atamanıza izin veren örtük dönüştürme işleci.

UTC ve yerel <xref:System.DateTime> değerler için <xref:System.DateTimeOffset.Offset%2A> , sonuçta elde edilen <xref:System.DateTimeOffset> değerin özelliği UTC veya yerel saat dilimi sapmasını doğru bir şekilde yansıtır. Örneğin, aşağıdaki kod UTC saatini eşdeğer <xref:System.DateTimeOffset> değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Bu durumda, `utcTime2` değişkeninin boşluğu 00:00 ' dir. Benzer şekilde, aşağıdaki kod yerel saati eşdeğer <xref:System.DateTimeOffset> değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ancak, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTime> <xref:System.DateTimeOffset> olan değerler için, bu iki dönüştürme yöntemi, yerel saat diliminin bir değeri olan bir değer oluşturur. <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> Bu, ABD 'de çalıştırılan aşağıdaki örnekte gösterilmiştir Pasifik standart saat dilimi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Değer, tarihi ve saati yerel saat dilimi veya UTC dışında bir şekilde yansıtıyor ise, bu değeri bir <xref:System.DateTimeOffset> değere dönüştürebilir ve daha fazla yüklenmiş <xref:System.DateTimeOffset.%23ctor%2A> oluşturucuyu çağırarak saat dilimi bilgilerini koruyabilirsiniz. <xref:System.DateTime> Örneğin, aşağıdaki örnek, merkezi standart saatini <xref:System.DateTimeOffset> yansıtan bir nesnesi oluşturur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Bu Oluşturucu aşırı yüklemesinin ikinci parametresi olan zamanın UTC <xref:System.TimeSpan> 'den sapmasını temsil eden bir nesne, zaman karşılık gelen saat diliminin <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> yöntemi çağırarak alınmalıdır. Metodun tek parametresi <xref:System.DateTime> , dönüştürülecek tarihi ve saati temsil eden değerdir. Saat dilimi yaz saati kaydetme süresini destekliyorsa, bu parametre, yöntemin bu belirli tarih ve saat için uygun sapmayı belirlemesine izin verir.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTimeOffset 'ten DateTime 'a dönüşümler

Özelliği, <xref:System.DateTime> dönüştürmek için en yaygın olarak kullanılır <xref:System.DateTimeOffset>. <xref:System.DateTimeOffset.DateTime%2A> Ancak, aşağıdaki örnekte gösterildiği <xref:System.DateTime> gibi <xref:System.DateTimeKind.Unspecified>, <xref:System.DateTime.Kind%2A> özelliği olan bir değer döndürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Bu, <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.DateTime%2A> özellik kullanıldığında değerin UTC ile olan ilişkisi ile ilgili tüm bilgilerin kaybolduğu anlamına gelir. Bu, <xref:System.DateTimeOffset> yapı, <xref:System.DateTimeOffset.DateTime%2A> <xref:System.DateTime.Kind%2A> özelliğinde yalnızca iki saat dilimini yansıttığından UTC saatine veya sistemin yerel saatine karşılık gelen değerleri etkiler.

Bir <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> değere dönüştürürken mümkün olduğunca çok zaman dilimi bilgilerini korumak için ve özelliklerini kullanabilirsiniz. <xref:System.DateTime>

### <a name="converting-a-utc-time"></a>UTC saatini dönüştürme

Dönüştürülmüş <xref:System.DateTimeOffset.DateTime%2A> bir değerin UTC saati olduğunu göstermek için <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> özelliğin değerini alabilirsiniz. <xref:System.DateTimeOffset.DateTime%2A> Özellikten iki şekilde farklılık gösterir:

- Özelliği <xref:System.DateTime> olan<xref:System.DateTime.Kind%2A>bir değer döndürür. <xref:System.DateTimeKind.Utc>

- Özellik değeri eşit <xref:System.TimeSpan.Zero?displayProperty=nameWithType>değilse, saati UTC 'ye dönüştürür. <xref:System.DateTimeOffset.Offset%2A>

> [!NOTE]
> Uygulamanız, dönüştürülmüş <xref:System.DateTime> değerlerin bir zamanda tek bir noktayı kesin bir şekilde <xref:System.DateTime> belirlemesini gerektiriyorsa, tüm <xref:System.DateTimeOffset> dönüştürmeleri işlemek için <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> özelliğini kullanmayı göz önünde bulundurmanız gerekir.

Aşağıdaki kod <xref:System.DateTimeOffset.UtcDateTime%2A> , bir <xref:System.TimeSpan.Zero?displayProperty=nameWithType> <xref:System.DateTimeOffset> değerideğereeşitolanbirdeğeridönüştürmekiçinözelliğinikullanır.<xref:System.DateTime>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Aşağıdaki kod, bir <xref:System.DateTimeOffset.UtcDateTime%2A> <xref:System.DateTimeOffset> değer üzerinde hem saat dilimi dönüştürmesi hem de tür dönüştürmesi gerçekleştirmek için özelliğini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Yerel saati dönüştürme

<xref:System.DateTimeOffset> Bir değerin yerel saati temsil ettiğini göstermek için, `static` <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.DateTime> değeri (`Shared` Visual Basic) <xref:System.DateTime.SpecifyKind%2A> yöntemine geçirebilirsiniz. Yöntemi, ilk parametresi olarak kendisine geçirilen tarih ve saati döndürür, ancak <xref:System.DateTime.Kind%2A> özelliğini ikinci parametresi tarafından belirtilen değere ayarlar. Aşağıdaki kod, bir değeri <xref:System.DateTime.SpecifyKind%2A> yerel saat dilimine karşılık <xref:System.DateTimeOffset> gelen bir değer dönüştürülürken yöntemini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Bir <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> değeri<xref:System.DateTimeOffset> yerel birdeğeredönüştürmekiçin<xref:System.DateTime> özelliğini de kullanabilirsiniz. Döndürülen <xref:System.DateTime.Kind%2A> değerin<xref:System.DateTime> özelliği<xref:System.DateTimeKind.Local>. Aşağıdaki kod, yerel saat <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> dilimine karşılık gelen bir <xref:System.DateTimeOffset> değer dönüştürülürken özelliğini kullanır. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

<xref:System.DateTime> <xref:System.DateTimeOffset> Özelliğinikullanarakbir<xref:System.DateTimeOffset.ToLocalTime%2A> değer aldığınızda, özelliğin erişimcisiöncedeğeriUTC'yedönüştürür,ardındanyönteminiçağırarakyerelsaatedönüştürür.`get` <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Bu, bir tür dönüştürmesi gerçekleştirirken bir saat dilimi dönüştürmesi <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> gerçekleştirmek için özelliğinden bir değer alabilmeniz anlamına gelir. Ayrıca, dönüştürme işlemi sırasında yerel saat diliminin ayarlama kurallarının uygulandığı anlamına gelir. Aşağıdaki kod, hem tür hem de saat <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> dilimi dönüştürmesi gerçekleştirmek için özelliğinin kullanımını gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Genel amaçlı bir dönüştürme yöntemi

Aşağıdaki örnek, değerleri `ConvertFromDateTimeOffset` <xref:System.DateTime> değerlere dönüştüren <xref:System.DateTimeOffset> adlı bir yöntemi tanımlar. Bu, sapmasını temel alarak <xref:System.DateTimeOffset> değerin UTC saati, yerel saat veya başka bir zaman olduğunu belirler ve döndürülen tarih ve saat <xref:System.DateTime.Kind%2A> değerinin özelliğini uygun şekilde tanımlar.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Aşağıdaki örnek, bir UTC `ConvertFromDateTimeOffset` saatini, yerel <xref:System.DateTimeOffset> saati ve ABD 'de bir saati temsil eden değerleri dönüştürmek için yöntemini çağırır. Merkezi Standart saat dilimi.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Bu kodun, uygulamaya ve Tarih ve saat değerlerinin kaynağına bağlı olarak her zaman geçerli olmayabilir:

- Bu, bir tarih ve saat değerinin, <xref:System.TimeSpan.Zero?displayProperty=nameWithType> sapmasını UTC 'yi temsil ettiğini varsayar. Aslında, UTC belirli bir saat diliminde bir zaman değildir, ancak dünyanın saat dilimlerindeki saatlerin standartlaştırılmış olduğu zamana göre belirlenir. Saat dilimleri de bir uzaklığa <xref:System.TimeSpan.Zero>sahip olabilir.

- Yerel saat dilimine eşit olan bir tarih ve saatin yerel saat dilimini temsil ettiğini varsayar. Tarih ve saat değerlerinin özgün saat dilimlerinden ilişkisi olmadığından, bu durum olmayabilir; Tarih ve saat, aynı uzaklığa sahip başka bir saat diliminde kaynaklı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
