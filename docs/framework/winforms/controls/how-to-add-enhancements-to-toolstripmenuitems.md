---
title: "Nasıl yapılır: ToolStripMenuItems'ne Geliştirmeler Ekleme"
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
ms.openlocfilehash: 61a79b9bbe101d7bf694240bdffdecee5187adf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182330"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="84e84-102">Nasıl yapılır: ToolStripMenuItems'ne Geliştirmeler Ekleme</span><span class="sxs-lookup"><span data-stu-id="84e84-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="84e84-103">Aşağıdaki yollarla kullanılabilirliğini <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> ve denetimlerini artırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="84e84-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="84e84-104">Bir özelliğin açık mı yoksa kapalı mı olduğunu (sözcük işleme uygulamasının kenar boşluğunda bir cetvelin görüntülenip görüntülenmediğini belirtmek veya **Pencere** menüsündeki gibi dosyalar listesindeki hangi dosyanın görüntülendiğini belirtmek için) işaret ekleyin.</span><span class="sxs-lookup"><span data-stu-id="84e84-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="84e84-105">Menü komutlarını görsel olarak temsil eden görüntüler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="84e84-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="84e84-106">Komutları gerçekleştirmek için fareye bir klavye alternatifi sağlamak için kısayol tuşlarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="84e84-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="84e84-107">Örneğin, CTRL+C tuşuna basarak **Kopyala** komutu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="84e84-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="84e84-108">Menü gezintisi için fareye bir klavye alternatifi sağlamak için erişim tuşlarını görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="84e84-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="84e84-109">Örneğin, ALT+F tuşuna basmak **Dosya** menüsünü seçer.</span><span class="sxs-lookup"><span data-stu-id="84e84-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="84e84-110">Ayırıcı çubuklarını grupla ilgili komutlara göster ve menüleri daha okunabilir hale getirin.</span><span class="sxs-lookup"><span data-stu-id="84e84-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="84e84-111">Menü komutunda onay işareti görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="84e84-112">Özelliğini <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> `true`.</span><span class="sxs-lookup"><span data-stu-id="84e84-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="84e84-113">Bu da <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="84e84-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="84e84-114">Bu yordamı yalnızca seçilip seçilmediğine bakılmaksızın menü komutunun varsayılan olarak denetlenmiş olarak görünmesini istiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="84e84-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="84e84-115">Her tıklamayla durumu değiştiren bir onay işareti görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="84e84-116">Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true`' ' ye ayarlayın</span><span class="sxs-lookup"><span data-stu-id="84e84-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="84e84-117">Menü komutuna resim eklemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="84e84-118">Menü komutunun <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğini görüntünün adına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84e84-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="84e84-119">Bu <xref:System.Windows.Forms.ToolStripItemDisplayStyle> menü komutunun özelliği <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ayarlanmışsa veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, görüntü görüntülenemez.</span><span class="sxs-lookup"><span data-stu-id="84e84-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84e84-120">Eğer isterseniz görüntü kenar boşluğu da bir onay işareti gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="84e84-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="84e84-121">Ayrıca, görüntünün <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini `true`,' olarak ayarlayabilirsiniz ve görüntü çalışma zamanında etrafında yumurtadan çıkmış bir kenarlık ile görünür.</span><span class="sxs-lookup"><span data-stu-id="84e84-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="84e84-122">Menü komutu için kısayol tuşu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="84e84-123">Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> özelliğini, **Açık** menü komutu için CTRL+O gibi istenilen <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> klavye `true`birleşimine ayarlayın ve özelliği ' ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84e84-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="84e84-124">Menü komutu için özel kısayol tuşlarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="84e84-125">Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> özelliğini SHIFT+CTRL+O yerine CTRL+SHIFT+O gibi istenen klavye kombinasyonuna <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> ayarlayın `true`ve özelliği ' ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="84e84-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="84e84-126">Menü komutu için erişim anahtarı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="84e84-127">Menü komutu <xref:System.Windows.Forms.ToolStripItem.Text%2A> için özelliği ayarladığınızda, erişim anahtarı olarak altı çizili olmasını istediğiniz harften önce bir ampersand (&) girin.</span><span class="sxs-lookup"><span data-stu-id="84e84-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="84e84-128">Örneğin, bir `&Open` menü <xref:System.Windows.Forms.ToolStripItem.Text%2A> öğesinin özelliği olarak yazmak, <u>O</u>kalem için günü nüründe görünen bir menü komutuyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="84e84-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="84e84-129">Bu menü komutuna gitmek için ALT <xref:System.Windows.Forms.MenuStrip>tuşuna basın ve menü adının erişim tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="84e84-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="84e84-130">Menü açıldığında ve erişim tuşlarına sahip öğeler gösterildiğinde, menü komutunu seçmek için erişim tuşuna basmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="84e84-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84e84-131">Aynı menü sisteminde ALT+F'yi iki kez tanımlamak gibi yinelenen erişim anahtarlarını tanımlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="84e84-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="84e84-132">Yinelenen erişim anahtarlarının seçim sırası garanti edilemez.</span><span class="sxs-lookup"><span data-stu-id="84e84-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="84e84-133">Menü komutları arasında ayırıcı çubuğu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="84e84-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="84e84-134">Sizin <xref:System.Windows.Forms.MenuStrip> ve içerdiği öğeleri tanımladıktan sonra, <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> menü komutlarını ve <xref:System.Windows.Forms.ToolStripSeparator> denetimlerini istediğiniz <xref:System.Windows.Forms.MenuStrip> sıraya eklemek için veya yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="84e84-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84e84-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84e84-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="84e84-136">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="84e84-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
