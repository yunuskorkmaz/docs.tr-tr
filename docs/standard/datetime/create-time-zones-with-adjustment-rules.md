---
title: 'Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80a5c04f7807638a4a8b114828083835f348ac08
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520470"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma

Bir uygulama tarafından istenen kesin saat dilimi bilgilerini, çeşitli nedenlerle belirli bir sistemde mevcut olmayabilir:

* Saat dilimi yerel sisteminin kayıt defterinde hiçbir zaman tanımlanmış.

* Saat dilimi ilgili verileri değiştirilemez veya kayıt defterinden kaldırıldı.

* Saat diliminin saat dilimi düzeltmeleri hakkında belirli bir geçmiş dönem için doğru bilgileri yok.

Bu gibi durumlarda çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanız için gereken saat dilimi tanımlamak için yöntemi. Bu yöntem aşırı yüklemeleri ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz. Gün ışığından yararlanma saat dilimi destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz. (Bu terimlerin tanımları için "Saat dilimi terminolojisi" bölümüne bakın. [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Özel saat dilimi çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi. Bunun yerine, bunlar tarafından döndürülen nesne başvurusu erişilebilir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.

Bu konuda, ayarlama kuralları ile saat dilimi oluşturulacağını gösterir. Gün ışığından yararlanma ayarlama kuralları desteklemeyen bir saat dilimi oluşturmak için bkz [nasıl yapılır: kuralları ayarlama olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Kayan ayarlama kuralları ile saat dilimi oluşturmak için

1. (Yani, her transition from uzağa içindir ve belirli bir zaman aralığı içinde geri Standart Saati) her ayarı için aşağıdakileri yapın:

    1. Saat dilimi ayarlama için başlangıç geçiş süresini tanımlayın.

       Çağırmalısınız <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> yöntemi ve bir <xref:System.DateTime> geçişi, geçiş işleminin yapıldığı ay tanımlayan bir tamsayı değeri, geçiş oluştuğu, haftanın gününü tanımlayan bir tamsayı değeri zaman tanımlayan değeri ve <xref:System.DayOfWeek> geçişin gerçekleştiği haftanın gününü tanımlayan değeri. Bu yöntem çağrı bir <xref:System.TimeZoneInfo.TransitionTime> nesne.

    2. Saat dilimi ayarlama bitiş geçiş süresini tanımlayın. Bu, başka bir çağrıyı gerektirir <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> yöntemi. Bu yöntem çağrısının ikinci bir örneğini oluşturur <xref:System.TimeZoneInfo.TransitionTime> nesne.

    3. Çağrı <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> yöntemi ve geçerli olan başlangıç ve bitiş tarihlerini ayarlama geçirin bir <xref:System.TimeSpan> süreyi geçiş ve iki tanımlayan nesnesi <xref:System.TimeZoneInfo.TransitionTime> ne zaman tanımlayan nesneleri gün ışığından gelen ve giden geçiş zaman oluşur. Bu yöntem çağrı bir <xref:System.TimeZoneInfo.AdjustmentRule> nesne.

    4. Ata <xref:System.TimeZoneInfo.AdjustmentRule> nesne dizisi olarak <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri.

2. Saat diliminin görünen adı tanımlayın. Görünen ad, saat diliminin uzaklığı ile eşgüdümlü evrensel saat (UTC) parantez içine alınmış ve bir veya daha fazla şehirlerin saat dilimini ya da bir veya daha cou saat dilimini tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izleyen girişleri veya saat dilimi bölgelerde.

3. Saat diliminin standart saat adını tanımlayın. Genellikle, bu dizenin saat diliminin tanımlayıcı olarak kullanılır.

4. Saat diliminin gün ışığından yararlanma saat adını tanımlayın.

5. Saat diliminin standart addan farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.

6. Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne. Saat dilimi ile UTC sonraki saatleri, pozitif bir sapma vardır. Saat dilimi ile UTC önceki bir kez bir negatif uzaklığa sahip.

7. Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> yeni saat dilimi örneklemek için yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir merkezi standart saat dilimi 1918 zaman aralıkları için mevcut çeşitli ayarlama kuralları içerir Amerika Birleşik Devletleri'nin tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Bu örnekte oluşturulan saat dilimi birden çok düzeltmesi kurallara sahiptir. Geçerli başlangıç ve bitiş tarihlerini ayarlama herhangi bir kural başka bir ayarlama kuralı tarihlerle çakışmadığından emin olmak için dikkatli olunması gerekir. Bir çakışma varsa bir <xref:System.InvalidTimeZoneException> oluşturulur.

Ayarlama kuralları değişken için değeri 5 geçirilir `week` parametresinin <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> geçişi, son haftanın belirli bir ay üzerinde ortaya çıktığını göstermek için yöntemi.

Dizi oluşturma <xref:System.TimeZoneInfo.AdjustmentRule> kullanmak için nesneleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> yöntemi çağrısı, kod başlatmak dizi boyutu ayarlamalar sayısına göre saat dilimini oluşturulması gerekir. Bunun yerine, bu kod örneği çağrıları <xref:System.Collections.Generic.List%601.Add%2A> her ayarlama kuralı için genel ekleme yöntemi <xref:System.Collections.Generic.List%601> koleksiyonunu <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri. Ardından kod çağırır <xref:System.Collections.Generic.List%601.CopyTo%2A> Bu koleksiyonun üyeleri diziye kopyalamak için yöntemi.

Örnekte ayrıca <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> sabit tarih ayarlamaları tanımlamak için yöntemi. Bu arama için benzer <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> yöntemi dışında olan yalnızca zaman, ay ve gün geçiş parametrelerinin gerektirir.

Örnek kod aşağıdaki gibi kullanarak test edilebilir:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
* [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
* [Nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
