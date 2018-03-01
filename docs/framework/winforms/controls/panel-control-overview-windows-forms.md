---
title: "Panel Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8855c88a0ec60cd0d44d73046e44c9614347d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="panel-control-overview-windows-forms"></a>Panel Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> denetimleri, diğer denetimler için tanımlanabilen bir gruplandırma sağlamak için kullanılır. Genellikle, işlev tarafından bir form ayırabilir için panelleri kullanın. Örneğin, kullanmak için hangi ertesi gün taşıyıcı gibi posta seçeneklerini belirtir. bir sipariş formu olabilir. Paneldeki tüm seçeneklerin gruplandırma kullanıcı mantıksal bir görsel ipucu verir. Tüm denetimler kolayca taşınabileceği tasarım sırasında zaman — taşıdığınızda <xref:System.Windows.Forms.Panel> denetlemek, tüm çok kapsanan denetimlerinden taşıyın. Masası'nda gruplanmış denetimleri aracılığıyla erişilebilir kendi <xref:System.Windows.Forms.Control.Controls%2A> özelliği. Bu özellik bir koleksiyonunu döndürür <xref:System.Windows.Forms.Control> genellikle bir denetim cast gerekir böylece örnekleri alınan belirli türünü bu şekilde.  
  
## <a name="panel-versus-groupbox"></a>GroupBox karşı paneli  
 <xref:System.Windows.Forms.Panel> Denetim benzer <xref:System.Windows.Forms.GroupBox> kontrol; ancak, yalnızca <xref:System.Windows.Forms.Panel> denetim kaydırma çubukları sahip olabilir ve yalnızca <xref:System.Windows.Forms.GroupBox> denetimi, bir resim yazısı görüntüler.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Kaydırma çubukları görüntülenecek ayarlamak <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> özelliğine `true`. Ayarlayarak paneli görünümünü özelleştirebilirsiniz <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, ve <xref:System.Windows.Forms.Panel.BorderStyle%2A> özellikleri. Daha fazla bilgi için <xref:System.Windows.Forms.Control.BackColor%2A> ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliklerini görmek [nasıl yapılır: bir panelin arka planını ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> Özelliği belirler paneli ile görünür hiçbir kenarlık ana hatlarıyla varsa (<xref:System.Windows.Forms.BorderStyle.None>), düz bir satır (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), ya da gölgeli bir satır (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Panel>  
 [GroupBox Denetimi](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panelinin Arka Planını Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
