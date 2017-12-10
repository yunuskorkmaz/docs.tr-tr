---
title: "Olaylar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ab40de46bf198cf683ec4847a42d88b3d4807e0
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
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
  
-   [Nasıl yapılır: abone olaylara ve aboneliği kaldırma](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Nasıl yapılır: .NET Framework yönergeleriyle uyumlu olayları yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Nasıl yapılır: türetilmiş sınıflarda temel sınıf olayları oluşturma](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [İş parçacığı eşitleme](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Nasıl yapılır: olay örneklerini depolamak için Sözlük kullanma](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Nasıl yapılır: özel olay erişimcilerini uygulama](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 [Temsilciler ve olaylar Lambda ifadeleri](http://go.microsoft.com/fwlink/?LinkId=195395) içinde [C# 3.0 Kılavuzu, üçüncü baskı: C# 3.0 programcıları için 250'den fazla çözüm](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Temsilciler ve olaylar](http://go.microsoft.com/fwlink/?LinkId=195418) içinde [öğrenme C# 3.0: C# 3.0 ile ilgili temel bilgileri Yöneticisi](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.EventHandler>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Windows Forms'ta olay işleyicileri oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Olay tabanlı zaman uyumsuz desen ile birden çok iş parçacıklı programlama](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
