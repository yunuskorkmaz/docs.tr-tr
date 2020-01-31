---
title: DataGridView Denetiminde Veri biçimlendirmeyi özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], changing colors in DataGridView control [Windows Forms]
- colors [Windows Forms], changing in DataGridView control [Windows Forms]
- data [Windows Forms], formatting in DataGridView control
- DataGridView control [Windows Forms], cell customization
- DataGridView control [Windows Forms], changing cell colors
- Windows Forms, changing colors of DataGridView cells
- DataGridView control [Windows Forms], substituting cell values for display
- data grids [Windows Forms], formatting data
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
ms.openlocfilehash: 6bc1a65b876df842df322db165dc08fcc0c931dc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746783"
---
# <a name="how-to-customize-data-formatting-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme
Aşağıdaki kod örneği, sütunlarının ve değerlerine göre hücrelerin nasıl görüntülendiğini değiştiren <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı için bir işleyicinin nasıl uygulanacağını gösterir.  
  
 Negatif sayılar içeren `Balance` sütununda bulunan hücrelere kırmızı bir arka plan verilir. Bu hücreleri negatif değerlerin etrafında parantez göstermek için para birimi olarak da biçimlendirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki verileri biçimlendirme](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 `Priority` sütunundaki hücreler, ilgili metin hücresi değerlerinin yerine görüntüleri görüntüler. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özelliği, her ikisi de metin hücresi değerini almak ve ilgili görüntü görüntüleme değerini ayarlamak için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
- yürütülebilir dosya ile aynı dizinde bulunan `highPri.bmp`, `mediumPri.bmp`ve `lowPri.bmp` adlı görüntüleri <xref:System.Drawing.Bitmap>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Drawing.Bitmap>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Biçimlendirme](data-formatting-in-the-windows-forms-datagridview-control.md)
