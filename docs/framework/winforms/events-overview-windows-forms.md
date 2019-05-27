---
title: Olaylara Genel Bakış (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, event handling
- events [Windows Forms], about events
- delegates [Windows Forms], multicast
- delegates [Windows Forms], events and
- multicast event delegates
- Windows Forms controls, events
ms.assetid: 814a6a43-a312-4791-88d8-f75f9a4f8c4c
ms.openlocfilehash: fddb51bfe998c360ca418374b119ec12f25b0fad
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052289"
---
# <a name="events-overview-windows-forms"></a>Olaylara Genel Bakış (Windows Forms)
Bir olay yanıt verebilirsiniz bir eylem veya "handle" kodunu içerir. Olaylar, fareyle tıklamak veya bir tuşuna basmak gibi bir kullanıcı eylemi tarafından oluşturulabilir; Program kodu tarafından; veya sistemi.

 Olay temelli uygulamalar, bir olaya yanıt olarak bir kod yürütün. Her form ve denetim programlayabileceğiniz olayları önceden tanımlanmış bir dizi kullanıma sunar. Bu olaylardan biri gerçekleşene ve ilişkili olay işleyicisinde kodu ise, bu kodu çağrılır.

 Bir nesne tarafından oluşturulan olayları türlerini farklılık gösterir ancak birçok türü çoğu denetimlere ortaktır. Örneğin, çoğu nesneyi işleyecek bir <xref:System.Windows.Forms.Control.Click> olay. Bir kullanıcı bir form tıklarsa formun kod <xref:System.Windows.Forms.Control.Click> olay işleyicisi yürütülür.

> [!NOTE]
>  Diğer olaylarla birlikte birçok olayları oluşur. Örneğin, içinde course, <xref:System.Windows.Forms.Control.DoubleClick> gerçekleşmesini olay <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>, ve <xref:System.Windows.Forms.Control.Click> olaylar gerçekleşir.

 Bir olay yükseltilip tüketileceğini hakkında daha fazla bilgi için bkz. [olayları](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Temsilciler ve kendi rolleri
 Temsilciler .NET Framework içinde olay işleme mekanizmalarını oluşturmak için kullanılan sınıflardır. Temsilciler kabaca günleriyle işlev işaretçilerine, görselde kullanılan C++ ve diğer nesne yönelimli programlama dili. İşlev işaretçileri, ancak nesne yönelimli, tür kullanımı uyumlu ve güvenli temsilciler. Ayrıca, burada bir işlev işaretçisi yalnızca belirli bir işleve bir başvuru içerir bir temsilci bir nesneye bir başvuru oluşur ve nesnesi içinde bir veya daha fazla yöntemlere başvuruyor.

 Bu olay modeli kullanan *Temsilciler* bunları işlemek için kullanılan yöntemleri için olaylar bağlamak için. Temsilci işleyicisi yöntemi belirterek olay bildirimi için kaydetmek diğer sınıflar sağlar. Olay gerçekleştiğinde temsilci ilişkili yöntemi çağırır. Temsilcileri tanımlama hakkında daha fazla bilgi için bkz. [olayları](../../standard/events/index.md).

 Temsilciler, tek bir yöntemi veya çok noktaya yayın başvurulan birden çok yöntem bağlanabilir. Bir olay için temsilci oluştururken siz (veya Windows) genellikle çok noktaya yayın olay oluşturursunuz. Nadir bir özel durum, birden çok kez olay mantıksal olarak tekrarlayın değil belirli yordam (örneğin, bir iletişim kutusunu görüntüleme) sonuçlanır bir olay olabilir. Çok noktaya yayın temsilci oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Temsilcileri (çok noktaya yayın temsilcileri) birleştirme](~/docs/csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Çok noktaya yayın temsilci bir bağlı yöntemleri çağırma listesini tutar. Çok noktaya yayını destekleyen temsilci bir <xref:System.Delegate.Combine%2A> bir yöntem çağırma listesine eklemek için gereken yöntemini ve bir <xref:System.Delegate.Remove%2A> kaldırmak için yöntemi.

 Uygulama tarafından bir olay kaydedildiğinde, bu olay için temsilci çağırarak denetim olayı başlatır. Temsilci sırayla ilişkili yöntemi çağırır. (Bir çok noktaya yayın temsilcisi) en yaygın durumda temsilci her ilişkili yöntem çağırma listesinde sırasıyla bir-çok bildirim sağlayan çağırır. Bu strateji, denetimin olay bildirimi için hedef nesnelerin listesini korumak gerekmez anlamına gelir — tüm kaydı ve bildirimi temsilci işler.

 Temsilciler çok bir bildirim sağlayan aynı yönteme bağlı birden fazla olayın da etkinleştirin. Örneğin, bir düğme tıklama olayı ve bir menü komutu – tıklama olayı hem de daha sonra aynı şekilde bu ayrı olayları işlemek için tek bir yöntemi çağırır aynı temsilci çağırabilirsiniz.

 Temsilciler ile kullanılan bir bağlama mekanizması dinamik: bir temsilci imzası olan, olay işleyicisinin eşleşen herhangi bir yöntemi için çalışma zamanında bağlanabilir. Bu özellik ile ayarlayın veya bağımlı bir yöntem bir koşula bağlı ve bir olay işleyicisi bir denetimi dinamik olarak eklemek için değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
