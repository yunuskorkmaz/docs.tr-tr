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
ms.openlocfilehash: 2b85f734a5f8b31531cfe48f87681d98304db09b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929637"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama
> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip>  
  
 <xref:System.Windows.Forms.ToolBar>düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeleri içinde görüntüleyebilir. Bu, [ImageList bileşen](imagelist-component-windows-forms.md) bileşenine görüntü eklenerek ve ardından <xref:System.Windows.Forms.ImageList> bileşeni <xref:System.Windows.Forms.ToolBar> denetimiyle ilişkilendirerek elde edilir.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Bir araç çubuğu düğmesine programlı bir simge ayarlamak için  
  
1. Bir yordamda, bir <xref:System.Windows.Forms.ImageList> bileşeni <xref:System.Windows.Forms.ToolBar> ve denetimi örneğini oluşturun.  
  
2. Aynı yordamda <xref:System.Windows.Forms.ImageList> bileşene bir görüntü atayın.  
  
3. Aynı yordamda denetimi <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> denetime atayın ve tek araç çubuğu düğmelerinin <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> özelliğini atayın.  
  
     Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol Belgelerim klasörüdür. Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır. Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır. Aşağıdaki örnekte, bir <xref:System.Windows.Forms.PictureBox> denetimin zaten eklendiği bir form varsayılır.  
  
     Yukarıdaki adımları izleyerek aşağıda gösterilene benzer bir kod yazmış olmanız gerekir.  
  
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
- [Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar Denetimi](toolbar-control-windows-forms.md)
- [ImageList Bileşeni](imagelist-component-windows-forms.md)
