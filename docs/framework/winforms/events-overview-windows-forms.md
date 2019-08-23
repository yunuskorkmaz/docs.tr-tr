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
ms.openlocfilehash: 92942066b5f08ada0154781ae54b5d8494944ca1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963471"
---
# <a name="events-overview-windows-forms"></a>Olaylara Genel Bakış (Windows Forms)
Bir olay, kod içinde "tanıtıcı" veya "işleme" için yanıt verebildiği bir eylemdir. Olaylar, fareyi tıklatmak veya bir tuşa basmak gibi bir kullanıcı eylemiyle oluşturulabilir; program koduna göre; veya sistem.

 Olay odaklı uygulamalar, bir olaya yanıt olarak kod yürütür. Her form ve denetim, programlama yoluyla programlayabilirsiniz, önceden tanımlanmış bir olay kümesi sunar. Bu olaylardan biri gerçekleşirse ve ilişkili olay işleyicisinde kod varsa, bu kod çağrılır.

 Bir nesne tarafından gerçekleştirilen olay türleri farklılık gösterir, ancak çoğu denetim için çok sayıda tür vardır. Örneğin, çoğu nesne bir <xref:System.Windows.Forms.Control.Click> olayı işleymeyecektir. Kullanıcı bir formu tıklarsa, formun <xref:System.Windows.Forms.Control.Click> olay işleyicisindeki kod yürütülür.

> [!NOTE]
> Birçok olay diğer olaylarla birlikte oluşur. Örneğin <xref:System.Windows.Forms.Control.DoubleClick> , olay gerçekleşme <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp>sırasında,, ve <xref:System.Windows.Forms.Control.Click> olayları oluşur.

 Bir olayı yükseltme ve kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Temsilciler ve rolleri
 Temsilciler, olay işleme mekanizmaları oluşturmak için .NET Framework içinde yaygın olarak kullanılan sınıflardır. Genellikle görsel C++ ve diğer nesne yönelimli dillerde kullanılan işlev işaretçilerine kabaca eşitlenmiş temsilciler. Ancak işlev işaretçilerinden farklı olarak, temsilciler nesne odaklı, tür açısından güvenli ve güvenlidir. Ayrıca, bir işlev işaretçisinin yalnızca belirli bir işleve yönelik bir başvuru içerdiği durumlarda, bir temsilci bir nesne başvurusundan oluşur ve nesne içindeki bir veya daha fazla yönteme başvurur.

 Bu olay modeli, olayları işlemek için kullanılan yöntemlere bağlamak için *temsilcileri* kullanır. Temsilci, diğer sınıfların bir işleyici yöntemi belirterek olay bildirimine kaydolmalarını sağlar. Olay gerçekleştiğinde, temsilci, bağlantılı yöntemi çağırır. Temsilcilerin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [Olaylar](../../standard/events/index.md).

 Temsilciler tek bir yönteme veya çok noktaya yayın olarak adlandırılan birden fazla yönteme bağlanabilir. Bir olay için temsilci oluştururken, sizin (veya Windows) genellikle bir çok noktaya yayın olayı oluşturur. Nadir bir özel durum, her olay için birden çok kez mantıksal olarak tekrarlanacak belirli bir yordam (iletişim kutusu görüntüleme gibi) ile sonuçlanan bir olay olabilir. Çok noktaya yayın temsilcisi oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Temsilcileri birleştirin (çok noktaya yayın](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)temsilcileri).

 Çok noktaya yayın temsilcisi, bağlandığı yöntemlerin çağırma listesini tutar. Çok noktaya yayın temsilcisi, <xref:System.Delegate.Combine%2A> çağırma listesine bir yöntem ekleme <xref:System.Delegate.Remove%2A> ve bunu kaldırma yöntemine yönelik bir yöntemi destekler.

 Uygulama tarafından bir olay kaydedildiğinde denetim, olayı bu olay için temsilciyi çağırarak başlatır. İçindeki temsilci, sırasıyla, bağlantılı yöntemi çağırır. En yaygın durumda (çok noktaya yayın temsilcisi), temsilci, tek-çok bildirimi sağlayan çağrı listesindeki her bir bağlantılı yöntemi çağırır. Bu strateji, denetimin olay bildirimi için hedef nesnelerin bir listesini tutması gerekmediği anlamına gelir; temsilci tüm kaydı ve bildirimleri işler.

 Temsilciler Ayrıca birden çok olayın aynı yönteme bağlanmasını sağlar ve çoktan bire bir bildirime izin verir. Örneğin, bir düğme tıklama olayı ve bir menü komutu – tıklama olayı aynı temsilciyi çağırabilir, daha sonra bu ayrı olayları aynı şekilde işlemek için tek bir yöntem çağırır.

 Temsilcilerle kullanılan bağlama mekanizması dinamiktir: bir temsilci çalışma zamanında, imzası olay işleyicisiyle eşleşen herhangi bir yönteme bağlanabilir. Bu özellikle, bir koşula bağlı olarak bağlı yöntemi ayarlayabilir veya değiştirebilir ve bir denetime dinamik olarak bir olay işleyicisi iliştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
