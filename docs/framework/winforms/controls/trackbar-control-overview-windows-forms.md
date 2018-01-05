---
title: "TrackBar Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a><span data-ttu-id="13bb5-102">TrackBar Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="13bb5-102">TrackBar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="13bb5-103">Windows Forms <xref:System.Windows.Forms.TrackBar> denetimi (bazen "kaydırıcı" denetimi olarak da adlandırılır), büyük miktarda bilgi arasında gezinmek için veya bir sayısal ayarı görsel olarak ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13bb5-103">The Windows Forms <xref:System.Windows.Forms.TrackBar> control (also sometimes called a "slider" control) is used for navigating through a large amount of information or for visually adjusting a numeric setting.</span></span> <span data-ttu-id="13bb5-104"><xref:System.Windows.Forms.TrackBar> Denetim da iki bölümden oluşur: olarak da bilinen bir kaydırıcı ve çizgilerinin kalan kısmıdır.</span><span class="sxs-lookup"><span data-stu-id="13bb5-104">The <xref:System.Windows.Forms.TrackBar> control has two parts: the thumb, also known as a slider, and the tick marks.</span></span> <span data-ttu-id="13bb5-105">Kaydırma ayarlanabilir bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="13bb5-105">The thumb is the part that can be adjusted.</span></span> <span data-ttu-id="13bb5-106">Konumuna karşılık gelen <xref:System.Windows.Forms.TrackBar.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="13bb5-106">Its position corresponds to the <xref:System.Windows.Forms.TrackBar.Value%2A> property.</span></span> <span data-ttu-id="13bb5-107">Değer çizgilerinin düzenli aralıklarla aralıklı visual göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="13bb5-107">The tick marks are visual indicators that are spaced at regular intervals.</span></span> <span data-ttu-id="13bb5-108">Trackbar belirtin ve yatay veya dikey hizalanabilir artışlarla taşır.</span><span class="sxs-lookup"><span data-stu-id="13bb5-108">The trackbar moves in increments that you specify and can be aligned horizontally or vertically.</span></span> <span data-ttu-id="13bb5-109">Örneğin, bir sistem için imleç blink oranı ya da fare hızı denetlemek için izleme çubuğunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13bb5-109">For example, you might use the track bar to control the cursor blink rate or mouse speed for a system.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="13bb5-110">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="13bb5-110">Key Properties</span></span>  
 <span data-ttu-id="13bb5-111">Anahtar özelliklerini <xref:System.Windows.Forms.TrackBar> denetim <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, ve <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span><span class="sxs-lookup"><span data-stu-id="13bb5-111">The key properties of the <xref:System.Windows.Forms.TrackBar> control are <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, and <xref:System.Windows.Forms.TrackBar.Maximum%2A>.</span></span> <span data-ttu-id="13bb5-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A>ticks aralığını olur.</span><span class="sxs-lookup"><span data-stu-id="13bb5-112"><xref:System.Windows.Forms.TrackBar.TickFrequency%2A> is the spacing of the ticks.</span></span> <span data-ttu-id="13bb5-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A>ve <xref:System.Windows.Forms.TrackBar.Maximum%2A> izleme çubuğunda temsil edilebilir en küçük ve en büyük değerler.</span><span class="sxs-lookup"><span data-stu-id="13bb5-113"><xref:System.Windows.Forms.TrackBar.Minimum%2A> and <xref:System.Windows.Forms.TrackBar.Maximum%2A> are the smallest and largest values that can be represented on the track bar.</span></span>  
  
 <span data-ttu-id="13bb5-114">İki önemli özellik <xref:System.Windows.Forms.TrackBar.SmallChange%2A> ve <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span><span class="sxs-lookup"><span data-stu-id="13bb5-114">Two other important properties are <xref:System.Windows.Forms.TrackBar.SmallChange%2A> and <xref:System.Windows.Forms.TrackBar.LargeChange%2A>.</span></span> <span data-ttu-id="13bb5-115">Değeri <xref:System.Windows.Forms.TrackBar.SmallChange%2A> özelliği, Flash taşır sol veya sağ ok tuşunu basılı sahip yanıt konumlar numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="13bb5-115">The value of the <xref:System.Windows.Forms.TrackBar.SmallChange%2A> property is the number of positions the thumb moves in response to having the LEFT or RIGHT ARROW key pressed.</span></span> <span data-ttu-id="13bb5-116">Değeri <xref:System.Windows.Forms.TrackBar.LargeChange%2A> özelliği, Flash PAGE UP veya PAGE DOWN tuşunu basılı sahip yanıt taşıdığında veya fare yanıtta tıklattığında ya da yan tarafında kalan kısmıdır izleme çubuğunda konumlar numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="13bb5-116">The value of the <xref:System.Windows.Forms.TrackBar.LargeChange%2A> property is the number of positions the thumb moves in response to having the PAGE UP or PAGE DOWN key pressed, or in response to mouse clicks on the track bar on either side of the thumb.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13bb5-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13bb5-117">See Also</span></span>  
 <xref:System.Windows.Forms.TrackBar>  
 [<span data-ttu-id="13bb5-118">TrackBar Denetimi</span><span class="sxs-lookup"><span data-stu-id="13bb5-118">TrackBar Control</span></span>](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
