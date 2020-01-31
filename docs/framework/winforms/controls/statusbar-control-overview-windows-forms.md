---
title: StatusBar Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742871"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="fd4ab-102">StatusBar Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fd4ab-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="fd4ab-103"><xref:System.Windows.Forms.StatusStrip> ve <xref:System.Windows.Forms.ToolStripStatusLabel> denetimleri yerini alır ve <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimlerine işlevsellik ekler; Ancak, <xref:System.Windows.Forms.StatusBar> ve <xref:System.Windows.Forms.StatusBarPanel> denetimleri hem geri uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="fd4ab-104">Windows Forms [StatusBar denetimi](statusbar-control-windows-forms.md) , genellikle pencerenin altında görüntülenen ve bir uygulamanın çeşitli durum bilgilerini görüntüleyebilen bir alan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="fd4ab-105"><xref:System.Windows.Forms.StatusBar> denetimleri, durumu göstermek için metin veya simgeleri görüntüleyen ve bir animasyonun çalıştığını gösteren bir animasyon içindeki bir simge dizisi olan durum çubuğu panellerine sahip olabilir; Örneğin, belgenin kaydedildiğini gösteren Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="fd4ab-106">StatusBar denetimini kullanma</span><span class="sxs-lookup"><span data-stu-id="fd4ab-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="fd4ab-107">Internet Explorer, fare köprünün üzerine geldiğinde bir sayfanın URL 'sini belirtmek için bir durum çubuğu kullanır; Microsoft Word size sayfa konumu, bölüm konumu ve üzerine yazma ve değişiklik izleme gibi düzenleme modları hakkında bilgi verir; Visual Studio, serbest yerleştirilmiş Windows 'u yerleştirilmiş veya kayan olarak nasıl işleyebileceğiniz hakkında içeriğe duyarlı bilgiler vermek için durum çubuğunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="fd4ab-108"><xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `false` (varsayılan) olarak ayarlayarak ve durum çubuğunun <xref:System.Windows.Forms.StatusBar.Text%2A> özelliğini durum çubuğunda görünmesini istediğiniz metin olarak ayarlayarak durum çubuğunda tek bir ileti görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="fd4ab-109"><xref:System.Windows.Forms.StatusBar.ShowPanels%2A> özelliğini `true` olarak ayarlayarak ve <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection><xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> yöntemini kullanarak birden fazla bilgi türü göstermek için durum çubuğunu panellere bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4ab-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd4ab-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="fd4ab-111">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="fd4ab-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
