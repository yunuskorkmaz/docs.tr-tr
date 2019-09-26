---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040071"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TreeView Denetimi ile Düğüm Ekleme ve Kaldırma

Windows Forms <xref:System.Windows.Forms.TreeView> denetimi düğümleri hiyerarşik bir şekilde görüntülediğinden, bir düğüm eklenirken, üst düğümünün ne olduğuna dikkat etmeniz gerekir.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.TreeView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Tasarımcıya düğüm eklemek veya kaldırmak için

1. <xref:System.Windows.Forms.TreeView> Denetimi seçin.

2. **Özellikler** penceresinde](./media/visual-studio-ellipsis-button.png)![, özelliğin<xref:System.Windows.Forms.TreeView.Nodes%2A> yanındaki Visual Studio 'nun Özellikler penceresi (... **) üç nokta (.** ..) düğmesine tıklayın.

     **TreeNode Düzenleyicisi** görünür.

3. Düğüm eklemek için bir kök düğümün mevcut olması gerekir; birisi yoksa, önce **kök Ekle** düğmesine tıklayarak bir kök eklemeniz gerekir. Ardından, kökü veya diğer düğümleri seçerek ve **alt Ekle** düğmesine tıklayarak alt düğümler ekleyebilirsiniz.

4. Düğümleri silmek için, silinecek düğümü seçin ve **Sil** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView denetimi için simgeler ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Windows Forms TreeView denetiminin tüm düğümlerinde yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
