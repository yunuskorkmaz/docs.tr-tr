---
title: "Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccd63cb88661db7601b87eec6bdf3a959afb8bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="0d9f4-102">Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme</span><span class="sxs-lookup"><span data-stu-id="0d9f4-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="0d9f4-103"><xref:System.Windows.Forms.ToolStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ToolBar> kontrol; ancak, <xref:System.Windows.Forms.ToolBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="0d9f4-104">Bütünleyici <xref:System.Windows.Forms.ToolBar> denetimidir ona eklediğiniz düğmeler.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="0d9f4-105">Bunlar, menü komutlarını kolay erişim sağlamak için kullanılabilir veya alternatif olarak, bunlar menü yapısındaki kullanılabilir değil, kullanıcılarınıza komutları kullanıma sunmak için uygulamanızın kullanıcı arabiriminin bir diğer alan yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>  
  
 <span data-ttu-id="0d9f4-106">Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="0d9f4-107">Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0d9f4-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d9f4-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0d9f4-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0d9f4-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="0d9f4-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="0d9f4-111">Tasarım zamanında düğmeleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="0d9f4-111">To add buttons at design time</span></span>  
  
1.  <span data-ttu-id="0d9f4-112">Seçin <xref:System.Windows.Forms.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-112">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="0d9f4-113">İçinde **özellikleri** penceresinde tıklatın <xref:System.Windows.Forms.ToolBar.Buttons%2A> onu seçin ve özellik **üç nokta** (![VisualStudioEllipsesButton ekran] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) açmak için düğmeye **ToolBarButton Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-113">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="0d9f4-114">Kullanım **Ekle** ve **kaldırmak** ekleyip düğmelerden Kaldır düğmelerini <xref:System.Windows.Forms.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-114">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
4.  <span data-ttu-id="0d9f4-115">Düğmelerin özelliklerini yapılandırmak **özellikleri** Düzenleyicisinin sağ taraftaki bölmede görüntülenen penceresi.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-115">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="0d9f4-116">Aşağıdaki tabloda dikkate alınması gereken bazı önemli özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-116">The following table shows some important properties to consider.</span></span>  
  
    |<span data-ttu-id="0d9f4-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="0d9f4-117">Property</span></span>|<span data-ttu-id="0d9f4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d9f4-118">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="0d9f4-119">Menü açılan araç çubuğu düğmesini görüntülenecek ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-119">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="0d9f4-120">Araç çubuğu düğme <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="0d9f4-121">Bu özellik bir örneğini alır <xref:System.Windows.Forms.ContextMenu> sınıfı bir başvuru olarak.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-121">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="0d9f4-122">İki durumlu stili araç çubuğu düğmesi kısmen gönderilen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-122">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="0d9f4-123">Araç çubuğu düğme <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-123">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="0d9f4-124">İki durumlu stili araç çubuğu düğmesi şu anda zorlanan durumda olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-124">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="0d9f4-125">Araç çubuğu düğme <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği ayarlanmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> veya <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-125">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="0d9f4-126">Araç çubuğu düğmesi stilini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-126">Sets the style of the toolbar button.</span></span> <span data-ttu-id="0d9f4-127">Değerlerden biri olmalıdır <xref:System.Windows.Forms.ToolBarButtonStyle> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-127">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="0d9f4-128">Düğme tarafından görüntülenen metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-128">The text string displayed by the button.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="0d9f4-129">Düğme için bir araç ipucu olarak görüntülenen metin.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-129">The text that appears as a ToolTip for the button.</span></span>|  
  
5.  <span data-ttu-id="0d9f4-130">Tıklatın **Tamam** iletişim kutusunu kapatmak ve belirttiğiniz panelleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-130">Click **OK** to close the dialog box and create the panels you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9f4-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d9f4-131">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="0d9f4-132">Nasıl yapılır: ToolBar Düğmesi için Simge Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0d9f4-132">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [<span data-ttu-id="0d9f4-133">Nasıl yapılır: Araç Çubuğu Düğmeleri için Menü Olaylarını Tetikleme</span><span class="sxs-lookup"><span data-stu-id="0d9f4-133">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="0d9f4-134">ToolBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d9f4-134">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="0d9f4-135">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="0d9f4-135">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
