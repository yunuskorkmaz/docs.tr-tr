---
title: "Bir DateTimeOffset nesnesinin örneğini oluşturma"
ms.custom: 
ms.date: 04/10/2017
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
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39095d3534de746008fd4710ffdb69db64c8cc86
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="instantiating-a-datetimeoffset-object"></a>Bir DateTimeOffset nesnesinin örneğini oluşturma

<xref:System.DateTimeOffset> Yapısı sunar, çeşitli yollarla yeni <xref:System.DateTimeOffset> değerleri. Bunların çoğu, yeni örnek oluşturma için doğrudan kullanılabilen yöntemler karşılık <xref:System.DateTime> değerlerle yeniliği tarih ve saat değeri Eşgüdümlü Evrensel Saat (UTC) gelen uzaklığı belirtmenizi sağlar. Özellikle, örneği bir <xref:System.DateTimeOffset> aşağıdaki yollarla değeri:

* Bir tarih ve saat değişmez değerine kullanarak.

* Çağırarak bir <xref:System.DateTimeOffset> Oluşturucusu.

* Örtük olarak bir değere dönüştürerek <xref:System.DateTimeOffset> değeri.

* Bir tarih ve saat dize gösterimini ayrıştırarak.

Bu konu, yeni başlatmasını bu yöntemleri gösteren daha ayrıntılı ve kod örnekleri sağlar <xref:System.DateTimeOffset> değerleri.

## <a name="date-and-time-literals"></a>Tarih ve saat değişmez değerleri

Örneği oluşturmak için en yaygın yollarından biri, destek diller için bir <xref:System.DateTime> değerdir tarih ve saati sabit kodlanmış bir dize değeri olarak sağlamak için. Örneğin, aşağıdaki Visual Basic kodu oluşturur bir <xref:System.DateTime> değeri 1 Ocak 2008 10: 00'da nesnesi.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>değerleri de başlatılabilir destek dilleri kullanırken tarih ve saat değişmez değerleri kullanarak <xref:System.DateTime> değişmez değerleri. Örneğin, aşağıdaki Visual Basic kodu oluşturur bir <xref:System.DateTimeOffset> nesnesi.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Konsol çıktısı gösterildiği gibi <xref:System.DateTimeOffset> bu yolla oluşturulan değer yerel saat dilimini uzaklığını atanır. Bunun anlamı bir <xref:System.DateTimeOffset> kodu farklı bilgisayarlarda çalıştırırsanız değişmez değer bir karakteri kullanarak atanmış bir değer tek bir zaman noktası tanımlamıyor.

## <a name="datetimeoffset-constructors"></a>DateTimeOffset oluşturucular

<xref:System.DateTimeOffset> Türü altı oluşturucular tanımlar. Dört tanesi doğrudan karşılık <xref:System.DateTime> ek bir parametre türü ile oluşturucular <xref:System.TimeSpan> tarihini tanımlar ve saati UTC uzaklığı. Bunlar tanımlamanıza izin bir <xref:System.DateTimeOffset> değerine göre her bir tarih ve saat bileşenleri değeri. Örneğin, aşağıdaki kod örneği oluşturmak için bu dört oluşturucular kullanır <xref:System.DateTimeOffset> 1/7/2008'in aynı değerlere sahip nesneleri 00:05:00 +01: 00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Dikkat edin, değeri <xref:System.DateTimeOffset> kullanarak örneği nesnesi bir <xref:System.Globalization.PersianCalendar> nesne kurucusu bağımsız değişkenlerinden biri olarak konsolda görüntülenen, bir tarih Farsça Takvim yerine Gregoryen olarak ifade edilir. Farsça takvimden bir tarih çıktısını almak için örnekte bkz <xref:System.Globalization.PersianCalendar> konu.

Diğer iki Oluşturucu Oluşturma bir <xref:System.DateTimeOffset> nesnesinin bir <xref:System.DateTime> değeri. Bunlardan ilki olan tek bir parametreye sahiptir <xref:System.DateTime> dönüştürmek için değer bir <xref:System.DateTimeOffset> değeri. Elde edilen uzaklık <xref:System.DateTimeOffset> değeri bağımlı <xref:System.DateTime.Kind%2A> Oluşturucusu kişinin tek bir parametre özelliği. Öğenin değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, uzaklık eşit ayarlanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Aksi durumda, kendi uzaklık, yerel saat dilimini eşit olarak ayarlanır. Aşağıdaki örnek örneği oluşturmak için bu oluşturucu kullanımını göstermektedir <xref:System.DateTimeOffset> UTC ve yerel saat dilimini temsil eden nesneler:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Aşırı yüklemesini çağırma <xref:System.DateTimeOffset> tek bir sahip Oluşturucusu <xref:System.DateTime> parametredir örtük bir dönüştürme gerçekleştirmek için eşdeğer bir <xref:System.DateTime> değeri bir <xref:System.DateTimeOffset> değeri.

Oluşturur ikinci oluşturucu bir <xref:System.DateTimeOffset> nesnesinin bir <xref:System.DateTime> değerine sahip iki parametre: <xref:System.DateTime> dönüştürmek için değeri ve <xref:System.TimeSpan> aralık UTC tarihi ve saatini temsil eden değeri. Bu uzaklık değeri karşılık gelmelidir <xref:System.DateTime.Kind%2A> Oluşturucusu 's ilk parametresinin özelliğini ya da bir <xref:System.ArgumentException> oluşturulur. Varsa <xref:System.DateTime.Kind%2A> ilk parametre özelliği <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, ikinci parametresinin değeri olmalıdır <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Varsa <xref:System.DateTime.Kind%2A> ilk parametre özelliği <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, ikinci parametresinin değeri yerel sistem saat dilimi uzaklığını olması gerekir. Varsa <xref:System.DateTime.Kind%2A> ilk parametre özelliği <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, uzaklık herhangi bir geçerli değeri olabilir. Aşağıdaki kod dönüştürmek için bu oluşturucu çağrıları gösterir <xref:System.DateTime> için <xref:System.DateTimeOffset> değerleri.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Örtük tür dönüştürmeleri

<xref:System.DateTimeOffset> Türü bir örtük tür dönüştürmesi destekler: gelen bir <xref:System.DateTime> değeri bir <xref:System.DateTimeOffset> değeri. (Bir örtük tür dönüştürme, bir açık atama (C# ' ta) veya (Visual Basic'te) dönüştürme gerektirmez ve bilgi kaybetmek olmayan bir bir türden diğerine dönüştürme diğerine olur. Kod gibi aşağıdaki mümkün kılar.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Elde edilen uzaklık <xref:System.DateTimeOffset> değeri bağımlı <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değeri. Öğenin değeri ise <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, uzaklık eşit ayarlanır <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Öğenin değeri ya da ise <xref:System.DateTimeKind.Local?displayProperty=nameWithType> veya <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, uzaklık, yerel saat dilimini eşit olarak ayarlanır.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Bir tarih ve saat dize gösterimini ayrıştırma

<xref:System.DateTimeOffset> Türünü destekleyen bir tarih dize gösterimini dönüştürmek ve içine zaman olanak tanıyan dört yöntem bir <xref:System.DateTimeOffset> değeri:

* <xref:System.DateTimeOffset.Parse%2A>, bir tarih dize gösterimini dönüştürmek ve süresi çalıştığı bir <xref:System.DateTimeOffset> değeri ve dönüştürme başarısız olursa bir özel durum oluşturur.

* <xref:System.DateTimeOffset.TryParse%2A>, bir tarih dize gösterimini dönüştürmek ve süresi çalıştığı bir <xref:System.DateTimeOffset> değeri ve döndürür `false` dönüştürme başarısız olursa.

* <xref:System.DateTimeOffset.ParseExact%2A>, çalıştığı bir tarih ve saat için belirtilen biçimde dize gösterimini dönüştürmek bir <xref:System.DateTimeOffset> değeri. Dönüştürme başarısız olursa yöntemi bir özel durum atar.

* <xref:System.DateTimeOffset.TryParseExact%2A>, çalıştığı bir tarih ve saat için belirtilen biçimde dize gösterimini dönüştürmek bir <xref:System.DateTimeOffset> değeri. Yöntem `false` dönüştürme başarısız olursa.

Aşağıdaki örnek, bu dört dize dönüştürme yöntemlerin her biri için çağrı örneğini gösterir. bir <xref:System.DateTimeOffset> değeri.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

[Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
