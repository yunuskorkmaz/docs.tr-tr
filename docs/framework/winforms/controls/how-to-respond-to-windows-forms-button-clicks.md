---
title: "Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 923eb7d1b1b5b442ce897619253a958019b239a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme
Windows Forms en temel kullanımını <xref:System.Windows.Forms.Button> denetimidir düğmesine tıklandığında bazı kodlar çalıştırmak için.  
  
 Tıklatarak bir <xref:System.Windows.Forms.Button> denetimi de oluşturur diğer olayların sayısı gibi <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, ve <xref:System.Windows.Forms.Control.MouseUp> olaylar. Bu ilgili olayları için olay işleyicileri eklemek istiyorsanız, eylemlerini çakışmasını emin olun. Düğmesini tıklatarak bir metin kutusunda kullanıcının girdiği bilgileri temizler, örneğin, fare işaretçisini düğmenin üzerinde duraklatma şimdi varolmayan bilgileri olan bir araç ipucu görüntülemelidir değil.  
  
 Kullanıcı çift çalışırsa <xref:System.Windows.Forms.Button> denetim, her tıklatma ayrı ayrı işlenir; diğer bir deyişle, denetim çift olay desteklemiyor.  
  
### <a name="to-respond-to-a-button-click"></a>Yanıt için bir düğmeye tıklayın.  
  
-   Düğmenin içinde `Click` <xref:System.EventHandler> çalıştırmak için kod yazma. `Button1_Click`denetime bağlı olmalıdır. Daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri oluşturma çalıştırma süresi için Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düğme denetimine genel bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows Forms düğme denetimi seçmenin yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Düğme denetimi](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
