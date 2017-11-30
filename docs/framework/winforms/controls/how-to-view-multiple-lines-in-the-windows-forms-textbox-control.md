---
title: "Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8f39e031835275818504151e66834f0634b7f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="79c11-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="79c11-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="79c11-103">Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> denetimi tek satırlık metin görüntüler ve kaydırma çubukları görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="79c11-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="79c11-104">Metin boşluktan uzunsa, metin yalnızca bir parçasının görünür olur.</span><span class="sxs-lookup"><span data-stu-id="79c11-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="79c11-105">Ayarlayarak bu varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, ve <xref:System.Windows.Forms.TextBox.ScrollBars%2A> uygun değerlere özellikleri.</span><span class="sxs-lookup"><span data-stu-id="79c11-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="79c11-106">TextBox denetiminde başı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="79c11-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="79c11-107">Bir çok satır başı görüntülenecek <xref:System.Windows.Forms.TextBox>, kullanın <xref:System.Environment.NewLine%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="79c11-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="79c11-108">Unutmayın, kaçış karakterleri yorumu (\\) dile özgüdür.</span><span class="sxs-lookup"><span data-stu-id="79c11-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="79c11-109">Visual Basic kullanan `Chr$(13) & Chr$(10)` satır başı ve satır besleme karakter birleşimi.</span><span class="sxs-lookup"><span data-stu-id="79c11-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="79c11-110">TextBox denetiminde birden fazla satır görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="79c11-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="79c11-111">Ayarlama <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="79c11-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="79c11-112">Varsa <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> olan `true` (varsayılan), Denetim metni olarak bir veya daha fazla paragraf sonra görüntülenir; Aksi takdirde, bazı satırlar kırpılmış denetimi kenarında bir liste olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="79c11-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="79c11-113">Ayarlama <xref:System.Windows.Forms.TextBox.ScrollBars%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="79c11-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="79c11-114">Değer</span><span class="sxs-lookup"><span data-stu-id="79c11-114">Value</span></span>|<span data-ttu-id="79c11-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79c11-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="79c11-116">Bir paragraf metni olacaksa, bu değeri kullanın, denetimi neredeyse her zaman uyar.</span><span class="sxs-lookup"><span data-stu-id="79c11-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="79c11-117">Kullanıcı, fare işaretçisini metin aynı anda görüntülemek için çok uzun olduğunda içindeki denetim hareket etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79c11-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="79c11-118">Satırları, bazıları olabilir genişliğinden daha uzun bir listesini görüntülemek istiyorsanız, bu değeri kullanın <xref:System.Windows.Forms.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="79c11-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="79c11-119">Liste denetimi yüksekliğini uzun olması durumunda bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="79c11-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="79c11-120">Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="79c11-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="79c11-121">Değer</span><span class="sxs-lookup"><span data-stu-id="79c11-121">Value</span></span>|<span data-ttu-id="79c11-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79c11-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="79c11-123">Satır sonu ulaşılana kadar sağa kaydırın şekilde metninin denetimde otomatik olarak, sarılır değil.</span><span class="sxs-lookup"><span data-stu-id="79c11-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="79c11-124">Bu değer belirlediğinizde kullanmak <xref:System.Windows.Forms.ScrollBars.Horizontal> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.Both>, yukarıdaki.</span><span class="sxs-lookup"><span data-stu-id="79c11-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="79c11-125">`true`(varsayılan)</span><span class="sxs-lookup"><span data-stu-id="79c11-125">`true` (default)</span></span>|<span data-ttu-id="79c11-126">Yatay kaydırma çubuğu görünmez.</span><span class="sxs-lookup"><span data-stu-id="79c11-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="79c11-127">Bu değer belirlediğinizde kullanmak <xref:System.Windows.Forms.ScrollBars.Vertical> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.None>, bir veya daha fazla paragraf görüntülemek için yukarıdaki.</span><span class="sxs-lookup"><span data-stu-id="79c11-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79c11-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79c11-128">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="79c11-129">TextBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="79c11-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="79c11-130">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını denetleme</span><span class="sxs-lookup"><span data-stu-id="79c11-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="79c11-131">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="79c11-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="79c11-132">Nasıl yapılır: salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="79c11-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="79c11-133">Nasıl yapılır: dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="79c11-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="79c11-134">Nasıl yapılır: metni seçme Windows Forms TextBox denetiminde</span><span class="sxs-lookup"><span data-stu-id="79c11-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="79c11-135">TextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="79c11-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
