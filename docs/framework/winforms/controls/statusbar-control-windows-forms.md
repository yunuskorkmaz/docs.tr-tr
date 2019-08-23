---
title: StatusBar Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 72a93fc32715596efc7fb0f8b941e62f7019d06c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964416"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="18aeb-102">StatusBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="18aeb-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="18aeb-103">Denetim yerini alır ve <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.ToolStripStatusLabel></span><span class="sxs-lookup"><span data-stu-id="18aeb-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="18aeb-104">Windows Forms <xref:System.Windows.Forms.StatusBar> denetim, genellikle pencerenin altında görüntülenen ve bir uygulamanın çeşitli durum bilgilerini görüntüleyebilen bir alan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18aeb-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="18aeb-105"><xref:System.Windows.Forms.StatusBar>denetimlerin durumu göstermek için simgeler görüntüleyen ve bir animasyonda bir işlemin çalıştığını gösteren bir dizi simge olan durum çubuğu panelleri olabilir. Örneğin, belgenin kaydedildiğini gösteren Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="18aeb-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18aeb-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="18aeb-106">In This Section</span></span>  
 [<span data-ttu-id="18aeb-107">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="18aeb-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="18aeb-108">, Kullanıcıların odağa sahip olan denetim <xref:System.Windows.Forms.StatusBar> için ilgili bilgileri görmesini sağlayan, denetimin genel kavramlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="18aeb-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="18aeb-109">Nasıl yapılır: Bir StatusBar Denetimine Panel ekleme</span><span class="sxs-lookup"><span data-stu-id="18aeb-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="18aeb-110"><xref:System.Windows.Forms.StatusBar> Denetime programlanabilir panellerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="18aeb-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="18aeb-111">Nasıl yapılır: Windows Forms StatusBar denetimindeki panelin tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="18aeb-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="18aeb-112">Denetimden<xref:System.Windows.Forms.StatusBar> oluşturulan olayların nasıl <xref:System.Windows.Forms.Control.Click> işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="18aeb-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="18aeb-113">Nasıl yapılır: Durum çubuğu panellerinin boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="18aeb-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="18aeb-114">Çalışma zamanında durum çubuğu panellerinin genişliğini ve yeniden boyutlandırma davranışını denetleyen özellikler hakkında ayrıntılı bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="18aeb-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="18aeb-115">İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="18aeb-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="18aeb-116">Durum çubuğu panellerinde verilerin programlı bir şekilde nasıl kontrol verileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="18aeb-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="18aeb-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="18aeb-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="18aeb-118">Sınıf ve üyeleri hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="18aeb-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="18aeb-119">' İ değiştirir ve <xref:System.Windows.Forms.StatusBar> denetime işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="18aeb-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18aeb-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="18aeb-120">Related Sections</span></span>  
 [<span data-ttu-id="18aeb-121">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="18aeb-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="18aeb-122">Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="18aeb-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
