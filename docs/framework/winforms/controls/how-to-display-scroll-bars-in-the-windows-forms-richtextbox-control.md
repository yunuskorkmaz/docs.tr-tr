---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="45581-102">Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="45581-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="45581-103">Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi gerektiği gibi yatay ve dikey kaydırma çubukları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="45581-104">Yedi olası değerler için <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> özelliği <xref:System.Windows.Forms.RichTextBox> aşağıdaki tabloda açıklanan denetim.</span><span class="sxs-lookup"><span data-stu-id="45581-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="45581-105">RichTextBox denetiminde kaydırma çubukları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="45581-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="45581-106">Ayarlama <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="45581-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="45581-107">Tür yatay kaydırma çubuğu dahil olmak üzere, görüntüler, <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliği ayarlanmış `false`.</span><span class="sxs-lookup"><span data-stu-id="45581-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="45581-108">Ayarlama <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> uygun bir değerde özelliğine <xref:System.Windows.Forms.RichTextBoxScrollBars> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="45581-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="45581-109">Değer</span><span class="sxs-lookup"><span data-stu-id="45581-109">Value</span></span>|<span data-ttu-id="45581-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45581-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="45581-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both>(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="45581-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="45581-112">Yalnızca metin genişliğini veya denetim uzunluğunu aştığında yatay veya dikey kaydırma çubukları veya her ikisini de görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="45581-113">Hiçbir zaman kaydırma çubuğunun herhangi bir türde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="45581-114">Yalnızca metin denetiminin genişliğini aştığında çubuğu yatay kaydırma görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="45581-115">(Bunun gerçekleşmesi <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmalıdır `false`.)</span><span class="sxs-lookup"><span data-stu-id="45581-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="45581-116">Yalnızca metin denetimin yüksekliğini aştığında çubuğu dikey bir kaydırma görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="45581-117">Yatay kaydırma ne zaman görüntüler <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmış `false`.</span><span class="sxs-lookup"><span data-stu-id="45581-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="45581-118">Metin denetimi genişliğini aşmayan zaman kaydırma çubuğu soluk görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="45581-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="45581-119">Her zaman bir dikey kaydırma çubuğu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="45581-120">Metin denetim uzunluğunu aşan değil kaydırma çubuğu soluk görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="45581-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="45581-121">Her zaman dikey kaydırma çubuğu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="45581-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="45581-122">Yatay kaydırma ne zaman görüntüler <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmış `false`.</span><span class="sxs-lookup"><span data-stu-id="45581-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="45581-123">Kaydırma çubukları metin genişliğini veya denetim uzunluğunu aşmayan gri görünür.</span><span class="sxs-lookup"><span data-stu-id="45581-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="45581-124">Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="45581-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="45581-125">Değer</span><span class="sxs-lookup"><span data-stu-id="45581-125">Value</span></span>|<span data-ttu-id="45581-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45581-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="45581-127">Denetimdeki metnin satır sonu ulaşılana kadar sağa kaydırın şekilde denetiminin genişliğini sığması için otomatik olarak ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="45581-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="45581-128">Yukarıdaki yatay kaydırma çubuklarını veya her ikisini de seçerseniz, bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="45581-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="45581-129">`true`(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="45581-129">`true` (default)</span></span>|<span data-ttu-id="45581-130">Denetimdeki metnin denetiminin genişliğini sığması için otomatik olarak düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="45581-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="45581-131">Yatay kaydırma çubuğu görünmez.</span><span class="sxs-lookup"><span data-stu-id="45581-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="45581-132">Dikey kaydırma çubuklarını veya hiçbiri, yukarıda, bir veya daha fazla paragraf görüntülemek için seçtiğiniz zaman bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="45581-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45581-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45581-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="45581-134">RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="45581-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="45581-135">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="45581-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
