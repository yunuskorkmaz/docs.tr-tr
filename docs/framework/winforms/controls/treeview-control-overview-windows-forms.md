---
title: TreeView Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 46df8ad1047d34c79348e1db7177d3211b181677
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717057"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView Denetimine Genel Bakış (Windows Forms)

Windows Forms ile <xref:System.Windows.Forms.TreeView> denetimi, kullanıcılara yol dosya ve klasörleri Windows işletim sisteminin Windows Gezgini özelliğinin sol bölmesinde görüntülenen gibi bir hiyerarşi düğümlerinin görüntüleyebilirsiniz. Ağaç görünümünde her düğüm adı verilen, diğer düğümler içerebilir *alt düğümleri*. Üst düğümleri görüntüleyebilir veya alt düğümleri olarak içeren düğümleri genişletilmiş veya daraltılmış. Ağaç görünümünün ayarlayarak düğümleri yanındaki onay kutularını ile ağaç görünümünde görüntüleyebilirsiniz <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> özelliğini `true`. Düğümün ayarlayarak sonra program aracılığıyla seçin veya temizleyin düğümleri yapabilecekleriniz <xref:System.Windows.Forms.TreeNode.Checked%2A> özelliğini `true` veya `false`.

## <a name="key-properties"></a>Anahtar Özellikler

Anahtar özelliklerini <xref:System.Windows.Forms.TreeView> denetimi <xref:System.Windows.Forms.TreeView.Nodes%2A> ve <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Özelliği, ağaç görünümünde en üst düzey düğümlerin listesini içerir. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Özelliği şu anda seçili düğümün ayarlar. Simgeler düğümlerin yanında görüntüleyebilirsiniz. Görüntülerden ekleyeceğini <xref:System.Windows.Forms.ImageList> ağaç görünümünün adlı <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliği. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Özelliği, ağaç görünümünde düğümler için varsayılan görüntü ayarlar. Görüntüleri görüntüleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Visual Studio 2005 kullanıyorsanız, büyük bir kitaplığa ile kullanabileceğiniz standart görüntü erişiminiz <xref:System.Windows.Forms.TreeView> denetimi.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TreeView>
- [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Ekleme ve Windows Forms TreeView denetimi ile düğüm kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView düğümüne tıklandığını belirleme](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)