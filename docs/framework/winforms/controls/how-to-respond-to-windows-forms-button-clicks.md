---
title: 'Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: a10eaa3ea62df9301a53f5609b503bfabcb50a46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110077"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme
Bir Windows Forms en temel kullanımını <xref:System.Windows.Forms.Button> düğmesine tıklandığında, bazı kodlar çalıştırmak için denetimidir.  
  
 Tıklayarak bir <xref:System.Windows.Forms.Button> denetimi aynı zamanda oluşturur birkaç diğer olaylar gibi <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, ve <xref:System.Windows.Forms.Control.MouseUp> olayları. Bu ilgili olayları için olay işleyicileri eklemek istiyorsanız, eylemlerini çakışmasını emin olun. Düğmeye tıklandığında, metin kutusuna kullanıcının girdiği bilgileri temizler, örneğin, fare işaretçisi düğmenin üzerine duraklatma bir araç ipucu artık var olmayan bu bilgilerle görüntülemelidir değil.  
  
 Kullanıcının çift çalışırsa <xref:System.Windows.Forms.Button> denetimi her tıklatma ayrı ayrı işlenir; diğer bir deyişle, denetime çift tıklama olay desteklemez.  
  
### <a name="to-respond-to-a-button-click"></a>Yanıt vermek için bir düğmeye tıklayın.  
  
-   Düğmenin içinde `Click` <xref:System.EventHandler> çalıştırmak için kod yazın. `Button1_Click` denetime bağlı olmalıdır. Daha fazla bilgi için [nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
