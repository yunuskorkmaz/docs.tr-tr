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
ms.openlocfilehash: 260146cd901fe2b80a73c01060ccd55958cd169e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203047"
---
# <a name="flowlayoutpanel-control-overview"></a>FlowLayoutPanel Denetimine Genel Bakış
<xref:System.Windows.Forms.FlowLayoutPanel> Denetim akışı yatay veya dikey yönde içeriği düzenler. Denetimin içeriği sonraki bir satır veya sonraki bir sütun sarabilirsiniz. Alternatif olarak, içeriği kaydırmayı yerine bölebilirsiniz.  
  
 Akış yönü değerini ayarlayarak belirtebilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> özelliği. <xref:System.Windows.Forms.FlowLayoutPanel> Denetimi doğru şekilde akış yönünü sağdan sola (RTL) düzeni tersine çevirir. Belirtebilirsiniz olmadığını <xref:System.Windows.Forms.FlowLayoutPanel> denetimin içeriği sarmalanmış veya değerini ayarlayarak kırpılarak <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> özelliği.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> Ayarladığınızda boyutları için içeriği otomatik olarak Denetim <xref:System.Windows.Forms.Control.AutoSize%2A> özelliğini `true`. Ayrıca sağlar bir **FlowBreak** özelliğini, alt denetimlerini. FlowBreak özelliğin değerini ayarlamak `true` neden <xref:System.Windows.Forms.FlowLayoutPanel> sonraki satır veya sütun kaydırılır ve geçerli akış yönü denetimlerinde düzenlemeyi durdurmak için denetimi.  
  
 Herhangi bir Windows Forms denetimini bir alt öğesi olabilir <xref:System.Windows.Forms.FlowLayoutPanel> denetim, diğer örnekleri dahil <xref:System.Windows.Forms.FlowLayoutPanel>. Bu özellik sayesinde, çalışma zamanında formunuzun boyutlarına uyum karmaşık düzenler oluşturabilirsiniz.  
  
 Ayrıca bkz: [izlenecek yol: FlowLayoutPanel kullanarak Windows Forms'da denetimleri düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [FlowLayoutPanel Denetimi](flowlayoutpanel-control-windows-forms.md)
