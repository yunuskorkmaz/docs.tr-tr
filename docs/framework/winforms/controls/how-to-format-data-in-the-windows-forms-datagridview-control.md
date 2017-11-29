---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme"
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49d5172b2638a7ac3a6a7bf005932ba4b3f9aba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme
Aşağıdaki yordamları kullanarak hücre değerlerini temel biçimlendirme göstermek <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliği bir <xref:System.Windows.Forms.DataGridView> denetim ve bir denetiminde belirli sütunların. Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Biçim para birimi ve tarih değerleri  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde biçimini kullanarak belirli sütunlar için ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sütunların özellik. Değerler `UnitPrice` sütun ayraç içinde kullanılması negatif değerler ile geçerli kültüre özgü para birimi biçiminde görünür. Değerler `ShipDate` sütun geçerli kültüre özgü kısa tarih biçiminde görünür. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> değerler, bakın [biçimlendirme türleri](../../../../docs/standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Null veritabanı değerlerini görüntüsünü özelleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle>. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> eşit değerlerini içeren tüm hücrelerdeki "Giriş" görüntülenecek özellik <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Hücrelerde metin tabanlı wordWrap etkinleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewTriState> numaralandırma değerleri. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> tüm denetim kaydırma modu ayarlamak için özellik.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>DataGridView hücrelerinde metin hizalamasını belirtmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> özelliği bir <xref:System.Windows.Forms.DataGridViewCellStyle> birine <xref:System.Windows.Forms.DataGridViewContentAlignment> numaralandırma değerleri. Aşağıdaki kod örneği kullanarak bir özel sütun için hizalama ayarlar <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> sütunun özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnekler gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `UnitPrice`, adlı bir sütun `ShipDate`ve adlı bir sütun `CustomerName`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için paylaşması gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı her öğe için stil özelliklerini ayarlama yerine aynı stilleri kullanın hücreleri nesneleri. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Veri biçimlendirmeyi Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Biçimlendirme türleri](../../../../docs/standard/base-types/formatting-types.md)
