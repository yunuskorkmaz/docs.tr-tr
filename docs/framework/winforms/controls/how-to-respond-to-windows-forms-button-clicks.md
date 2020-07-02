---
title: Düğme Tıklamalarına Yanıt Verme
description: Windows Forms düğme tıklamalarına nasıl yanıt verileceğini öğrenin. Windows Forms düğme denetiminin en temel kullanımı, düğme tıklandığında bazı kodları çalıştırkullanmaktır.
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
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619734"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme
Windows Forms denetiminin en temel kullanımı, <xref:System.Windows.Forms.Button> düğme tıklandığında bazı kodları çalıştırkullanmaktır.  
  
 Bir <xref:System.Windows.Forms.Button> denetime tıkladığınızda <xref:System.Windows.Forms.Control.MouseEnter> ,, ve olayları gibi birçok farklı olay da oluşturulur <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> . Bu ilgili olaylar için olay işleyicileri eklemek istiyorsanız, eylemlerinin çakışmadığından emin olun. Örneğin, düğmeye tıkladığınızda kullanıcının bir metin kutusuna girdiği bilgiler temizlenir, fare işaretçisini düğme üzerinde duraklatmak, bu, varolmayan bilgilerin bulunduğu bir araç ipucunu göstermemelidir.  
  
 Kullanıcı denetime çift tıkladenerse <xref:System.Windows.Forms.Button> , her tıklama ayrı olarak işlenir; diğer bir deyişle, denetim çift tıklama olayını desteklemez.  
  
### <a name="to-respond-to-a-button-click"></a>Düğme tıklamasına yanıt vermek için  
  
- Düğme, `Click` <xref:System.EventHandler> çalıştırılacak kodu yazın. `Button1_Click`denetime bağlanmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
- [Windows Forms Düğme Denetimi Seçmenin Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Düğme Denetimi](button-control-windows-forms.md)
