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
ms.openlocfilehash: 458347df7e17aabc1e9e21d66ad1b5a96200fe28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198562"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="84fb5-102">Nasıl yapılır: ToolStripMenuItems'e Geliştirmeler Ekleme</span><span class="sxs-lookup"><span data-stu-id="84fb5-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="84fb5-103">Kitaplığın kullanılabilirliğini geliştirebilirsiniz <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> aşağıdaki yollarla denetimler:</span><span class="sxs-lookup"><span data-stu-id="84fb5-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="84fb5-104">Cetvel bir kelime işleme uygulaması kenar boşluğu görüntülenip görüntülenmeyeceğini gibi bir özellik üzerinde açık olup olmadığını belirlemek için ya da hangi dosyaların listesini dosyasında itibariyle gösterilen, bu tür belirtmek için onay işaretleri ekleme bir **penceresi** menüsü.</span><span class="sxs-lookup"><span data-stu-id="84fb5-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="84fb5-105">Görsel olarak menü komutları temsil eden görüntüleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="84fb5-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="84fb5-106">Komutları gerçekleştirmek için fare bir klavye alternatif sağlamak için bir kısayol tuşları görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="84fb5-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="84fb5-107">Örneğin, CTRL + C tuşlarına basarak gerçekleştirir **kopyalama** komutu.</span><span class="sxs-lookup"><span data-stu-id="84fb5-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="84fb5-108">Menü gezinme için fare bir klavye alternatif sağlamak için erişim anahtarlarını görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="84fb5-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="84fb5-109">Örneğin, ALT + F tuşlarına seçer **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="84fb5-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="84fb5-110">İlgili komutları gruplamak ve menüler daha okunaklı hale getirmek için ayırıcı çubukları gösterme.</span><span class="sxs-lookup"><span data-stu-id="84fb5-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="84fb5-111">Bir onay işareti menü komutunun görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="84fb5-112">Ayarlama, <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="84fb5-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="84fb5-113">Bu ayrıca ayarlar <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="84fb5-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="84fb5-114">Menü komutunu seçili değişir bakılmaksızın varsayılan olarak işaretli görünmesini istiyorsanız, bu yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="84fb5-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="84fb5-115">Onay işareti her bir tıklamayla durum değişikliklerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="84fb5-116">Menü komut kümesi <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="84fb5-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="84fb5-117">Bir görüntü için bir menü komutu eklemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="84fb5-118">Menü komut kümesi <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğini görüntünün adı.</span><span class="sxs-lookup"><span data-stu-id="84fb5-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="84fb5-119">Varsa <xref:System.Windows.Forms.ToolStripItemDisplayStyle> özelliği bu menü komutunun <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, görüntünün görüntülenemiyor.</span><span class="sxs-lookup"><span data-stu-id="84fb5-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84fb5-120">Görüntü boşluğunu, bu nedenle seçerseniz bir onay işareti da gösterebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84fb5-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="84fb5-121">Ayrıca, ayarlayabilirsiniz <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> görüntüye özelliği `true`, ve görüntü taranmış bir kenarlık ile çalışma zamanında görünür.</span><span class="sxs-lookup"><span data-stu-id="84fb5-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="84fb5-122">Bir menü komutu için bir kısayol tuşu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="84fb5-123">Menü komut kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> istenen klavye birleşimi için CTRL + O gibi özelliğini **açık** menü komutu ve kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="84fb5-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="84fb5-124">Bir menü komutu özel kısayol tuşları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="84fb5-125">Menü komut kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> CTRL + SHIFT + O yerine SHIFT + CTRL + O ve ayarlama gibi istediğiniz klavye birleşimi özelliğini <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="84fb5-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="84fb5-126">Bir menü komutu için bir erişim anahtarı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="84fb5-127">Ayarladığınızda <xref:System.Windows.Forms.ToolStripItem.Text%2A> menü komutu için özellik girin ve işareti (&) istediğiniz erişim anahtarı olarak altı çizili harfi önce.</span><span class="sxs-lookup"><span data-stu-id="84fb5-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="84fb5-128">Örneğin, yazmaya `&Open` olarak <xref:System.Windows.Forms.ToolStripItem.Text%2A> bir menü öğesinin özelliği olarak görünür bir menü komutu sonuçlanır <u>O</u>kalem.</span><span class="sxs-lookup"><span data-stu-id="84fb5-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="84fb5-129">Bu komutu gitmek için odaklanmak için ALT tuşuna basın <xref:System.Windows.Forms.MenuStrip>ve menü adının erişim tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="84fb5-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="84fb5-130">Menüyü açılır ve erişim anahtarları ile öğeleri gösteren, yalnızca menü komutunu seçmek için erişim anahtarı tuşuna basmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="84fb5-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84fb5-131">ALT + F iki kez aynı menü sisteminde tanımlama gibi yinelenen erişim tuşları, tanımlamamaya özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="84fb5-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="84fb5-132">Yinelenen erişim tuşları seçimi sırasını garanti edilemez.</span><span class="sxs-lookup"><span data-stu-id="84fb5-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="84fb5-133">Menü komutları arasında bir ayırıcı çubuk görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84fb5-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="84fb5-134">Tanımladıktan sonra <xref:System.Windows.Forms.MenuStrip> ve onu içerecek, öğeleri kullanım <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> veya <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> menü komutları ekleme yöntemi ve <xref:System.Windows.Forms.ToolStripSeparator> için denetimleri <xref:System.Windows.Forms.MenuStrip> istediğiniz sırayla.</span><span class="sxs-lookup"><span data-stu-id="84fb5-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84fb5-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84fb5-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="84fb5-136">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="84fb5-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
