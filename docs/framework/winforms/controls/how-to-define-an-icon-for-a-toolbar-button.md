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
# <a name="how-to-define-an-icon-for-a-toolbar-button"></a><span data-ttu-id="ed88d-102">Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama</span><span class="sxs-lookup"><span data-stu-id="ed88d-102">How to: Define an Icon for a ToolBar Button</span></span>
> [!NOTE]
> <span data-ttu-id="ed88d-103">Denetim, <xref:System.Windows.Forms.ToolStrip> denetimin <xref:System.Windows.Forms.ToolBar> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.ToolBar> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="ed88d-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ed88d-104"><xref:System.Windows.Forms.ToolBar>düğmeler, kullanıcılar tarafından kolay tanımlama için içlerindeki simgeleri görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ed88d-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="ed88d-105">Bu, [ImageList Bileşeni](imagelist-component-windows-forms.md) bileşenine görüntü ekleyerek ve bileşenle <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> denetimle ilişkilendirilerek elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ed88d-105">This is achieved through adding images to the [ImageList Component](imagelist-component-windows-forms.md) component and then associating the <xref:System.Windows.Forms.ImageList> component with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-programmatically"></a><span data-ttu-id="ed88d-106">Araç çubuğu düğmesi için simgeyi programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ed88d-106">To set an icon for a toolbar button programmatically</span></span>  
  
1. <span data-ttu-id="ed88d-107">Bir yordamda, bir <xref:System.Windows.Forms.ImageList> bileşeni ve <xref:System.Windows.Forms.ToolBar> denetimi anında yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ed88d-107">In a procedure, instantiate an <xref:System.Windows.Forms.ImageList> component and a <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2. <span data-ttu-id="ed88d-108">Aynı yordamda, <xref:System.Windows.Forms.ImageList> bileşene bir görüntü atayın.</span><span class="sxs-lookup"><span data-stu-id="ed88d-108">In the same procedure, assign an image to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
3. <span data-ttu-id="ed88d-109">Aynı yordamda, <xref:System.Windows.Forms.ImageList> denetimi denetime <xref:System.Windows.Forms.ToolBar> atayın ve <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> tek tek araç çubuğu düğmelerinin özelliğini atayın.</span><span class="sxs-lookup"><span data-stu-id="ed88d-109">In the same procedure, assign the <xref:System.Windows.Forms.ImageList> control to the <xref:System.Windows.Forms.ToolBar> control and assign the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of the individual toolbar buttons.</span></span>  
  
     <span data-ttu-id="ed88d-110">Aşağıdaki kod örneğinde, görüntünün konumu için ayarlanan yol **Belgelerim** klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="ed88d-110">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="ed88d-111">Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğinizden, bu işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="ed88d-111">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="ed88d-112">Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ed88d-112">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="ed88d-113">Aşağıdaki <xref:System.Windows.Forms.PictureBox> örnekte, denetimzaten eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ed88d-113">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
     <span data-ttu-id="ed88d-114">Yukarıdaki adımları izleyerek, aşağıda görüntülenen benzer kod yazmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed88d-114">Following the steps above, you should have written code similar to that displayed below.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed88d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed88d-115">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="ed88d-116">Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme</span><span class="sxs-lookup"><span data-stu-id="ed88d-116">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="ed88d-117">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="ed88d-117">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="ed88d-118">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ed88d-118">ImageList Component</span></span>](imagelist-component-windows-forms.md)
