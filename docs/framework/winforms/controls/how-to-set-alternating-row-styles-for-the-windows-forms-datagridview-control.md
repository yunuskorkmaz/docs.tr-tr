---
title: DataGridView denetimi için alternatif satır stillerini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: b87ad50ef7e5118a95998949bc62299955856b27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747127"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama
Tablo verileri genellikle, değişen satırlarda farklı arka plan rengine sahip olan bir defter benzeri biçimde kullanıcılara sunulur. Bu biçim, özellikle çok sayıda sütunu olan geniş tablolar ile, kullanıcıların her satırda hangi hücrelerin olduğunu söylemesini kolaylaştırır.  
  
 <xref:System.Windows.Forms.DataGridView> denetimiyle, değişen satırlar için tüm stil bilgilerini belirtebilirsiniz. Bu, alternatif satırları ayırt etmek için arka plan rengine ek olarak, ön plan rengi ve yazı tipi gibi stil özellikleri kullanmanıza olanak sağlar.  
  
 Visual Studio 'da bu görev için destek vardır.  Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetimi Için alternatif satır stillerini ayarlama](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Alternatif satır stillerini programlı olarak ayarlamak için  
  
- <xref:System.Windows.Forms.DataGridView><xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özellikleri tarafından döndürülen <xref:System.Windows.Forms.DataGridViewCellStyle> nesnelerinin özelliklerini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özellikleri kullanılarak belirtilen stiller, sütun ve <xref:System.Windows.Forms.DataGridView> düzeyinde belirtilen stilleri geçersiz kılar, ancak tek satır ve hücre düzeyinde ayarlanan stiller tarafından geçersiz kılınır. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 En yüksek ölçeklenebilirlik için, her bir öğe için stil özelliklerini ayrı ayrı ayarlamak yerine, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırda, sütunda veya aynı stilleri kullanan hücrelerde paylaşabilirsiniz. Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
