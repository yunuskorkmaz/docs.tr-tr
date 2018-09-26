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
ms.openlocfilehash: eb55796480bea896383da479fe23a5d8967a52e3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090532"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems'ne Geliştirmeler Ekleme
Kitaplığın kullanılabilirliğini geliştirebilirsiniz <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> aşağıdaki yollarla denetimler:  
  
-   Cetvel bir kelime işleme uygulaması kenar boşluğu görüntülenip görüntülenmeyeceğini gibi bir özellik üzerinde açık olup olmadığını belirlemek için ya da hangi dosyaların listesini dosyasında itibariyle gösterilen, bu tür belirtmek için onay işaretleri ekleme bir **penceresi** menüsü.  
  
-   Görsel olarak menü komutları temsil eden görüntüleri ekleyin.  
  
-   Komutları gerçekleştirmek için fare bir klavye alternatif sağlamak için bir kısayol tuşları görüntüleme. Örneğin, CTRL + C tuşlarına basarak gerçekleştirir **kopyalama** komutu.  
  
-   Menü gezinme için fare bir klavye alternatif sağlamak için erişim anahtarlarını görüntüleme. Örneğin, ALT + F tuşlarına seçer **dosya** menüsü.  
  
-   İlgili komutları gruplamak ve menüler daha okunaklı hale getirmek için ayırıcı çubukları gösterme.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Bir onay işareti menü komutunun görüntülemek için  
  
-   Ayarlama, <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini `true`.  
  
     Bu ayrıca ayarlar <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliğini `true`. Menü komutunu seçili değişir bakılmaksızın varsayılan olarak işaretli görünmesini istiyorsanız, bu yordamı kullanın.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Onay işareti her bir tıklamayla durum değişikliklerini görüntülemek için  
  
-   Menü komut kümesi <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true`.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Bir görüntü için bir menü komutu eklemek için  
  
-   Menü komut kümesi <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğini görüntünün adı. Varsa <xref:System.Windows.Forms.ToolStripItemDisplayStyle> özelliği bu menü komutunun <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, görüntünün görüntülenemiyor.  
  
> [!NOTE]
>  Görüntü boşluğunu, bu nedenle seçerseniz bir onay işareti da gösterebilirsiniz. Ayrıca, ayarlayabilirsiniz <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> görüntüye özelliği `true`, ve görüntü taranmış bir kenarlık ile çalışma zamanında görünür.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Bir menü komutu için bir kısayol tuşu görüntülemek için  
  
-   Menü komut kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> istenen klavye birleşimi için CTRL + O gibi özelliğini **açık** menü komutu ve kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini `true`.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Bir menü komutu özel kısayol tuşları görüntülemek için  
  
-   Menü komut kümesi <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> CTRL + SHIFT + O yerine SHIFT + CTRL + O ve ayarlama gibi istediğiniz klavye birleşimi özelliğini <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini `true`.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Bir menü komutu için bir erişim anahtarı görüntülemek için  
  
-   Ayarladığınızda <xref:System.Windows.Forms.ToolStripItem.Text%2A> menü komutu için özellik girin ve işareti (&) istediğiniz erişim anahtarı olarak altı çizili harfi önce. Örneğin, yazmaya `&Open` olarak <xref:System.Windows.Forms.ToolStripItem.Text%2A> bir menü öğesinin özelliği olarak görünür bir menü komutu sonuçlanır <u>O</u>kalem.
  
     Bu komutu gitmek için odaklanmak için ALT tuşuna basın <xref:System.Windows.Forms.MenuStrip>ve menü adının erişim tuşuna basın. Menüyü açılır ve erişim anahtarları ile öğeleri gösteren, yalnızca menü komutunu seçmek için erişim anahtarı tuşuna basmanız gerekir.  
  
> [!NOTE]
>  ALT + F iki kez aynı menü sisteminde tanımlama gibi yinelenen erişim tuşları, tanımlamamaya özen gösterin. Yinelenen erişim tuşları seçimi sırasını garanti edilemez.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Menü komutları arasında bir ayırıcı çubuk görüntülemek için  
  
-   Tanımladıktan sonra <xref:System.Windows.Forms.MenuStrip> ve onu içerecek, öğeleri kullanım <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> veya <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> menü komutları ekleme yöntemi ve <xref:System.Windows.Forms.ToolStripSeparator> için denetimleri <xref:System.Windows.Forms.MenuStrip> istediğiniz sırayla.  
  
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
