---
title: StatusBar Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964429"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="06c40-102">StatusBar Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="06c40-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="06c40-103"><xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> Ve denetimleri, vedenetimlerine<xref:System.Windows.Forms.StatusBarPanel> işlevsellik ekler ve bunları ekler; ancak, ve denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.ToolStripStatusLabel> 'yu.</span><span class="sxs-lookup"><span data-stu-id="06c40-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="06c40-104">Windows Forms [StatusBar denetimi](statusbar-control-windows-forms.md) , genellikle pencerenin altında görüntülenen ve bir uygulamanın çeşitli durum bilgilerini görüntüleyebilen bir alan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06c40-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="06c40-105"><xref:System.Windows.Forms.StatusBar>denetimlerin, durumu göstermek için metin veya simgeleri görüntüleyen ve bir animasyonun çalıştığını gösteren bir animasyon içindeki simge dizisi olan durum çubuğu panellerine sahip olabilir; Örneğin, belgenin kaydedildiğini gösteren Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="06c40-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="06c40-106">StatusBar denetimini kullanma</span><span class="sxs-lookup"><span data-stu-id="06c40-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="06c40-107">Internet Explorer, fare köprünün üzerine geldiğinde bir sayfanın URL 'sini belirtmek için bir durum çubuğu kullanır; Microsoft Word size sayfa konumu, bölüm konumu ve üzerine yazma ve değişiklik izleme gibi düzenleme modları hakkında bilgi verir; Visual Studio, serbest yerleştirilmiş Windows 'u yerleştirilmiş veya kayan olarak nasıl işleyebileceğiniz hakkında içeriğe duyarlı bilgiler vermek için durum çubuğunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="06c40-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="06c40-108"><xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Özelliği `false` (<xref:System.Windows.Forms.StatusBar.Text%2A> varsayılan) olarak ayarlayarak durum çubuğunda tek bir ileti görüntüleyebilir ve durum çubuğunun özelliğini durum çubuğunda görünmesini istediğiniz metin olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06c40-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="06c40-109"><xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Özelliğini olarak `true` ayarlayarak vemetodunu<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> kullanarak, birden fazla bilgi türü göstermek için durum çubuğunu panellere bölebilirsiniz. <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection></span><span class="sxs-lookup"><span data-stu-id="06c40-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c40-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06c40-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="06c40-111">Nasıl yapılır: Windows Forms StatusBar denetimindeki panelin tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="06c40-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
