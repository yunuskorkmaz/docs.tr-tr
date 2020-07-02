---
title: 'Nasıl yapılır: birden çok olayı tek bir olay Işleyicisine bağlama'
description: C# ' de Özellikler penceresi olay görünümünü kullanarak birden çok olayı Windows Forms ' de tek bir olay işleyicisine bağlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621892"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama
Uygulama tasarımınızda, birden çok olay için tek bir olay işleyicisi kullanmak veya aynı yordamı gerçekleştirmek için birden çok olay olması gerektiğini fark edebilirsiniz. Örneğin, bir menü komutuna sahip olacak bir menü komutunun aynı işlevi, aynı işlevselliğe sahip olmaları durumunda sizin formunuzdaki bir düğmeyle oluşturması için genellikle güçlü bir zaman tasarrufu vardır. Bunu, C# ' deki Özellikler penceresi olaylar görünümünü kullanarak veya `Handles` anahtar sözcüğünü ve Visual Basic kod Düzenleyicisi 'Ndeki **sınıf adı** ve **Yöntem adı** açılır kutularını kullanarak yapabilirsiniz.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Birden çok olayı Visual Basic bir tek olay işleyicisine bağlamak için  
  
1. Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.  
  
2. **Sınıf adı** açılan kutusundan, olay işleyicisi tutamacına sahip olmasını istediğiniz denetimlerden birini seçin.  
  
3. **Yöntem adı** açılan kutusundan, olay işleyicisinin işlemesini istediğiniz olaylardan birini seçin.  
  
4. Kod Düzenleyicisi, uygun olay işleyicisini ekler ve ekleme noktasını yönteminin içine yerleştirir. Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.Click> denetimin olayıdır <xref:System.Windows.Forms.Button> .  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. İstediğiniz diğer olayları `Handles` yan tümcesine ekleyin.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. Olay işleyicisine uygun kodu ekleyin.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Birden çok olayı C 'de tek bir olay işleyicisine bağlamak için\#
  
1. Bir olay işleyicisine bağlamak istediğiniz denetimi seçin.  
  
2. Özellikler penceresi, **Olaylar** düğmesine (![Olaylar düğmesi](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")) tıklayın.  
  
3. İşlemek istediğiniz olayın adına tıklayın.  
  
4. Olay adının yanındaki değer bölümünde, işlemek istediğiniz olayın yöntem imzasıyla eşleşen mevcut olay işleyicilerinin listesini göstermek için açılan düğmeye tıklayın.  
  
5. Listeden uygun olay işleyicisini seçin.  
  
     Olayı, var olan olay işleyicisine bağlamak için forma eklenecek.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
