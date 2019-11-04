---
title: Olaylar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: d70ec5784d56bad60fbc33ae0b992de1bebfce38
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417952"
---
# <a name="events-c-programming-guide"></a>Olaylar (C# Programlama Kılavuzu)
Olaylar, bir [sınıf](../../language-reference/keywords/class.md) ya da nesnenin, ilgi çekici bir şeyler gerçekleştiğinde diğer sınıflara veya nesnelere bildirilmesini sağlar. Olayı gönderen (veya *başlatan*) sınıf *Yayımcı* olarak adlandırılır ve olayı alan (veya *işleyen*) sınıflar *aboneler*olarak adlandırılır.  
  
 Tipik C# bir Windows Forms veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından oluşturulan olaylara abone olursunuz. Bir denetimin yayımladığı olaylara gözatabilmek ve işlemek istediklerinizi seçmek için Visual C# tümleşik geliştirme ortamı 'Nı (IDE) kullanabilirsiniz. IDE, otomatik olarak boş bir olay işleyici yöntemi ve olaya abone olmak için kod eklemenin kolay bir yolunu sunar. Daha fazla bilgi için bkz. [nasıl yapılır: olaylara abone olma ve aboneliği kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Olaylara Genel Bakış  
 Olaylar aşağıdaki özelliklere sahiptir:  
  
- Yayımcı bir olayın ne zaman gerçekleştiğini belirler; aboneler olaya yanıt olarak hangi eylemin alınacağını tespit ediyor.  
  
- Bir olay birden çok aboneye sahip olabilir. Bir abone birden çok yayımcıların birden çok olayını işleyebilir.  
  
- Abone olmayan olaylar hiçbir şekilde oluşturulmaz.  
  
- Olaylar genellikle grafik kullanıcı arabirimlerinde düğme tıklamaları veya menü seçimleri gibi kullanıcı eylemlerini işaret etmek için kullanılır.  
  
- Bir olayda birden çok abone olduğunda, olay işleyicileri bir olay oluşturulduğunda zaman uyumlu olarak çağrılır. Olayları zaman uyumsuz olarak çağırmak için bkz. [zaman uyumlu yöntemleri zaman uyumsuz çağırma](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- .NET Framework sınıf kitaplığında olaylar, <xref:System.EventHandler> temsilciyi ve <xref:System.EventArgs> temel sınıfını temel alır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
- [Nasıl yapılır: Olaylara Abone Olma ve Aboneliği Kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [Nasıl yapılır: .NET Framework Yönergeleriyle Uyumlu Olayları Yayımlama](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma](./how-to-raise-base-class-events-in-derived-classes.md)  
  
- [Nasıl yapılır: arabirim olaylarını uygulama](./how-to-implement-interface-events.md)  
  
- [Nasıl yapılır: Özel Olay Erişimcilerini Uygulama](./how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Olaylar](~/_csharplang/spec/classes.md#events) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 3,0 tanımlama kitabı, üçüncü sürüm 'de [Temsilciler, olaylar ve lambda ifadeleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [ C# : 3,0 programcılar için C# 250 ' den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Öğrenme C# 3,0 C# ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29) ' deki [Temsilciler ve olaylar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) : 3,0 temelleri ana  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>
- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](../delegates/index.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
