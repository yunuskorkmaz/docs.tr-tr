---
title: 'Nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026555"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma

Bir uygulama tarafından istenen kesin saat dilimi bilgilerini, çeşitli nedenlerle belirli bir sistemde mevcut olmayabilir:

* Saat dilimi yerel sisteminin kayıt defterinde hiçbir zaman tanımlanmış.

* Saat dilimi ilgili verileri değiştirilemez veya kayıt defterinden kaldırıldı.

* Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi düzeltmeleri hakkında doğru bilgileri yok.

Bu gibi durumlarda çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanız için gereken saat dilimi tanımlamak için yöntemi. Bu yöntem aşırı yüklemeleri ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz. Gün ışığından yararlanma saat dilimi destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz. (Bu terimlerin tanımları için "Saat dilimi terminolojisi" bölümüne bakın. [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Özel saat dilimi çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi. Bunun yerine, bunlar tarafından döndürülen nesne başvurusu erişilebilir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.

Bu konuda, bir saat dilimi ayarlama kuralları olmadan oluşturma gösterilmektedir. Gün ışığından yararlanma ayarlama kuralları destekleyen bir saat dilimi oluşturmak için bkz [nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Bir saat dilimi ayarlama kuralları olmadan oluşturmak için

1. Saat diliminin görünen adı tanımlayın.

   Görünen ad, saat diliminin uzaklığı ile eşgüdümlü evrensel saat (UTC) parantez içine alınmış ve bir veya daha fazla şehirlerin saat dilimini ya da bir veya daha cou saat dilimini tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izleyen girişleri veya saat dilimi bölgelerde.

2. Saat diliminin standart saat adını tanımlayın. Genellikle, bu dizenin saat diliminin tanımlayıcı olarak kullanılır.

3. Saat diliminin standart addan farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.

4. Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne. Saat dilimi ile UTC sonraki saatleri, pozitif bir sapma vardır. Saat dilimi ile UTC önceki bir kez bir negatif uzaklığa sahip.

5. Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> yeni saat dilimi örneklemek için yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Mawson, ayarlama kuralları yok Antarktika, özel bir saat dilimi tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Atanan dize <xref:System.TimeZoneInfo.DisplayName%2A> özelliği UTC saat diliminin uzaklığı saat dilimini kolay açıklaması tarafından izlendiği standart bir biçim izler.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
