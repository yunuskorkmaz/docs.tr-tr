---
title: "Olaylar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72563b9e37c26257a2bf5939f63ece050ec003ab
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/24/2018
---
# <a name="events-c-programming-guide"></a>Olaylar (C# Programlama Kılavuzu)
Olayları etkinleştir bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya diğer bildirmek için nesne sınıfları nesneleri çeken bir şey olduğunda. Gönderir sınıfı (veya *başlatır*) olay çağrılır *yayımcı* ve alma sınıfları (veya *işlemek*) olay çağrılır *aboneleri* .  
  
 Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından oluşturulan olaylara abone olun. Kullanabileceğiniz [!INCLUDE[csprcs](~/includes/csprcs-md.md)] tümleşik geliştirme ortamı (IDE) bir denetim yayımlar etkinliklere göz atın ve işlemek için istediğiniz olanları seçebilirsiniz. IDE boş olay işleyicisi yöntemi ve olaya abone için kodu otomatik olarak ekler. Daha fazla bilgi için bkz: [nasıl yapılır: abone olma ve aboneliği olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Olaylara Genel Bakış  
 Olayları aşağıdaki özelliklere sahiptir:  
  
-   Yayımcı, ne zaman bir olay tetiklenir belirler; aboneleri olaya yanıt olarak yapılan eylemi belirler.  
  
-   Bir olay birden çok abone olabilir. Bir abonenin birden çok yayımcılar birden çok olaylarından işleyebilir.  
  
-   Abone olan olayları hiçbir zaman oluşturulur.  
  
-   Olaylar, genellikle kullanıcı eylemlerini düğme tıklamaları veya menü seçimleri grafik kullanıcı arabirimleri gibi göstermek için kullanılır.  
  
-   Bir olay birden çok abone olduğunda, bir olay oluşturulduğunda olay işleyicileri zaman uyumlu olarak çağrılır. Olaylar zaman uyumsuz olarak çağırmak için bkz: [çağırma zaman uyumlu yöntemleri zaman uyumsuz olarak](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
-   İçinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı olayları temel <xref:System.EventHandler> temsilci ve <xref:System.EventArgs> temel sınıfı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [İş Parçacığı Eşitleme](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Nasıl yapılır: Özel Olay Erişimcilerini Uygulama](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 [Temsilciler ve olaylar Lambda ifadeleri](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) içinde [C# 3.0 Kılavuzu, üçüncü baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Temsilciler ve olaylar](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) içinde [öğrenme C# 3.0: C# 3.0 ile ilgili temel bilgileri Yöneticisi](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.EventHandler>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
