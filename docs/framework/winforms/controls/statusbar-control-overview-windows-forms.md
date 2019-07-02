---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 4e1816ef221641f5ad54fb429442ed43289b592a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505431"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="6a780-102">StatusBar Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6a780-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="6a780-103"><xref:System.Windows.Forms.StatusStrip> Ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetler; ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri korunur geriye dönük uyumluluk ve gelecekte kullanım için varsa, ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="6a780-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="6a780-104">Windows Forms [StatusBar denetimine](statusbar-control-windows-forms.md) formlarında genellikle bir uygulama çeşitli durum bilgilerini görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a780-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="6a780-105"><xref:System.Windows.Forms.StatusBar> denetimleri, metin veya durumu ya da bir işlemin çalıştığını gösteren simgeler animasyonda bir dizi belirtmek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, belgeyi Microsoft Word gösteren kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="6a780-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="6a780-106">StatusBar denetimi kullanma</span><span class="sxs-lookup"><span data-stu-id="6a780-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="6a780-107">Internet Explorer köprünün üzerine fare geldiğinde, bir sayfanın URL'sini belirtmek için bir durum çubuğu kullanır; Microsoft Word sayfası konumu, bölüm konumu ve üzerine yazma ve izleme düzeltme gibi modları düzenleme hakkında bilgi sağlar; ve Visual Studio yerleştirilebilir pencerelerin kayan ya da yerleşik olarak işlemek nasıl belirten gibi bağlama duyarlı bilgileri vermek için durum çubuğunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a780-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="6a780-108">Ayarlayarak durum çubuğuna tek bir ileti görüntüleyebilir <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `false` (varsayılan) ve ayarı <xref:System.Windows.Forms.StatusBar.Text%2A> özelliği durum çubuğuna durum çubuğunda görüntülenmesini istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="6a780-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="6a780-109">Paneller ayarlayarak birden fazla tür bilgileri görüntülemek için durum çubuğunu bölebilirsiniz <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true` ve kullanarak <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemi <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="6a780-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a780-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a780-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="6a780-111">Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="6a780-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
