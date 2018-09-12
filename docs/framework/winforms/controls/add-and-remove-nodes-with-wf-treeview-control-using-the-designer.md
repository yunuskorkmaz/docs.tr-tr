---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 95f3f097d8e01828f2727bac742c752b656019e5
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708977"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma
Windows Forms çünkü <xref:System.Windows.Forms.TreeView> denetimi dikkat kendi üst düğümlerinin nedir için ödeme gerekir düğüm eklerken bu düğümleri hiyerarşik bir biçimde görüntüler.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.TreeView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Ekleme veya düğümleri kaldırma Tasarımcısı'nda  
  
1.  Seçin <xref:System.Windows.Forms.TreeView> denetimi.  
  
2.  İçinde **özellikleri** penceresinde tıklayın **üç nokta** (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) düğmesinin yanındaki <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği.  
  
     **Editor objektu TreeNode** görünür.  
  
3.  Düğümler eklemek için bir kök düğümü olmalıdır; bir mevcut değilse, öncelikle bir kök tıklayarak eklemelisiniz **ekleme kök** düğmesi. Kök veya başka bir düğüme seçtikten sonra alt düğümleri ekleyebilirsiniz **alt öğe Ekle** düğmesi.  
  
4.  Düğümleri silmek için silin ve ardından için düğümü seçin **Sil** düğmesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
