---
title: "Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma"
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
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 14c5e02ce5af03d063260af19e9dd1a970a93ab6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma

Bir uygulama tarafından istenen kesin saat dilimi bilgilerini çeşitli nedenlerle belirli bir sistemde mevcut değil:

* Saat dilimi yerel sistemin kayıt defterinde hiçbir zaman tanımlamıştır.

* Saat dilimi hakkındaki verileri değiştirilemiyor veya kayıt defteri anahtarından kaldırılamıyor.

* Saat dilimi var, ancak belirli bir geçmiş dönem için saat dilimi düzeltmeleri hakkında doğru bilgileri yok.

Bu durumlarda, çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanızın gerektirdiği saat dilimi tanımlamak için yöntem. Bu yöntem aşırı ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz. Saat diliminin gün ışığından yararlanma saati destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz. (Bu koşulları tanımları için "Saat dilimi terminolojisi" bölümüne bakın [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Özel saat dilimlerini çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi. Bunun yerine, bunlar yalnızca tarafından döndürülen nesne başvurusu aracılığıyla erişilebilen <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.

Bu konuda ayarlama kuralları olmadan saat dilimi oluşturulacağını gösterir. Yaz Saati ayarlama kuralları destekleyen bir saat dilimi oluşturmak için bkz: [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Ayarlama kuralları olmadan saat dilimi oluşturmak için

1. Saat diliminin görünen adı tanımlayın.

   Görünen ad saat diliminin uzaklığı gelen Eşgüdümlü Evrensel Saat (UTC) parantez içine alınmış ve saat dilimi, bir veya birkaçı Şehir saat dilimi ya da bir veya daha fazla cou tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler girişleri veya saat dilimi bölgelerde.

2. Saat diliminin standart saat adını tanımlayın. Genellikle, bu dize saat diliminin tanımlayıcı olarak kullanılır.

3. Saat diliminin standart adından farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.

4. Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne. Saat dilimi UTC sonraki sürelerine sahip bir pozitif uzaklığı vardır. Saat dilimi UTC önceki sürelerine sahip negatif uzaklık vardır.

5. Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> yeni saat dilimine örneği oluşturmak için yöntem.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel bir saat dilimi Mawson, ayarlama kuralları yok Antarktika tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

Atanan dize <xref:System.TimeZoneInfo.DisplayName%2A> özelliği tarafından kolay bir açıklama saat dilimi UTC saat diliminin uzaklığı izlendiği standart bir biçim izler.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
