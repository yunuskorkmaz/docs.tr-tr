---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: b7206d2896ad391f8a45e1fbb612cdb49004182d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama
Tablo verisi genellikle defter benzeri biçimde kullanıcılara değişik satırların farklı arka plan renklerini sahip olduğu sunulur. Bu biçim, kullanıcıların her satırda, özellikle çok sayıda sütuna sahip geniş tablolar ile hangi hücrelerin olduğunu bildirir kolaylaştırır.  
  
 İle <xref:System.Windows.Forms.DataGridView> denetimi satırların değişerek için tam stil bilgilerini belirtebilirsiniz. Stil özelliklerini kullanmak bu etkinleştirir, ön plan rengini ve değişen satırları ayırt etmek için yazı tipi, arka plan rengi, ek olarak gibi.  
  
 Visual Studio'da bu görev için desteği yoktur.  Ayrıca bkz. [nasıl yapılır: ayarlama Alternatif satır stillerini Windows Forms DataGridView denetimi kullanan bir tasarımcı](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Ayarlamak için alternatif satır stillerini program aracılığıyla  
  
-   Özellik kümesinin <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen nesne <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliklerini <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  Kullanarak belirtilen stillerini <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özellikler sütunu belirtilen stillerini geçersiz kılar ve <xref:System.Windows.Forms.DataGridView> düzey, ancak tek tek satır ve hücre düzeyinde ayarlanan stilleri tarafından geçersiz kılınır. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için paylaşması gerekir <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı her öğe için stil özelliklerini ayarlama yerine aynı stilleri kullanın hücreleri nesneleri. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
