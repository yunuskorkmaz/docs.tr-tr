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
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="ed650-102">StatusBar Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ed650-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="ed650-103"><xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için ise, ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ed650-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ed650-104">Windows Forms [StatusBar denetimi](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) formlarda genellikle uygulamanın çeşitli durum bilgileri görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed650-104">The Windows Forms [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="ed650-105"><xref:System.Windows.Forms.StatusBar>denetimlerin metin veya durum veya bir dizi bir işlemin çalıştığını belirten bir animasyon simgeleri göstermek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] Belge kaydedildiğinde gösteren.</span><span class="sxs-lookup"><span data-stu-id="ed650-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="ed650-106">StatusBar denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="ed650-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="ed650-107">Internet Explorer, fare köprünün üzerine geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] sayfa konum, bölüm konumu ve düzenleme modunu üzerine yazma ve izleme; düzeltme gibi bilgileri verir ve [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] nasıl dockable yönetileceğini söyleyen gibi bağlama duyarlı bilgi vermek için durum çubuğunu kullanır Windows yerleşik veya kayan olarak.</span><span class="sxs-lookup"><span data-stu-id="ed650-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="ed650-108">Ayarlayarak tek bir ileti durum çubuğunda görüntüleyebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğunun için durum çubuğunda görünmesini istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="ed650-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="ed650-109">Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğine `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="ed650-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed650-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed650-110">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="ed650-111">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="ed650-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
