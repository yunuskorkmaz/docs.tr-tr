---
title: TreeView Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 44b5e27273d122f38ea00e009302d427305977a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743213"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView Denetimine Genel Bakış (Windows Forms)

Windows Forms <xref:System.Windows.Forms.TreeView> denetimi sayesinde, Windows işletim sisteminin Windows Gezgini özelliğinin sol bölmesinde dosya ve klasörlerin görüntülenme şekli gibi kullanıcılara bir düğüm hiyerarşisi görüntüleyebilirsiniz. Ağaç görünümündeki her düğüm, *alt düğümler*olarak adlandırılan diğer düğümleri içerebilir. Üst düğümleri veya alt düğümleri içeren düğümleri genişletilmiş veya daraltılmış olarak görüntüleyebilirsiniz. Ayrıca ağaç görünümünün <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> özelliğini `true`olarak ayarlayarak, düğümlerin yanındaki onay kutularından bir ağaç görünümü görüntüleyebilirsiniz. Daha sonra, düğümün <xref:System.Windows.Forms.TreeNode.Checked%2A> özelliğini `true` veya `false`olarak ayarlayarak düğümleri programlı bir şekilde seçebilir veya temizleyebilirsiniz.

## <a name="key-properties"></a>Anahtar Özellikler

<xref:System.Windows.Forms.TreeView> denetiminin temel özellikleri <xref:System.Windows.Forms.TreeView.Nodes%2A> ve <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliği, ağaç görünümündeki en üst düzey düğümlerin listesini içerir. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> özelliği şu anda seçili olan düğümü ayarlar. Düğümlerin yanındaki simgeleri görüntüleyebilirsiniz. Denetim, ağaç görünümünün <xref:System.Windows.Forms.TreeView.ImageList%2A> özelliğinde adlı <xref:System.Windows.Forms.ImageList> görüntüleri kullanır. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> özelliği, ağaç görünümündeki düğümler için varsayılan görüntüyü ayarlar. Görüntüleri görüntüleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: simgeleri Windows Forms TreeView denetimi Için ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md). Visual Studio 2005 kullanıyorsanız, <xref:System.Windows.Forms.TreeView> denetimiyle kullanabileceğiniz büyük bir standart görüntü kitaplığına erişirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TreeView>
- [TreeView Denetimi](treeview-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
