---
title: "Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme"
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
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bbdf2ec4f2353662f1077b9d95966e0a2ebd316
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme
Herhangi bir Windows formunda tanımladığınız bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetim. Her kullanıcının hangi bağımsız olarak formunda diğer denetimi odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında. Bu tür bir düğme genellikle hızlı bir şekilde bir işlem için herhangi bir eylem kaydetmeden çıkmak kullanıcının etkinleştirmek için programlanmış.  
  
### <a name="to-designate-the-cancel-button"></a>İptal düğmesi atamak için  
  
1.  Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğine uygun <xref:System.Windows.Forms.Button> denetim.  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Düğme denetimine genel bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows Forms düğme denetimi seçmenin yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Windows Forms düğmesini kabul et düğmesi olarak belirtme](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Düğme denetimi](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
