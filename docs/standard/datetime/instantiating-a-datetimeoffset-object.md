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
ms.openlocfilehash: 1b1178623258393eab28a7087eb04c47b55a9176
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122320"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Bir DateTimeOffset nesnesinin örneğini oluşturma

<xref:System.DateTimeOffset> yapısı, yeni <xref:System.DateTimeOffset> değerler oluşturmak için çeşitli yollar sunar. Bunların birçoğu, yeni <xref:System.DateTime> değerleri örneği oluşturma için kullanılabilen yöntemlere karşılık gelir ve Tarih ve saat değerinin Eşgüdümlü Evrensel Saat (UTC) ile sapmasını belirtmenize olanak tanır. Özellikle, aşağıdaki yollarla bir <xref:System.DateTimeOffset> değeri örneği oluşturabilirsiniz:

- Tarih ve saat değişmez değerini kullanarak.

- <xref:System.DateTimeOffset> Oluşturucu çağırarak.

- Bir değeri örtük olarak <xref:System.DateTimeOffset> değere dönüştürerek.

- Bir tarih ve saatin dize gösterimini ayrıştırarak.

Bu konu, yeni <xref:System.DateTimeOffset> değerleri örneklemenize yönelik bu yöntemleri gösteren daha ayrıntılı ve kod örnekleri sunar.

## <a name="date-and-time-literals"></a>Tarih ve saat sabit değerleri

Bunu destekleyen diller için, <xref:System.DateTime> bir değeri örneketmenin en yaygın yöntemlerinden biri, tarihi ve saati sabit kodlanmış değişmez değer olarak sağlamaktır. Örneğin, aşağıdaki Visual Basic kodu değeri 1 Ocak 2008, 10:00 ' de olan bir <xref:System.DateTime> nesnesi oluşturur.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> değerler, <xref:System.DateTime> değişmez değerleri destekleyen diller kullanılırken tarih ve saat değerleri kullanılarak da başlatılabilir. Örneğin, aşağıdaki Visual Basic kodu bir <xref:System.DateTimeOffset> nesnesi oluşturur.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Konsol çıkışında gösterildiği gibi, bu şekilde oluşturulan <xref:System.DateTimeOffset> değeri yerel saat diliminin sapmasını atanır. Bu, bir karakter sabiti kullanılarak atanan bir <xref:System.DateTimeOffset> değerinin, kod farklı bilgisayarlarda çalıştırıldığında tek bir zaman noktasını tanımlayamayacağı anlamına gelir.

## <a name="datetimeoffset-constructors"></a>DateTimeOffset oluşturucuları

<xref:System.DateTimeOffset> türü altı Oluşturucu tanımlar. Bunlardan dördü, tarih ve saatin UTC 'den sapmasını tanımlayan <xref:System.TimeSpan> türünde ek bir parametre ile doğrudan <xref:System.DateTime> oluşturuculara karşılık gelir. Bunlar, bireysel tarih ve saat bileşenlerinin değerine göre <xref:System.DateTimeOffset> bir değer tanımlamanızı sağlar. Örneğin, aşağıdaki kod, 7/1/2008 12:05 ve 01:00 arasındaki özdeş değerlerle <xref:System.DateTimeOffset> nesneleri örneklemek için bu dört Oluşturucu kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Bir <xref:System.Globalization.PersianCalendar> nesnesi kullanılarak örneği oluşturulan <xref:System.DateTimeOffset> nesnenin değeri konsola görüntülendiğinde, bu, Farsça takviminde değil, Gregoryen 'da bir tarih olarak ifade edilir. Farsça takvimini kullanarak bir tarih çıktısını almak için <xref:System.Globalization.PersianCalendar> konusunun örneğine bakın.

Diğer iki Oluşturucu bir <xref:System.DateTime> değerinden <xref:System.DateTimeOffset> nesnesi oluşturur. Bunlardan ilki tek bir parametreye sahiptir, <xref:System.DateTime> değeri <xref:System.DateTimeOffset> değerine dönüştürülür. Elde edilen <xref:System.DateTimeOffset> değerinin boşluğu, oluşturucunun tek parametresinin <xref:System.DateTime.Kind%2A> özelliğine bağlıdır. Değeri <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>ise, konum <xref:System.TimeSpan.Zero?displayProperty=nameWithType>eşit olarak ayarlanır. Aksi takdirde, kendi kayması yerel saat dilimine eşit olarak ayarlanır. Aşağıdaki örnekte, bu oluşturucunun UTC ve yerel saat dilimini temsil eden <xref:System.DateTimeOffset> nesneleri örneğini oluşturmak için kullanımı gösterilmektedir:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Tek bir <xref:System.DateTime> parametresine sahip <xref:System.DateTimeOffset> oluşturucusunun aşırı yüklemesini çağırmak, bir <xref:System.DateTime> değerinin örtük bir şekilde bir <xref:System.DateTimeOffset> değere dönüştürülmesini gerçekleştirmeye eşdeğerdir.

Bir <xref:System.DateTime> değerinden <xref:System.DateTimeOffset> nesnesi oluşturan ikinci oluşturucunun iki parametresi vardır: dönüştürülecek <xref:System.DateTime> değeri ve Tarih ve saatin UTC 'den sapmasını temsil eden bir <xref:System.TimeSpan> değeri. Bu fark değeri, oluşturucunun ilk parametresinin <xref:System.DateTime.Kind%2A> özelliğine karşılık gelmelidir veya bir <xref:System.ArgumentException> oluşturulur. İlk parametrenin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, ikinci parametrenin değeri <xref:System.TimeSpan.Zero?displayProperty=nameWithType>olmalıdır. İlk parametrenin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, ikinci parametrenin değeri yerel sistemin saat diliminin kayması olmalıdır. İlk parametrenin <xref:System.DateTime.Kind%2A> özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, fark geçerli bir değer olabilir. Aşağıdaki kod, <xref:System.DateTime> <xref:System.DateTimeOffset> değerlere dönüştürmek için bu oluşturucuya yapılan çağrıları gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Örtük tür dönüştürme

<xref:System.DateTimeOffset> türü bir örtük tür dönüştürmeyi destekler: bir <xref:System.DateTime> değerinden <xref:System.DateTimeOffset> değerine. (Örtük tür dönüştürme, bir türden diğerine, açık bir dönüştürme (ın C#) veya dönüştürme gerektirmeyen (Visual Basic) ve bilgi içermeyen bir dönüşümtür. Kodu aşağıdakine benzer hale getirir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Elde edilen <xref:System.DateTimeOffset> değerinin boşluğu <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerine bağlıdır. Değeri <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>ise, konum <xref:System.TimeSpan.Zero?displayProperty=nameWithType>eşit olarak ayarlanır. Değeri <xref:System.DateTimeKind.Local?displayProperty=nameWithType> veya <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>ise, konum yerel saat dilimine eşit olarak ayarlanır.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Tarih ve saatin dize gösterimini ayrıştırma

<xref:System.DateTimeOffset> türü, bir tarih ve saatin dize gösterimini <xref:System.DateTimeOffset> bir değere dönüştürmenize olanak sağlayan dört yöntemi destekler:

- <xref:System.DateTimeOffset.Parse%2A>, bir tarih ve saatin dize gösterimini <xref:System.DateTimeOffset> değerine dönüştürmeye çalışır ve dönüştürme başarısız olursa bir özel durum oluşturur.

- <xref:System.DateTimeOffset.TryParse%2A>, bir tarih ve saatin dize gösterimini <xref:System.DateTimeOffset> değerine dönüştürmeye ve dönüştürme başarısız olursa `false` döndürmeye çalışır.

- <xref:System.DateTimeOffset.ParseExact%2A>, belirtilen biçimdeki bir tarih ve saatin dize gösterimini <xref:System.DateTimeOffset> bir değere dönüştürmeye çalışır. Dönüştürme başarısız olursa Yöntem bir özel durum oluşturur.

- <xref:System.DateTimeOffset.TryParseExact%2A>, belirtilen biçimdeki bir tarih ve saatin dize gösterimini <xref:System.DateTimeOffset> bir değere dönüştürmeye çalışır. Dönüştürme başarısız olursa Yöntem `false` döndürür.

Aşağıdaki örnek, <xref:System.DateTimeOffset> bir değer örneği oluşturmak için bu dört dize dönüştürme yöntemlerinden her birine yapılan çağrıları gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
