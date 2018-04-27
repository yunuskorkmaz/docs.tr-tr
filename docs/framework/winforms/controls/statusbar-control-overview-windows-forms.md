---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e84ae7d62649c0c547417e954560ac0faccafdd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar Denetimine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için ise, ' ı seçin.  
  
 Windows Forms [StatusBar denetimi](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) formlarda genellikle uygulamanın çeşitli durum bilgileri görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır. <xref:System.Windows.Forms.StatusBar> denetimlerin metin veya durum veya bir dizi bir işlemin çalıştığını belirten bir animasyon simgeleri göstermek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] Belge kaydedildiğinde gösteren.  
  
## <a name="using-the-statusbar-control"></a>StatusBar denetimi kullanma  
 Internet Explorer, fare köprünün üzerine geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] sayfa konum, bölüm konumu ve üzerine yazma ve değişiklik izleme; ve Visual Studio kullanan gibi durum çubuğu nasıl dockable windows yönetileceğini söyleyen gibi bağlama duyarlı bilgi vermek için düzenleme modunu hakkında bilgi sağlar olarak yerleşik veya kayan.  
  
 Ayarlayarak tek bir ileti durum çubuğunda görüntüleyebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğunun için durum çubuğunda görünmesini istediğiniz metin. Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
