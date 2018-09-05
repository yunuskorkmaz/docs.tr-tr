---
title: FlowLayoutPanel Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- FlowLayoutPanel
helpviewer_keywords:
- forms [Windows Forms], dynamic layout
- layout [Windows Forms], dynamic
- Windows Forms, dynamic layout
- FlowLayoutPanel control [Windows Forms], about FlowLayoutPanel control
ms.assetid: 3883e024-f5a0-456d-9c27-b4dfa1cc9045
ms.openlocfilehash: 73767114da1c04222fb8ceaf812153421c4597aa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563818"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel Denetimine Genel Bakış
<xref:System.Windows.Forms.FlowLayoutPanel> Denetim akışı yatay veya dikey yönde içeriği düzenler. Denetimin içeriği sonraki bir satır veya sonraki bir sütun sarabilirsiniz. Alternatif olarak, içeriği kaydırmayı yerine bölebilirsiniz.  
  
 Akış yönü değerini ayarlayarak belirtebilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliği. <xref:System.Windows.Forms.FlowLayoutPanel> Denetimi doğru şekilde akış yönünü sağdan sola (RTL) düzeni tersine çevirir. Belirtebilirsiniz olmadığını <xref:System.Windows.Forms.FlowLayoutPanel> denetimin içeriği sarmalanmış veya değerini ayarlayarak kırpılarak <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliği.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ayarladığınızda boyutları için içeriği otomatik olarak Denetim <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`. Ayrıca sağlar bir **FlowBreak** özelliğini, alt denetimlerini. FlowBreak özelliğin değerini ayarlamak `true` neden <xref:System.Windows.Forms.FlowLayoutPanel> sonraki satır veya sütun kaydırılır ve geçerli akış yönü denetimlerinde düzenlemeyi durdurmak için denetimi.  
  
 Herhangi bir Windows Forms denetimini bir alt öğesi olabilir <xref:System.Windows.Forms.FlowLayoutPanel> denetim, diğer örnekleri dahil <xref:System.Windows.Forms.FlowLayoutPanel>. Bu özellik sayesinde, çalışma zamanında formunuzun boyutlarına uyum karmaşık düzenler oluşturabilirsiniz.  
  
 Ayrıca bkz: [izlenecek yol: Windows Forms kullanarak FlowLayoutPanel düzenleme denetimleri](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [FlowLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-windows-forms.md)
