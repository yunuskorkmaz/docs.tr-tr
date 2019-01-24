---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları dondurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: b7a657af2d6caf2217aedf56422f135f0b2d667e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619428"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları dondurma
Kullanıcılar, Windows formlarında gösterilen verileri görüntülerken <xref:System.Windows.Forms.DataGridView> denetimi, bazen için ihtiyaç duydukları tek bir sütun veya sütun kümesi için sık bakın. Örneğin, müşteri bilgilerinin birçok sütunları içeren bir tablo görüntülerken, müşteri adına dışında görünür bölgesi için diğer sütunları etkinleştirme sırasında her zaman görüntülemek yararlıdır.  
  
 Bu davranışı elde etmek için denetiminde sütunları dondurma. Sütun dondurma, tüm sütunları solunda (veya sağdan sola dil komut sağındakiyle) de dondurulmuş. Diğer tüm sütunlar kaydırabilirsiniz sırada dondurulmuş sütun değiştirilmez.  
  
> [!NOTE]
>  Sütun yeniden sıralamayı etkinse, dondurulmuş sütun Grup çözülmüş sütunlardan farklı olarak kabul edilir. Kullanıcı iki grupta sütunları konumlandırabilirsiniz, ancak bunlar bir sütun bir grubundan diğerine taşıyamazsınız.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Özelliği sütunun sütun her zaman bir grid içinde görünür olup olmadığını belirler.  
  
 Visual Studio'da bu görevi için desteği yoktur.  Ayrıca bkz: [nasıl yapılır: Sütunları dondurma Windows Forms DataGridView denetimi Tasarımcısı'nı kullanarak](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).  
  
### <a name="to-freeze-a-column-programmatically"></a>Bir sütunu programlı olarak dondurmak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> özelliğini `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `AddToCartButton`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sütunları yeniden sıralamayı etkinleştirme](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
