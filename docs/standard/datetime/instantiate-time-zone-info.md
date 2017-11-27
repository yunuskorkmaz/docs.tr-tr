---
title: "Nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma"
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
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: defc8c9981b8476660c9c99d20bc50142ee9dfad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma

Örneği oluşturmak için en yaygın yolu bir <xref:System.TimeZoneInfo> nesnesidir ilgili bilgileri kayıt defterinden alınamadı. Bu konuda ele alınmıştır örneği oluşturmak nasıl bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesnesi.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Timezoneınfo nesnesinin örneğini oluşturmak için

1. Bildirme bir <xref:System.TimeZoneInfo> nesnesi.

2. Çağrı `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> yöntemi.

3. Yöntemi tarafından oluşturulan tüm özel durumları işleme özellikle <xref:System.TimeZoneNotFoundException> saat dilimi kayıt defterinde tanımlanmazsa oluşur.

## <a name="example"></a>Örnek

Aşağıdaki kod alır bir <xref:System.TimeZoneInfo> Doğu Standart saat dilimi temsil eder ve karşılık gelen Doğu Standart Saati yerel saate görüntüleyen nesnesi.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Yöntemin tek bir parametre, saat almak istediğiniz nesnenin karşılık gelen dilimi tanımlayıcısıdır <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> özelliği. Saat dilimi benzersiz olarak tanımlayan bir anahtar alanı saat dilimi tanımlayıcısıdır. Çoğu anahtarları görece kısa olsa da, saat dilimi tanımlayıcı daha uzun. Çoğu durumda, karşılık gelen değeri <xref:System.TimeZoneInfo.StandardName%2A> özelliği bir <xref:System.TimeZoneInfo> saat diliminin standart saat adını sağlamak için kullanılan nesne. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı sağladığınız emin olmak için en iyi sisteminizdeki kullanılabilir saat dilimlerini numaralandırma ve bunlar üzerinde mevcut saat dilimlerini tanımlayıcıların not edin yoludur. Çizim için bkz: [nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md). [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) konu, seçili saat dilimi tanımlayıcıları listesini de içerir.

Saat dilimi bulunursa, yöntem, <xref:System.TimeZoneInfo> nesnesi. Saat dilimi bulunamazsa, yöntem oluşturulur bir <xref:System.TimeZoneNotFoundException>. Saat dilimi bulundu, ancak verileri bozuk veya eksik yöntemi atar bir <xref:System.InvalidTimeZoneException>.

Uygulamanızı mevcut bir saat dilimini temel dayalıysa, ilk çağırmalısınız <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> kayıt defterinden saat dilimi bilgilerini alma yöntemi. Yöntem çağrısının başarısız olursa, özel durum işleyici sonra saat dilimi yeni bir örneğini oluşturmak veya seri hale getirilmiş bir seri durumdan tarafından yeniden oluşturun <xref:System.TimeZoneInfo> nesnesi. Bkz: [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) bir örnek.

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md)
