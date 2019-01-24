---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminin seçim modunu ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
- data grids [Windows Forms], selection mode
ms.assetid: 2f241643-7f82-4583-8757-03494f63b465
ms.openlocfilehash: 65fb7360d45baea4fff20d06316d3955f0064207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539746"
---
# <a name="how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminin seçim modunu ayarlama
Aşağıdaki kod örneğinde nasıl yapılandırılacağını gösteren bir <xref:System.Windows.Forms.DataGridView> denetim böylece satır içinde otomatik olarak herhangi bir yere tıklayarak tüm satırı seçer ve bu nedenle aynı anda yalnızca bir satır seçilebilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#065)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#065](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#065)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Seçim Modları](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
