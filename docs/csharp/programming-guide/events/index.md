---
title: Olaylar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 8923bb4263c6857e7c2e194851befdc48f33a89e
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50743956"
---
# <a name="events-c-programming-guide"></a>Olaylar (C# Programlama Kılavuzu)
Olayları etkinleştirmektedir bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya diğer bildirmek için nesne sınıfları veya nesneleri ilgilendiğiniz bir sorun oluştuğunda. Gönderen sınıfı (veya *başlatır*) olay çağrılır *yayımcı* ve alan sınıfları (veya *işlemek*) olay çağrılır *aboneleri* .  
  
 Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimleri tarafından oluşturulan olaylara abone olun. Visual C# tümleşik geliştirme ortamı (IDE) bir denetim yayımlayan olayları ve kullanmak istediğiniz olanları seçmek için kullanabilirsiniz. IDE boş olay işleyicisi yöntemi ve olaya abone olmak için kodu otomatik olarak ekler. Daha fazla bilgi için [nasıl yapılır: abone olma ve aboneliği, olaylarından](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Olaylara Genel Bakış  
 Olayları, aşağıdaki özelliklere sahiptir:  
  
-   Yayımcı, bir olay olduğunda tetiklenir belirler; Aboneler, olaya yanıt olarak yapılan bir eylemi belirler.  
  
-   Bir olayın birden fazla aboneye sahip olabilir. Bir abonenin birden çok yayımcılardan birden çok olay işleyebilir.  
  
-   Abone olan olaylar hiçbir zaman oluşturulur.  
  
-   Olaylar genellikle, düğme tıklamaları veya grafik kullanıcı arabirimleri menü seçimleri gibi kullanıcı eylemlerini göstermek için kullanılır.  
  
-   Bir olay birden çok abone olduğunda, bir olay oluştuğunda olay işleyicileri zaman uyumlu olarak çağrılır. Olayları zaman uyumsuz olarak çağırma hakkında bilgi için bkz: [uyumsuz zaman uyumlu yöntemleri çağırma](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
-   İçinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı, olayları temel <xref:System.EventHandler> temsilci ve <xref:System.EventArgs> temel sınıfı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Nasıl yapılır: Olay Örneklerini Depolamak için Sözlük Kullanma](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Nasıl yapılır: Özel Olay Erişimcilerini Uygulama](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [olayları](~/_csharplang/spec/classes.md#events) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 [Temsilciler, olayları ve Lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) içinde [C# 3.0 Cookbook, Third Edition: C# 3.0 programcıları için 250'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Temsilciler ve olaylar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) içinde [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.EventHandler>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
