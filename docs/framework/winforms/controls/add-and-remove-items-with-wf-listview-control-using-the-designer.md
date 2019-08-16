---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040081"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma

Bir Windows Forms <xref:System.Windows.Forms.ListView> denetimine öğe ekleme işlemi, öncelikle öğeyi belirtmektir ve bu öğeye özellikler atamaktan oluşur. Liste öğelerini ekleme veya kaldırma işlemi herhangi bir zamanda yapılabilir.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

### <a name="to-add-or-remove-items-using-the-designer"></a>Tasarımcı kullanarak öğe eklemek veya kaldırmak için

1. <xref:System.Windows.Forms.ListView> Denetimi seçin.

2. **Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.ListView.Items%2A> yanındaki Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi (...) üç nokta (...) düğmesine tıklayın.

     **ListViewItem koleksiyonu Düzenleyicisi** görünür.

3. Bir öğe eklemek için **Ekle** düğmesine tıklayın. Ardından, <xref:System.Windows.Forms.ListView.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.

4. Bir öğeyi kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine sütun ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle alt öğeleri sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Nasıl yapılır: Windows Forms ListView denetimindeki öğeleri gruplandırma](how-to-group-items-in-a-windows-forms-listview-control.md)
