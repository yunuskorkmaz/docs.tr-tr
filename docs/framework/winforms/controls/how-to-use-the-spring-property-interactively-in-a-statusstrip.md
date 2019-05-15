---
title: 'Nasıl yapılır: Bir StatusStrip içinde Spring Özelliğini Etkileşimli Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: 8750c48d08161260a1dba6ab69098980f25a5d55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589641"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Nasıl yapılır: Bir StatusStrip içinde Spring Özelliğini Etkileşimli Kullanma
Kullanabileceğiniz <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> konumlandırmak için özellik bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimine bir <xref:System.Windows.Forms.StatusStrip> denetimi. <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Özelliği olup olmadığını <xref:System.Windows.Forms.ToolStripStatusLabel> denetimi otomatik olarak mevcut alan doldurulur üzerinde <xref:System.Windows.Forms.StatusStrip> denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> konumlandırmak için özellik bir <xref:System.Windows.Forms.ToolStripStatusLabel> denetimine bir <xref:System.Windows.Forms.StatusStrip> denetimi. <xref:System.Windows.Forms.ToolStripItem.Click> Olay işleyicisi bir özel gerçekleştirir- ya da değerini değiştirmek için (XOR) işlemi <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> özelliği.  
  
 Bu kod örneği kullanmak için derlemek ve uygulamayı çalıştırın ve ardından **Orta (Spring)** üzerinde <xref:System.Windows.Forms.StatusStrip> değerini değiştirmek için Denetim <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> özelliği.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- System.Windows.Forms System.Design ve System.Drawing derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
