---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: a0ef450559a1106de635c6d3b16891c23c41b050
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725057"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama
İçinde <xref:System.Windows.Forms.DataGridView> denetimi, metin kutusu sütunları kullanma diğer sütun türleri otomatik olarak sıralı değildir ancak varsayılan olarak, Otomatik sıralama. Bazen bu Varsayılanları geçersiz kılmak istersiniz. Örneğin, metin, sayı veya numaralandırma hücre değerlerinin yerine görüntüleri görüntüleyebilirsiniz. Görüntüleri sıralanamaz karşın, temel alınan değerleri temsil ettikleri sıralanabilir.  
  
 İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik değeri bir sütunun sıralama davranışını belirler.  
  
 Aşağıdaki yordamda gösterildiği `Priority` sütundan [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Bu sütunu image sütununa ve varsayılan olarak sıralanabilir değil. Otomatik olarak sıralanabilir şekilde, dizeler, ancak gerçek hücre değerlerini içerir.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Bir sütunun sıralama modu ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Priority`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sıralamayı özelleştirme](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
