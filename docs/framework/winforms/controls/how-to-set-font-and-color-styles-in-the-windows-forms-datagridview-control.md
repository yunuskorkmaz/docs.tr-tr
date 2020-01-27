---
title: DataGridView denetiminde yazı tipi ve renk stillerini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746750"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama
<xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının özelliklerini ayarlayarak <xref:System.Windows.Forms.DataGridView> denetim içindeki hücrelerin görsel görünümünü belirtebilirsiniz. Bu sınıfın örneklerini <xref:System.Windows.Forms.DataGridView> sınıfının ve yardımcı sınıflarının çeşitli özelliklerinden alabilir veya bu özelliklere atanmak üzere <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri örnekleyebilirsiniz.  
  
 Aşağıdaki yordamlarda <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliğini kullanarak hücre görünümünün temel özelleştirmesi gösterilmektedir. Denetimdeki her hücre, sütun, satır veya hücre düzeyinde geçersiz kılınmadıkça, bu özellik ile belirtilen stilleri devralır. Stil devralmayla ilgili bir örnek için bkz. [nasıl yapılır: Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının ek kullanımları hakkında daha fazla bilgi için Ayrıca bkz. bölümünde listelenen konulara bakın.  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ve veri biçimlerini ayarlama](default-cell-styles-datagridview.md).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>DataGridView hücreleri tarafından kullanılan yazı tipini belirtmek için  
  
- Bir <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özelliğini ayarlayın. Aşağıdaki kod örneği, tüm denetimin yazı tipini ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>DataGridView hücrelerinin ön plan ve arka plan renklerini belirtmek için  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> özelliklerini ayarlayın. Aşağıdaki kod örneği, tüm denetimin bu stillerini ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Seçili DataGridView hücrelerinin ön plan ve arka plan renklerini belirtmek için  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> özelliklerini ayarlayın. Aşağıdaki kod örneği, tüm denetimin bu stillerini ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için, her bir öğe için stil özelliklerini ayrı ayrı ayarlamak yerine, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırda, sütunda veya aynı stilleri kullanan hücrelerde paylaşabilirsiniz. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
