---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme"
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
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 545a3bff5e810f9c0a995366e7f6460930f9e936
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme
İşleyerek herhangi bir hücreyi görünümünü özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CellPainting> olay. Ayıklamak <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Drawing.Graphics> gelen <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Bu <xref:System.Drawing.Graphics>, tüm görünümünü etkileyebilir <xref:System.Windows.Forms.DataGridView> denetimi, ancak genellikle istediğiniz yalnızca şu anda boyanır hücre görünümünü etkiler. <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Özelliği <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> boyama işlemlerinizin şu anda boyanır hücre kısıtlamak olanak tanır.  
  
 Aşağıdaki kod örneğinde tüm hücreleri boyamak bir `ContactName` sütun kullanarak <xref:System.Windows.Forms.DataGridView> denetimin renk düzenini. Her hücrenin metin içeriği içinde boyanır <xref:System.Drawing.Color.Crimson%2A>, ve bir iç dikdörtgen aynı renkte çizilir <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` ile bir `ContactName` gibi Northwind örnek veritabanı müşteriler tablodaki bir sütun.  
  
-   Sistem, System.Windows.Forms ve System.Drawing derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [Windows Forms DataGridView denetimini özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
