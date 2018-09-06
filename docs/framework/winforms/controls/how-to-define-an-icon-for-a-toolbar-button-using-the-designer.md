---
title: 'Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: f26e21d824420fc4ff0480de21f260309c5c2e11
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856614"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="37980-102">Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama</span><span class="sxs-lookup"><span data-stu-id="37980-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="37980-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ToolBar> denetler; ancak, <xref:System.Windows.Forms.ToolBar> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="37980-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="37980-104"><xref:System.Windows.Forms.ToolBar> düğmeler, kullanıcılar tarafından kolay bir şekilde tanımlanması için simgeler içlerindeki görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="37980-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="37980-105">Bu görüntüleri eklerken size sağlanır <xref:System.Windows.Forms.ImageList> bileşeni ve onunla ilişkili <xref:System.Windows.Forms.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="37980-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="37980-106">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form ile bir <xref:System.Windows.Forms.ToolBar> denetimi ve bir <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="37980-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="37980-107">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="37980-107">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37980-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="37980-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="37980-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="37980-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="37980-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="37980-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="37980-111">Tasarım zamanında bir araç çubuğu düğmesi için simge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="37980-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="37980-112">Görüntüleri ekleme <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="37980-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="37980-113">Daha fazla bilgi için [nasıl yapılır: tasarımcı ile ImageList görüntüleri ekleyip](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="37980-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="37980-114">Seçin <xref:System.Windows.Forms.ToolBar> formunuzdaki denetimi.</span><span class="sxs-lookup"><span data-stu-id="37980-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="37980-115">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ImageList%2A> özelliğini <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="37980-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="37980-116">Tıklayın <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.Buttons%2A> özelliği seçin ve üç nokta simgesine tıklayın (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmakiçindüğmeyi**ToolBarButton Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="37980-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="37980-117">Kullanım **Ekle** düğmeleri eklemek için Ekle düğmesine <xref:System.Windows.Forms.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="37980-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="37980-118">İçinde **özellikleri** sağ tarafındaki bölmede görüntülenen penceresi **ToolBarButton Koleksiyonu Düzenleyicisi**ayarlayın <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> her araç çubuğu düğmesi listede yer alan değerlerden birine özelliği, eklediğiniz görüntülerinden alınan <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="37980-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37980-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37980-119">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="37980-120">Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme</span><span class="sxs-lookup"><span data-stu-id="37980-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="37980-121">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="37980-121">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="37980-122">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="37980-122">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
