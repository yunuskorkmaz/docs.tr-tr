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
ms.openlocfilehash: e8aec1915fabb7e18d6dc3ed584d041c273cb78d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama
Hücrelerde görsel görünümünü belirtebilirsiniz bir <xref:System.Windows.Forms.DataGridView> özelliklerini ayarlayarak denetim <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı. Bu sınıfın örnekleri, çeşitli özelliklerinden almak <xref:System.Windows.Forms.DataGridView> sınıf ve bunun yardımcı sınıfları veya örneği <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri atama için bu özellikleri.  
  
 Aşağıdaki yordamlar hücre görünümünü kullanarak temel özelleştirme göstermektedir <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği. Her hücre denetimindeki sütun, satır veya hücre düzeyinde geçersiz kılınmadığı sürece bu özelliği üzerinden belirtilen stillerini devralır. Stil devralma örneği için bkz: [nasıl yapılır: ayarlama varsayılan hücre stilleri Windows Forms DataGridView denetimi için](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Ek kullanımlarını hakkında bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ayrıca bkz. bölümünde listelenen konulara bakın.  
  
 Visual Studio'da bu görev için kapsamlı destek yoktur.  Ayrıca bkz. [nasıl yapılır: varsayılan hücre stillerini ayarlama ve veri biçimleri Windows Forms DataGridView denetimi kullanan bir tasarımcı](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>DataGridView hücrelerinde tarafından kullanılan yazı tipini belirtmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> tüm denetimi için yazı tipini ayarlamak için özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>DataGridView hücrelerinin ön ve arka plan renklerini belirtmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> özelliklerini bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> bu stiller tüm denetim için ayarlamak için özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Seçili DataGridView hücrelerinin ön ve arka plan renklerini belirtmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> özelliklerini bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> bu stiller tüm denetim için ayarlamak için özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için paylaşması gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı her öğe için stil özelliklerini ayarlama yerine aynı stilleri kullanın hücreleri nesneleri. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
