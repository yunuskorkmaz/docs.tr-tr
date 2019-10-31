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
ms.openlocfilehash: 344d8307318d5a2e50eddb39ef488cd8c5f2fdac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129098"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma

Bir uygulama için gerekli kesin saat dilimi bilgileri, bazı nedenlerle belirli bir sistemde mevcut olmayabilir:

- Saat dilimi, yerel sistemin kayıt defterinde hiç tanımlanmadı.

- Saat dilimi hakkındaki veriler, kayıt defterinden değiştirilmiş veya kaldırılmış.

- Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi ayarlamaları hakkında doğru bilgilere sahip değildir.

Bu durumlarda, uygulamanız için gereken saat dilimini tanımlamak üzere <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemini çağırabilirsiniz. Bu yöntemin aşırı yüklerini, ayarlama kuralları olan veya olmayan bir saat dilimi oluşturmak için kullanabilirsiniz. Saat dilimi yaz saati kaydetme süresini destekliyorsa, düzeltilen veya kayan ayarlama kuralları ile ayarlamalar tanımlayabilirsiniz. (Bu terimlerin tanımları için, [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)konusundaki "saat dilimi terminolojisi" bölümüne bakın.)

> [!IMPORTANT]
> <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi çağırarak oluşturulan özel saat dilimleri kayıt defterine eklenmez. Bunun yerine, yalnızca <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi çağrısının döndürdüğü nesne başvurusu aracılığıyla erişilebilir.

Bu konuda, ayarlama kuralları olmayan bir saat dilimini nasıl oluşturacağınız gösterilmektedir. Gün ışığından yararlanma zaman ayarlama kurallarını destekleyen bir saat dilimi oluşturmak için bkz. [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Ayarlama kuralları olmadan bir saat dilimi oluşturmak için

1. Saat diliminin görünen adını tanımlayın.

   Görünen ad, saat diliminin Eşgüdümlü Evrensel Saat (UTC) arasındaki kaydırın parantez içine alındığı ve ardından saat dilimini, saat diliminizdeki bir veya daha fazla şehirden veya bir ya da daha fazlasını tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler saat dilimindeki ndenemeler veya bölgeler.

2. Saat diliminin standart zamanının adını tanımlayın. Genellikle, bu dize saat diliminin tanımlayıcısı olarak da kullanılır.

3. Saat diliminin standart adından farklı bir tanımlayıcı kullanmak istiyorsanız, saat dilimi tanımlayıcısını tanımlayın.

4. Saat diliminin UTC 'den sapmasını tanımlayan bir <xref:System.TimeSpan> nesnesi örneği oluşturun. UTC 'den sonraki saatlere sahip saat dilimleri pozitif bir uzaklığa sahiptir. UTC 'den önceki zamanlarla saat dilimlerinin negatif bir boşluğu vardır.

5. Yeni saat dilimini başlatmak için <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> yöntemini çağırın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hiçbir ayarlama kuralı olmayan Mawson, Antarktika için özel bir saat dilimini tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<xref:System.TimeZoneInfo.DisplayName%2A> özelliğine atanan dize, saat diliminin UTC 'ye ait sapmasını ve ardından saat diliminin kolay bir açıklamasını izleyen standart bir biçim izler.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
