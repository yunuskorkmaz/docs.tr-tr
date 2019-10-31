---
title: 'Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: 5975270dd6a166bb625278a97f4c60851cbe7942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122293"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma

<xref:System.TimeZoneInfo> nesnesini örneketmenin en yaygın yolu, kayıt defterinden onunla ilgili bilgi almak için kullanılır. Bu konu, yerel sistem kayıt defterinden bir <xref:System.TimeZoneInfo> nesnesinin örneğini oluşturmayı açıklamaktadır.

### <a name="to-instantiate-a-timezoneinfo-object"></a>TimeZoneInfo nesnesinin örneğini oluşturmak için

1. <xref:System.TimeZoneInfo> nesnesi bildirin.

2. `static` (`Shared` Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> yöntemini çağırın.

3. Yöntemi tarafından oluşturulan özel durumları, özellikle de saat dilimi kayıt defterinde tanımlanmamışsa oluşturulan <xref:System.TimeZoneNotFoundException> işleyin.

## <a name="example"></a>Örnek

Aşağıdaki kod Doğu Standart saat dilimini temsil eden bir <xref:System.TimeZoneInfo> nesnesi alır ve yerel saate karşılık gelen Doğu Standart saatini görüntüler.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> yönteminin tek parametresi, almak istediğiniz zaman diliminin tanımlayıcısıdır, bu da nesnenin <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> özelliğine karşılık gelir. Saat dilimi tanımlayıcısı, saat dilimini benzersiz bir şekilde tanımlayan bir anahtar alanıdır. Çoğu anahtar görece kısaysa, saat dilimi tanımlayıcısı oldukça uzun olur. Çoğu durumda, değeri bir <xref:System.TimeZoneInfo> nesnesinin, saat diliminin standart zamanının adını sağlamak için kullanılan <xref:System.TimeZoneInfo.StandardName%2A> özelliğine karşılık gelir. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı belirttiğinizden emin olmanın en iyi yolu, sisteminizde kullanılabilir olan saat dilimlerini listelemek ve bunlar üzerinde mevcut olan saat dilimlerinin tanımlayıcılarını aklınızda hale getirmek. Bir çizim için bkz. [nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md). [Bir yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) konusu, seçilen saat dilimi tanımlayıcılarının listesini de içerir.

Saat dilimi bulunursa, yöntemi <xref:System.TimeZoneInfo> nesnesini döndürür. Saat dilimi bulunamazsa yöntem bir <xref:System.TimeZoneNotFoundException>oluşturur. Saat dilimi bulunursa ancak verileri bozuksa veya tamamlanmamışsa, yöntem bir <xref:System.InvalidTimeZoneException>oluşturur.

Uygulamanız olması gereken bir saat dilimini kullanıyorsa, önce kayıt defterinden saat dilimi bilgilerini almak için <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemini çağırmanız gerekir. Yöntem çağrısı başarısız olursa, özel durum işleyiciniz daha sonra zaman diliminin yeni bir örneğini oluşturmalı veya seri hale getirilmiş bir <xref:System.TimeZoneInfo> nesnesinin serisini kaldırarak yeniden oluşturmalısınız. Bir örnek için bkz. [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md)
