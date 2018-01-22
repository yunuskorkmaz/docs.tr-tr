---
title: "Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85be18b2cbb4e0fe729c335016fa8e7348f7be13
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="5911f-102">Nasıl yapılır: Tasarımcı Kullanarak ToolBar Düğmesi için Simge Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5911f-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="5911f-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ToolBar> kontrol; ancak, <xref:System.Windows.Forms.ToolBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="5911f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="5911f-104"><xref:System.Windows.Forms.ToolBar>düğmeleri kullanıcılar tarafından kolay bir şekilde tanımlanması için bunları içinde simge görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5911f-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="5911f-105">Bu görüntüleri ekleme aracılığıyla elde edilen <xref:System.Windows.Forms.ImageList> bileşeni ve onunla ilişkili <xref:System.Windows.Forms.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="5911f-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="5911f-106">Aşağıdaki yordamı gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ToolBar> denetim ve bir <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="5911f-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="5911f-107">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5911f-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5911f-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5911f-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5911f-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5911f-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5911f-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5911f-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="5911f-111">Tasarım zamanında bir araç çubuğu düğmesi için simge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5911f-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="5911f-112">Görüntüleri ekleme <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="5911f-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="5911f-113">Daha fazla bilgi için bkz: [nasıl yapılır: tasarımcı ile ImageList'görüntüleri ekleyip](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="5911f-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="5911f-114">Seçin <xref:System.Windows.Forms.ToolBar> formunuzda denetim.</span><span class="sxs-lookup"><span data-stu-id="5911f-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="5911f-115">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.ImageList%2A> özelliğine <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="5911f-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="5911f-116">Tıklatın <xref:System.Windows.Forms.ToolBar> denetimin <xref:System.Windows.Forms.ToolBar.Buttons%2A> seçin ve üç nokta düğmesine özelliği (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) açmakiçindüğmeye**ToolBarButton Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="5911f-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="5911f-117">Kullanım **Ekle** düğmeleri için Ekle düğmesini <xref:System.Windows.Forms.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="5911f-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="5911f-118">İçinde **özellikleri** sağ taraftaki bölmede görüntülenen penceresi **ToolBarButton Koleksiyonu Düzenleyicisi**ayarlayın <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> her araç çubuğu düğmesi listesinde değerlerden birine özelliği, eklediğiniz görüntülerden çizilmiş <xref:System.Windows.Forms.ImageList> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="5911f-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5911f-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5911f-119">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="5911f-120">Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme</span><span class="sxs-lookup"><span data-stu-id="5911f-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="5911f-121">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="5911f-121">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="5911f-122">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="5911f-122">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
