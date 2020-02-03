---
title: DataGridView denetiminde verileri biçimlendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 9ee2869cf4085b5acfdf1f8c440151be506dbe3e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736778"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme
Aşağıdaki yordamlarda, bir <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliğini ve bir denetimdeki belirli sütunları kullanarak hücre değerlerinin temel biçimlendirilmesi gösterilmektedir. Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: veri biçimlendirmeyi özelleştirme Windows Forms DataGridView denetiminde](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Para birimi ve tarih değerlerini biçimlendirmek için  
  
- Bir <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliğini ayarlayın. Aşağıdaki kod örneği, sütunların <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliğini kullanarak belirli sütunların biçimini ayarlar. `UnitPrice` sütunundaki değerler, parantez içine alınmış negatif değerlerle birlikte geçerli kültüre özgü para birimi biçiminde görüntülenir. `ShipDate` sütunundaki değerler, geçerli kültüre özgü kısa tarih biçiminde görüntülenir. <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> değerler hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Null veritabanı değerlerinin görüntülenmesini özelleştirmek için  
  
- Bir <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliğini ayarlayın. Aşağıdaki kod örneği, <xref:System.DBNull.Value?displayProperty=nameWithType>eşit değerler içeren tüm hücrelerde "No entry" göstermek için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Metin tabanlı hücrelerde WordWrap özelliğini etkinleştirmek için  
  
- Bir <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewTriState> sabit listesi değerlerinden birine ayarlayın. Aşağıdaki kod örneği, tüm denetimin Wrap modunu ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>DataGridView hücrelerinin metin hizalamasını belirtmek için  
  
- Bir <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> özelliğini <xref:System.Windows.Forms.DataGridViewContentAlignment> sabit listesi değerlerinden birine ayarlayın. Aşağıdaki kod örneği, sütunun <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliğini kullanarak belirli bir sütunun hizalamasını ayarlar.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneklerde şunlar gerekir:  
  
- `UnitPrice`adlı bir sütun, `ShipDate`adlı bir sütun ve `CustomerName`adlı bir sütun içeren `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için, her bir öğe için stil özelliklerini ayrı ayrı ayarlamak yerine birden çok satır, sütun veya hücre arasında <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri paylaşabilirsiniz. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
