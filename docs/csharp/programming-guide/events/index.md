---
title: Olaylar-C# Programlama Kılavuzu
description: Olaylar hakkında bilgi edinin. Olaylar, bir sınıf ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar.
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 14c18006e393dece5d32d30c2a727d797515c779
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167463"
---
# <a name="events-c-programming-guide"></a>Olaylar (C# Programlama Kılavuzu)

Olaylar, bir [sınıf](../../language-reference/keywords/class.md) ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar. Olayı gönderen (veya *başlatan*) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya *işleyen*) sınıflar *aboneler*olarak adlandırılır.  
  
Tipik bir C# Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından oluşturulan olaylara abone olursunuz. Visual C# tümleşik geliştirme ortamı 'nı (IDE) bir denetimin yayımladığı olaylara gözatıp işlemek istediğiniz olanları seçebilirsiniz. IDE, otomatik olarak boş bir olay işleyici yöntemi ve olaya abone olmak için kod eklemenin kolay bir yolunu sunar. Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md).
  
## <a name="events-overview"></a>Olaylara Genel Bakış  

 Olaylar aşağıdaki özelliklere sahiptir:  
  
- Yayımcı bir olayın ne zaman gerçekleştiğini belirler; aboneler olaya yanıt olarak hangi eylemin alınacağını tespit ediyor.  
  
- Bir olay birden çok aboneye sahip olabilir. Bir abone birden çok yayımcıların birden çok olayını işleyebilir.  
  
- Abone olmayan olaylar hiçbir şekilde oluşturulmaz.  
  
- Olaylar genellikle grafik kullanıcı arabirimlerinde düğme tıklamaları veya menü seçimleri gibi kullanıcı eylemlerini işaret etmek için kullanılır.  
  
- Bir olayda birden çok abone olduğunda, olay işleyicileri bir olay oluşturulduğunda zaman uyumlu olarak çağrılır. Olayları zaman uyumsuz olarak çağırmak için bkz. [zaman uyumlu yöntemleri zaman uyumsuz çağırma](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- .NET sınıf kitaplığında, olaylar <xref:System.EventHandler> temsilciyi ve <xref:System.EventArgs> temel sınıfı temel alır.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 Daha fazla bilgi için bkz.  
  
- [Olaylara abone olma ve aboneliği kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [.NET Kılavuzlarına uygun olaylar yayımlama](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Türetilmiş sınıflarda temel sınıf olayları oluşturma](./how-to-raise-base-class-events-in-derived-classes.md)

- [Arabirim olaylarını uygulama](./how-to-implement-interface-events.md)

- [Özel olay erişimcilerini uygulama](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Olaylar](~/_csharplang/spec/classes.md#events) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  

 C# 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) [: c# 3,0 programcıları için 250 ' den fazla çözüm](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))  
  
 Öğreniminde [Temsilciler ve olaylar](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) [c# 3,0: C# 3,0 temelleri ana](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>
- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](../delegates/index.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
