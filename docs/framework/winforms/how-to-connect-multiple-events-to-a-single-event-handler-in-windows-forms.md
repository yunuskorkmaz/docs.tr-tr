---
title: 'Nasıl yapılır: birden çok olayı tek bir olay Işleyicisine bağlama'
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
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739599"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama
Uygulama tasarımınızda, birden çok olay için tek bir olay işleyicisi kullanmak veya aynı yordamı gerçekleştirmek için birden çok olay olması gerektiğini fark edebilirsiniz. Örneğin, bir menü komutuna sahip olacak bir menü komutunun aynı işlevi, aynı işlevselliğe sahip olmaları durumunda sizin formunuzdaki bir düğmeyle oluşturması için genellikle güçlü bir zaman tasarrufu vardır. Bunu, içindeki C# Özellikler penceresi olaylar görünümünü kullanarak veya `Handles` anahtar sözcüğünü ve Visual Basic kod düzenleyicisinde **sınıf adı** ve **Yöntem adı** açılır kutularını kullanarak yapabilirsiniz.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Birden çok olayı Visual Basic bir tek olay işleyicisine bağlamak için  
  
1. Forma sağ tıklayın ve **kodu görüntüle**' yi seçin.  
  
2. **Sınıf adı** açılan kutusundan, olay işleyicisi tutamacına sahip olmasını istediğiniz denetimlerden birini seçin.  
  
3. **Yöntem adı** açılan kutusundan, olay işleyicisinin işlemesini istediğiniz olaylardan birini seçin.  
  
4. Kod Düzenleyicisi, uygun olay işleyicisini ekler ve ekleme noktasını yönteminin içine yerleştirir. Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> denetimi için <xref:System.Windows.Forms.Control.Click> olayıdır.  
  
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
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Birden çok olayı C\# tek bir olay işleyicisine bağlamak için
  
1. Bir olay işleyicisine bağlamak istediğiniz denetimi seçin.  
  
2. Özellikler penceresi, **Olaylar** düğmesine (![Olaylar düğmesi](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")) tıklayın.  
  
3. İşlemek istediğiniz olayın adına tıklayın.  
  
4. Olay adının yanındaki değer bölümünde, işlemek istediğiniz olayın yöntem imzasıyla eşleşen mevcut olay işleyicilerinin listesini göstermek için açılan düğmeye tıklayın.  
  
5. Listeden uygun olay işleyicisini seçin.  
  
     Olayı, var olan olay işleyicisine bağlamak için forma eklenecek.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
