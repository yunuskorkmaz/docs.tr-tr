---
title: "Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama"
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
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967030"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Tek Olay İşleyicisine Birden Fazla Olay Bağlama
Uygulama tasarımınızı, bunu tek olay işleyicisine birden fazla olaylar için kullanın veya sahip birden çok olayı aynı yordamı gerçekleştirmek için gerekli bulabilirsiniz. Örneğin, genellikle bir güçlü zaman-bir menü komutu, bunlar aynı işlevselliği göstermek, form üzerindeki bir düğme gibi aynı olay yükseltmek için koruyucu olur. Özellikler penceresinde olayların görünümünü kullanarak bunu yapabilirsiniz C# veya bu adı kullanıyor `Handles` anahtar sözcüğü ve **sınıf adı** ve **yöntem adı** Visual Basic Kod Düzenleyicisi'nde açılır kutuları.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Visual Basic'te tek olay işleyicisine birden fazla olay bağlama için  
  
1. Formun sağ tıklatın ve seçin **kodu görüntüle**.  
  
2. Gelen **sınıf adı** açılan kutusunda, olay işleyicisi işlemek istediğiniz denetimlerin birini seçin.  
  
3. Gelen **yöntem adı** açılan kutusunda, aşağıdakilerden birini işlemek için olay işleyicisi istediğiniz olayları seçin.  
  
4. Kod Düzenleyicisi, uygun bir olay işleyicisi ekler ve yöntemi içinde ekleme noktasını yerleştirir. Aşağıdaki örnekte olduğu <xref:System.Windows.Forms.Control.Click> olayı <xref:System.Windows.Forms.Button> denetimi.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Ekleme için işlenen istediğiniz diğer olaylar `Handles` yan tümcesi.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. Uygun kodu olay işleyicisine ekleyin.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>C'de tek olay işleyicisine birden fazla olay bağlama için\#
  
1. Bir olay işleyicisi bağlanmak istediğiniz denetimi seçin.  
  
2. Özellikler penceresinde tıklayın **olayları** düğmesine (![olayları düğmesi](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3. Kullanmak istediğiniz olayın adına tıklayın.  
  
4. Olay adının yanındaki değeri bölümünde, kullanmak istediğiniz olay yöntem imzasını eşleşen var olan olay işleyicilerinin bir listesini görüntülemek için açılan düğmesine tıklayın.  
  
5. Uygun bir olay işleyicisi listeden seçin.  
  
     Kodu varolan olay işleyicisine olaya bağlamak için forma eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
