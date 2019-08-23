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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems'e Geliştirmeler Ekleme
<xref:System.Windows.Forms.MenuStrip> Ve<xref:System.Windows.Forms.ContextMenuStrip> denetimlerinin kullanılabilirliğini aşağıdaki yollarla geliştirebilirsiniz:  
  
- Bir özelliğin bir sözcük işleme uygulamasının kenar boşluğunda görüntülenip görüntülenmediğini veya bir **pencere** menüsü gibi bir dosya listesindeki hangi dosyanın görüntülendiğini belirtmek gibi bir özelliğin açık veya kapalı olup olmadığını belirlemek için onay işaretleri ekleyin.  
  
- Menü komutlarını görsel olarak temsil eden görüntüler ekleyin.  
  
- Komutları gerçekleştirmek için fareye bir klavye alternatifi sağlamak için kısayol tuşlarını görüntüleyin. Örneğin, CTRL + C tuşlarına basıldığında **Kopyala** komutu gerçekleştirilir.  
  
- Menü gezintisi için fareye bir klavye alternatifi sağlamak için erişim tuşlarını görüntüleyin. Örneğin, ALT + F tuşlarına basmak **Dosya** menüsünü seçer.  
  
- İlgili komutları gruplamak ve menülerin daha okunaklı olmasını sağlamak için ayırıcı çubukları görüntüleyin.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Bir menü komutunda onay işareti göstermek için  
  
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Özelliğini olarak`true`ayarlayın.  
  
     Bu ayrıca <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliğini olarak `true`ayarlar. Bu yordamı yalnızca menü komutunun seçili olup olmamasına bakılmaksızın varsayılan olarak işaretlenmiş olarak görünmesini istiyorsanız kullanın.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Her tıklamayla durumu değiştiren bir onay işareti göstermek için  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini olarak `true`ayarlayın.  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Bir menü komutuna görüntü eklemek için  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğini görüntünün adı olarak ayarlayın. Bu menü komutunun <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>özelliği veya olarak ayarlandıysa, görüntü görüntülenemez. <xref:System.Windows.Forms.ToolStripItemDisplayStyle>  
  
> [!NOTE]
> Ayrıca seçim yaparsanız, resim kenar boşluğu bir onay işareti de gösterebilir. Ayrıca, görüntünün <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini olarak `true`ayarlayabilirsiniz ve resim çalışma zamanında etrafında taranmış bir kenarlıkla birlikte görüntülenir.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Bir menü komutu için kısayol tuşu görüntüleme  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> özelliğini, **Aç** menü komutu için CTRL + O gibi istenen klavye birleşimine ayarlayın ve <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini olarak `true`ayarlayın.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Bir menü komutu için özel kısayol tuşlarını görüntüleme  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> özelliğini, SHIFT + CTRL + o yerine CTRL + SHIFT + o gibi istenen klavye birleşimine ayarlayın ve <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> özelliğini olarak `true`ayarlayın.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Bir menü komutu için erişim anahtarını görüntüleme  
  
- Menü komutu için <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ayarladığınızda, erişim anahtarı olarak altı çizili olmasını istediğiniz harfin önüne bir ve işareti (&) girin. Örneğin, bir menü `&Open` öğesinin <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliği olarak yazıldığında, <u>O</u>kalem olarak görünen bir menü komutuna neden olur.
  
     Bu menü komutuna gitmek için alt tuşuna basarak odağı <xref:System.Windows.Forms.MenuStrip>verin ve menü adının erişim tuşuna basın. Menü açıldığında ve erişim anahtarlarına sahip öğeleri gösteriyorsa, menü komutunu seçmek için yalnızca erişim tuşuna basmanız gerekir.  
  
> [!NOTE]
> Aynı menü sisteminde ALT + F 'yi iki kez tanımlamak gibi yinelenen erişim anahtarları tanımlamaktan kaçının. Yinelenen erişim anahtarlarının seçim sırası garanti edilemez.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Menü komutları arasında bir ayırıcı çubuk göstermek için  
  
- Uygulamanızı <xref:System.Windows.Forms.MenuStrip> ve içereceği öğeleri tanımladıktan sonra, menü komutlarını ve <xref:System.Windows.Forms.ToolStripSeparator> denetimlerini istediğiniz sırada <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> öğesine <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> <xref:System.Windows.Forms.MenuStrip> eklemek için veya yöntemini kullanın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
