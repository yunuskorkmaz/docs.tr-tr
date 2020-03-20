---
title: 'Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 369946581847b4bdcf8bc658aeb94b14c529061c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182283"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma
Uygulama geliştirmedeki yaygın görevler, formlarınızdaki herhangi bir kapsayıcı denetimine denetimler <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.GroupBox> eklemek ve denetimleri kaldırmaktır (örneğin, veya denetim, hatta formun kendisi). Tasarım zamanında, denetimler doğrudan bir panele veya grup kutusuna sürüklenebilir. Çalışma zamanında, bu denetimler, üzerlerine hangi denetimlerin yerleştirildiğini izleyen bir `Controls` koleksiyon tutar.  
  
> [!NOTE]
> Aşağıdaki kod örneği, içindeki denetimkoleksiyonunu koruyan tüm denetimler için geçerlidir.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Koleksiyona denetim eklemek için programlı olarak  
  
1. Eklenecek denetimin bir örneğini oluşturun.  
  
2. Yeni denetimin özelliklerini ayarlayın.  
  
3. Denetimi üst denetimin `Controls` koleksiyonuna ekleyin.  
  
     Aşağıdaki kod örneği, <xref:System.Windows.Forms.Button> denetimin bir örneğinin nasıl oluşturulabildiğini gösterir. Bir denetimiçeren bir <xref:System.Windows.Forms.Panel> form gerektirir ve oluşturulan düğme için olay `NewPanelButton_Click`işleme yöntemi zaten vardır.  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Denetimleri koleksiyondan programlı olarak kaldırmak için  
  
1. Olay işleyicisini olaydan kaldırın. Visual Basic'te [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcük anahtar sözcüklerini kullanın; C#'da [-= işleci](../../../csharp/language-reference/operators/subtraction-operator.md)kullanın.  
  
2. Panelin `Remove` `Controls` koleksiyonundan istenen denetimi silmek için yöntemi kullanın.  
  
3. Denetim <xref:System.Windows.Forms.Control.Dispose%2A> tarafından kullanılan tüm kaynakları serbest bırakmak için yöntemi arayın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Panel>
- [Panel Denetimi](panel-control-windows-forms.md)
