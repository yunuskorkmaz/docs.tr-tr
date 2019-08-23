---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966653"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Dondurma
Kullanıcılar bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminde görüntülendiklerinde verileri görüntülerken, bazen tek bir sütuna veya sütun kümesine sıklıkla başvurmaları gerekir. Örneğin, çok sayıda sütun içeren bir müşteri bilgileri tablosu görüntülenirken, diğer sütunların görünür bölgenin dışına kaymasını sağlayan müşteri adını her zaman görüntülemek yararlı olur.  
  
 Bu davranışı başarmak için denetimdeki sütunları dondurabilirsiniz. Bir sütunu dondurduktan sonra, sol tarafında (veya sağdan sola dil betiklerine ait olan) tüm sütunlar da dondurulur. Dondurulmuş sütunlar, diğer tüm sütunlar kaydırılarken yerinde kalır.  
  
> [!NOTE]
> Sütun yeniden sıralama etkinse, Dondurulmuş sütunlar dondurulmamış sütunlardan farklı bir grup olarak değerlendirilir. Kullanıcılar her iki gruptaki sütunları yeniden konumlandırabilirsiniz, ancak bir sütunu bir gruptan diğerine taşıyamaz.  
  
 Bir <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> sütunun özelliği, sütunun kılavuz içinde her zaman görünür olup olmadığını belirler.  
  
 Visual Studio 'da bu görev için destek vardır.  Ayrıca bkz [. nasıl yapılır: Tasarımcıyı](freeze-columns-in-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView Denetimindeki sütunları dondurma.  
  
### <a name="to-freeze-a-column-programmatically"></a>Bir sütunu programlı bir şekilde dondurmak için  
  
- Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğini `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Adında <xref:System.Windows.Forms.DataGridView> bir sütun içerenadlı`dataGridView1` bir denetim. `AddToCartButton`  
  
- <xref:System?displayProperty=nameWithType> Ve<xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sütun yeniden sıralamayı etkinleştir](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
