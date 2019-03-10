---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminin hücrelerinde görüntü görüntüleme'
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
ms.openlocfilehash: 280f274a0957f098add7fbf2e3b919c33c4c5233
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704417"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminin hücrelerinde görüntü görüntüleme
Bir resim veya grafik veri satırında görüntüleyebilen değerlerinden biri. Genellikle, bu grafik bir çalışanın fotoğraf veya bir şirket logosu biçiminde.  
  
 Resim ekleme basit veri içinde görüntülediğinizde <xref:System.Windows.Forms.DataGridView> denetimi. <xref:System.Windows.Forms.DataGridView> Denetimi tarafından desteklenen herhangi bir resim biçimi yerel olarak işleme <xref:System.Drawing.Image> OLE yanı sıra, sınıf resim bazı veritabanları tarafından kullanılan biçimi.  
  
 Varsa <xref:System.Windows.Forms.DataGridView> tarafından otomatik olarak görüntülenir, denetiminin veri kaynağına sahip bir sütun görüntülerin <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 Aşağıdaki kod örneği, katıştırılmış bir kaynaktan bir simgeyi çıkarma ve bir bit eşlem görüntülenmek üzere her bir hücresinde göreceğiniz bir görüntü sütunu Dönüştür gösterilmektedir. Metinsel hücre değerlerine karşılık gelen görüntülerle değiştiren başka bir örnek için bkz [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Adlı bir katıştırılmış simge kaynağı `tree.ico`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Drawing?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
