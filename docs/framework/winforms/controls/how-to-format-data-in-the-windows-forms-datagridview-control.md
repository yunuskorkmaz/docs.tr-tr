---
title: DataGridView denetiminde verileri biçimlendirme
description: Windows Forms DataGridView denetiminin DefaultCellStyle özelliğini kullanarak hücre değerlerini biçimlendirmeyi ve denetimdeki belirli sütunları kullanmayı öğrenin.
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
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622815"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme
Aşağıdaki yordamlarda, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> bir denetimin özelliğini <xref:System.Windows.Forms.DataGridView> ve bir denetimdeki belirli sütunları kullanarak hücre değerlerinin temel biçimlendirmesi gösterilmektedir. Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: veri biçimlendirmeyi özelleştirme Windows Forms DataGridView denetiminde](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Para birimi ve tarih değerlerini biçimlendirmek için  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>Öğesinin özelliğini ayarlayın <xref:System.Windows.Forms.DataGridViewCellStyle> . Aşağıdaki kod örneği, sütunların özelliğini kullanarak belirli sütunların biçimini ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> . `UnitPrice`Sütundaki değerler, parantez içine alınmış negatif değerlerle birlikte geçerli kültüre özgü para birimi biçiminde görüntülenir. `ShipDate`Sütundaki değerler geçerli kültüre özgü kısa tarih biçiminde görüntülenir. Değerler hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Null veritabanı değerlerinin görüntülenmesini özelleştirmek için  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>Öğesinin özelliğini ayarlayın <xref:System.Windows.Forms.DataGridViewCellStyle> . Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> değerine eşit değer içeren tüm hücrelerde "giriş yok" göstermek için özelliğini kullanır <xref:System.DBNull.Value?displayProperty=nameWithType> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Metin tabanlı hücrelerde WordWrap özelliğini etkinleştirmek için  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>Öğesinin özelliğini <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewTriState> sabit listesi değerlerinden birine ayarlayın. Aşağıdaki kod örneği, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> tüm denetim için Wrap modunu ayarlamak için özelliğini kullanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>DataGridView hücrelerinin metin hizalamasını belirtmek için  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>Öğesinin özelliğini <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewContentAlignment> sabit listesi değerlerinden birine ayarlayın. Aşağıdaki kod örneği, sütununun özelliğini kullanarak belirli bir sütunun hizalamasını ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneklerde şunlar gerekir:  
  
- Adında bir sütun, adlı bir sütun ve adlı bir sütun <xref:System.Windows.Forms.DataGridView> içeren adlı bir denetim `dataGridView1` `UnitPrice` `ShipDate` `CustomerName` .  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> Ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerinin başvuruları.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri her öğe için stil özelliklerini ayrı ayrı ayarlamak yerine, aynı stilleri kullanan birden çok satır, sütun veya hücrede paylaşabilirsiniz. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [Biçimlendirme Türleri](../../../standard/base-types/formatting-types.md)
