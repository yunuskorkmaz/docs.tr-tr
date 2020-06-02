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
ms.openlocfilehash: b7e938581dfde3f1566aa2506302292686c2fc5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278174"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma

Bir uygulama için gerekli kesin saat dilimi bilgileri, bazı nedenlerle belirli bir sistemde mevcut olmayabilir:

- Saat dilimi, yerel sistemin kayıt defterinde hiç tanımlanmadı.

- Saat dilimi hakkındaki veriler, kayıt defterinden değiştirilmiş veya kaldırılmış.

- Saat dilimi, belirli bir geçmiş dönem için saat dilimi ayarlamaları hakkında doğru bilgilere sahip değildir.

Bu durumlarda, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> uygulamanız için gereken saat dilimini tanımlamak için yöntemini çağırabilirsiniz. Bu yöntemin aşırı yüklerini, ayarlama kuralları olan veya olmayan bir saat dilimi oluşturmak için kullanabilirsiniz. Saat dilimi yaz saati kaydetme süresini destekliyorsa, düzeltilen veya kayan ayarlama kuralları ile ayarlamalar tanımlayabilirsiniz. (Bu terimlerin tanımları için, [saat dilimine genel bakış](time-zone-overview.md)konusundaki "saat dilimi terminolojisi" bölümüne bakın.)

> [!IMPORTANT]
> Yöntemi çağırarak oluşturulan özel saat dilimleri <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterine eklenmez. Bunun yerine, yalnızca Yöntem çağrısı tarafından döndürülen nesne başvurusu aracılığıyla erişilebilir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> .

Bu konuda, ayarlama kuralları ile saat dilimi oluşturma gösterilmektedir. Gün ışığından yararlanma zaman ayarlama kurallarını desteklemeyen bir saat dilimi oluşturmak için bkz. [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Kayan ayarlama kuralları ile saat dilimi oluşturmak için

1. Her ayarlama için (diğer bir deyişle, belirli bir zaman aralığı içinde her bir geçiş ve standart saate geri döndüğünüzde) şunları yapın:

    1. Saat dilimi ayarlaması için başlangıç geçiş süresini tanımlayın.

       <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>Yöntemini çağırmanız ve <xref:System.DateTime> geçiş saatini tanımlayan bir değer, geçişin ayını tanımlayan bir tamsayı değeri, geçişin gerçekleştiği haftayı tanımlayan bir tamsayı değeri ve <xref:System.DayOfWeek> geçişin gerçekleştiği haftanın gününü tanımlayan bir değer geçirmeniz gerekir... Bu yöntem çağrısı bir <xref:System.TimeZoneInfo.TransitionTime> nesnesi başlatır.

    2. Saat dilimi ayarlaması için bitiş geçiş süresini tanımlayın. Bu yöntem için başka bir çağrı gerekir <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> . Bu yöntem çağrısı ikinci bir <xref:System.TimeZoneInfo.TransitionTime> nesnesi başlatır.

    3. Yöntemi çağırın <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> ve ayarlamanın geçerli başlangıç ve bitiş tarihleri, <xref:System.TimeSpan> geçişte zaman miktarını tanımlayan bir nesne ve <xref:System.TimeZoneInfo.TransitionTime> yaz saati kaydetme saatinin ne zaman yapılacağını tanımlayan iki nesne oluşur. Bu yöntem çağrısı bir <xref:System.TimeZoneInfo.AdjustmentRule> nesnesi başlatır.

    4. <xref:System.TimeZoneInfo.AdjustmentRule>Nesneyi bir nesne dizisine atayın <xref:System.TimeZoneInfo.AdjustmentRule> .

2. Saat diliminin görünen adını tanımlayın. Görünen ad, saat diliminin Eşgüdümlü Evrensel Saat (UTC) arasındaki kaydırın parantez içine alındığı ve ardından saat dilimini tanımlayan bir dize, saat diliminizdeki bir veya daha fazla şehir ya da saat dilimindeki ülkelerin veya bölgelerin bir ya da daha fazlasını tanımlayan oldukça standart bir biçim izler.

3. Saat diliminin standart zamanının adını tanımlayın. Genellikle, bu dize saat diliminin tanımlayıcısı olarak da kullanılır.

4. Saat diliminin yaz saatinin adını tanımlayın.

5. Saat diliminin standart adından farklı bir tanımlayıcı kullanmak istiyorsanız, saat dilimi tanımlayıcısını tanımlayın.

6. <xref:System.TimeSpan>Saat DILIMININ UTC 'den sapmasını tanımlayan bir nesne oluşturun. UTC 'den sonraki saatlere sahip saat dilimleri pozitif bir uzaklığa sahiptir. UTC 'den önceki zamanlarla saat dilimlerinin negatif bir boşluğu vardır.

7. <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>Yeni saat dilimini oluşturmak için yöntemini çağırın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, 1918 'e kadar çeşitli zaman aralıkları için ayarlama kuralları içeren Birleşik Devletler için merkezi bir standart saat dilimini tanımlar.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Bu örnekte oluşturulan saat diliminin birden çok ayarlama kuralı vardır. Herhangi bir ayarlama kuralının etkin başlangıç ve bitiş tarihlerinin başka bir ayarlama kuralındaki tarihlerle çakışmadığından emin olmak için dikkatli olunmalıdır. Çakışma varsa, bir <xref:System.InvalidTimeZoneException> atılır.

Kayan ayarlama kuralları için 5 değeri, `week` <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> belirli bir ayın son haftasında geçişin gerçekleşeceğini göstermek için yönteminin parametresine geçirilir.

<xref:System.TimeZoneInfo.AdjustmentRule>Yöntem çağrısında kullanılacak nesne dizisini oluştururken <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> , kod diziyi, saat dilimi için oluşturulacak ayarlama sayısı için gereken boyuta başlatabilir. Bunun yerine, bu kod örneği, <xref:System.Collections.Generic.List%601.Add%2A> her ayarlama kuralını bir genel nesne koleksiyonuna eklemek için yöntemini çağırır <xref:System.Collections.Generic.List%601> <xref:System.TimeZoneInfo.AdjustmentRule> . Kodu daha sonra <xref:System.Collections.Generic.List%601.CopyTo%2A> Bu koleksiyonun üyelerini diziye kopyalamak için yöntemini çağırır.

Örnek ayrıca, <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> sabit tarih ayarlamalarını tanımlamak için yöntemini kullanır. Bu, yöntemi çağırmaya benzerdir <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> , ancak geçiş parametrelerinin yalnızca saatini, ayını ve gününü gerektirir.

Örnek, aşağıdakiler gibi kod kullanılarak test edilebilir:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Aşağıdaki ad alanları içeri aktarılmalıdır:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Saat dilimine genel bakış](time-zone-overview.md)
- [Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md)
