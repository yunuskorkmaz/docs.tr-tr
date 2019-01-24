---
title: Üyeleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 246ddeeab9814f32b0a3bf0d3586007a434d3953
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592856"
---
# <a name="members-c-programming-guide"></a>Üyeler (C# Programlama Kılavuzu)
Sınıflar ve yapılar, kendi verilerini ve davranışlarını temsil eden üyelere sahiptir. Sınıfında, devralma hiyerarşisindeki tüm sınıflarda bildirilen tüm üyeleri (oluşturucular ve sonlandırıcılar dışında) bir sınıfın üyeleri bildirilen tüm üyeleri içerir. Temel sınıflardaki özel üyeler devralınır ancak türetilmiş sınıflardan erişilebilir değildir.  
  
 Aşağıdaki tablo, bir sınıfın veya yapının içerebileceği üye türlerini listeler:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)|Alanlar, sınıf kapsamında bildirilen değişkenlerdir. Bir alan, yerleşik bir sayısal tür veya başka bir sınıfın bir örneği olabilir. Örneğin bir takvim sınıfı, geçerli tarihi içeren bir alana sahip olabilir.|  
|[Sabitler](../../../csharp/programming-guide/classes-and-structs/constants.md)|Sabitler, değeri derleme zamanında atanan ve değiştirilemeyen alanlar veya özelliklerdir.|  
|[Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)|Özellikler, bir sınıftaki alanlar gibi erişilen o sınıftaki öğelerdir. Bir özellik, nesne bilgisi olmadan değiştirilmesini engellemek üzere bir sınıf alanı için koruma sağlayabilir.|  
|[Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)|Yöntemler, bir sınıfın gerçekleştirebildiği eylemleri tanımlar. Yöntemler girdi verilerini sağlayan parametreleri alabilir ve parametreler ile çıktı verilerini döndürebilir. Ayrıca yöntemler parametre kullanmadan bir değeri doğrudan döndürebilir.|  
|[Olaylar](../../../csharp/programming-guide/events/index.md)|Olaylar, diğer nesnelere düğme tıklamaları veya bir yöntemin başarıyla tamamlanması gibi örnekleri sağlar. Olaylar, temsilciler kullanılarak tanımlanır ve tetiklenir.|  
|[İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Aşırı yüklenmiş operatörler sınıfı üyeleri olarak kabul edilir. Bir operatörü aşırı yüklediğinizde bu operatörü bir sınıftaki genel statik bir yöntem olarak tanımlarsınız. Önceden tanımlı operatörler (`+`, `*`, `<` vb.) üye olarak kabul edilmez. Daha fazla bilgi için [fazla yüklenebilir işleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).|  
|[Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)|Dizinleyiciler, bir nesnenin dizilere benzer şekilde dizinlenmesini sağlar.|  
|[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Yapıcılar, nesne ilk oluşturulduğunda çağırılan yöntemlerdir. Bunlar genellikle bir nesneye ait verileri başlatmak için kullanılır.|  
|[Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)|Sonlandırıcılar nadiren C# dilinde kullanılır. Bunlar, nesne bellekten kaldırılmak üzereyken çalışma zamanı yürütme alt yapısı tarafından çağrılan yöntemlerdir. Bu yöntemler, genellikle yayınlanması gereken tüm kaynakların uygun şekilde işlendiğinden emin olmak için kullanılır.|  
|[İç içe Geçmiş Türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|İç içe olan türler, başka bir türde bildirilen türlerdir. İç içe türler genellikle yalnızca bunları içeren türler tarafından kullanılan nesneleri tanımlamak için kullanılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)
- [İç içe Geçmiş Türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md)
- [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)
- [Aşırı Yüklenebilir İşleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
