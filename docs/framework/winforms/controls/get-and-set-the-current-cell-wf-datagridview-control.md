---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b53d135a1d019ce20dfc8c5c2c1ba59e5968306e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama
Etkileşim <xref:System.Windows.Forms.DataGridView> hangi hücrenin şu anda etkin olan program aracılığıyla bulmak, genellikle gerektirir. Geçerli hücreyi değiştirmeniz gerekebilir. Bu görevleri gerçekleştirebilir <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.  
  
> [!NOTE]
>  Bir satır veya sahip sütunu geçerli hücre ayarlanamıyor kendi <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özelliğini `false`.  
  
 Bağlı olarak <xref:System.Windows.Forms.DataGridView> geçerli hücreyi değiştirme denetiminin seçim modunu seçimi değiştirebilirsiniz. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki seçim modları](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Geçerli hücreyi programlı olarak almak için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Geçerli hücreyi programlı olarak ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği <xref:System.Windows.Forms.DataGridView> denetim. Aşağıdaki kod örneğinde, 0, 1 sütunu satır için geçerli hücreyi ayarlanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   <xref:System.Windows.Forms.Button> adlı denetimleri `getCurrentCellButton` ve `setCurrentCellButton`. Visual C# ' ta, eklemelisiniz <xref:System.Windows.Forms.Control.Click> kod örneği ilişkili olay işleyicisini her düğme için olayları.  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Windows Forms DataGridView Denetimindeki Seçim Modları](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
