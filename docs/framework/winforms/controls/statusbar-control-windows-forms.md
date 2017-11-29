---
title: StatusBar Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d1a350075811dc02ae33efd1a6ae05328c4ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="10616-102">StatusBar Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="10616-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="10616-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.StatusBar> kontrol; ancak, <xref:System.Windows.Forms.StatusBar> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="10616-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="10616-104">Windows Forms <xref:System.Windows.Forms.StatusBar> denetimi formlarında genellikle uygulamanın çeşitli durum bilgileri görüntüleyebilir, bir penceresinin en altında görüntülenen bir alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10616-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="10616-105"><xref:System.Windows.Forms.StatusBar>denetimlerin durumu veya bir dizi bir işlemin çalıştığını belirten bir animasyon simgeleri göstermek için simgeler görüntüleme durum çubuğu panellerinin bunlardaki olabilir; Örneğin, Microsoft gösteren Word belgesi kaydediliyor.</span><span class="sxs-lookup"><span data-stu-id="10616-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10616-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="10616-106">In This Section</span></span>  
 [<span data-ttu-id="10616-107">StatusBar denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="10616-107">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="10616-108">Genel kavramlarını tanıtır <xref:System.Windows.Forms.StatusBar> odaklanmış denetimi için ilgili bilgileri görmelerini sağlar denetim.</span><span class="sxs-lookup"><span data-stu-id="10616-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="10616-109">Nasıl yapılır: bir StatusBar denetimine panel ekleme</span><span class="sxs-lookup"><span data-stu-id="10616-109">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="10616-110">Programlanabilir paneller ekleme açıklar <xref:System.Windows.Forms.StatusBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="10616-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="10616-111">Nasıl yapılır: Windows Forms StatusBar denetiminde hangi panele tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="10616-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="10616-112">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.Control.Click> olayları yükseltilmiş <xref:System.Windows.Forms.StatusBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="10616-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="10616-113">Nasıl yapılır: durum çubuğu panellerinin boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="10616-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="10616-114">Genişlik denetleyen ve çalışma zamanında durum çubuğu panellerinin davranışını yeniden boyutlandırma özelliklerindeki ayrıntılarını verir.</span><span class="sxs-lookup"><span data-stu-id="10616-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="10616-115">İzlenecek yol: Çalışma zamanında durum çubuğu bilgilerini güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="10616-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="10616-116">Durum çubuğu panellerinin içinde verileri programlı olarak denetlemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10616-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="10616-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="10616-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="10616-118">Sınıf ve üyelerine başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="10616-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="10616-119">Değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.StatusBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="10616-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="10616-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="10616-120">Related Sections</span></span>  
 [<span data-ttu-id="10616-121">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="10616-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="10616-122">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="10616-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
