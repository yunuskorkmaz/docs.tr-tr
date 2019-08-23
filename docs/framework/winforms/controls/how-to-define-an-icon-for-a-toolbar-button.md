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
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="78a3f-102">Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama</span><span class="sxs-lookup"><span data-stu-id="78a3f-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="78a3f-103">Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="78a3f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="78a3f-104"><xref:System.Windows.Forms.ToolBar>düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeleri içinde görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="78a3f-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="78a3f-105">Bu, [ImageList bileşen](imagelist-component-windows-forms.md) bileşenine görüntü eklenerek ve ardından <xref:System.Windows.Forms.ImageList> bileşeni <xref:System.Windows.Forms.ToolBar> denetimiyle ilişkilendirerek elde edilir.</span><span class="sxs-lookup"><span data-stu-id="78a3f-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="78a3f-106">Bir araç çubuğu düğmesine programlı bir simge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="78a3f-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="78a3f-107">Bir yordamda, bir <xref:System.Windows.Forms.ImageList> bileşeni <xref:System.Windows.Forms.ToolBar> ve denetimi örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78a3f-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="78a3f-108">Aynı yordamda <xref:System.Windows.Forms.ImageList> bileşene bir görüntü atayın.</span><span class="sxs-lookup"><span data-stu-id="78a3f-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="78a3f-109">Aynı yordamda denetimi <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> denetime atayın ve tek araç çubuğu düğmelerinin <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> özelliğini atayın.</span><span class="sxs-lookup"><span data-stu-id="78a3f-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="78a3f-110">Aşağıdaki kod örneğinde, görüntü konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="78a3f-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="78a3f-111">Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="78a3f-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="78a3f-112">Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="78a3f-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="78a3f-113">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.PictureBox> denetimin zaten eklendiği bir form varsayılır.</span><span class="sxs-lookup"><span data-stu-id="78a3f-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="78a3f-114">Yukarıdaki adımları izleyerek aşağıda gösterilene benzer bir kod yazmış olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78a3f-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78a3f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78a3f-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="78a3f-116">Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları</span><span class="sxs-lookup"><span data-stu-id="78a3f-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="78a3f-117">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="78a3f-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="78a3f-118">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="78a3f-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
