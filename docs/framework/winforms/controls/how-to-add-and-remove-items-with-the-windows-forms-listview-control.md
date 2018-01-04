---
title: "Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a66d0da6e010efbad77e9544267d1b6af9d1233
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma
Windows Forms için bir öğe ekleme işlemini <xref:System.Windows.Forms.ListView> denetim oluşur öncelikle öğesi belirtme ve Özellikler atayarak. Liste öğe ekleme veya kaldırma herhangi bir zamanda yapılabilir.  
  
### <a name="to-add-items-programmatically"></a>Öğeleri programlı olarak eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ListView.Items%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>Program aracılığıyla öğeleri kaldırmak için  
  
1.  Kullanım <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.ListView.Items%2A> özelliği. <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> Yöntemi, tek bir öğe kaldırır; <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> yöntemi listeden tüm öğeleri kaldırır.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
