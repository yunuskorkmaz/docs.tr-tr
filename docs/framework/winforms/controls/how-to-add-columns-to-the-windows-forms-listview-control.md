---
title: ListView Denetimine sütun ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: dd438ffbadddfc37ec9eb15e59a908bb58472a45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744590"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme
Ayrıntılar görünümünde <xref:System.Windows.Forms.ListView> denetimi her liste öğesi için birden çok sütun görüntüleyebilir. Sütunları, her liste öğesiyle ilgili birkaç tür bilgiyi kullanıcıya göstermek için kullanabilirsiniz. Örneğin bir dosya listesi, dosyanın son değiştirilme dosya adını, dosya türünü, boyutunu ve tarihini görüntüleyebilir. Sütunları oluşturulduktan sonra doldurma hakkında daha fazla bilgi için bkz. [nasıl yapılır: alt öğeleri Windows Forms ListView denetimiyle sütunlarda görüntüleme](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Program aracılığıyla sütun eklemek için  
  
1. Denetimin <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details>olarak ayarlayın.  
  
2. Liste görünümünün <xref:System.Windows.Forms.ListView.Columns%2A> özelliğinin <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> yöntemini kullanın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
