---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimine Sütunlar Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 10963fcb6d87ed74f73ecf4f1831a56eae5a392d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658454"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimine Sütunlar Ekleme

Windows Forms <xref:System.Windows.Forms.ListView> denetimi, **Ayrıntılar** görünümünde her liste öğesi için birden çok sütun görüntüleyebilir. Sütunları, her liste öğesiyle ilgili çeşitli bilgi türlerini göstermek için kullanabilirsiniz. Örneğin bir dosya listesi, dosyanın son değiştirilme dosya adını, dosya türünü, boyutunu ve tarihini görüntüleyebilir. Sütunları oluşturulduktan sonra doldurma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms ListView denetimiyle](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)alt öğeleri sütunlarda görüntüleyin.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

### <a name="to-add-columns-in-the-designer"></a>Tasarımcıya sütun eklemek için

1. **Özellikler** penceresinde, denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğini olarak <xref:System.Windows.Forms.View.Details>ayarlayın.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Columns%2A> özelliğin yanındaki **üç nokta** ![düğmesini (Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi) (...) tıklayın.

     **ColumnHeader koleksiyon Düzenleyicisi** görünür.

3. Yeni sütunlar eklemek için **Ekle** düğmesini kullanın. Daha sonra sütun başlığını seçebilir ve metnini (sütunun açıklamalı alt yazısı), metin hizalamasını ve genişliği ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle alt öğeleri sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView denetimine özel bilgi ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
