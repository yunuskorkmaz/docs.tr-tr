---
title: Panel Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: c346a9b77d49cde007310a2beb13bed3b1f30d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501778"
---
# <a name="panel-control-overview-windows-forms"></a>Panel Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> denetimleri, diğer denetimleri için tanımlanabilen bir gruplama sağlamak için kullanılır. Genellikle, bir form işlevi tarafından alt bölümlere ayırmak için panoları kullanın. Örneğin, bir sipariş formu gibi kullanmak için hangi gece taşıyıcı postalama seçenekleri belirten olabilir. Tüm seçenekleri panelindeki bir gruplandırma kullanıcı mantıksal olarak görsel bir ipucu sağlar. Tasarım sırasında tüm denetimlerin bir kolayca taşınabilir zaman — taşıdığınızda <xref:System.Windows.Forms.Panel> denetlemek, tüm çok kapsanan denetimlerini Taşı. Bir panel içinde gruplanmış denetimleri aracılığıyla erişilebilen, <xref:System.Windows.Forms.Control.Controls%2A> özelliği. Bu özellik bir koleksiyonunu döndürür <xref:System.Windows.Forms.Control> alınan belirli, türüne bu şekilde örnekleri, genellikle bir denetimi cast gerekecektir.  
  
## <a name="panel-versus-groupbox"></a>Paneli GroupBox ile karşılaştırması  
 <xref:System.Windows.Forms.Panel> Denetim benzer <xref:System.Windows.Forms.GroupBox> denetler; ancak, yalnızca <xref:System.Windows.Forms.Panel> denetimi, kaydırma çubukları sahip olabilir ve yalnızca <xref:System.Windows.Forms.GroupBox> denetimi, bir başlık görüntüler.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Kaydırma çubukları görüntülenecek kümesi <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> özelliğini `true`. Ayarlayarak paneli görünümünü özelleştirebilirsiniz <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, ve <xref:System.Windows.Forms.Panel.BorderStyle%2A> özellikleri. Daha fazla bilgi için <xref:System.Windows.Forms.Control.BackColor%2A> ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> özellikleri görmek [nasıl yapılır: Bir panelin arka planını ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> Özelliği belirler paneli görünür bir kenarlık ile özetlenen varsa (<xref:System.Windows.Forms.BorderStyle.None>), düz bir çizgi (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), veya gölgeli bir satır (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Panel>
- [GroupBox Denetimi](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms Panel denetimi ile denetimleri gruplandırma](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms panelinin arka planını ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
