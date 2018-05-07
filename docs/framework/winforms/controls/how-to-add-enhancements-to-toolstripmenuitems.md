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
ms.openlocfilehash: 37843d27211bd07c2749b3e6fc14ec03d7bf570d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems'ne Geliştirmeler Ekleme
Kullanılabilirliğini artırmak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> aşağıdaki yollarla denetimleri:  
  
-   Cetvel sözcük uygulama kenar boşluğu görüntülenip görüntülenmeyeceğini gibi bir özelliğini açmak veya kapatmak açık olup olmadığını belirlemek için hangi dosyaların bir listesini dosyasında açık olarak görüntülenen, bu tür belirtmek için veya onay işaretleri ekleme bir **penceresi** menüsü.  
  
-   Menü komutları görsel olarak temsil eden görüntüleri ekleyin.  
  
-   Fare bir klavye alternatif komutlar gerçekleştirmek için sağlamak için kısayol tuşları görüntüleme. Örneğin, CTRL + C tuşlarına basarak gerçekleştirir **kopyalama** komutu.  
  
-   Menü gezinti için fare bir klavye alternatif sağlamak için erişim tuşları görüntüleme. Örneğin, ALT + F tuşlarına bastıktan seçer **dosya** menüsü.  
  
-   İlgili komutları gruplandırma ve menüleri daha okunabilir hale ayırıcı çubukları gösterme.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Bir onay işareti menü komutunda görüntülemek için  
  
-   Ayarlama, <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğine `true`.  
  
     Bu ayrıca ayarlar <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliğine `true`. Yalnızca seçili olup olmadığını bakılmaksızın varsayılan olarak işaretli görünmesi menü komutu istiyorsanız bu yordamı kullanın.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Her bir tıklatmayla durumu değişir bir onay işareti görüntülemek için  
  
-   Menü komutuna ayarlamak <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğine `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Menü komutu için bir resim eklemek için  
  
-   Menü komutuna ayarlamak <xref:System.Windows.Forms.ToolStripItem.Image%2A> görüntü adı özelliği. Varsa <xref:System.Windows.Forms.ToolStripItemDisplayStyle> bu menü komutu özelliği ayarlanmış <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, görüntü görüntülenemiyor.  
  
> [!NOTE]
>  Resim kenar, bu nedenle seçerseniz bir onay işareti de gösterebilir. Ayrıca, ayarlayabileceğiniz <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> görüntüye özelliğinin `true`, ve görüntünün taranmış kenarlık çalışma zamanında görünür.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Menü komutu için bir kısayol tuşu görüntülemek için  
  
-   Menü komutuna ayarlamak <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> için CTRL + O gibi istenen tuş bileşimini özelliğine **açık** menü komutu ve kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğine `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Menü komutu özel kısayol tuşları görüntülemek için  
  
-   Menü komutuna ayarlamak <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> CTRL + SHIFT + O yerine SHIFT + CTRL + O ve kümesi gibi istenen tuş bileşimini özelliğine <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğine `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Menü komutu için bir erişim anahtarı görüntülemek için  
  
-   Ayarladığınızda <xref:System.Windows.Forms.ToolStripItem.Text%2A> menü komutu için özellik girin ve işareti (&) istediğiniz erişim tuşu olarak altı çizili harfi önce. Örneğin `&Open` olarak <xref:System.Windows.Forms.ToolStripItem.Text%2A> menü öğesi özelliği olarak görünen menü komutu sonuçlanacak **O**kalem.  
  
     Bu menü komutu gitmek için odağı vermek için ALT tuşuna basın <xref:System.Windows.Forms.MenuStrip>ve menü adının erişim tuşuna basın. Menüyü açılır ve öğeleri ile erişim anahtarlarını gösterir, yalnızca menü komutunu seçmek için erişim tuşuna gerekir.  
  
> [!NOTE]
>  ALT + F iki kere aynı menü sisteminde tanımlama gibi yinelenen erişim tuşları, tanımlamamaya özen gösterin. Yinelenen erişim tuşları seçimi sırasını garanti edilemez.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Menü komutları arasına bir ayırıcı çubuk görüntülemek için  
  
-   Tanımladıktan sonra <xref:System.Windows.Forms.MenuStrip> ve onu içerecek, öğeleri kullanım <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> veya <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> menü komutlarını ekleme yöntemi ve <xref:System.Windows.Forms.ToolStripSeparator> için denetimler <xref:System.Windows.Forms.MenuStrip> istediğiniz sırayla.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
