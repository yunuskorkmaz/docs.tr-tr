---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: fd627e3aaed7330a05c46b9e2ca0a213404e0bfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625744"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama
İçinde <xref:System.Windows.Forms.DataGridView> denetimi, metin kutusu sütunları kullanma diğer sütun türleri otomatik olarak sıralı değildir ancak varsayılan olarak, Otomatik sıralama. Bazen bu Varsayılanları geçersiz kılmak istersiniz. Örneğin, metin, sayı veya numaralandırma hücre değerlerinin yerine görüntüleri görüntüleyebilirsiniz. Görüntüleri sıralanamaz karşın, temel alınan değerleri temsil ettikleri sıralanabilir.  
  
 İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik değeri bir sütunun sıralama davranışını belirler.  
  
 Aşağıdaki yordamda gösterildiği `Priority` sütundan [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Bu sütunu image sütununa ve varsayılan olarak sıralanabilir değil. Otomatik olarak sıralanabilir şekilde, dizeler, ancak gerçek hücre değerlerini içerir.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Bir sütunun sıralama modu ayarlamak için  
  
- Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Priority`.  
  
- Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sıralamayı özelleştirme](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
