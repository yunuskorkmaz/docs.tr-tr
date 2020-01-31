---
title: Tasarımcıyı kullanarak ListView Denetimine sütun ekleme
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744615"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimine Sütunlar Ekleme

Windows Forms <xref:System.Windows.Forms.ListView> denetimi, **Ayrıntılar** görünümünde her liste öğesi için birden çok sütun görüntüleyebilir. Sütunları, her liste öğesiyle ilgili çeşitli bilgi türlerini göstermek için kullanabilirsiniz. Örneğin bir dosya listesi, dosyanın son değiştirilme dosya adını, dosya türünü, boyutunu ve tarihini görüntüleyebilir. Sütunları oluşturulduktan sonra doldurma hakkında daha fazla bilgi için bkz. [nasıl yapılır: öğeleri Windows Forms ListView denetimiyle sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-columns-in-the-designer"></a>Tasarımcıya sütun eklemek için

1. **Özellikler** penceresinde, denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>olarak ayarlayın.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Columns%2A> özelliğinin yanındaki Visual Studio.](./media/visual-studio-ellipsis-button.png)) Özellikler penceresi **üç nokta düğmesini** (...)![tıklatın.

     **ColumnHeader koleksiyon Düzenleyicisi** görünür.

3. Yeni sütunlar eklemek için **Ekle** düğmesini kullanın. Daha sonra sütun başlığını seçebilir ve metnini (sütunun açıklamalı alt yazısı), metin hizalamasını ve genişliği ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
