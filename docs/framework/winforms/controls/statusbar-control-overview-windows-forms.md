---
title: "StatusBar Denetimine Genel Bakış (Windows Forms)"
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
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df8e6b8484cf3b35c684445445ddc41adc358698
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için ise, ' ı seçin.  
  
 Windows Forms [StatusBar denetimi](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) formlarda genellikle uygulamanın çeşitli durum bilgileri görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır. <xref:System.Windows.Forms.StatusBar>denetimlerin metin veya durum veya bir dizi bir işlemin çalıştığını belirten bir animasyon simgeleri göstermek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] Belge kaydedildiğinde gösteren.  
  
## <a name="using-the-statusbar-control"></a>StatusBar denetimi kullanma  
 Internet Explorer, fare köprünün üzerine geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] sayfa konum, bölüm konumu ve düzenleme modunu üzerine yazma ve izleme; düzeltme gibi bilgileri verir ve [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] nasıl dockable yönetileceğini söyleyen gibi bağlama duyarlı bilgi vermek için durum çubuğunu kullanır Windows yerleşik veya kayan olarak.  
  
 Ayarlayarak tek bir ileti durum çubuğunda görüntüleyebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğunun için durum çubuğunda görünmesini istediğiniz metin. Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
