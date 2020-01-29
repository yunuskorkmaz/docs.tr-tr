---
title: Düğme Tıklamalarına Yanıt Verme
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
ms.openlocfilehash: dd6cf75a316257c86a23b44a818422336c12aa67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735722"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme
Windows Forms <xref:System.Windows.Forms.Button> denetiminin en temel kullanımı, düğme tıklandığında bazı kodları çalıştırmıştır.  
  
 <xref:System.Windows.Forms.Button> denetimine tıkladığınızda, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>ve <xref:System.Windows.Forms.Control.MouseUp> olayları gibi çeşitli olaylar da oluşturulur. Bu ilgili olaylar için olay işleyicileri eklemek istiyorsanız, eylemlerinin çakışmadığından emin olun. Örneğin, düğmeye tıkladığınızda kullanıcının bir metin kutusuna girdiği bilgiler temizlenir, fare işaretçisini düğme üzerinde duraklatmak, bu, varolmayan bilgilerin bulunduğu bir araç ipucunu göstermemelidir.  
  
 Kullanıcı <xref:System.Windows.Forms.Button> denetimine çift tıkladenerse, her tıklama ayrı olarak işlenir; diğer bir deyişle, denetim çift tıklama olayını desteklemez.  
  
### <a name="to-respond-to-a-button-click"></a>Düğme tıklamasına yanıt vermek için  
  
- Düğmenin `Click`, çalıştırılacak kodu yazın <xref:System.EventHandler>. `Button1_Click` denetime bağlanmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
