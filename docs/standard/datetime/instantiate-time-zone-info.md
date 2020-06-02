---
title: 'Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: e8d50419dc21a1748a88c96c200806d0558f0e5a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276888"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma

Bir nesneyi başlatmak için en yaygın yol, <xref:System.TimeZoneInfo> kayıt defterinden ilgili bilgileri almak için kullanılır. Bu konuda <xref:System.TimeZoneInfo> , yerel sistem kayıt defterinden bir nesnenin örneğini oluşturma konusu ele alınmaktadır.

### <a name="to-instantiate-a-timezoneinfo-object"></a>TimeZoneInfo nesnesinin örneğini oluşturmak için

1. Bir <xref:System.TimeZoneInfo> nesne bildirin.

2. `static`( `Shared` Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metodunu çağırın.

3. Yöntemi tarafından oluşturulan özel durumları işleyin, özellikle, <xref:System.TimeZoneNotFoundException> saat dilimi kayıt defterinde tanımlanmamışsa oluşturulur.

## <a name="example"></a>Örnek

Aşağıdaki kod <xref:System.TimeZoneInfo> Doğu Standart saat dilimini temsil eden bir nesnesi alır ve yerel saate karşılık gelen Doğu Standart saatini görüntüler.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType>Yöntemin tek parametresi, almak istediğiniz zaman diliminin tanımlayıcısıdır, bu da nesnenin özelliğine karşılık gelir <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> . Saat dilimi tanımlayıcısı, saat dilimini benzersiz bir şekilde tanımlayan bir anahtar alanıdır. Çoğu anahtar görece kısaysa, saat dilimi tanımlayıcısı oldukça uzun olur. Çoğu durumda, değeri, <xref:System.TimeZoneInfo.StandardName%2A> <xref:System.TimeZoneInfo> saat diliminin standart zamanının adını sağlamak için kullanılan bir nesnenin özelliğine karşılık gelir. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı belirttiğinizden emin olmanın en iyi yolu, sisteminizde kullanılabilir olan saat dilimlerini listelemek ve bunlar üzerinde mevcut olan saat dilimlerinin tanımlayıcılarını aklınızda hale getirmek. Bir çizim için bkz. [nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](enumerate-time-zones.md). [Bir yerel sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md) konusu, seçilen saat dilimi tanımlayıcılarının listesini de içerir.

Saat dilimi bulunursa, yöntemi <xref:System.TimeZoneInfo> nesnesini döndürür. Saat dilimi bulunamazsa yöntem bir oluşturur <xref:System.TimeZoneNotFoundException> . Saat dilimi bulunursa ancak verileri bozuksa veya tamamlanmamışsa, yöntem bir oluşturur <xref:System.InvalidTimeZoneException> .

Uygulamanız bulunması gereken bir saat dilimini kullanıyorsa, önce <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> kayıt defterinden saat dilimi bilgilerini almak için yöntemini çağırmanız gerekir. Yöntem çağrısı başarısız olursa, özel durum işleyiciniz daha sonra zaman diliminin yeni bir örneğini oluşturmalı veya seri hale getirilmiş bir nesneyi seri durumdan çıkarmak için yeniden oluşturmanız gerekir <xref:System.TimeZoneInfo> . Bir örnek için bkz. [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](access-utc-and-local.md)
