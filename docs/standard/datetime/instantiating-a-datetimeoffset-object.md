---
title: Bir DateTimeOffset nesnesinin örneğini oluşturma
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50cc71b62581e1fb9302fe241abf6349afd33f8d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106638"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Bir DateTimeOffset nesnesinin örneğini oluşturma

<xref:System.DateTimeOffset> Yapı Yeni<xref:System.DateTimeOffset> değerler oluşturmak için çeşitli yollar sunar. Çoğu, yeni <xref:System.DateTime> değerleri örneklenme için kullanılabilen yöntemlere karşılık gelir ve Tarih ve saat değerinin Eşgüdümlü Evrensel Saat (UTC) ile sapmasını belirtmenize olanak tanır. Özellikle, aşağıdaki yollarla bir <xref:System.DateTimeOffset> değer örneği oluşturabilirsiniz:

- Tarih ve saat değişmez değerini kullanarak.

- Bir <xref:System.DateTimeOffset> oluşturucuyu çağırarak.

- Bir değeri <xref:System.DateTimeOffset> örtük olarak değere dönüştürerek.

- Bir tarih ve saatin dize gösterimini ayrıştırarak.

Bu konu, yeni <xref:System.DateTimeOffset> değerleri örneklemenize yönelik bu yöntemleri gösteren daha ayrıntılı ve kod örnekleri sunar.

## <a name="date-and-time-literals"></a>Tarih ve saat sabit değerleri

Bunu destekleyen diller için, bir <xref:System.DateTime> değeri örneketmenin en yaygın yöntemlerinden biri, tarihi ve saati sabit kodlanmış değişmez değer olarak sağlamaktır. Örneğin, aşağıdaki Visual Basic kodu değeri 1 Ocak 2008 <xref:System.DateTime> , 10:00 ' de olan bir nesne oluşturur.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>değerler, değişmez değerleri destekleyen <xref:System.DateTime> diller kullanılırken tarih ve saat değişmez değerleri kullanılarak da başlatılabilir. Örneğin, aşağıdaki Visual Basic kodu bir <xref:System.DateTimeOffset> nesnesi oluşturur.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Konsol çıktısı gösterdiği gibi, <xref:System.DateTimeOffset> bu şekilde oluşturulan değer yerel saat diliminin sapmasını atanır. Yani, bir karakter <xref:System.DateTimeOffset> sabiti kullanılarak atanan bir değer, kod farklı bilgisayarlarda çalıştırıldığında tek bir zaman noktası tanımlamaz.

## <a name="datetimeoffset-constructors"></a>DateTimeOffset oluşturucuları

<xref:System.DateTimeOffset> Tür altı Oluşturucu tanımlar. Bunlardan dördü, doğrudan <xref:System.DateTime> oluşturuculara karşılık gelir ve Tarih ve saatin UTC 'den sapmasını tanımlayan ek türde <xref:System.TimeSpan> bir parametredir. Bunlar, bireysel tarih ve saat <xref:System.DateTimeOffset> bileşenlerinin değerine göre bir değer tanımlamanızı sağlar. Örneğin, aşağıdaki kod, 7/1/2008 12:05 ve 01:00 arasındaki özdeş değerleri içeren <xref:System.DateTimeOffset> nesneleri örneklemek için bu dört Oluşturucu kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Bir nesne kullanılarak, Oluşturucu için bağımsız değişkenlerden <xref:System.DateTimeOffset> biri olarak bir <xref:System.Globalization.PersianCalendar> nesnesi kullanılarak örneklenen nesnenin değeri, bu, Farsça takvimi yerine Gregoryen 'da bir tarih olarak ifade edilir. Farsça takvimini kullanarak bir tarih çıktısını almak için <xref:System.Globalization.PersianCalendar> konusundaki örneğe bakın.

Diğer iki Oluşturucu bir <xref:System.DateTimeOffset> <xref:System.DateTime> değerden bir nesne oluşturur. Bunlardan ilki tek bir parametreye, <xref:System.DateTime> bir <xref:System.DateTimeOffset> değere dönüştürülecek değere sahiptir. Elde edilen <xref:System.DateTimeOffset> değerin boşluğu, oluşturucunun tek parametresinin <xref:System.DateTime.Kind%2A> özelliğine bağlıdır. Değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, konum değerine <xref:System.TimeSpan.Zero?displayProperty=nameWithType>eşit olarak ayarlanır. Aksi takdirde, kendi kayması yerel saat dilimine eşit olarak ayarlanır. Aşağıdaki örnek, UTC ve yerel saat dilimini temsil eden nesnelerin <xref:System.DateTimeOffset> örneğini oluşturmak için bu oluşturucunun kullanımını göstermektedir:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Tek <xref:System.DateTimeOffset> <xref:System.DateTime> <xref:System.DateTimeOffset> bir parametreye sahip olan oluşturucunun aşırı yüklemesini çağırmak, bir değerin örtülü olarak bir değere dönüştürülmesini gerçekleştirmeye eşdeğerdir. <xref:System.DateTime>

Bir <xref:System.DateTimeOffset> <xref:System.DateTime> <xref:System.TimeSpan> değerden bir nesne oluşturan ikinci oluşturucunun iki parametresi vardır: dönüştürülecek değer ve Tarih ve saatin UTC 'den sapmasını temsil eden bir değer. <xref:System.DateTime> Bu fark değeri, oluşturucunun ilk parametresinin <xref:System.DateTime.Kind%2A> özelliğine karşılık gelmelidir veya bir <xref:System.ArgumentException> oluşturulur. İlk parametrenin <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> <xref:System.TimeSpan.Zero?displayProperty=nameWithType>özelliği ise ikinci parametrenin değeri olmalıdır. <xref:System.DateTime.Kind%2A> İlk parametrenin <xref:System.DateTimeKind.Local?displayProperty=nameWithType>özelliği ise, ikinci parametrenin değeri yerel sistemin saat diliminin kayması olmalıdır. <xref:System.DateTime.Kind%2A> İlk parametrenin <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>özelliği ise, fark geçerli bir değer olabilir. <xref:System.DateTime.Kind%2A> Aşağıdaki kod, <xref:System.DateTime> <xref:System.DateTimeOffset> değerlere dönüştürmek için bu oluşturucuya yapılan çağrıları gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Örtük tür dönüştürme

Tür bir örtük tür dönüşümünü destekler: bir <xref:System.DateTime> değerden bir <xref:System.DateTimeOffset> değere. <xref:System.DateTimeOffset> (Örtük tür dönüştürme, bir türden diğerine, açık bir dönüştürme (ın C#) veya dönüştürme gerektirmeyen (Visual Basic) ve bilgi içermeyen bir dönüşümtür. Kodu aşağıdakine benzer hale getirir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Elde edilen <xref:System.DateTimeOffset> değerin boşluğu, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerine bağlıdır. Değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, konum değerine <xref:System.TimeSpan.Zero?displayProperty=nameWithType>eşit olarak ayarlanır. Ya da <xref:System.DateTimeKind.Local?displayProperty=nameWithType> değeri veya <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>ise, konum yerel saat dilimine eşit olarak ayarlanır.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Tarih ve saatin dize gösterimini ayrıştırma

Türü bir tarih ve saatin dize gösterimini bir <xref:System.DateTimeOffset> değere dönüştürmenize olanak sağlayan dört yöntemi destekler: <xref:System.DateTimeOffset>

- <xref:System.DateTimeOffset.Parse%2A>, bir tarih ve saatin <xref:System.DateTimeOffset> dize gösterimini değere dönüştürmeyi ve dönüştürme başarısız olursa bir özel durum oluşturur.

- <xref:System.DateTimeOffset.TryParse%2A>, bir tarih ve saatin dize temsilini bir <xref:System.DateTimeOffset> değere dönüştürmeye ve dönüştürme başarısız olursa, döndürmeye `false` çalışır.

- <xref:System.DateTimeOffset.ParseExact%2A>, belirtilen biçimdeki <xref:System.DateTimeOffset> tarih ve saatin dize gösterimini değere dönüştürmeye çalışır. Dönüştürme başarısız olursa Yöntem bir özel durum oluşturur.

- <xref:System.DateTimeOffset.TryParseExact%2A>, belirtilen biçimdeki <xref:System.DateTimeOffset> tarih ve saatin dize gösterimini değere dönüştürmeye çalışır. Dönüştürme başarısız olursa `false` , yöntemi döndürür.

Aşağıdaki örnek, bir <xref:System.DateTimeOffset> değer örneği oluşturmak için bu dört dize dönüştürme yönteminin her birine yapılan çağrıları gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
