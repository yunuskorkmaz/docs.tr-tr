---
title: 'Nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetimi'
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
ms.openlocfilehash: 0699aec73c0a48efe88fc2901ef11c70d6f639d7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721287"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetimi
Aşağıdaki yordamlar temel kullanarak hücre değerlerinin biçimlendirilmesi göstermektedir <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği bir <xref:System.Windows.Forms.DataGridView> denetimi ve belirli bir denetim sütun. Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Biçimi para birimi ve tarih değerleri  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneği kullanarak belirli sütunları biçimini ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özellik sütunları. Değerler `UnitPrice` sütunu parantez içine negatif değerler içeren geçerli kültüre özgü para birimi biçiminde görünür. Değerler `ShipDate` sütun geçerli kültüre özgü kısa tarih biçiminde görünür. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> değerleri, görmek [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Boş veritabanı değerlerini görüntüsünü özelleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> "giriş materyali" eşit olan değerleri içeren tüm hücreleri görüntülenecek özelliği <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Hücrelerde metin tabanlı sözcük kaydırmayı etkinleştirme  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewTriState> sabit listesi değerleri. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> eksiksiz bir denetim için kaydırma modu ayarlamak için özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>DataGridView hücrelerinin metin hizalaması belirtmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewContentAlignment> sabit listesi değerleri. Aşağıdaki kod örneği kullanarak belirli bir sütun için hizalamasını ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sütunun özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `UnitPrice`, adlı bir sütun `ShipDate`, adlı bir sütun `CustomerName`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için paylaşmalıdır <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırları, sütunları veya hücreleri stil özellikleri her öğe için ayrı olarak ayarlamak yerine aynı stili kullanın. Daha fazla bilgi için [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
