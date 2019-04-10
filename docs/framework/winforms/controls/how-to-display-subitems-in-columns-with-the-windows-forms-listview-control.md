---
title: 'Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 318521cc1377be89ef54706d80c8b2990a6ba1b8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339300"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme
Windows Forms <xref:System.Windows.Forms.ListView> denetim ek metin ya da Ayrıntılar görünümünde her öğenin alt öğelerini görüntüleyebilir. İlk sütun öğesi metni, örneğin çalışan sayısını görüntüler. İkinci, üçüncü ve sonraki sütunları görüntülemek birinci, ikinci ve sonraki ilişkili alt öğesi.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Liste öğesi alt öğesi eklemek için  
  
1. Gerekli tüm sütunları ekleyin. İlk sütun öğenin görüntüleyeceği için <xref:System.Windows.Forms.ListView.Text%2A> özelliği, bir alt öğesi sayısından daha fazla sütun gerekir. Sütunlar ekleme ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: Sütunları Windows Forms ListView denetiminde ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Çağrı <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> yöntemi tarafından döndürülen koleksiyon <xref:System.Windows.Forms.ListViewItem.SubItems%2A> öğenin özellik. Aşağıdaki kod örneği, bir liste öğesi için bölüm ve çalışan adını ayarlar.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
