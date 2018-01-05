---
title: "HScrollBar ve VScrollBar Denetimlerine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a6f1d569234f7cee4b5eedc81fcc68a41fcf0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a><span data-ttu-id="a8ec2-102">HScrollBar ve VScrollBar Denetimlerine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a8ec2-102">HScrollBar and VScrollBar Controls Overview (Windows Forms)</span></span>
<span data-ttu-id="a8ec2-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> denetimleri kaydırarak ya da yatay veya dikey olarak bir uygulama veya denetim içinde uzun bir listesi ile kolay gezinme öğeleri veya büyük miktarda bilgi sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> controls are used to provide easy navigation through a long list of items or a large amount of information by scrolling either horizontally or vertically within an application or control.</span></span> <span data-ttu-id="a8ec2-104">Kaydırma çubukları Windows arabiriminin ortak bir öğesi olan böylece <xref:System.Windows.Forms.ScrollBar> denetim öğesinden türetilen değil denetimleri ile kullanılan genellikle <xref:System.Windows.Forms.ScrollableControl> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-104">Scroll bars are a common element of the Windows interface, so the <xref:System.Windows.Forms.ScrollBar> control is often used with controls that do not derive from the <xref:System.Windows.Forms.ScrollableControl> class.</span></span> <span data-ttu-id="a8ec2-105">Benzer şekilde, içerecek şekilde Çoğu geliştirici seçin <xref:System.Windows.Forms.ScrollBar> denetim kendi kullanıcı denetimleri yazarken.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-105">Similarly, many developers choose to incorporate the <xref:System.Windows.Forms.ScrollBar> control when authoring their own user controls.</span></span>  
  
 <span data-ttu-id="a8ec2-106"><xref:System.Windows.Forms.HScrollBar> (Yatay) ve <xref:System.Windows.Forms.VScrollBar> (dikey) denetimleri diğer denetimlerden bağımsız olarak çalışır ve olaylar, özellikleri ve yöntemleri kendi kümesine sahip.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-106">The <xref:System.Windows.Forms.HScrollBar> (horizontal) and <xref:System.Windows.Forms.VScrollBar> (vertical) controls operate independently from other controls and have their own set of events, properties, and methods.</span></span> <span data-ttu-id="a8ec2-107"><xref:System.Windows.Forms.ScrollBar>denetimleri metin kutuları, liste kutuları, birleşik giriş kutuları veya MDI formları bağlı yerleşik kaydırma çubukları ile aynı değildir ( <xref:System.Windows.Forms.TextBox> denetimi sahip bir <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliğini denetime bağlı kaydırma çubuklarını gösterme veya gizleme).</span><span class="sxs-lookup"><span data-stu-id="a8ec2-107"><xref:System.Windows.Forms.ScrollBar> controls are not the same as the built-in scroll bars that are attached to text boxes, list boxes, combo boxes, or MDI forms (the <xref:System.Windows.Forms.TextBox> control has a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to show or hide scroll bars that are attached to the control).</span></span>  
  
 <span data-ttu-id="a8ec2-108"><xref:System.Windows.Forms.ScrollBar> Denetimleri kullanın <xref:System.Windows.Forms.ScrollBar.Scroll> kaydırma çubuğu taşıma (bazen Flash adlandırılır) kaydırma kutusunun izlemek için olay.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-108">The <xref:System.Windows.Forms.ScrollBar> controls use the <xref:System.Windows.Forms.ScrollBar.Scroll> event to monitor the movement of the scroll box (sometimes referred to as the thumb) along the scroll bar.</span></span> <span data-ttu-id="a8ec2-109">Kullanarak <xref:System.Windows.Forms.ScrollBar.Scroll> olay sürüklenen gibi kaydırma çubuğu değeri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-109">Using the <xref:System.Windows.Forms.ScrollBar.Scroll> event provides access to the scroll bar value as it is being dragged.</span></span>  
  
## <a name="value-property"></a><span data-ttu-id="a8ec2-110">Value özelliği</span><span class="sxs-lookup"><span data-stu-id="a8ec2-110">Value Property</span></span>  
 <span data-ttu-id="a8ec2-111"><xref:System.Windows.Forms.ScrollBar.Value%2A> (Bu, varsayılan olarak, 0) özelliği bir `integer` kaydırma çubuğuna ait kaydırma kutusunun konumuna karşılık gelen değer.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-111">The <xref:System.Windows.Forms.ScrollBar.Value%2A> property (which, by default, is 0) is an `integer` value corresponding to the position of the scroll box in the scroll bar.</span></span> <span data-ttu-id="a8ec2-112">Kaydırma kutusunun konumundaki en düşük değer olduğunda (için yatay kaydırma çubuklarını) en solundaki konumu ya da üst konumunu (dikey kaydırma çubukları) taşır.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-112">When the scroll box position is at the minimum value, it moves to the left-most position (for horizontal scroll bars) or the top position (for vertical scroll bars).</span></span> <span data-ttu-id="a8ec2-113">Kaydırma kutusu en büyük değer, en sağdaki kaydırma kutusuna taşınır veya alt konumunu olduğunda.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-113">When the scroll box is at the maximum value, the scroll box moves to the right-most or bottom position.</span></span> <span data-ttu-id="a8ec2-114">Benzer şekilde, bir değer aralığın üst ve alt arasında yarısı ortasında kaydırma çubuğunun Kaydırma kutusu başında köşesine yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-114">Similarly, a value halfway between the bottom and top of the range places the leading edge of the scroll box in the middle of the scroll bar.</span></span>  
  
 <span data-ttu-id="a8ec2-115">Kaydırma çubuğu değerini değiştirmek için fare tıklamaları kullanarak ek olarak, bir kullanıcı Kaydırma kutusu çubuğu boyunca herhangi bir noktaya sürükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-115">In addition to using mouse clicks to change the scroll bar value, a user can also drag the scroll box to any point along the bar.</span></span> <span data-ttu-id="a8ec2-116">Sonuç değeri kaydırma kutusunun konumuna bağlıdır, ancak bu her zaman aralığı içinde <xref:System.Windows.Forms.ScrollBar.Minimum%2A> için <xref:System.Windows.Forms.ScrollBar.Maximum%2A> kullanıcı tarafından ayarlanan özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-116">The resulting value depends on the position of the scroll box, but it is always within the range of the <xref:System.Windows.Forms.ScrollBar.Minimum%2A> to <xref:System.Windows.Forms.ScrollBar.Maximum%2A> properties set by the user.</span></span>  
  
## <a name="largechange-and-smallchange-properties"></a><span data-ttu-id="a8ec2-117">LargeChange ve SmallChange özellikleri</span><span class="sxs-lookup"><span data-stu-id="a8ec2-117">LargeChange and SmallChange Properties</span></span>  
 <span data-ttu-id="a8ec2-118">Kullanıcı PAGE UP veya PAGE DOWN tuşuna bastığında veya her iki yanına kaydırma kutusunun kaydırma çubuğu izlemede içinde tıklattığında <xref:System.Windows.Forms.ScrollBar.Value%2A> içinde ayarlanan değere göre özelliği değişiklikler <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-118">When the user presses the PAGE UP or PAGE DOWN key or clicks in the scroll bar track on either side of the scroll box, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> property.</span></span>  
  
 <span data-ttu-id="a8ec2-119">Kullanıcı oku birini bastığında anahtarları veya kaydırma çubuğu düğmelerinin birini tıklattığında <xref:System.Windows.Forms.ScrollBar.Value%2A> içinde ayarlanan değere göre özelliği değişiklikler <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-119">When the user presses one of the arrow keys or clicks one of the scroll bar buttons, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ec2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-120">See Also</span></span>  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [<span data-ttu-id="a8ec2-121">.NET Framework 2.0 için Windows Forms'a ekleme</span><span class="sxs-lookup"><span data-stu-id="a8ec2-121">Additions to Windows Forms for the .NET Framework 2.0</span></span>](http://msdn.microsoft.com/en-us/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [<span data-ttu-id="a8ec2-122">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="a8ec2-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
