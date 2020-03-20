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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>Nasıl yapılır: ToolStripMenuItems'ne Geliştirmeler Ekleme
Aşağıdaki yollarla kullanılabilirliğini <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> ve denetimlerini artırabilirsiniz:  
  
- Bir özelliğin açık mı yoksa kapalı mı olduğunu (sözcük işleme uygulamasının kenar boşluğunda bir cetvelin görüntülenip görüntülenmediğini belirtmek veya **Pencere** menüsündeki gibi dosyalar listesindeki hangi dosyanın görüntülendiğini belirtmek için) işaret ekleyin.  
  
- Menü komutlarını görsel olarak temsil eden görüntüler ekleyin.  
  
- Komutları gerçekleştirmek için fareye bir klavye alternatifi sağlamak için kısayol tuşlarını görüntüleyin. Örneğin, CTRL+C tuşuna basarak **Kopyala** komutu gerçekleştirir.  
  
- Menü gezintisi için fareye bir klavye alternatifi sağlamak için erişim tuşlarını görüntüleyin. Örneğin, ALT+F tuşuna basmak **Dosya** menüsünü seçer.  
  
- Ayırıcı çubuklarını grupla ilgili komutlara göster ve menüleri daha okunabilir hale getirin.  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>Menü komutunda onay işareti görüntülemek için  
  
- Özelliğini <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> `true`.  
  
     Bu da <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> özelliği `true`. Bu yordamı yalnızca seçilip seçilmediğine bakılmaksızın menü komutunun varsayılan olarak denetlenmiş olarak görünmesini istiyorsanız kullanın.  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>Her tıklamayla durumu değiştiren bir onay işareti görüntülemek için  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> özelliğini `true`' ' ye ayarlayın  
  
### <a name="to-add-an-image-to-a-menu-command"></a>Menü komutuna resim eklemek için  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripItem.Image%2A> özelliğini görüntünün adına ayarlayın. Bu <xref:System.Windows.Forms.ToolStripItemDisplayStyle> menü komutunun özelliği <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ayarlanmışsa veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, görüntü görüntülenemez.  
  
> [!NOTE]
> Eğer isterseniz görüntü kenar boşluğu da bir onay işareti gösterebilir. Ayrıca, görüntünün <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> özelliğini `true`,' olarak ayarlayabilirsiniz ve görüntü çalışma zamanında etrafında yumurtadan çıkmış bir kenarlık ile görünür.  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>Menü komutu için kısayol tuşu görüntülemek için  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> özelliğini, **Açık** menü komutu için CTRL+O gibi istenilen <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> klavye `true`birleşimine ayarlayın ve özelliği ' ye ayarlayın.  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>Menü komutu için özel kısayol tuşlarını görüntülemek için  
  
- Menü komutunun <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> özelliğini SHIFT+CTRL+O yerine CTRL+SHIFT+O gibi istenen klavye kombinasyonuna <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> ayarlayın `true`ve özelliği ' ye ayarlayın.  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>Menü komutu için erişim anahtarı görüntülemek için  
  
- Menü komutu <xref:System.Windows.Forms.ToolStripItem.Text%2A> için özelliği ayarladığınızda, erişim anahtarı olarak altı çizili olmasını istediğiniz harften önce bir ampersand (&) girin. Örneğin, bir `&Open` menü <xref:System.Windows.Forms.ToolStripItem.Text%2A> öğesinin özelliği olarak yazmak, <u>O</u>kalem için günü nüründe görünen bir menü komutuyla sonuçlanır.
  
     Bu menü komutuna gitmek için ALT <xref:System.Windows.Forms.MenuStrip>tuşuna basın ve menü adının erişim tuşuna basın. Menü açıldığında ve erişim tuşlarına sahip öğeler gösterildiğinde, menü komutunu seçmek için erişim tuşuna basmanız yeterlidir.  
  
> [!NOTE]
> Aynı menü sisteminde ALT+F'yi iki kez tanımlamak gibi yinelenen erişim anahtarlarını tanımlamaktan kaçının. Yinelenen erişim anahtarlarının seçim sırası garanti edilemez.  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>Menü komutları arasında ayırıcı çubuğu görüntülemek için  
  
- Sizin <xref:System.Windows.Forms.MenuStrip> ve içerdiği öğeleri tanımladıktan sonra, <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> menü komutlarını ve <xref:System.Windows.Forms.ToolStripSeparator> denetimlerini istediğiniz <xref:System.Windows.Forms.MenuStrip> sıraya eklemek için veya yöntemi kullanın.  
  
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
