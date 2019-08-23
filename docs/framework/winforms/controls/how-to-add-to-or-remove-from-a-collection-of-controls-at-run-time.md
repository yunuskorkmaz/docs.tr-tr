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
ms.openlocfilehash: 87ad4c957ac5b99438684d398a0c5ad7d126c406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925039"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Nasıl yapılır: Çalışma Zamanında bir Denetimler Koleksiyonuna Ekleme veya Kaldırma
Uygulama geliştirmede ortak görevler, formlarınızda ( <xref:System.Windows.Forms.Panel> veya <xref:System.Windows.Forms.GroupBox> denetimi gibi) herhangi bir kapsayıcı denetimine denetim ekleme ve denetimleri kaldırma (hatta formun kendisi gibi). Tasarım zamanında, denetimler doğrudan bir panel veya grup kutusu üzerinde sürüklenebilir. Çalışma zamanında, bu denetimler, bunlara hangi `Controls` denetimlerin yerleştirileceğini izleyen bir koleksiyonu korur.  
  
> [!NOTE]
> Aşağıdaki kod örneği, içindeki bir denetim koleksiyonunu tutan tüm denetimler için geçerlidir.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Bir koleksiyona programlı bir denetim eklemek için  
  
1. Eklenecek denetimin bir örneğini oluşturun.  
  
2. Yeni denetimin özelliklerini ayarlayın.  
  
3. Denetimi üst denetimin `Controls` koleksiyonuna ekleyin.  
  
     Aşağıdaki kod örneği, <xref:System.Windows.Forms.Button> denetimin bir örneğinin nasıl oluşturulacağını gösterir. <xref:System.Windows.Forms.Panel> Denetim içeren bir form ve `NewPanelButton_Click`oluşturulmakta olan düğme için olay işleme yönteminin zaten var olduğunu gerektirir.  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Bir koleksiyondan denetimleri programlı bir şekilde kaldırmak için  
  
1. Olay işleyicisini olaydan kaldırın. Visual Basic ' de [RemoveHandler deyimin](../../../visual-basic/language-reference/statements/removehandler-statement.md) anahtar sözcüğünü kullanın; içinde C# [-= işlecini](../../../csharp/language-reference/operators/subtraction-operator.md)kullanın.  
  
2. İstenen denetimi`Controls` panel koleksiyonundan silmek için yöntemini kullanın. `Remove`  
  
3. Denetim tarafından kullanılan tüm kaynakları serbest bırakmak için yönteminiçağırın.<xref:System.Windows.Forms.Control.Dispose%2A>  
  
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
