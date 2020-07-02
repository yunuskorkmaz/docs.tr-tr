---
title: DataGridView denetiminde geçerli hücreyi al ve ayarla
description: Windows Forms DataGridView denetiminde geçerli hücreyi alarak ve ayarlayarak, şu anda hangi hücrenin etkin olduğunu programlı bir şekilde bulmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622217"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama
İle etkileşim, <xref:System.Windows.Forms.DataGridView> genellikle hangi hücrenin etkin olduğunu programlı bir şekilde keşfetmenizi gerektirir. Geçerli hücreyi de değiştirmeniz gerekebilir. Bu görevleri özelliği ile gerçekleştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .  
  
> [!NOTE]
> Özelliği olarak ayarlanmış bir satır veya sütundaki geçerli hücreyi ayarlayamazsınız <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> `false` .  
  
 <xref:System.Windows.Forms.DataGridView>Denetimin seçim moduna bağlı olarak, geçerli hücreyi değiştirmek seçimi değiştirebilir. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
### <a name="to-get-the-current-cell-programmatically"></a>Geçerli hücreyi programlı bir şekilde almak için  
  
- <xref:System.Windows.Forms.DataGridView>Denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini kullanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Geçerli hücreyi programlı bir şekilde ayarlamak için  
  
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>Denetimin özelliğini ayarlayın <xref:System.Windows.Forms.DataGridView> . Aşağıdaki kod örneğinde, geçerli hücre satır 0, sütun 1 olarak ayarlanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Windows.Forms.Button>ve adlı `getCurrentCellButton` denetimler `setCurrentCellButton` . Visual C# ' ta, <xref:System.Windows.Forms.Control.Click> her düğmenin olayını örnek kodda ilişkili olay işleyicisine eklemeniz gerekir.  
  
- <xref:System.Windows.Forms.DataGridView>Adlı bir denetim `dataGridView1` .  
  
- <xref:System?displayProperty=nameWithType>Ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Seçim Modları](selection-modes-in-the-windows-forms-datagridview-control.md)
