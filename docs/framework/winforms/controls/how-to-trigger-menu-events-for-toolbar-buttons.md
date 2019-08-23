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
ms.openlocfilehash: 381b8ba08db6ff5bb817c9c89008dacb1085ac1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956032"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip>  
  
 Windows formunuz araç çubuğu düğmeleriyle bir <xref:System.Windows.Forms.ToolBar> denetim özelliklarsa, kullanıcının hangi düğmeyi tıkladığı hakkında bilgi edinmek isteyeceksiniz.  
  
 <xref:System.Windows.Forms.ToolBar.ButtonClick> Denetiminolayında<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> , sınıfının<xref:System.Windows.Forms.ToolBarButtonClickEventArgs> özelliğini değerlendirebilirsiniz. <xref:System.Windows.Forms.ToolBar> Aşağıdaki örnekte, hangi düğmenin tıklandığını gösteren bir ileti kutusu gösterilir. Ayrıntılar için bkz <xref:System.Windows.Forms.MessageBox>.  
  
 Aşağıdaki örnek, bir denetimin <xref:System.Windows.Forms.ToolBar> bir Windows formuna eklendiğini varsayar.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Bir araç çubuğunda tıklama olayını işlemek için  
  
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
  
2. <xref:System.Windows.Forms.ToolBar> Denetimin olayıiçinbirolayişleyicisiekleyin.<xref:System.Windows.Forms.ToolBar.ButtonClick> Tıklanan araç çubuğu düğmesini belirleyebilmek için <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> bir Case anahtarlama ifadesini ve sınıfını kullanın. Buna bağlı olarak, uygun bir ileti kutusu görüntüleyin.  
  
    > [!NOTE]
    > Bu örnekte yalnızca bir yer tutucu olarak bir ileti kutusu kullanılır. Araç çubuğu düğmelerine tıklandığında yürütülecek diğer kodu ekleyebilirsiniz.  
  
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
- [Nasıl yapılır: Araç çubuğu denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md)
- [Nasıl yapılır: Bir araç çubuğu düğmesi için simge tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
