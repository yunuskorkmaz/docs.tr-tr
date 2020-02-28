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
ms.openlocfilehash: 5c19296f75e9e002e88263c5e5efa9917e185ebc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156042"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>DateTime ve DateTimeOffset arasında dönüştürme

<xref:System.DateTimeOffset> yapısı <xref:System.DateTime> yapısından daha fazla zaman dilimi tanıma olanağı sağlasa da, <xref:System.DateTime> parametreleri yöntem çağrılarında daha yaygın olarak kullanılır. Bu nedenle, <xref:System.DateTimeOffset> değerlerini <xref:System.DateTime> değerlerine ve tam tersi olarak dönüştürme özelliği özellikle önemlidir. Bu konuda, bu dönüşümler mümkün olduğunca çok saat dilimi bilgilerini koruyan bir şekilde nasıl gerçekleştirileceği gösterilmektedir.

> [!NOTE]
> <xref:System.DateTime> ve <xref:System.DateTimeOffset> türlerinin her ikisi de saat dilimlerindeki zamanları temsil eden bazı sınırlamalara sahiptir. <xref:System.DateTime.Kind%2A> özelliği ile, <xref:System.DateTime> yalnızca Eşgüdümlü Evrensel Saat (UTC) ve sistemin yerel saat dilimini yansıtabilir. <xref:System.DateTimeOffset> UTC 'den bir zamanın konumunu yansıtır, ancak bu, o kaydırın ait olduğu gerçek saat dilimini yansıtmaz. Saat değerleri ve saat dilimleri desteğiyle ilgili ayrıntılar için bkz. [DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Tarih saatten DateTimeOffset 'e dönüştürme

<xref:System.DateTimeOffset> yapısı, çoğu Dönüştürmelere uygun <xref:System.DateTimeOffset> dönüştürmeye <xref:System.DateTime> gerçekleştirmenin iki benzer yolunu sağlar:

- <xref:System.DateTime> değere göre yeni bir <xref:System.DateTimeOffset> nesnesi oluşturan <xref:System.DateTimeOffset.%23ctor%2A> Oluşturucu.

- Bir <xref:System.DateTimeOffset> nesnesine <xref:System.DateTime> değer atamanıza izin veren örtük dönüştürme işleci.

UTC ve yerel <xref:System.DateTime> değerleri için, elde edilen <xref:System.DateTimeOffset> değerin <xref:System.DateTimeOffset.Offset%2A> özelliği UTC veya yerel saat dilimi sapmasını doğru bir şekilde yansıtır. Örneğin, aşağıdaki kod UTC saatini eşdeğer <xref:System.DateTimeOffset> değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Bu durumda `utcTime2` değişkeninin boşluğu 00:00 ' dir. Benzer şekilde, aşağıdaki kod bir yerel saati eşdeğer <xref:System.DateTimeOffset> değerine dönüştürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Ancak, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>olan <xref:System.DateTime> değerler için, bu iki dönüştürme yöntemi, yerel saat diliminin sapmasını olan bir <xref:System.DateTimeOffset> değeri üretir. Bu, ABD Pasifik standart saat diliminde çalıştırılan aşağıdaki örnekte gösterilmiştir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

<xref:System.DateTime> değeri, tarihi ve saati yerel saat dilimi veya UTC dışında bir şekilde yansıtıyor ise, aşırı yüklenmiş <xref:System.DateTimeOffset.%23ctor%2A> oluşturucusunu çağırarak onu bir <xref:System.DateTimeOffset> değerine dönüştürebilir ve saat dilimi bilgilerini koruyabilirsiniz. Örneğin, aşağıdaki örnek merkezi standart saatini yansıtan bir <xref:System.DateTimeOffset> nesnesi oluşturur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Bu Oluşturucu aşırı yüklemesinin ikinci parametresi olan zamanın UTC 'den sapmasını temsil eden bir <xref:System.TimeSpan> nesnesi, zaman karşılık gelen saat diliminin <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> yöntemi çağırarak alınmalıdır. Metodun tek parametresi, dönüştürülecek tarihi ve saati temsil eden <xref:System.DateTime> değerdir. Saat dilimi yaz saati kaydetme süresini destekliyorsa, bu parametre, yöntemin bu belirli tarih ve saat için uygun sapmayı belirlemesine izin verir.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>DateTimeOffset 'ten DateTime 'a dönüşümler

<xref:System.DateTimeOffset.DateTime%2A> özelliği en yaygın olarak <xref:System.DateTime> dönüştürmeye <xref:System.DateTimeOffset> gerçekleştirmek için kullanılır. Ancak, aşağıdaki örnekte gösterildiği gibi, <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified>olan <xref:System.DateTime> bir değer döndürür.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Bu, <xref:System.DateTimeOffset.DateTime%2A> özelliği kullanıldığında, <xref:System.DateTimeOffset> değerinin UTC ile ilişkisi ile ilgili herhangi bir bilginin dönüştürme tarafından kaybedildiği anlamına gelir. Bu, <xref:System.DateTimeOffset.DateTime%2A> yapısı <xref:System.DateTime.Kind%2A> özelliğinde yalnızca iki saat dilimini yansıttığından UTC saatine veya sistemin yerel saatine karşılık gelen <xref:System.DateTimeOffset> değerlerini etkiler.

Bir <xref:System.DateTimeOffset> <xref:System.DateTime> değerine dönüştürürken mümkün olduğunca çok zaman dilimi bilgilerini korumak için <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> ve <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliklerini kullanabilirsiniz.

### <a name="converting-a-utc-time"></a>UTC saatini dönüştürme

Dönüştürülen <xref:System.DateTimeOffset.DateTime%2A> değerinin UTC saati olduğunu belirtmek için, <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> özelliğinin değerini alabilirsiniz. <xref:System.DateTimeOffset.DateTime%2A> özelliğinden iki şekilde farklılık gösterir:

- <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc>olan <xref:System.DateTime> bir değer döndürür.

- <xref:System.DateTimeOffset.Offset%2A> Özellik değeri <xref:System.TimeSpan.Zero?displayProperty=nameWithType>eşit değilse, saati UTC 'ye dönüştürür.

> [!NOTE]
> Uygulamanız, dönüştürülmüş <xref:System.DateTime> değerlerinin bir zamanda tek bir noktayı kesin olarak belirlemesini gerektiriyorsa, tüm <xref:System.DateTimeOffset> <xref:System.DateTime> Dönüştürmelere işlemek için <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> özelliğini kullanmayı göz önünde bulundurmanız gerekir.

Aşağıdaki kod, <xref:System.DateTimeOffset.UtcDateTime%2A> özelliğini, sapmasını eşit <xref:System.TimeSpan.Zero?displayProperty=nameWithType> bir <xref:System.DateTime> değere <xref:System.DateTimeOffset> dönüştürmek için kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Aşağıdaki kod, bir <xref:System.DateTimeOffset> değerinde hem saat dilimi dönüştürmesi hem de tür dönüştürmesi gerçekleştirmek için <xref:System.DateTimeOffset.UtcDateTime%2A> özelliğini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Yerel saati dönüştürme

<xref:System.DateTimeOffset> bir değerin yerel saati temsil ettiğini göstermek için <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.DateTime> değerini `static` (`Shared` Visual Basic) <xref:System.DateTime.SpecifyKind%2A> yöntemine geçirebilirsiniz. Yöntemi, ilk parametresi olarak kendisine geçirilen tarih ve saati döndürür, ancak <xref:System.DateTime.Kind%2A> özelliğini ikinci parametresi tarafından belirtilen değere ayarlar. Aşağıdaki kod, sapmayı yerel saat dilimine karşılık gelen bir <xref:System.DateTimeOffset> değerini dönüştürürken <xref:System.DateTime.SpecifyKind%2A> yöntemini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

<xref:System.DateTimeOffset> bir değeri yerel <xref:System.DateTime> değerine dönüştürmek için <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliğini de kullanabilirsiniz. Döndürülen <xref:System.DateTime> değerinin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local>. Aşağıdaki kod, sapmayı yerel saat dilimine karşılık gelen bir <xref:System.DateTimeOffset> değerini dönüştürürken <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliğini kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliğini kullanarak bir <xref:System.DateTime> değeri aldığınızda, özelliğin `get` erişimcisi önce <xref:System.DateTimeOffset> değeri UTC 'ye dönüştürür, sonra da <xref:System.DateTimeOffset.ToLocalTime%2A> yöntemini çağırarak yerel saate dönüştürür. Bu, <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliğinden bir değer alabilmeniz için, bir tür dönüştürmesi gerçekleştirirken aynı anda bir saat dilimi dönüştürmesi gerçekleştirebilir. Ayrıca, dönüştürme işlemi sırasında yerel saat diliminin ayarlama kurallarının uygulandığı anlamına gelir. Aşağıdaki kod, hem tür hem de saat dilimi dönüştürmesi gerçekleştirmek için <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> özelliğinin kullanımını gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Genel amaçlı bir dönüştürme yöntemi

Aşağıdaki örnek, <xref:System.DateTimeOffset> değerlerini <xref:System.DateTime> değerlerine dönüştüren `ConvertFromDateTimeOffset` adlı bir yöntemi tanımlar. Bu, sapmasını temel alarak, <xref:System.DateTimeOffset> değerin UTC saati, yerel saat veya başka bir zaman olduğunu belirler ve döndürülen tarih ve saat değerinin <xref:System.DateTime.Kind%2A> özelliğini uygun şekilde tanımlar.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Aşağıdaki örnek, bir UTC saatini, yerel saati ve ABD Orta standart saat diliminde bir saati temsil eden <xref:System.DateTimeOffset> değerlerini dönüştürmek için `ConvertFromDateTimeOffset` yöntemini çağırır.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Bu kodun, uygulamaya ve Tarih ve saat değerlerinin kaynağına bağlı olarak her zaman geçerli olmayabilir:

- Bu, bir tarih ve saat değerinin, uzaklığa göre <xref:System.TimeSpan.Zero?displayProperty=nameWithType> UTC 'yi temsil ettiğini varsayar. Aslında, UTC belirli bir saat diliminde bir zaman değildir, ancak dünyanın saat dilimlerindeki saatlerin standartlaştırılmış olduğu zamana göre belirlenir. Saat dilimleri de <xref:System.TimeSpan.Zero>bir uzaklığa sahip olabilir.

- Yerel saat dilimine eşit olan bir tarih ve saatin yerel saat dilimini temsil ettiğini varsayar. Tarih ve saat değerlerinin özgün saat dilimlerinden ilişkisi olmadığından, bu durum olmayabilir; Tarih ve saat, aynı uzaklığa sahip başka bir saat diliminde kaynaklı olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
