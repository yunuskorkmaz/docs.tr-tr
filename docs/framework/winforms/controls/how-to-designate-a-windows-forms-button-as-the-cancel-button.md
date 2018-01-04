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
ms.workload: dotnet
ms.openlocfilehash: f3f61828b4c8b65ae984685610d6d8609953376a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Düğme Kontrolüne Genel Bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows Forms Düğme Kontrolü Seçme Yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Düğme Kontrolü](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
