---
title: 'Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278044"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma

Bir uygulama için gerekli kesin saat dilimi bilgileri, bazı nedenlerle belirli bir sistemde mevcut olmayabilir:

- Saat dilimi, yerel sistemin kayıt defterinde hiç tanımlanmadı.

- Saat dilimi hakkındaki veriler, kayıt defterinden değiştirilmiş veya kaldırılmış.

- Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi ayarlamaları hakkında doğru bilgilere sahip değildir.

Bu durumlarda, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanız için gereken saat dilimini tanımlamak için yöntemini çağırabilirsiniz. Bu yöntemin aşırı yüklerini, ayarlama kuralları olan veya olmayan bir saat dilimi oluşturmak için kullanabilirsiniz. Saat dilimi yaz saati kaydetme süresini destekliyorsa, düzeltilen veya kayan ayarlama kuralları ile ayarlamalar tanımlayabilirsiniz. (Bu terimlerin tanımları için, [saat dilimine genel bakış](time-zone-overview.md)konusundaki "saat dilimi terminolojisi" bölümüne bakın.)

> [!IMPORTANT]
> Yöntemi çağırarak oluşturulan özel saat dilimleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterine eklenmez. Bunun yerine, yalnızca Yöntem çağrısı tarafından döndürülen nesne başvurusu aracılığıyla erişilebilir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> .

Bu konuda, ayarlama kuralları olmayan bir saat dilimini nasıl oluşturacağınız gösterilmektedir. Gün ışığından yararlanma zaman ayarlama kurallarını destekleyen bir saat dilimi oluşturmak için bkz. [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Ayarlama kuralları olmadan bir saat dilimi oluşturmak için

1. Saat diliminin görünen adını tanımlayın.

   Görünen ad, saat diliminin Eşgüdümlü Evrensel Saat (UTC) arasındaki kaydırın parantez içine alındığı ve ardından saat dilimini tanımlayan bir dize, saat diliminizdeki bir veya daha fazla şehir ya da saat dilimindeki ülkelerin veya bölgelerin bir ya da daha fazlasını tanımlayan oldukça standart bir biçim izler.

2. Saat diliminin standart zamanının adını tanımlayın. Genellikle, bu dize saat diliminin tanımlayıcısı olarak da kullanılır.

3. Saat diliminin standart adından farklı bir tanımlayıcı kullanmak istiyorsanız, saat dilimi tanımlayıcısını tanımlayın.

4. <xref:System.TimeSpan>Saat DILIMININ UTC 'den sapmasını tanımlayan bir nesne oluşturun. UTC 'den sonraki saatlere sahip saat dilimleri pozitif bir uzaklığa sahiptir. UTC 'den önceki zamanlarla saat dilimlerinin negatif bir boşluğu vardır.

5. <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>Yeni saat dilimini oluşturmak için yöntemini çağırın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hiçbir ayarlama kuralı olmayan Mawson, Antarktika için özel bir saat dilimini tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Özelliğe atanan dize, <xref:System.TimeZoneInfo.DisplayName%2A> saat DILIMININ UTC 'ye ait sapmasını ve ardından saat diliminin kolay bir açıklamasını izleyen standart bir biçim izler.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Saat dilimine genel bakış](time-zone-overview.md)
- [Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md)
