---
title: "Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama"
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
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd55034ee97b6e13da8a8a0bdadb8c191ba16ae2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama
İle <xref:System.Windows.Forms.DataGridView> denetimi, belirli sütunları ve satırları ve tüm denetim için varsayılan hücre stillerini belirtebilirsiniz. Bu varsayılan aşağı sütun düzeyi sonra satır düzeyinde sonra hücre düzeyi denetim düzeyden filtreleyin. Belirli bir varsa <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği hücre düzeyinde ayarlanmamışsa, varsayılan özellik ayarı satır düzeyinde kullanılır. Özelliği de satır düzeyinde ayarlanmazsa, varsayılan sütun ayarı kullanılır. Son olarak, özellik de sütun düzeyinde varsayılan ayarlı değil, <xref:System.Windows.Forms.DataGridView> ayarı kullanılır. Bu ayar, birçok düzeyde özellik ayarları çoğaltmak olmamasına özen gösterin. Her düzey, yalnızca yukarıdaki düzeyleri farklı stilleri belirtin. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Visual Studio'da bu görev için kapsamlı destek yoktur.  Ayrıca bkz. [nasıl yapılır: varsayılan hücre stillerini ayarlama ve veri biçimleri Windows Forms DataGridView denetimi kullanan bir tasarımcı](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Varsayılan hücre stilleri programlı olarak ayarlamak için  
  
1.  Özellik kümesinin <xref:System.Windows.Forms.DataGridViewCellStyle> üzerinden alınan <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  Oluşturma ve başlatma yeni <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satır ve sütun tarafından kullanım için.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  Ayarlama `DefaultCellStyle` belirli satırları ve sütunları özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Çok büyük veri kümeleri ile çalışırken en büyük ölçeklenebilirlik elde etmek için paylaşmalıdır <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı ayrı ayrı öğeler stil özelliklerini ayarlamak yerine aynı stilleri kullanın hücreleri nesneleri. Ayrıca, paylaşılan satırlar oluşturmak ve bunları kullanarak erişim <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> özelliği. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetimini ölçeklendirme için en iyi uygulamalar](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetimi için alternatif satır stillerini ayarlama](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
