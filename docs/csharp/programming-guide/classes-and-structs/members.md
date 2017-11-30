---
title: "Üyeler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 184d4f2976b8594c308efeb113a0490499e3460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="members-c-programming-guide"></a>Üyeler (C# Programlama Kılavuzu)
Sınıflar ve yapılar, kendi verilerini ve davranışlarını temsil eden üyelere sahiptir. Sınıf üyeleri (oluşturucular ve sonlandırıcılar dışında) tüm üyeleri tüm sınıflar, devralma hiyerarşisi içinde bildirilen birlikte sınıfı tüm üyeleri olarak bildirilen dahil eder. Temel sınıflardaki özel üyeler devralınır ancak türetilmiş sınıflardan erişilebilir değildir.  
  
 Aşağıdaki tablo, bir sınıfın veya yapının içerebileceği üye türlerini listeler:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[Alanları](../../../csharp/programming-guide/classes-and-structs/fields.md)|Alanlar, sınıf kapsamında bildirilen değişkenlerdir. Bir alan, yerleşik bir sayısal tür veya başka bir sınıfın bir örneği olabilir. Örneğin bir takvim sınıfı, geçerli tarihi içeren bir alana sahip olabilir.|  
|[Sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md)|Sabitler, değeri derleme zamanında atanan ve değiştirilemeyen alanlar veya özelliklerdir.|  
|[Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)|Özellikler, bir sınıftaki alanlar gibi erişilen o sınıftaki öğelerdir. Bir özellik, nesne bilgisi olmadan değiştirilmesini engellemek üzere bir sınıf alanı için koruma sağlayabilir.|  
|[Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)|Yöntemler, bir sınıfın gerçekleştirebildiği eylemleri tanımlar. Yöntemler girdi verilerini sağlayan parametreleri alabilir ve parametreler ile çıktı verilerini döndürebilir. Ayrıca yöntemler parametre kullanmadan bir değeri doğrudan döndürebilir.|  
|[Olayları](../../../csharp/programming-guide/events/index.md)|Olaylar, diğer nesnelere düğme tıklamaları veya bir yöntemin başarıyla tamamlanması gibi örnekleri sağlar. Olaylar, temsilciler kullanılarak tanımlanır ve tetiklenir.|  
|[İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Aşırı yüklenmiş operatörler sınıfı üyeleri olarak kabul edilir. Bir operatörü aşırı yüklediğinizde bu operatörü bir sınıftaki genel statik bir yöntem olarak tanımlarsınız. Önceden tanımlı operatörler (`+`, `*`, `<` vb.) üye olarak kabul edilmez. Daha fazla bilgi için bkz: [fazla yüklenebilir işleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).|  
|[Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)|Dizinleyiciler, bir nesnenin dizilere benzer şekilde dizinlenmesini sağlar.|  
|[Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Yapıcılar, nesne ilk oluşturulduğunda çağırılan yöntemlerdir. Bunlar genellikle bir nesneye ait verileri başlatmak için kullanılır.|  
|[Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)|C# ' ta nadiren sonlandırıcılar kullanılır. Bunlar, nesne bellekten kaldırılmak üzereyken çalışma zamanı yürütme alt yapısı tarafından çağrılan yöntemlerdir. Bu yöntemler, genellikle yayınlanması gereken tüm kaynakların uygun şekilde işlendiğinden emin olmak için kullanılır.|  
|[İç içe geçmiş türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|İç içe olan türler, başka bir türde bildirilen türlerdir. İç içe türler genellikle yalnızca bunları içeren türler tarafından kullanılan nesneleri tanımlamak için kullanılır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Alanları](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)  
 [İç içe geçmiş türler](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
 [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Fazla yüklenebilir işleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
