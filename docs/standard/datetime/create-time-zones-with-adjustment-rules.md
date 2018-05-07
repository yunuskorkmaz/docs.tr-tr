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
ms.openlocfilehash: c63b93e0dc587571605edb305979b8f97bf54cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma

Bir uygulama tarafından istenen kesin saat dilimi bilgilerini çeşitli nedenlerle belirli bir sistemde mevcut değil:

* Saat dilimi yerel sistemin kayıt defterinde hiçbir zaman tanımlamıştır.

* Saat dilimi hakkındaki verileri değiştirilemiyor veya kayıt defteri anahtarından kaldırılamıyor.

* Saat dilimi, belirli bir geçmiş dönem için saat dilimi düzeltmeleri hakkında doğru bilgileri yok.

Bu durumlarda, çağırabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanızın gerektirdiği saat dilimi tanımlamak için yöntem. Bu yöntem aşırı ile veya ayarlama kuralları olmadan saat dilimi oluşturmak için kullanabilirsiniz. Saat diliminin gün ışığından yararlanma saati destekliyorsa, ayarlamalar ya da sabit veya değişken ayarlama kuralları ile tanımlayabilirsiniz. (Bu koşulları tanımları için "Saat dilimi terminolojisi" bölümüne bakın [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Özel saat dilimlerini çağrılarak oluşturulan <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi kayıt defterine eklenmedi. Bunun yerine, bunlar yalnızca tarafından döndürülen nesne başvurusu aracılığıyla erişilebilen <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntem çağrısı.

Bu konuda ayarlama kuralları ile saat dilimi oluşturulacağını gösterir. Yaz Saati ayarlama kuralları desteklemeyen bir saat dilimi oluşturmak için bkz: [nasıl yapılır: oluşturmak saat dilimleri olmadan ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Bir saat dilimi ayarlama kuralları kayan oluşturmak için

1. (Yani, her transition from uzağa içindir ve Standart Saati için belirli bir zaman aralığı içinde geri) her ayarlaması için aşağıdakileri yapın:

    1. Saat dilimi ayarlaması için başlangıç geçiş süresi tanımlayın.

       Çağırmalısınız <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> yöntemi ve bu geçirin bir <xref:System.DateTime> geçişi, geçiş ayın tanımlayan bir tamsayı değeri, geçiş oluştuğu, haftanın tanımlayan bir tamsayı değeri süresini tanımlayan değeri ve <xref:System.DayOfWeek> geçiş oluştuğu haftanın gününü tanımlayan değeri. Bu yöntem çağrısı başlatır bir <xref:System.TimeZoneInfo.TransitionTime> nesnesi.

    2. Saat dilimi ayarlaması için bitiş geçiş süresi tanımlayın. Bu, başka bir çağrıyı gerektirir <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> yöntemi. Bu yöntem çağrısı ikinci bir örneğini oluşturur <xref:System.TimeZoneInfo.TransitionTime> nesnesi.

    3. Çağrı <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> yöntemi ve etkili başlangıç ve bitiş tarihleri ayarlama geçirin bir <xref:System.TimeSpan> süreyi geçişi ve iki tanımlayan nesne <xref:System.TimeZoneInfo.TransitionTime> ne zaman tanımlayan nesneleri gün ışığından gelen ve giden geçişleri zaman oluşur. Bu yöntem çağrısı başlatır bir <xref:System.TimeZoneInfo.AdjustmentRule> nesnesi.

    4. Ata <xref:System.TimeZoneInfo.AdjustmentRule> bir dizi nesneyi <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri.

2. Saat diliminin görünen adı tanımlayın. Görünen ad saat diliminin uzaklığı gelen Eşgüdümlü Evrensel Saat (UTC) parantez içine alınmış ve saat dilimi, bir veya birkaçı Şehir saat dilimi ya da bir veya daha fazla cou tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler girişleri veya saat dilimi bölgelerde.

3. Saat diliminin standart saat adını tanımlayın. Genellikle, bu dize saat diliminin tanımlayıcı olarak kullanılır.

4. Saat diliminin gün ışığından yararlanma saati adını tanımlayın.

5. Saat diliminin standart adından farklı bir kimlik kullanmak istiyorsanız, saat dilimi tanımlayıcı tanımlayın.

6. Örneği bir <xref:System.TimeSpan> UTC saat diliminin uzaklığı tanımlayan nesne. Saat dilimi UTC sonraki sürelerine sahip bir pozitif uzaklığı vardır. Saat dilimi UTC önceki sürelerine sahip negatif uzaklık vardır.

7. Çağrı <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> yeni saat dilimine örneği oluşturmak için yöntem.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir merkezi standart saat dilimi 1918 zaman aralıkları için mevcut çeşitli ayarlama kuralları içerir Amerika Birleşik Devletleri'nin tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Bu örnekte oluşturulan saat dilimi birden çok ayarlama kuralları vardır. Geçerli başlangıç ve bitiş tarihleri herhangi bir ayarı kuralın başka bir ayarlama kuralı tarihlerle çakışmadığından emin olmak için dikkatli olunması gerekir. Bir çakışma varsa bir <xref:System.InvalidTimeZoneException> oluşturulur.

Ayarlama kuralları değişken için değeri 5 geçirilir `week` parametresinin <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> geçişi belirli bir ay son haftasında ortaya çıktığını göstermek için yöntem.

Dizi oluşturma <xref:System.TimeZoneInfo.AdjustmentRule> kullanmak için nesneleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> yöntem çağrısı kodu başlatmak için saat dilimi oluşturulacak ayarlamalar sayısına göre gerekli boyutu diziye. Bunun yerine, bu kod örneği çağırır <xref:System.Collections.Generic.List%601.Add%2A> her ayarlama kuralı için genel ekleme yöntemi <xref:System.Collections.Generic.List%601> koleksiyonu <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri. Kod sonra çağırır <xref:System.Collections.Generic.List%601.CopyTo%2A> Bu koleksiyonun üyeleri dizisine kopyalamak için yöntem.

Bu örnek ayrıca kullanır <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> sabit tarih ayarlamaları tanımlamak için yöntem. Bu arama için benzer <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> yalnızca zaman, ay ve gün geçiş parametrelerden biri olan gerektirir dışında yöntemi.

Örnek kod aşağıdaki gibi kullanarak test edilebilir:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Şu ad alanlarından alınan olduğunu:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
[nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
