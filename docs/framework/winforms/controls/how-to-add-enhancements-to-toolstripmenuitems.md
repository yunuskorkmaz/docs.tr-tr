---
title: "Nasıl yapılır: ToolStripMenuItems'e Geliştirmeler Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: 9e95c3623bf9bad8395f586392a0557ad1cde880
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912579"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="7707c-102">Nasıl yapılır: ToolStripMenuItems'e Geliştirmeler Ekleme</span><span class="sxs-lookup"><span data-stu-id="7707c-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="7707c-103"><xref:System.Windows.Forms.MenuStrip> Ve<xref:System.Windows.Forms.ContextMenuStrip> denetimlerinin kullanılabilirliğini aşağıdaki yollarla geliştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7707c-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="7707c-104">Bir özelliğin bir sözcük işleme uygulamasının kenar boşluğunda görüntülenip görüntülenmediğini veya bir **pencere** menüsü gibi bir dosya listesindeki hangi dosyanın görüntülendiğini belirtmek gibi bir özelliğin açık veya kapalı olup olmadığını belirlemek için onay işaretleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7707c-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="7707c-105">Menü komutlarını görsel olarak temsil eden görüntüler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7707c-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="7707c-106">Komutları gerçekleştirmek için fareye bir klavye alternatifi sağlamak için kısayol tuşlarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7707c-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="7707c-107">Örneğin, CTRL + C tuşlarına basıldığında **Kopyala** komutu gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7707c-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="7707c-108">Menü gezintisi için fareye bir klavye alternatifi sağlamak için erişim tuşlarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7707c-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="7707c-109">Örneğin, ALT + F tuşlarına basmak **Dosya** menüsünü seçer.</span><span class="sxs-lookup"><span data-stu-id="7707c-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="7707c-110">İlgili komutları gruplamak ve menülerin daha okunaklı olmasını sağlamak için ayırıcı çubukları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7707c-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="7707c-111">Bir menü komutunda onay işareti göstermek için</span><span class="sxs-lookup"><span data-stu-id="7707c-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="7707c-112"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliğini olarak`true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7707c-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="7707c-113">Bu ayrıca <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliğini olarak `true`ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7707c-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="7707c-114">Bu yordamı yalnızca menü komutunun seçili olup olmamasına bakılmaksızın varsayılan olarak işaretlenmiş olarak görünmesini istiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="7707c-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="7707c-115">Her tıklamayla durumu değiştiren bir onay işareti göstermek için</span><span class="sxs-lookup"><span data-stu-id="7707c-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="7707c-116">Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7707c-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="7707c-117">Bir menü komutuna görüntü eklemek için</span><span class="sxs-lookup"><span data-stu-id="7707c-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="7707c-118">Menü komutunun <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğini görüntünün adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7707c-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="7707c-119">Bu menü komutunun <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>özelliği veya olarak ayarlandıysa, görüntü görüntülenemez. <xref:System.Windows.Forms.ToolStripItemDisplayStyle></span><span class="sxs-lookup"><span data-stu-id="7707c-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7707c-120">Ayrıca seçim yaparsanız, resim kenar boşluğu bir onay işareti de gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7707c-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="7707c-121">Ayrıca, görüntünün <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini olarak `true`ayarlayabilirsiniz ve resim çalışma zamanında etrafında taranmış bir kenarlıkla birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7707c-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="7707c-122">Bir menü komutu için kısayol tuşu görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7707c-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="7707c-123">Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> özelliğini, **Aç** menü komutu için CTRL + O gibi istenen klavye birleşimine ayarlayın ve <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7707c-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="7707c-124">Bir menü komutu için özel kısayol tuşlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7707c-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="7707c-125">Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> özelliğini, SHIFT + CTRL + o yerine CTRL + SHIFT + o gibi istenen klavye birleşimine ayarlayın ve <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7707c-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="7707c-126">Bir menü komutu için erişim anahtarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7707c-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="7707c-127">Menü komutu için <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ayarladığınızda, erişim anahtarı olarak altı çizili olmasını istediğiniz harfin önüne bir ve işareti (&) girin.</span><span class="sxs-lookup"><span data-stu-id="7707c-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="7707c-128">Örneğin, bir menü `&Open` öğesinin <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliği olarak yazıldığında, <u>O</u>kalem olarak görünen bir menü komutuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="7707c-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="7707c-129">Bu menü komutuna gitmek için alt tuşuna basarak odağı <xref:System.Windows.Forms.MenuStrip>verin ve menü adının erişim tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7707c-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="7707c-130">Menü açıldığında ve erişim anahtarlarına sahip öğeleri gösteriyorsa, menü komutunu seçmek için yalnızca erişim tuşuna basmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7707c-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7707c-131">Aynı menü sisteminde ALT + F 'yi iki kez tanımlamak gibi yinelenen erişim anahtarları tanımlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="7707c-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="7707c-132">Yinelenen erişim anahtarlarının seçim sırası garanti edilemez.</span><span class="sxs-lookup"><span data-stu-id="7707c-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="7707c-133">Menü komutları arasında bir ayırıcı çubuk göstermek için</span><span class="sxs-lookup"><span data-stu-id="7707c-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="7707c-134">Uygulamanızı <xref:System.Windows.Forms.MenuStrip> ve içereceği öğeleri tanımladıktan sonra, menü komutlarını ve <xref:System.Windows.Forms.ToolStripSeparator> denetimlerini istediğiniz sırada <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> öğesine <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> <xref:System.Windows.Forms.MenuStrip> eklemek için veya yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7707c-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7707c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7707c-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="7707c-136">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7707c-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
