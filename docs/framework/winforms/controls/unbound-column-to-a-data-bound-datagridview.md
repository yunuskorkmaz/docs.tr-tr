---
title: 'Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 40308f7e8cc12dcff5b7d4393645f6a9007cc2b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215845"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme
Görüntü içinde veri <xref:System.Windows.Forms.DataGridView> denetim normalde bir tür veri kaynağından gelir, ancak bir veri kaynağından gelmeyen veri sütununu görüntülemek isteyebilirsiniz. Bu tür bir sütun bağlantısız sütun adı verilir. Bağlanmamış sütunlar birçok biçimde olabilir. Genellikle, bir veri satırı ayrıntılarını erişim sağlamak için kullanılırlar.  
  
 Aşağıdaki kod örneği, bağlantısız sütun oluşturma işlemini gösterir **ayrıntıları** bir alt tabloda gösterilecek düğmeler ilgili bir ana tablodaki belirli bir satır için ana/ayrıntı senaryo uyguladığınızda. Düğme tıklamalarına yanıt verme için uygulayan bir <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> alt tablo içeren bir form görüntüler olay işleyicisi.  
  
 Visual Studio'da bu görevi için desteği yoktur.  Ayrıca bkz: [nasıl yapılır: Ekle ve Kaldır sütunları Windows Forms DataGridView Tasarımcısı'nı kullanarak denetiminde](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
