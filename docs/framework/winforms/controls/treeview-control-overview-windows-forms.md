---
title: TreeView Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 6326f8976e20b5b72e1b6690ab323c8581411156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView Denetimine Genel Bakış (Windows Forms)
Windows Forms ile <xref:System.Windows.Forms.TreeView> denetim, kullanıcılara, yol dosyaları ve klasörleri Windows işletim sisteminin Windows Explorer özelliği sol bölmesinde görüntülenen gibi bir hiyerarşi düğümlerinin görüntüleyebilir. Ağaç görünümünde her düğüm olarak adlandırılan, diğer düğümler içerebilir *alt düğümleri*. Üst düğüm görüntüleyebilir veya alt düğümleri olarak içeren düğümler genişletilen veya daraltılmış. Ağaç görünümün ayarlayarak düğümleri yanındaki onay kutularını bulunduğu ağaç görünümü görüntüleyebilirsiniz <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> özelliğine `true`. Ardından program aracılığıyla seçin veya temizleyin düğümleri düğümün ayarlayarak yapabilirsiniz <xref:System.Windows.Forms.TreeNode.Checked%2A> özelliğine `true` veya `false`.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Anahtar özelliklerini <xref:System.Windows.Forms.TreeView> denetim <xref:System.Windows.Forms.TreeView.Nodes%2A> ve <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Özelliği, ağaç görünümünde üst düzey düğüm listesi içerir. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Özelliği şu anda seçili düğümün ayarlar. Düğümleri yanındaki simge görüntüleyebilirsiniz. Görüntülerden ekleyeceğini <xref:System.Windows.Forms.ImageList> ağaç görünümünde 's adlı <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliği. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Özelliği, ağaç görünümünde düğümler için varsayılan görüntü ayarlar. Görüntüleri görüntüleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Kullanıyorsanız [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], büyük bir kitaplığı ile birlikte kullanabileceğiniz standart görüntülerinin erişimi <xref:System.Windows.Forms.TreeView> denetim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TreeView>  
 [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
