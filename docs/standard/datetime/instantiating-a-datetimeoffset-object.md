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
ms.openlocfilehash: 6d8f4254da256bf2814f66aa62d43204fb302701
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584168"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Bir DateTimeOffset nesnesinin örneğini oluşturma

<xref:System.DateTimeOffset> Yapısı çeşitli yeni yollar sunar <xref:System.DateTimeOffset> değerleri. Bunların çoğu, yeni örnekleme için doğrudan yöntemleri karşılık <xref:System.DateTime> değerlerle tarih ve saat değerinin, Eşgüdümlü Evrensel Saat (UTC) uzaklığını belirtmenize olanak tanıyan geliştirmeler. Özellikle, örneği bir <xref:System.DateTimeOffset> aşağıdaki yollarla değeri:

* Bir tarih ve saat değişmez değeri kullanarak.

* Çağırarak bir <xref:System.DateTimeOffset> Oluşturucusu.

* Örtük olarak bir değere dönüştürerek <xref:System.DateTimeOffset> değeri.

* Bir tarih ve saat dize gösterimini ayrıştırarak.

Bu konu, yeni örnekleme bu yöntemleri gösterilmektedir. daha fazla ayrıntı ve kod örnekleri sağlar <xref:System.DateTimeOffset> değerleri.

## <a name="date-and-time-literals"></a>Tarih ve saat değişmez değerleri

Örneği oluşturmak için en yaygın yollarından biri destekleyen diller için bir <xref:System.DateTime> değerdir tarih ve saat sabit kodlanmış bir değişmez değer olarak sağlamak için. Örneğin, aşağıdaki Visual Basic kod oluşturur bir <xref:System.DateTime> değeri, 2008 1 Ocak, 10: 00'da olan nesne.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> değerleri de başlatılabilir destekleyen dillerin kullanıldığı durumlar tarih ve saat değişmez değerleri kullanarak <xref:System.DateTime> değişmez. Örneğin, aşağıdaki Visual Basic kod oluşturur bir <xref:System.DateTimeOffset> nesne.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Konsol çıkışını gösterildiği gibi <xref:System.DateTimeOffset> bu şekilde oluşturulan değer yerel saat diliminin uzaklığı atanır. Diğer bir deyişle bir <xref:System.DateTimeOffset> kullanılarak bir karakter sabiti değeri değil tanımlamak tek bir zaman noktası kodu farklı bilgisayarlarda çalıştırırsanız.

## <a name="datetimeoffset-constructors"></a>DateTimeOffset oluşturucular

<xref:System.DateTimeOffset> Altı oluşturucular türü tanımlar. Dört tanesi doğrudan karşılık gelen <xref:System.DateTime> oluşturucularla ek bir parametre türü <xref:System.TimeSpan> tanımlayan tarihi ve zamanı, UTC ile olan uzaklığını. Bunlar tanımlamanıza izin bir <xref:System.DateTimeOffset> değerine göre her bir tarih ve saati bileşenlerini değeri. Örneğin, aşağıdaki kod örneği oluşturmak için bu dört oluşturucular kullanır <xref:System.DateTimeOffset> 1/7/2008 aynı değerlere sahip nesneleri 00:05:00 +01: 00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Unutmayın, değerini <xref:System.DateTimeOffset> nesne örneği kullanarak bir <xref:System.Globalization.PersianCalendar> nesnesi oluşturucusuna bağımsız değişkenlerden biri olarak konsolda görüntülenen, bir tarihi Fars takvimiyle yerine Gregoryen olarak ifade edilir. Bir tarihi Fars takvimi kullanılarak çıktısını almak için örneğe bakın <xref:System.Globalization.PersianCalendar> konu.

Diğer iki Oluşturucu Oluşturma bir <xref:System.DateTimeOffset> nesnesinden bir <xref:System.DateTime> değeri. Bunlardan ilki tek bir parametreye sahip <xref:System.DateTime> dönüştürmek için değer bir <xref:System.DateTimeOffset> değeri. Uzaklık ortaya çıkan <xref:System.DateTimeOffset> değeri bağlıdır <xref:System.DateTime.Kind%2A> oluşturucunun tek bir parametre özelliği. Öğenin değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, uzaklığı için eşit olarak ayarlanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Aksi takdirde, uzaklığı, yerel saat dilimi eşit olarak ayarlanır. Aşağıdaki örnek oluşturmak için bu oluşturucu kullanışını <xref:System.DateTimeOffset> UTC ve yerel saat dilimini temsil eden nesneler:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Aşırı yüklemesini çağırmak <xref:System.DateTimeOffset> sahip tek bir oluşturucu <xref:System.DateTime> parametresi, örtük bir dönüştürme gerçekleştirmek için eşdeğer bir <xref:System.DateTime> değerini bir <xref:System.DateTimeOffset> değeri.

Oluşturan ikinci oluşturucu bir <xref:System.DateTimeOffset> nesnesinden bir <xref:System.DateTime> değer iki parametreye sahiptir: <xref:System.DateTime> dönüştürmek için değer ve bir <xref:System.TimeSpan> tarihi ve saati temsil eden değerinin UTC ile olan uzaklığını. Bu uzaklık değeri karşılık gelmelidir <xref:System.DateTime.Kind%2A> özelliği oluşturucunun ilk parametrenin veya <xref:System.ArgumentException> oluşturulur. Varsa <xref:System.DateTime.Kind%2A> ilk parametre özelliği <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, ikinci parametresinin değeri olmalıdır <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Varsa <xref:System.DateTime.Kind%2A> ilk parametre özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, ikinci parametresinin değerini, yerel sistem saat dilimi uzaklığı olmalıdır. Varsa <xref:System.DateTime.Kind%2A> ilk parametre özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, uzaklık geçerli bir değer olabilir. Aşağıdaki kod bu oluşturucu dönüştürmek için çağrıları gösterir <xref:System.DateTime> için <xref:System.DateTimeOffset> değerleri.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Örtük tür dönüştürme

<xref:System.DateTimeOffset> Türünü destekleyen bir örtük tür dönüştürme: gelen bir <xref:System.DateTime> değerini bir <xref:System.DateTimeOffset> değeri. (Bir örtük tür dönüştürme, bir açık tür dönüştürme (C# ' de) veya (Visual Basic'te) dönüştürme gerektirmez ve bilgileri kaybetmez bir türden diğerine dönüştürmedir. Kod aşağıdaki olası gibi kolaylaştırır.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Uzaklık ortaya çıkan <xref:System.DateTimeOffset> değeri bağlıdır <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değeri. Öğenin değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, uzaklığı için eşit olarak ayarlanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Öğenin değeri ya da ise <xref:System.DateTimeKind.Local?displayProperty=nameWithType> veya <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, uzaklığı, yerel saat dilimi eşit olarak ayarlanır.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Bir tarih ve saat dize gösterimini ayrıştırma

<xref:System.DateTimeOffset> Türünü destekleyen bir tarihin dize gösterimine dönüştürmek ve içine zaman olanak tanıyan dört yöntemi bir <xref:System.DateTimeOffset> değeri:

* <xref:System.DateTimeOffset.Parse%2A>, bir tarihin dize gösterimine dönüştürmek ve süresi çalıştığı bir <xref:System.DateTimeOffset> değer ve dönüştürme başarısız olursa bir özel durum oluşturur.

* <xref:System.DateTimeOffset.TryParse%2A>, bir tarihin dize gösterimine dönüştürmek ve süresi çalıştığı bir <xref:System.DateTimeOffset> döndürür ve değeri `false` dönüştürme başarısız olursa.

* <xref:System.DateTimeOffset.ParseExact%2A>, bir tarih ve saat için belirtilen biçimde dize gösterimini dönüştürmeye çalıştığı bir <xref:System.DateTimeOffset> değeri. Dönüştürme başarısız olursa yöntem bir özel durum oluşturur.

* <xref:System.DateTimeOffset.TryParseExact%2A>, bir tarih ve saat için belirtilen biçimde dize gösterimini dönüştürmeye çalıştığı bir <xref:System.DateTimeOffset> değeri. Yöntem döndürür `false` dönüştürme başarısız olursa.

Bu dört dize dönüştürme yöntemlerin her biri için çağrı örneğini aşağıdaki örnekte bir <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
