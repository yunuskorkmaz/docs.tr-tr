---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: e5069dd46a31a65f65a17d750b685d82762e3d11
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038202"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="4df5a-102">Nasıl yapılır: Tasarımcı Kullanarak bir ToolBar Denetimine Düğme Ekleme</span><span class="sxs-lookup"><span data-stu-id="4df5a-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="4df5a-103">Denetim yerini alır ve <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="4df5a-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="4df5a-104"><xref:System.Windows.Forms.ToolBar> Denetimin integral bir bölümü, ona eklediğiniz düğmelerdir.</span><span class="sxs-lookup"><span data-stu-id="4df5a-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="4df5a-105">Bunlar menü komutlarına kolay erişim sağlamak için kullanılabilir veya alternatif olarak, menü yapısında kullanılamayan kullanıcılarınıza komutları göstermek için uygulamanızın kullanıcı arabiriminin başka bir alanına yerleştirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="4df5a-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>

<span data-ttu-id="4df5a-106">Aşağıdaki yordam, bir <xref:System.Windows.Forms.ToolBar> denetim içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4df5a-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="4df5a-107">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4df5a-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="4df5a-108">Tasarım zamanında düğme eklemek için</span><span class="sxs-lookup"><span data-stu-id="4df5a-108">To add buttons at design time</span></span>

1. <span data-ttu-id="4df5a-109"><xref:System.Windows.Forms.ToolBar> Denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="4df5a-109">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>

2. <span data-ttu-id="4df5a-110">**Özellikler** penceresinde, <xref:System.Windows.Forms.ToolBar.Buttons%2A> özelliği tıklatıp seçin ve sonra da Visual Studio 'nun Özellikler penceresi üç nokta (![...) düğmesini tıklatın.](./media/visual-studio-ellipsis-button.png)ToolBarButton 'ı açmak için  **Koleksiyon Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="4df5a-110">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

3. <span data-ttu-id="4df5a-111">Denetime düğme eklemek ve kaldırmak için Ekle ve **Kaldır** düğmelerini kullanın. <xref:System.Windows.Forms.ToolBar></span><span class="sxs-lookup"><span data-stu-id="4df5a-111">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>

4. <span data-ttu-id="4df5a-112">Düzenleyicinin sağ tarafındaki bölmede görüntülenen **Özellikler** penceresinde tek düğmelerin özelliklerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4df5a-112">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="4df5a-113">Aşağıdaki tabloda dikkate alınması gereken bazı önemli özellikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4df5a-113">The following table shows some important properties to consider.</span></span>

    |<span data-ttu-id="4df5a-114">Özellik</span><span class="sxs-lookup"><span data-stu-id="4df5a-114">Property</span></span>|<span data-ttu-id="4df5a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4df5a-115">Description</span></span>|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="4df5a-116">Açılan araç çubuğu düğmesinde görüntülenecek menüyü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4df5a-116">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="4df5a-117">Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği olarak <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5a-117">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="4df5a-118">Bu özellik, <xref:System.Windows.Forms.ContextMenu> bir başvuru olarak sınıfının bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="4df5a-118">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="4df5a-119">Bir değiştirme stili araç çubuğu düğmesinin kısmen gönderilip atılmayacağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4df5a-119">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="4df5a-120">Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği olarak <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5a-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="4df5a-121">Geçiş stili bir araç çubuğu düğmesinin Şu anda basılmış durumunda olup olmadığını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4df5a-121">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="4df5a-122">Araç çubuğu düğmesinin <xref:System.Windows.Forms.ToolBarButton.Style%2A> özelliği veya <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>olarak <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5a-122">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="4df5a-123">Araç çubuğu düğmesinin stilini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4df5a-123">Sets the style of the toolbar button.</span></span> <span data-ttu-id="4df5a-124"><xref:System.Windows.Forms.ToolBarButtonStyle> Numaralandırmadaki değerlerden biri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5a-124">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="4df5a-125">Düğme tarafından görünen metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="4df5a-125">The text string displayed by the button.</span></span>|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="4df5a-126">Düğme için araç Ipucu olarak görünen metin.</span><span class="sxs-lookup"><span data-stu-id="4df5a-126">The text that appears as a ToolTip for the button.</span></span>|

5. <span data-ttu-id="4df5a-127">İletişim kutusunu kapatmak ve belirlediğiniz bölmeleri oluşturmak için **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4df5a-127">Click **OK** to close the dialog box and create the panels you specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="4df5a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4df5a-128">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="4df5a-129">Nasıl yapılır: Bir araç çubuğu düğmesi için simge tanımlama</span><span class="sxs-lookup"><span data-stu-id="4df5a-129">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="4df5a-130">Nasıl yapılır: Araç çubuğu düğmeleri için tetikleyici menü olayları</span><span class="sxs-lookup"><span data-stu-id="4df5a-130">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="4df5a-131">ToolBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4df5a-131">ToolBar Control Overview</span></span>](toolbar-control-overview-windows-forms.md)
- [<span data-ttu-id="4df5a-132">ToolBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="4df5a-132">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
