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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ff38325e26dd1bc946f6f12c365b6dea3e228
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669179"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma

Örneği oluşturmak için en yaygın yolu bir <xref:System.TimeZoneInfo> nesnedir ilgili bilgileri kayıt defterinden alınamıyor. Bu konuda örneklemek anlatılmaktadır bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesne.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Bir Timezoneınfo nesnesinin örneğini oluşturmak için

1. Bildirme bir <xref:System.TimeZoneInfo> nesne.

2. Çağrı `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> yöntemi.

3. Yöntemi tarafından oluşturulan özel durumları işlemek özellikle <xref:System.TimeZoneNotFoundException> saat dilimini kayıt defterinde tanımlı değilse, oluşturulur.

## <a name="example"></a>Örnek

Aşağıdaki kod alır bir <xref:System.TimeZoneInfo> Doğu Standart saat dilimini temsil eder ve karşılık gelen Doğu Standart Saati yerel saate görüntüleyen bir nesne.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Yöntemin tek parametresi, saat, almak istediğiniz nesnenin karşılık gelen dilimi tanımlayıcısıdır <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> özelliği. Saat dilimi benzersiz olarak tanımlayan bir anahtar alan saat dilimi tanımlayıcısıdır. Saat dilimi tanımlayıcı çoğu anahtarları görece kısa olsa da, daha uzun. Çoğu durumda, karşılık gelen değeri <xref:System.TimeZoneInfo.StandardName%2A> özelliği bir <xref:System.TimeZoneInfo> saat diliminin standart saat adını sağlamak için kullanılan nesne. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı sağlamanız emin olmak için en iyi yolu, sisteminizde mevcut saat dilimlerini numaralandırma ve bunlar üzerinde mevcut saat dilimlerini tanımlayıcıların Not sağlamaktır. Çizim için bkz: [nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md). [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) konu ayrıca seçili saat dilimi tanımlayıcıları listesini içerir.

Saat dilimi bulunursa yöntem döndürür, <xref:System.TimeZoneInfo> nesne. Saat dilimi bulunamazsa çağırılıyorsa yöntem bir <xref:System.TimeZoneNotFoundException>. Saat dilimi bulundu, ancak verileri bozuk veya eksik çağırılıyorsa yöntem bir <xref:System.InvalidTimeZoneException>.

İlk uygulamanızı bulunması gereken bir saat dilimi üzerinde dayanıyorsa çağırmalısınız <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> yöntemi saat dilimi bilgileri kayıt defterinden alınamıyor. Yöntem çağrısı başarısız olursa, özel durum işleyicisi ardından saat dilimini yeni bir örneğini oluşturabilir veya seri hale getirilmiş bir seri durumdan çıkarılırken tarafından yeniden oluşturabilirsiniz <xref:System.TimeZoneInfo> nesne. Bkz: [nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) örneği.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md)
