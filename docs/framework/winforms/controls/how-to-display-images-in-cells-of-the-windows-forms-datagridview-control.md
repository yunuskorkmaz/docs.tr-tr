---
title: DataGridView denetiminin hücrelerinde görüntü görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740280"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Hücrelerinde Resim Görüntüleme
Bir resim veya grafik, bir veri satırında görüntülenebilecek değerlerden biridir. Genellikle, bu grafikler bir çalışanın fotoğrafı veya şirket logosu biçimini alır.  
  
 <xref:System.Windows.Forms.DataGridView> denetimi içinde veri görüntülediğinizde resimleri eklemek basittir. <xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Drawing.Image> sınıfının desteklediği tüm görüntü biçimlerini ve bazı veritabanları tarafından kullanılan OLE resim biçimini yerel olarak işler.  
  
 <xref:System.Windows.Forms.DataGridView> denetimin veri kaynağında bir görüntü sütunu varsa, bu, <xref:System.Windows.Forms.DataGridView> denetimi tarafından otomatik olarak görüntülenir.  
  
 Aşağıdaki kod örneği, gömülü bir kaynaktan bir simgenin nasıl ayıklanacağını ve bir görüntü sütununun her hücresinde görüntülenmek üzere bir bit eşlem 'e nasıl dönüştürüleceğini gösterir. Metin hücresi değerlerini karşılık gelen görüntülerle değiştiren başka bir örnek için, bkz. [nasıl yapılır: veri biçimlendirmeyi özelleştirme Windows Forms DataGridView denetiminde](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- `tree.ico`adlı gömülü bir simge kaynağı.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>ve <xref:System.Drawing?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
