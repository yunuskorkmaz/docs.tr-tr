---
title: ListView denetimiyle alt öğeleri sütunlarda görüntüleme
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
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745551"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme
Windows Forms <xref:System.Windows.Forms.ListView> denetimi, Ayrıntılar görünümündeki her öğe için ek metin veya alt öğeleri görüntüleyebilir. İlk sütunda öğe metni, örneğin bir çalışan numarası görüntülenir. İkinci, üçüncü ve sonraki sütunlar birinci, ikinci ve sonraki ilişkili alt öğeleri görüntüler.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Bir liste öğesine alt öğeleri eklemek için  
  
1. Gereken sütunları ekleyin. İlk sütunda öğenin <xref:System.Windows.Forms.ListView.Text%2A> özelliği görüntülendiği için, alt öğeleri olan bir sütundan daha fazla olması gerekir. Sütun ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: sütunları Windows Forms ListView denetimine ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2. Bir öğenin <xref:System.Windows.Forms.ListViewItem.SubItems%2A> özelliği tarafından döndürülen koleksiyonun <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> yöntemini çağırın. Aşağıdaki kod örneği, bir liste öğesi için çalışan adı ve departmanı belirler.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
