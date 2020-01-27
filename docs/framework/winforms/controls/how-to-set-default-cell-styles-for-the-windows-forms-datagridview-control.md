---
title: DataGridView denetimi için varsayılan hücre stillerini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744875"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama
<xref:System.Windows.Forms.DataGridView> denetimiyle, tüm denetim için ve belirli sütun ve satırlar için varsayılan hücre stillerini belirtebilirsiniz. Bu varsayılanlar, denetim düzeyinden sütun düzeyine, ardından satır düzeyine, sonra da hücre düzeyine göre filtreleyerek ayarlar. Belirli bir <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği hücre düzeyinde ayarlanmamışsa, satır düzeyindeki varsayılan özellik ayarı kullanılır. Özellik satır düzeyinde de ayarlanmamışsa, varsayılan sütun ayarı kullanılır. Son olarak, özellik sütun düzeyinde de ayarlanmamışsa, varsayılan <xref:System.Windows.Forms.DataGridView> ayarı kullanılır. Bu ayarla, özellik ayarlarını birden çok düzeyde çoğaltmak zorunda kalmaktan kaçınabilirsiniz. Her düzeyde, yukarıdaki düzeyden farklı olan stilleri belirtmeniz yeterlidir. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ve veri biçimlerini ayarlama](default-cell-styles-datagridview.md).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Varsayılan hücre stillerini programlı olarak ayarlamak için  
  
1. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliği aracılığıyla alınan <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. Birden çok satır ve sütun tarafından kullanılmak üzere yeni <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri oluşturun ve başlatın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. Belirli satırların ve sütunların `DefaultCellStyle` özelliğini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Çok büyük veri kümeleriyle çalışırken en yüksek ölçeklenebilirlik elde etmek için, tek tek öğeler için stil özelliklerini ayrı ayrı ayarlamak yerine, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırda, sütunda veya aynı stilleri kullanan hücrelerden paylaşmanız gerekir. Ayrıca, <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> özelliğini kullanarak paylaşılan satırlar oluşturmanız ve bunlara erişmeniz gerekir. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
