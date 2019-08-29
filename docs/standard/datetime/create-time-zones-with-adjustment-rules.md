---
title: 'Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma'
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
ms.openlocfilehash: 6ae739d3c5dd233c2129950666846979edfba370
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106682"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma

Bir uygulama için gerekli kesin saat dilimi bilgileri, bazı nedenlerle belirli bir sistemde mevcut olmayabilir:

- Saat dilimi, yerel sistemin kayıt defterinde hiç tanımlanmadı.

- Saat dilimi hakkındaki veriler, kayıt defterinden değiştirilmiş veya kaldırılmış.

- Saat dilimi, belirli bir geçmiş dönem için saat dilimi ayarlamaları hakkında doğru bilgilere sahip değildir.

Bu durumlarda, uygulamanız için gereken saat dilimini <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> tanımlamak için yöntemini çağırabilirsiniz. Bu yöntemin aşırı yüklerini, ayarlama kuralları olan veya olmayan bir saat dilimi oluşturmak için kullanabilirsiniz. Saat dilimi yaz saati kaydetme süresini destekliyorsa, düzeltilen veya kayan ayarlama kuralları ile ayarlamalar tanımlayabilirsiniz. (Bu terimlerin tanımları için, [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)konusundaki "saat dilimi terminolojisi" bölümüne bakın.)

> [!IMPORTANT]
> <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> Yöntemi çağırarak oluşturulan özel saat dilimleri kayıt defterine eklenmez. Bunun yerine, yalnızca <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> Yöntem çağrısı tarafından döndürülen nesne başvurusu aracılığıyla erişilebilir.

Bu konuda, ayarlama kuralları ile saat dilimi oluşturma gösterilmektedir. Gün ışığından yararlanma zaman ayarlama kurallarını desteklemeyen bir saat dilimi oluşturmak için bkz [. nasıl yapılır: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)olmadan saat dilimleri oluşturun.

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Kayan ayarlama kuralları ile saat dilimi oluşturmak için

1. Her ayarlama için (diğer bir deyişle, belirli bir zaman aralığı içinde her bir geçiş ve standart saate geri döndüğünüzde) şunları yapın:

    1. Saat dilimi ayarlaması için başlangıç geçiş süresini tanımlayın.

       <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> Yöntemini çağırmanız ve geçiş zamanını tanımlayan bir <xref:System.DateTime> değer, geçişin ayını tanımlayan bir tamsayı değeri, geçişin gerçekleştiği haftayı tanımlayan bir tamsayı değeri ve bir <xref:System.DayOfWeek> ile geçişin gerçekleştiği haftanın gününü tanımlayan değer. Bu yöntem çağrısı bir <xref:System.TimeZoneInfo.TransitionTime> nesnesi başlatır.

    2. Saat dilimi ayarlaması için bitiş geçiş süresini tanımlayın. Bu <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> Yöntem için başka bir çağrı gerekir. Bu yöntem çağrısı ikinci <xref:System.TimeZoneInfo.TransitionTime> bir nesnesi başlatır.

    3. Yöntemi çağırın ve ayarlamanın etkili başlangıç ve bitiş tarihleri, geçişte zaman miktarını tanımlayan bir <xref:System.TimeSpan> nesne ve günışığından yararlanma saati ile geçiş sırasında tanımlayan iki <xref:System.TimeZoneInfo.TransitionTime>nesne <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> zaman meydana gelir. Bu yöntem çağrısı bir <xref:System.TimeZoneInfo.AdjustmentRule> nesnesi başlatır.

    4. Nesneyi bir nesne <xref:System.TimeZoneInfo.AdjustmentRule> dizisine atayın. <xref:System.TimeZoneInfo.AdjustmentRule>

2. Saat diliminin görünen adını tanımlayın. Görünen ad, saat diliminin Eşgüdümlü Evrensel Saat (UTC) arasındaki kaydırın parantez içine alındığı ve ardından saat dilimini, saat diliminizdeki bir veya daha fazla şehirden veya bir ya da daha fazlasını tanımlayan bir dize tarafından izlenen oldukça standart bir biçim izler saat dilimindeki ndenemeler veya bölgeler.

3. Saat diliminin standart zamanının adını tanımlayın. Genellikle, bu dize saat diliminin tanımlayıcısı olarak da kullanılır.

4. Saat diliminin yaz saatinin adını tanımlayın.

5. Saat diliminin standart adından farklı bir tanımlayıcı kullanmak istiyorsanız, saat dilimi tanımlayıcısını tanımlayın.

6. Saat diliminin <xref:System.TimeSpan> UTC 'den sapmasını tanımlayan bir nesne oluşturun. UTC 'den sonraki saatlere sahip saat dilimleri pozitif bir uzaklığa sahiptir. UTC 'den önceki zamanlarla saat dilimlerinin negatif bir boşluğu vardır.

7. Yeni saat dilimini oluşturmak için yönteminiçağırın.<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>

## <a name="example"></a>Örnek

Aşağıdaki örnek, 1918 'e kadar çeşitli zaman aralıkları için ayarlama kuralları içeren Birleşik Devletler için merkezi bir standart saat dilimini tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Bu örnekte oluşturulan saat diliminin birden çok ayarlama kuralı vardır. Herhangi bir ayarlama kuralının etkin başlangıç ve bitiş tarihlerinin başka bir ayarlama kuralındaki tarihlerle çakışmadığından emin olmak için dikkatli olunmalıdır. Çakışma varsa, bir <xref:System.InvalidTimeZoneException> atılır.

Kayan ayarlama kuralları için 5 değeri, belirli bir ayın son haftasında geçişin gerçekleşeceğini göstermek için `week` <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> yönteminin parametresine geçirilir.

<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> Yöntem çağrısında kullanılacak <xref:System.TimeZoneInfo.AdjustmentRule> nesne dizisini oluştururken, kod diziyi, saat dilimi için oluşturulacak ayarlama sayısı için gereken boyuta başlatabilir. Bunun yerine, bu kod örneği, <xref:System.Collections.Generic.List%601.Add%2A> her ayarlama kuralını bir genel <xref:System.Collections.Generic.List%601> <xref:System.TimeZoneInfo.AdjustmentRule> nesne koleksiyonuna eklemek için yöntemini çağırır. Kodu daha sonra bu koleksiyonun <xref:System.Collections.Generic.List%601.CopyTo%2A> üyelerini diziye kopyalamak için yöntemini çağırır.

Örnek ayrıca, <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> sabit tarih ayarlamalarını tanımlamak için yöntemini kullanır. Bu, <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> yöntemi çağırmaya benzerdir, ancak geçiş parametrelerinin yalnızca saatini, ayını ve gününü gerektirir.

Örnek, aşağıdakiler gibi kod kullanılarak test edilebilir:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md)
- [Nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
