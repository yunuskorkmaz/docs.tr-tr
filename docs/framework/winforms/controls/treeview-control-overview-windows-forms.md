---
title: TreeView Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: cc3fb394a2c55b7095a8111e7018b754985ab0e1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793597"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView Denetimine Genel Bakış (Windows Forms)

Windows Forms ile <xref:System.Windows.Forms.TreeView> denetimi, kullanıcılara yol dosya ve klasörleri Windows işletim sisteminin Windows Gezgini özelliğinin sol bölmesinde görüntülenen gibi bir hiyerarşi düğümlerinin görüntüleyebilirsiniz. Ağaç görünümünde her düğüm adı verilen, diğer düğümler içerebilir *alt düğümleri*. Üst düğümleri görüntüleyebilir veya alt düğümleri olarak içeren düğümleri genişletilmiş veya daraltılmış. Ağaç görünümünün ayarlayarak düğümleri yanındaki onay kutularını ile ağaç görünümünde görüntüleyebilirsiniz <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> özelliğini `true`. Düğümün ayarlayarak sonra program aracılığıyla seçin veya temizleyin düğümleri yapabilecekleriniz <xref:System.Windows.Forms.TreeNode.Checked%2A> özelliğini `true` veya `false`.

## <a name="key-properties"></a>Anahtar Özellikler

Anahtar özelliklerini <xref:System.Windows.Forms.TreeView> denetimi <xref:System.Windows.Forms.TreeView.Nodes%2A> ve <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Özelliği, ağaç görünümünde en üst düzey düğümlerin listesini içerir. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Özelliği şu anda seçili düğümün ayarlar. Simgeler düğümlerin yanında görüntüleyebilirsiniz. Görüntülerden ekleyeceğini <xref:System.Windows.Forms.ImageList> ağaç görünümünün adlı <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliği. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Özelliği, ağaç görünümünde düğümler için varsayılan görüntü ayarlar. Görüntüleri görüntüleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Visual Studio 2005 kullanıyorsanız, büyük bir kitaplığa ile kullanabileceğiniz standart görüntü erişiminiz <xref:System.Windows.Forms.TreeView> denetimi.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Windows.Forms.TreeView>
- [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)