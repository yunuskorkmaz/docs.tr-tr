---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933695"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama
İle etkileşim, <xref:System.Windows.Forms.DataGridView> genellikle hangi hücrenin etkin olduğunu programlı bir şekilde keşfetmenizi gerektirir. Geçerli hücreyi de değiştirmeniz gerekebilir. Bu görevleri <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği ile gerçekleştirebilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> Özelliği olarak`false`ayarlanmış bir satır veya sütundaki geçerli hücreyi ayarlayamazsınız.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimin seçim moduna bağlı olarak, geçerli hücreyi değiştirmek seçimi değiştirebilir. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
### <a name="to-get-the-current-cell-programmatically"></a>Geçerli hücreyi programlı bir şekilde almak için  
  
- <xref:System.Windows.Forms.DataGridView> Denetimin<xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini kullanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Geçerli hücreyi programlı bir şekilde ayarlamak için  
  
- <xref:System.Windows.Forms.DataGridView> Denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini ayarlayın. Aşağıdaki kod örneğinde, geçerli hücre satır 0, sütun 1 olarak ayarlanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Windows.Forms.Button>`getCurrentCellButton` ve`setCurrentCellButton`adlı denetimler. Görselde C#, her düğmenin olayını örnek <xref:System.Windows.Forms.Control.Click> kodda ilişkili olay işleyicisine bağlamanız gerekir.  
  
- <xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.  
  
- <xref:System?displayProperty=nameWithType> Ve<xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Seçim Modları](selection-modes-in-the-windows-forms-datagridview-control.md)
