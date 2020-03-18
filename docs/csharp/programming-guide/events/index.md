---
title: Etkinlikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712318"
---
# <a name="events-c-programming-guide"></a>Olaylar (C# Programlama Kılavuzu)
Olaylar, ilgi çekici bir şey oluştuğunda bir [sınıfın](../../language-reference/keywords/class.md) veya nesnenin diğer sınıfları veya nesneleri bildirmesini sağlar. Olayı gönderen (veya *yükselten)* sınıfa *yayımcı,* olayı alan (veya *işleyen)* sınıflara *abone*denir.  
  
Tipik bir C# Windows Formları veya Web uygulamasında, düğmeler ve liste kutuları gibi denetimler tarafından yükseltilen olaylara abone olursunuz. Denetimin yayımettiği olaylara göz atmak ve işlemek istediğiniz etkinlikleri seçmek için Visual C# tümleşik geliştirme ortamını (IDE) kullanabilirsiniz. IDE, boş bir olay işleyicisi yöntemini ve olaya abone olmak için kodu otomatik olarak eklemek için kolay bir yol sağlar. Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](./how-to-subscribe-to-and-unsubscribe-from-events.md)
  
## <a name="events-overview"></a>Olaylara Genel Bakış  
 Olaylar aşağıdaki özelliklere sahiptir:  
  
- Yayımcı, bir olayın ne zaman büyütülür olduğunu belirler; aboneler, olaya yanıt olarak hangi eylemin ne olduğunu belirler.  
  
- Bir olayın birden çok abonesi olabilir. Abone, birden çok yayımcıdan birden çok olayı işleyebilir.  
  
- Abonesi olmayan etkinlikler hiçbir zaman yükseltilmez.  
  
- Olaylar genellikle düğme tıklamaları veya grafik kullanıcı arabirimlerindeki menü seçimleri gibi kullanıcı eylemlerini işaret lemek için kullanılır.  
  
- Bir olayın birden çok abonesi olduğunda, bir olay yükseltildiğinde olay işleyicileri eşzamanlı olarak çağrılır. Olayları eşzamanlı olarak çağırmak için Eşzamanlı [Arama Yöntemlerini Eşitleme'ye](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)bakın.  
  
- .NET Framework sınıf kitaplığında olaylar <xref:System.EventHandler> temsilcive <xref:System.EventArgs> taban sınıfa dayanır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.  
  
- [Olaylara abone olma ve aboneliği kaldırma](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [.NET Framework Yönergeleriyle uyumlu olayları yayımlama](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Türetilmiş sınıflarda temel sınıf olayları oluşturma](./how-to-raise-base-class-events-in-derived-classes.md)

- [Arabirim olaylarını uygulama](./how-to-implement-interface-events.md)

- [Özel olay erişimcilerini uygulama](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Etkinlikler'e](~/_csharplang/spec/classes.md#events) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="featured-book-chapters"></a>Özel Kitap Bölümleri  
 C# 3.0 Yemek Kitabında [Delegeler, Etkinlikler ve Lambda İfadeleri,](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) [Üçüncü Baskı: C# 3.0 programcıları için 250'den fazla çözüm](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [C#](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) 3.0 Öğrenmede Delegeler ve [Etkinlikler: C# 3.0'ın temellerinde ustalaşma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventHandler>
- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](../delegates/index.md)
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
