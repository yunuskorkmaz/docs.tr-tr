---
title: 'Nasıl yapılır: Windows Forms DataGridView denetimi için alternatif satır stillerini ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: ba5aaec9e66f1d3c66bb50709f6fbd4afde893ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562732"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetimi için alternatif satır stillerini ayarlama
Tablo verileri genellikle kullanıcılara büyük defter benzeri biçimde değişen satırları farklı arka plan renkleri sahip olduğu sunulur. Bu biçim, özellikle fazla sayıda sütun sahip geniş tabloların ile her bir satırdaki hücreleri olduğunu bildirir kullanıcıların kolaylaştırır.  
  
 İle <xref:System.Windows.Forms.DataGridView> denetimi için alternatif satırlar tam stil bilgilerini belirtebilirsiniz. Ön plan rengini ve değişen satırları ayırt etmek için yazı tipini, arka plan rengi, ek olarak bu etkinleştirir stil özellikleri kullanmak ister.  
  
 Visual Studio'da bu görevi için desteği yoktur.  Ayrıca bkz: [nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama](https://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Ayarlamak için alternatif satır stillerini program aracılığıyla  
  
-   Özelliklerini ayarlama <xref:System.Windows.Forms.DataGridViewCellStyle> tarafından döndürülen nesne <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliklerini <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  Stilleri kullanarak belirtilen <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> belirtilen sütun stillerini geçersiz kılma özellikleri ve <xref:System.Windows.Forms.DataGridView> düzey, ancak tek satır ve hücre düzeyinde ayarlanan stilleri tarafından geçersiz kılınır. Daha fazla bilgi için [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için paylaşmalıdır <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırları, sütunları veya hücreleri stil özellikleri her öğe için ayrı olarak ayarlamak yerine aynı stili kullanın. Daha fazla bilgi için [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde yazı tipi ve renk stillerini ayarlama](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
