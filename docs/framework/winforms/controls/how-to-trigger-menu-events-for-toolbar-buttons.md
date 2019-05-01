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
ms.openlocfilehash: 0f5afde1cc0be772baff373c84c82f81df284b9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785833"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 Windows Form özelliklerinizi bir <xref:System.Windows.Forms.ToolBar> denetimi araç çubuğu düğmeleri ile hangi kullanıcı düğmesi bilmek isteyeceksiniz.  
  
 Üzerinde <xref:System.Windows.Forms.ToolBar.ButtonClick> olayı <xref:System.Windows.Forms.ToolBar> denetimi değerlendirme <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> özelliği <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> sınıfı. Aşağıdaki örnekte, hangi düğmesine tıklandığını belirten bir ileti kutusu gösterilir. Ayrıntılar için bkz <xref:System.Windows.Forms.MessageBox>.  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Forms.ToolBar> Windows Form denetimi eklendi.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Araç çubuğundaki Click olayını işlemek için  
  
1. Bir yordamda araç çubuğu düğmelerine ekleme <xref:System.Windows.Forms.ToolBar> denetimi.  
  
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
  
2. İçin bir olay işleyicisi ekleme <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ButtonClick> olay. Kullanım deyimi değiştirme ve <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> tıklandığını araç çubuğu düğmesi belirlemek için sınıf. Bunu temel alarak, uygun bir ileti kutusu gösterir.  
  
    > [!NOTE]
    >  Bir ileti kutusu yalnızca, bu örnekte bir yer tutucu olarak kullanılıyor. Araç çubuğu düğmeleri tıklatıldığında yürütülecek diğer kod eklemekten çekinmeyin.  
  
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
- [Nasıl yapılır: Bir ToolBar denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md)
- [Nasıl yapılır: ToolBar düğmesi için simge tanımlama](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
