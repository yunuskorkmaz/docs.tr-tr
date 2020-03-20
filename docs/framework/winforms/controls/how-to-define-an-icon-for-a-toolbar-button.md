---
title: 'Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- buttons [Windows Forms], icons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: 84db98b4-8566-49ce-b2c8-1fd66a5eb3a0
ms.openlocfilehash: 84c67c7d2584390ba3e48cb83820c65c6bb45d1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182203"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama
> [!NOTE]
> Denetim, <xref:System.Windows.Forms.ToolStrip> denetimin <xref:System.Windows.Forms.ToolBar> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.ToolBar> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.  
  
 <xref:System.Windows.Forms.ToolBar>düğmeler, kullanıcılar tarafından kolay tanımlama için içlerindeki simgeleri görüntüleyebilir. Bu, [ImageList Bileşeni](imagelist-component-windows-forms.md) bileşenine görüntü ekleyerek ve bileşenle <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> denetimle ilişkilendirilerek elde edilir.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Araç çubuğu düğmesi için simgeyi programlı olarak ayarlamak için  
  
1. Bir yordamda, bir <xref:System.Windows.Forms.ImageList> bileşeni ve <xref:System.Windows.Forms.ToolBar> denetimi anında yerleştirin.  
  
2. Aynı yordamda, <xref:System.Windows.Forms.ImageList> bileşene bir görüntü atayın.  
  
3. Aynı yordamda, <xref:System.Windows.Forms.ImageList> denetimi denetime <xref:System.Windows.Forms.ToolBar> atayın ve <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> tek tek araç çubuğu düğmelerinin özelliğini atayın.  
  
     Aşağıdaki kod örneğinde, görüntünün konumu için ayarlanan yol **Belgelerim** klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğinizden, bu işlem yapılır. Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır. Aşağıdaki <xref:System.Windows.Forms.PictureBox> örnekte, denetimzaten eklenmiştir.  
  
     Yukarıdaki adımları izleyerek, aşağıda görüntülenen benzer kod yazmış olmalıdır.  
  
    ```vb  
    Public Sub InitializeMyToolBar()  
    ' Instantiate an ImageList component and a ToolBar control.  
       Dim ToolBar1 as New ToolBar  
       Dim ImageList1 as New ImageList  
    ' Assign an image to the ImageList component.  
    ' You should replace the bold image  
    ' in the sample below with an icon of your own choosing.  
       Dim myImage As System.Drawing.Image = _
          Image.FromFile Image.FromFile _  
          (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.Personal) _  
          & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    ' Create a ToolBarButton.  
       Dim ToolBarButton1 As New ToolBarButton()  
    ' Add the ToolBarButton to the ToolBar.  
       ToolBar1.Buttons.Add(toolBarButton1)  
    ' Assign an ImageList to the ToolBar.  
       ToolBar1.ImageList = ImageList1  
    ' Assign the ImageIndex property of the ToolBarButton.  
       ToolBarButton1.ImageIndex = 0  
    End Sub  
    ```  
  
    ```csharp  
    public void InitializeMyToolBar()  
    {  
       // Instantiate an ImageList component and a ToolBar control.  
       ToolBar toolBar1 = new  ToolBar();
       ImageList imageList1 = new ImageList();  
       // Assign an image to the ImageList component.  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       Image myImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
       // Create a ToolBarButton.  
       ToolBarButton toolBarButton1 = new ToolBarButton();  
       // Add the ToolBarButton to the ToolBar.  
       toolBar1.Buttons.Add(toolBarButton1);  
       // Assign an ImageList to the ToolBar.  
       toolBar1.ImageList = imageList1;  
       // Assign ImageIndex property of the ToolBarButton.  
       toolBarButton1.ImageIndex = 0;  
    }  
    ```  
  
    ```cpp  
    public:  
       void InitializeMyToolBar()  
       {  
          // Instantiate an ImageList component and a ToolBar control.  
          ToolBar ^ toolBar1 = gcnew  ToolBar();
          ImageList ^ imageList1 = gcnew ImageList();  
          // Assign an image to the ImageList component.  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          Image ^ myImage = Image::FromFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
          // Create a ToolBarButton.  
          ToolBarButton ^ toolBarButton1 = gcnew ToolBarButton();  
          // Add the ToolBarButton to the ToolBar.  
          toolBar1->Buttons->Add(toolBarButton1);  
          // Assign an ImageList to the ToolBar.  
          toolBar1->ImageList = imageList1;  
          // Assign ImageIndex property of the ToolBarButton.  
          toolBarButton1->ImageIndex = 0;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolBar>
- [Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
- [ImageList Bileşeni](imagelist-component-windows-forms.md)
