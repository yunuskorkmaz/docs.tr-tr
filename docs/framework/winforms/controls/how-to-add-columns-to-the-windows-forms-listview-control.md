---
title: 'Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: eed032ec0bacd50666c30979b33362dabf00d565
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700201"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme
Ayrıntılar görünümünde <xref:System.Windows.Forms.ListView> denetimi, her bir liste öğesi için birden fazla sütun görüntüleyebilirsiniz. Her liste öğesi hakkında bilgi türlerinden kullanıcıya görüntülenecek sütunları kullanabilirsiniz. Örneğin, dosya adı, dosya türü, boyutu ve dosyanın en son değiştirildiği tarih dosyaların listesini görüntüleyebilirsiniz. Oluşturulduktan sonra sütun doldurma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Görüntü denetimiyle Windows sütunlardaki alt öğeleri Forms ListView denetiminde](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Program aracılığıyla sütunlar eklemek için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>.  
  
2.  Kullanım <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> liste görünümünün yöntemi <xref:System.Windows.Forms.ListView.Columns%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ListView>
- [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
