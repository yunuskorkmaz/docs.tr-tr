---
title: 'Nasıl yapılır: ToolBar düğmesi için simge tanımlama'
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
ms.openlocfilehash: fb4a492b081cd9f9e3ccc1d47a4120c705058dd0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712753"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="7d1a3-102">Nasıl yapılır: ToolBar düğmesi için simge tanımlama</span><span class="sxs-lookup"><span data-stu-id="7d1a3-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
>  <span data-ttu-id="7d1a3-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="7d1a3-104"><xref:System.Windows.Forms.ToolBar> düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeler içlerindeki görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="7d1a3-105">Bu görüntüleri eklerken size sağlanır [ImageList bileşeni](imagelist-component-windows-forms.md) bileşeni ve ardından ilişkilendirme <xref:System.Windows.Forms.ImageList> ile bileşen <xref:System.Windows.Forms.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="7d1a3-106">Araç çubuğu düğmesi için simge program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7d1a3-106">To set an icon for a toolbar button programmatically</span></span>  
  
1.  <span data-ttu-id="7d1a3-107">Bir yordamda örneği bir <xref:System.Windows.Forms.ImageList> bileşeni ve bir <xref:System.Windows.Forms.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="7d1a3-108">Aynı yordamı, görüntüye atama <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3.  <span data-ttu-id="7d1a3-109">Aynı yordamı, Ata <xref:System.Windows.Forms.ImageList> denetimini <xref:System.Windows.Forms.ToolBar> denetlemek ve atama <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> tek araç çubuğu düğmelerinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="7d1a3-110">Aşağıdaki kod örneğinde yolunu ayarlamak için görüntü konumunu **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="7d1a3-111">Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="7d1a3-112">Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="7d1a3-113">Aşağıdaki örnekte bir form varsayar bir <xref:System.Windows.Forms.PictureBox> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="7d1a3-114">Yukarıdaki adımları kod, aşağıda gösterilen benzer yazmış olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d1a3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d1a3-115">See also</span></span>
- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="7d1a3-116">Nasıl yapılır: Araç çubuğu düğmeleri için menü olaylarını tetikleme</span><span class="sxs-lookup"><span data-stu-id="7d1a3-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="7d1a3-117">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="7d1a3-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="7d1a3-118">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="7d1a3-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
