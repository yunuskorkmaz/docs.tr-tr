---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 5fdefa7d7e7c7ef543f677be7beb61dfee54e077
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077322"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="d4b8f-102">StatusBar Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d4b8f-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="d4b8f-103"><xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d4b8f-104">Windows Forms [StatusBar denetimine](statusbar-control-windows-forms.md) formlarında genellikle bir uygulama çeşitli durum bilgilerini görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <xref:System.Windows.Forms.StatusBar> <span data-ttu-id="d4b8f-105">denetimleri, metin veya durumu ya da bir işlemin çalıştığını gösteren simgeler animasyonda bir dizi belirtmek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] Belge kaydedildiğinde gösteren.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-105">controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="d4b8f-106">StatusBar denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="d4b8f-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="d4b8f-107">Internet Explorer köprünün üzerine fare geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] sayfası konumu, bölüm konumu ve üzerine yazma ve değişiklik izleme; ve Visual Studio kullanan gibi durum çubuğunun yerleştirilebilir pencerelerin işlemek nasıl belirten gibi bağlama duyarlı bilgileri vermek için düzenleme modunu bilgiler verir olarak yerleşik veya kayan.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="d4b8f-108">Ayarlayarak durum çubuğuna tek bir ileti görüntüleyebilir <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğuna durum çubuğunda görüntülenmesini istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="d4b8f-109">Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b8f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4b8f-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="d4b8f-111">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="d4b8f-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
