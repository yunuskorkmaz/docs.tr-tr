---
title: Veriye bağlı bir DataGridView denetimine Ilişkisiz sütun ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747069"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme
<xref:System.Windows.Forms.DataGridView> denetiminde görüntülenen veriler normalde bazı tür bir veri kaynağından gelir, ancak veri kaynağından gelmeyen veri sütununu göstermek isteyebilirsiniz. Bu tür bir sütuna ilişkisiz sütun denir. İlişkisiz sütunlar birçok form alabilir. Genellikle, bir veri satırının ayrıntılarına erişim sağlamak için kullanılır.  
  
 Aşağıdaki kod örneği, ana/ayrıntı senaryosunu uyguladığınızda üst tablodaki belirli bir satırla ilgili bir alt tablo göstermek için ilişkisiz bir **ayrıntı** düğmesi sütununun nasıl oluşturulduğunu gösterir. Düğme tıklamalarına yanıt vermek için, alt tabloyu içeren bir form görüntüleyen <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> olay işleyicisi uygulayın.  
  
 Visual Studio 'da bu görev için destek vardır.  Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları](data-display-modes-in-the-windows-forms-datagridview-control.md)
