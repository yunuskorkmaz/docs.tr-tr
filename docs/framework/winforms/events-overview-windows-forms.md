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
ms.openlocfilehash: 4abcf20b851f349a2b5df78c1fe1d15f729a5462
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344998"
---
# <a name="events-overview-windows-forms"></a>Olaylara Genel Bakış (Windows Forms)
Bir olay, kod içinde "tanıtıcı" veya "işleme" için yanıt verebildiği bir eylemdir. Olaylar, fareyi tıklatmak veya bir tuşa basmak gibi bir kullanıcı eylemiyle oluşturulabilir; program koduna göre; veya sistem.

 Olay odaklı uygulamalar, bir olaya yanıt olarak kod yürütür. Her form ve denetim, programlama yoluyla programlayabilirsiniz, önceden tanımlanmış bir olay kümesi sunar. Bu olaylardan biri gerçekleşirse ve ilişkili olay işleyicisinde kod varsa, bu kod çağrılır.

 Bir nesne tarafından gerçekleştirilen olay türleri farklılık gösterir, ancak çoğu denetim için çok sayıda tür vardır. Örneğin, çoğu nesne <xref:System.Windows.Forms.Control.Click> olayını işler. Kullanıcı bir formu tıklarsa, formun <xref:System.Windows.Forms.Control.Click> olay işleyicisindeki kod yürütülür.

> [!NOTE]
> Birçok olay diğer olaylarla birlikte oluşur. Örneğin, <xref:System.Windows.Forms.Control.DoubleClick> olayın meydana geldiğini <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseUp>ve <xref:System.Windows.Forms.Control.Click> olayları meydana gelir.

 Bir olayı yükseltme ve kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../../standard/events/index.md).

## <a name="delegates-and-their-role"></a>Temsilciler ve rolleri
 Temsilciler, olay işleme mekanizmaları oluşturmak için .NET Framework içinde yaygın olarak kullanılan sınıflardır. Genellikle görsel C++ ve diğer nesne yönelimli dillerde kullanılan işlev işaretçilerine kabaca eşitlenmiş temsilciler. Ancak işlev işaretçilerinden farklı olarak, temsilciler nesne odaklı, tür açısından güvenli ve güvenlidir. Ayrıca, bir işlev işaretçisinin yalnızca belirli bir işleve yönelik bir başvuru içerdiği durumlarda, bir temsilci bir nesne başvurusundan oluşur ve nesne içindeki bir veya daha fazla yönteme başvurur.

 Bu olay modeli, olayları işlemek için kullanılan yöntemlere bağlamak için *temsilcileri* kullanır. Temsilci, diğer sınıfların bir işleyici yöntemi belirterek olay bildirimine kaydolmalarını sağlar. Olay gerçekleştiğinde, temsilci, bağlantılı yöntemi çağırır. Temsilcilerin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [Olaylar](../../standard/events/index.md).

Temsilciler tek bir yönteme veya çok noktaya yayın olarak adlandırılan birden fazla yönteme bağlanabilir. Bir olay için temsilci oluştururken, sizin (veya Windows) genellikle bir çok noktaya yayın olayı oluşturur. Nadir bir özel durum, her olay için birden çok kez mantıksal olarak tekrarlanacak belirli bir yordam (iletişim kutusu görüntüleme gibi) ile sonuçlanan bir olay olabilir. Çok noktaya yayın temsilcisi oluşturma hakkında daha fazla bilgi için bkz. [temsilcileri birleştirme (çok noktaya yayın temsilcileri)](../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

 Çok noktaya yayın temsilcisi, bağlandığı yöntemlerin çağırma listesini tutar. Çok noktaya yayın temsilcisi, çağırma listesine bir yöntem eklemek için bir <xref:System.Delegate.Combine%2A> yöntemini ve bunu kaldırmak için bir <xref:System.Delegate.Remove%2A> yöntemini destekler.

 Uygulama tarafından bir olay kaydedildiğinde denetim, olayı bu olay için temsilciyi çağırarak başlatır. İçindeki temsilci, sırasıyla, bağlantılı yöntemi çağırır. En yaygın durumda (çok noktaya yayın temsilcisi), temsilci, tek-çok bildirimi sağlayan çağrı listesindeki her bir bağlantılı yöntemi çağırır. Bu strateji, denetimin olay bildirimi için hedef nesnelerin bir listesini tutması gerekmediği anlamına gelir; temsilci tüm kaydı ve bildirimleri işler.

 Temsilciler Ayrıca birden çok olayın aynı yönteme bağlanmasını sağlar ve çoktan bire bir bildirime izin verir. Örneğin, bir düğme tıklama olayı ve bir menü komutu – tıklama olayı aynı temsilciyi çağırabilir, daha sonra bu ayrı olayları aynı şekilde işlemek için tek bir yöntem çağırır.

 Temsilcilerle kullanılan bağlama mekanizması dinamiktir: bir temsilci çalışma zamanında, imzası olay işleyicisiyle eşleşen herhangi bir yönteme bağlanabilir. Bu özellikle, bir koşula bağlı olarak bağlı yöntemi ayarlayabilir veya değiştirebilir ve bir denetime dinamik olarak bir olay işleyicisi iliştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
