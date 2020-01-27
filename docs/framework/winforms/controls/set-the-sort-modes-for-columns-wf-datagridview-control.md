---
title: DataGridView Denetimindeki sütunlar için sıralama modlarını ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743004"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama
<xref:System.Windows.Forms.DataGridView> denetiminde metin kutusu sütunları otomatik sıralamayı varsayılan olarak kullanır, diğer sütun türleri otomatik olarak sıralanmaz. Bazen bu Varsayılanları geçersiz kılmak isteyeceksiniz. Örneğin, resimleri metin, sayı veya numaralandırma hücresi değerlerinin yerine görüntüleyebilirsiniz. Görüntüler sıralanamadığından, temsil ettikleri temel değerler sıralanabilir.  
  
 <xref:System.Windows.Forms.DataGridView> denetiminde, bir sütunun <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliği değeri sıralama davranışını belirler.  
  
 Aşağıdaki yordamda, [Windows Forms DataGridView Denetimindeki nasıl yapılır: veri biçimlendirmesini özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)`Priority` sütunu gösterilmektedir. Bu sütun bir resim sütunudur ve varsayılan olarak sıralanabilir değildir. Ancak, dizeler olan gerçek hücre değerlerini içerir, bu nedenle otomatik olarak sıralanabilir.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Bir sütunun sıralama modunu ayarlamak için  
  
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özelliğini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `Priority`adlı bir sütun içeren `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
