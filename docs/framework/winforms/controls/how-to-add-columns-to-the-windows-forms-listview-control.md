---
title: "Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme"
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
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4895d9fbd84ac00291a717e47102f3d0e04176f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme
Ayrıntılar görünümünde <xref:System.Windows.Forms.ListView> denetim her liste öğesi için birden çok sütun görüntüleyebilir. Her liste öğesi hakkında bilgi çeşitli türleri kullanıcıya görüntülenecek sütunları kullanabilirsiniz. Örneğin, dosya adı, dosya türü, boyutu ve dosyanın en son değiştirildiği tarih dosyaların bir listesini görüntüleyebilirsiniz. Oluşturulduktan sonra sütun doldurma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Sütunları programlı olarak eklemek için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.ListView.View%2A> özelliğine <xref:System.Windows.Forms.View.Details>.  
  
2.  Kullanım <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> listesi görünümün yöntemi <xref:System.Windows.Forms.ListView.Columns%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
