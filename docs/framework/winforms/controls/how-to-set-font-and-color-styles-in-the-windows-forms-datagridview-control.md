---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama'
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
ms.openlocfilehash: ad2426ed9643fd46927c4f8b6373fedbec372d38
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638102"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama
Hücreleri görsel görünümünü belirtebilirsiniz bir <xref:System.Windows.Forms.DataGridView> denetim özelliklerini ayarlayarak <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı. Bu sınıfın örnekleri çeşitli özelliklerinden alabilirsiniz <xref:System.Windows.Forms.DataGridView> sınıf ve bunun yardımcı sınıfları veya örneği <xref:System.Windows.Forms.DataGridViewCellStyle> atama bu özellikler için nesneleri.  
  
 Aşağıdaki yordamlar hücre görünümü kullanarak temel bir özelleştirme göstermektedir <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği. Her hücre denetimindeki sütun, satır veya hücre düzeyinde geçersiz kılınmadığı sürece, bu özelliği belirtilen stilleri devralır. Stil devralımı örneği için bkz: [nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Ek kullanımı hakkında bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ayrıca bkz. bölümünde listelenen konulara bakın.  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  Ayrıca bkz: [nasıl yapılır: DataGridView denetimi Tasarımcı kullanarak Windows formları için varsayılan hücre stilleri ve veri biçimleri ayarlama](default-cell-styles-datagridview.md).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>DataGridView hücrelerinin tarafından kullanılan yazıtipi belirtmek için  
  
- Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> tüm denetim yazı tipini ayarlamak için özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>DataGridView hücrelerinin ön ve arka plan renkleri belirtmek için  
  
- Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> özelliklerini bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> bu stiller tüm denetim için ayarlanacak özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Seçili DataGridView hücrelerinin ön ve arka plan renkleri belirtmek için  
  
- Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> özelliklerini bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> bu stiller tüm denetim için ayarlanacak özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
- Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için paylaşmalıdır <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırları, sütunları veya hücreleri stil özellikleri her öğe için ayrı olarak ayarlamak yerine aynı stili kullanın. Daha fazla bilgi için [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
