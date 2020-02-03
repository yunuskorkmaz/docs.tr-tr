---
title: StatusBar Denetimi
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 4d48cf497eeedcff6290dfa8ddecf38ce8ff7c63
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742856"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="308cd-102">StatusBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="308cd-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="308cd-103"><xref:System.Windows.Forms.ToolStripStatusLabel> denetimi yerini alır ve <xref:System.Windows.Forms.StatusBar> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.StatusBar> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="308cd-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="308cd-104">Windows Forms <xref:System.Windows.Forms.StatusBar> denetimi, genellikle pencerenin alt kısmında görüntülenen ve bir uygulamanın çeşitli durum bilgilerini görüntüleyebilen bir alan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="308cd-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="308cd-105"><xref:System.Windows.Forms.StatusBar> denetimleri, durumu göstermek için simgeler görüntüleyen veya bir animasyonda bir işlemin çalıştığını gösteren bir dizi simge olan durum çubuğu panellerine sahip olabilir; Örneğin, belgenin kaydedildiğini gösteren Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="308cd-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="308cd-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="308cd-106">In This Section</span></span>  
 [<span data-ttu-id="308cd-107">StatusBar Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="308cd-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="308cd-108"><xref:System.Windows.Forms.StatusBar> denetimin genel kavramlarını tanıtır, bu, kullanıcıların odağa sahip olan denetim için ilgili bilgileri görmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="308cd-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="308cd-109">Nasıl yapılır: Bir StatusBar Denetimine Panel Ekleme</span><span class="sxs-lookup"><span data-stu-id="308cd-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="308cd-110"><xref:System.Windows.Forms.StatusBar> denetimine programlanabilir panellerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="308cd-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="308cd-111">Nasıl yapılır: Windows Forms StatusBar Denetiminde Hangi Panele Tıklandığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="308cd-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="308cd-112"><xref:System.Windows.Forms.StatusBar> denetiminden çıkarılan <xref:System.Windows.Forms.Control.Click> olaylarının nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="308cd-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="308cd-113">Nasıl yapılır: Durum Çubuğu Panellerinin Boyutunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="308cd-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="308cd-114">Çalışma zamanında durum çubuğu panellerinin genişliğini ve yeniden boyutlandırma davranışını denetleyen özellikler hakkında ayrıntılı bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="308cd-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="308cd-115">İzlenecek yol: Çalışma Zamanında Durum Çubuğu Bilgilerini Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="308cd-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="308cd-116">Durum çubuğu panellerinde verilerin programlı bir şekilde nasıl kontrol verileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="308cd-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="308cd-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="308cd-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="308cd-118">Sınıf ve üyeleri hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="308cd-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="308cd-119">Öğesini değiştirir ve <xref:System.Windows.Forms.StatusBar> denetimine işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="308cd-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="308cd-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="308cd-120">Related Sections</span></span>  
 [<span data-ttu-id="308cd-121">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="308cd-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="308cd-122">Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="308cd-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
