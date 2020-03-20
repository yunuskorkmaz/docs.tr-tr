---
title: 'Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182071"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.ToolStrip> denetimin <xref:System.Windows.Forms.ToolBar> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.ToolBar> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.  
  
 Windows Form'unuzda <xref:System.Windows.Forms.ToolBar> araç çubuğu düğmeleriyle bir denetim varsa, kullanıcının hangi düğmeyi tıklattıklarını bilmek istersiniz.  
  
 Denetim <xref:System.Windows.Forms.ToolBar.ButtonClick> durumunda, sınıfın özelliğini <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> değerlendirebilirsiniz. <xref:System.Windows.Forms.ToolBar> Aşağıdaki örnekte, hangi düğmenin tıklandığını belirten bir ileti kutusu gösterilir. Ayrıntılar için bkz. <xref:System.Windows.Forms.MessageBox>.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.ToolBar> windows formuna bir denetim eklendiğini varsayar.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Araç çubuğundaki Click olayını işlemek için  
  
1. Bir yordamda, <xref:System.Windows.Forms.ToolBar> denetime araç çubuğu düğmeleri ekleyin.  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. Denetimolayı için bir <xref:System.Windows.Forms.ToolBar> olay işleyicisi <xref:System.Windows.Forms.ToolBar.ButtonClick> ekleyin. Tıklanan araç çubuğu <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> düğmesini belirlemek için büyük/küçük harf anahtarlama deyimini ve sınıfı kullanın. Buna dayanarak, uygun bir ileti kutusu gösterin.  
  
    > [!NOTE]
    > İleti kutusu bu örnekte yalnızca yer tutucu olarak kullanılıyor. Araç çubuğu düğmeleri tıklandığında yürütmek için başka kod eklemekten çekinmeyin.  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [Nasıl yapılır: Bir ToolBar Denetimine Düğme Ekleme](how-to-add-buttons-to-a-toolbar-control.md)
- [Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
