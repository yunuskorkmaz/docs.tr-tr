---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Görüntü Görüntüleme"
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
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b2e06298d0ead9a2dd9fa554af0c42df5d61d56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Görüntü Görüntüleme
Resim veya grafik veri satırında görüntüleyebilirsiniz değerlerinden biri. Genellikle, bu grafik bir çalışanın fotoğraf veya bir şirket logosu şeklinde.  
  
 Resimler ekleme basit veri içinde görüntülediğinizde <xref:System.Windows.Forms.DataGridView> denetim. <xref:System.Windows.Forms.DataGridView> Denetim yerel işler tarafından desteklenen herhangi bir resim biçimi <xref:System.Drawing.Image> OLE yanı sıra sınıfı resim bazı veritabanı tarafından kullanılan biçimi.  
  
 Varsa <xref:System.Windows.Forms.DataGridView> denetimin veri kaynağına sahip bir sütun görüntülerinin, tarafından otomatik olarak görüntülenir <xref:System.Windows.Forms.DataGridView> denetim.  
  
 Aşağıdaki kod örneğinde, katıştırılmış bir kaynaktan bir simge ayıklayın ve her bir görüntü sütunu hücrenin görüntülemek için bir bit eşlem Dönüştür gösterilmiştir. Karşılık gelen görüntülerle metinsel hücre değerlerini değiştirir başka bir örnek için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Adlı bir katıştırılmış simgesi Kaynak `tree.ico`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Drawing?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
