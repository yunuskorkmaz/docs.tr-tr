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
ms.openlocfilehash: c290af0c9cef619000a6620ba35209489856c5b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281602"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Bir DateTimeOffset nesnesinin örneğini oluşturma

<xref:System.DateTimeOffset>Yapı yeni değerler oluşturmak için çeşitli yollar sunar <xref:System.DateTimeOffset> . Çoğu, yeni değerleri örneklenme için kullanılabilen yöntemlere karşılık gelir <xref:System.DateTime> ve Tarih ve saat değerinin Eşgüdümlü Evrensel Saat (UTC) ile sapmasını belirtmenize olanak tanır. Özellikle, <xref:System.DateTimeOffset> aşağıdaki yollarla bir değer örneği oluşturabilirsiniz:

- Tarih ve saat değişmez değerini kullanarak.

- Bir oluşturucuyu çağırarak <xref:System.DateTimeOffset> .

- Bir değeri örtük olarak değere dönüştürerek <xref:System.DateTimeOffset> .

- Bir tarih ve saatin dize gösterimini ayrıştırarak.

Bu konu, yeni değerleri örneklemenize yönelik bu yöntemleri gösteren daha ayrıntılı ve kod örnekleri sunar <xref:System.DateTimeOffset> .

## <a name="date-and-time-literals"></a>Tarih ve saat sabit değerleri

Bunu destekleyen diller için, bir değeri örneketmenin en yaygın yöntemlerinden biri, <xref:System.DateTime> tarihi ve saati sabit kodlanmış değişmez değer olarak sağlamaktır. Örneğin, aşağıdaki Visual Basic kodu <xref:System.DateTime> değeri 1 ocak 2008, 10:00 ' de olan bir nesne oluşturur.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>değerler, değişmez değerleri destekleyen diller kullanılırken tarih ve saat değişmez değerleri kullanılarak da başlatılabilir <xref:System.DateTime> . Örneğin, aşağıdaki Visual Basic kodu bir <xref:System.DateTimeOffset> nesnesi oluşturur.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Konsol çıktısı gösterdiği gibi, <xref:System.DateTimeOffset> Bu şekilde oluşturulan değer yerel saat diliminin sapmasını atanır. Yani <xref:System.DateTimeOffset> , bir karakter sabiti kullanılarak atanan bir değer, kod farklı bilgisayarlarda çalıştırıldığında tek bir zaman noktası tanımlamaz.

## <a name="datetimeoffset-constructors"></a>DateTimeOffset oluşturucuları

<xref:System.DateTimeOffset>Tür altı Oluşturucu tanımlar. Bunlardan dördü, doğrudan oluşturuculara karşılık gelir <xref:System.DateTime> <xref:System.TimeSpan> ve Tarih ve saatin UTC 'den sapmasını tanımlayan ek türde bir parametredir. Bunlar, <xref:System.DateTimeOffset> bireysel tarih ve saat bileşenlerinin değerine göre bir değer tanımlamanızı sağlar. Örneğin, aşağıdaki kod, <xref:System.DateTimeOffset> 7/1/2008 12:05 ve 01:00 arasındaki özdeş değerleri içeren nesneleri örneklemek için bu dört Oluşturucu kullanır.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

<xref:System.DateTimeOffset>Bir nesne kullanılarak, <xref:System.Globalization.PersianCalendar> Oluşturucu için bağımsız değişkenlerden biri olarak bir nesnesi kullanılarak örneklenen nesnenin değeri, bu, Farsça takvimi yerine Gregoryen 'da bir tarih olarak ifade edilir. Farsça takvimini kullanarak bir tarih çıktısını almak için konusundaki örneğe bakın <xref:System.Globalization.PersianCalendar> .

Diğer iki Oluşturucu <xref:System.DateTimeOffset> bir değerden bir nesne oluşturur <xref:System.DateTime> . Bunlardan ilki tek bir parametreye, <xref:System.DateTime> bir değere dönüştürülecek değere sahiptir <xref:System.DateTimeOffset> . Elde edilen değerin boşluğu, <xref:System.DateTimeOffset> <xref:System.DateTime.Kind%2A> oluşturucunun tek parametresinin özelliğine bağlıdır. Değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , konum değerine eşit olarak ayarlanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Aksi takdirde, kendi kayması yerel saat dilimine eşit olarak ayarlanır. Aşağıdaki örnek, <xref:System.DateTimeOffset> UTC ve yerel saat dilimini temsil eden nesnelerin örneğini oluşturmak için bu oluşturucunun kullanımını göstermektedir:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Tek bir parametreye sahip olan oluşturucunun aşırı yüklemesini çağırmak, bir <xref:System.DateTimeOffset> <xref:System.DateTime> değerin örtülü olarak bir değere dönüştürülmesini gerçekleştirmeye eşdeğerdir <xref:System.DateTime> <xref:System.DateTimeOffset> .

Bir değerden bir nesne oluşturan ikinci oluşturucunun <xref:System.DateTimeOffset> <xref:System.DateTime> iki parametresi vardır: <xref:System.DateTime> dönüştürülecek değer ve <xref:System.TimeSpan> Tarih ve saatin UTC 'den sapmasını temsil eden bir değer. Bu fark değeri, <xref:System.DateTime.Kind%2A> oluşturucunun ilk parametresinin özelliğine karşılık gelmelidir veya bir oluşturulur <xref:System.ArgumentException> . <xref:System.DateTime.Kind%2A>İlk parametrenin özelliği ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> ikinci parametrenin değeri olmalıdır <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . <xref:System.DateTime.Kind%2A>İlk parametrenin özelliği ise <xref:System.DateTimeKind.Local?displayProperty=nameWithType> , ikinci parametrenin değeri yerel sistemin saat diliminin kayması olmalıdır. <xref:System.DateTime.Kind%2A>İlk parametrenin özelliği ise <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , fark geçerli bir değer olabilir. Aşağıdaki kod, değerlere dönüştürmek için bu oluşturucuya yapılan çağrıları <xref:System.DateTime> gösterir <xref:System.DateTimeOffset> .

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Örtük tür dönüştürme

<xref:System.DateTimeOffset>Tür bir örtük tür dönüşümünü destekler: bir <xref:System.DateTime> değerden bir <xref:System.DateTimeOffset> değere. (Örtük tür dönüştürme, bir türden diğerine (C# ' de) veya dönüştürmeye (Visual Basic) sahip olmayan ve bilgi kaybetmez bir tür dönüştürmedir. Kodu aşağıdakine benzer hale getirir.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Elde edilen değerin boşluğu, <xref:System.DateTimeOffset> <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerine bağlıdır. Değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , konum değerine eşit olarak ayarlanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Ya da değeri veya ise <xref:System.DateTimeKind.Local?displayProperty=nameWithType> <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , konum yerel saat dilimine eşit olarak ayarlanır.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Tarih ve saatin dize gösterimini ayrıştırma

<xref:System.DateTimeOffset>Türü bir tarih ve saatin dize gösterimini bir değere dönüştürmenize olanak sağlayan dört yöntemi destekler <xref:System.DateTimeOffset> :

- <xref:System.DateTimeOffset.Parse%2A>, bir tarih ve saatin dize gösterimini <xref:System.DateTimeOffset> değere dönüştürmeyi ve dönüştürme başarısız olursa bir özel durum oluşturur.

- <xref:System.DateTimeOffset.TryParse%2A>, bir tarih ve saatin dize temsilini bir <xref:System.DateTimeOffset> değere dönüştürmeye ve dönüştürme başarısız olursa, döndürmeye çalışır `false` .

- <xref:System.DateTimeOffset.ParseExact%2A>, belirtilen biçimdeki tarih ve saatin dize gösterimini değere dönüştürmeye çalışır <xref:System.DateTimeOffset> . Dönüştürme başarısız olursa Yöntem bir özel durum oluşturur.

- <xref:System.DateTimeOffset.TryParseExact%2A>, belirtilen biçimdeki tarih ve saatin dize gösterimini değere dönüştürmeye çalışır <xref:System.DateTimeOffset> . `false`Dönüştürme başarısız olursa, yöntemi döndürür.

Aşağıdaki örnek, bir değer örneği oluşturmak için bu dört dize dönüştürme yönteminin her birine yapılan çağrıları gösterir <xref:System.DateTimeOffset> .

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
