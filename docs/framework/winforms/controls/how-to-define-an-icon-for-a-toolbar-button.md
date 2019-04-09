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
ms.openlocfilehash: 0d4a17528ca3eb81f93419491766e370be551b1e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153133"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a>Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  
  
 <xref:System.Windows.Forms.ToolBar> düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeler içlerindeki görüntüleyebilir. Bu görüntüleri eklerken size sağlanır [ImageList bileşeni](imagelist-component-windows-forms.md) bileşeni ve ardından ilişkilendirme <xref:System.Windows.Forms.ImageList> ile bileşen <xref:System.Windows.Forms.ToolBar> denetimi.  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a>Araç çubuğu düğmesi için simge program üzerinden ayarlamak için  
  
1.  Bir yordamda örneği bir <xref:System.Windows.Forms.ImageList> bileşeni ve bir <xref:System.Windows.Forms.ToolBar> denetimi.  
  
2.  Aynı yordamı, görüntüye atama <xref:System.Windows.Forms.ImageList> bileşeni.  
  
3.  Aynı yordamı, Ata <xref:System.Windows.Forms.ImageList> denetimini <xref:System.Windows.Forms.ToolBar> denetlemek ve atama <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> tek araç çubuğu düğmelerinin özelliği.  
  
     Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Belgelerim** klasör. Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir. Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar. Aşağıdaki örnekte bir form varsayar bir <xref:System.Windows.Forms.PictureBox> denetim zaten eklendi.  
  
     Yukarıdaki adımları kod, aşağıda gösterilen benzer yazmış olduğunuz.  
  
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
