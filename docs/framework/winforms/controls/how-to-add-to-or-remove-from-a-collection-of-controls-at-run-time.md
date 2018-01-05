---
title: "Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma"
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
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 548ca8d682ffea6f2afa03124719a1bb5097a2fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma
Uygulama geliştirme, ortak görevler için denetimler ekleme ve herhangi bir kapsayıcı denetimi, formlarında denetimleri kaldırma (gibi <xref:System.Windows.Forms.Panel> veya <xref:System.Windows.Forms.GroupBox> denetim veya formun kendisi bile). Tasarım zamanında denetimleri doğrudan Masası veya grup kutusu sürüklenebilir. Bu denetimler çalışma zamanında korumak bir `Controls` hangi denetimlerin üzerine yerleştirilen izler koleksiyonu.  
  
> [!NOTE]
>  Aşağıdaki kod örneğinde içindeki denetimler koleksiyonuna tutar herhangi bir denetimi uygular.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Bir denetim program aracılığıyla bir koleksiyona eklemek için  
  
1.  Eklenecek denetim örneği oluşturun.  
  
2.  Yeni denetim özelliklerini ayarlayın.  
  
3.  Denetimine ekleme `Controls` üst denetim koleksiyonu.  
  
     Aşağıdaki kod örneğinde bir örneğini oluşturmak gösterilmiştir <xref:System.Windows.Forms.Button> denetim. Bir formla gerektiren bir <xref:System.Windows.Forms.Panel> denetimi ve bu düğme için olay işleme yöntemi oluşturuluyor, `NewPanelButton_Click`, zaten mevcut.  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Denetimlerini programlı olarak koleksiyondan kaldırmak için  
  
1.  Olay işleyicisi olaydan kaldırın. İçinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], kullanın [RemoveHandler deyimi](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcüğü; [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], kullanın [-= işleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
2.  Kullanım `Remove` istenen Denetim Masası'ndan 's silmek için yöntemi `Controls` koleksiyonu.  
  
3.  Çağrı <xref:System.Windows.Forms.Control.Dispose%2A> denetimi tarafından kullanılan tüm kaynakları serbest bırakmak için yöntem.  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Panel>  
 [Panel Denetimi](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
