---
title: ListView denetimiyle öğe ekleme ve kaldırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: bbfe99db857ebe3a80bf99926f3ce0bec38a1f3f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743144"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma
Bir Windows Forms <xref:System.Windows.Forms.ListView> denetimine öğe ekleme işlemi, öncelikle öğeyi belirtmesinin ve bu öğeye özellikler atamaktan oluşur. Liste öğelerini ekleme veya kaldırma işlemi herhangi bir zamanda yapılabilir.  
  
### <a name="to-add-items-programmatically"></a>Program aracılığıyla öğe eklemek için  
  
1. <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> yöntemini kullanın.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Öğeleri programlı olarak kaldırmak için  
  
1. <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemini kullanın. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> yöntemi tek bir öğeyi kaldırır; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi listedeki tüm öğeleri kaldırır.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
