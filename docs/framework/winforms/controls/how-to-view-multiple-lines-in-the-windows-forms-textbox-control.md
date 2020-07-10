---
title: TextBox denetiminde birden çok satırı görüntüleme
description: Çoklu satır, WordWrap ve kaydırma çubuğu özelliklerini ayarlayarak Windows Forms metin kutusu denetiminde birden çok satırı görüntülemeyi öğrenin.
ms.date: 03/30/2017
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
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174477"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="e53a0-103">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e53a0-103">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="e53a0-104">Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> Denetim tek satırlık bir metin görüntüler ve kaydırma çubuklarını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="e53a0-104">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="e53a0-105">Metin, kullanılabilir alandan uzunsa metnin yalnızca bir kısmı görünür olur.</span><span class="sxs-lookup"><span data-stu-id="e53a0-105">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="e53a0-106"><xref:System.Windows.Forms.TextBox.Multiline%2A>,, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> Ve özelliklerini uygun değerlere ayarlayarak bu varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.ScrollBars%2A> .</span><span class="sxs-lookup"><span data-stu-id="e53a0-106">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="e53a0-107">TextBox denetiminde bir satır başı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e53a0-107">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="e53a0-108">Bir satır başını çok satırlı olarak göstermek için <xref:System.Windows.Forms.TextBox> <xref:System.Environment.NewLine%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-108">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="e53a0-109">Kaçış karakterlerinin () yorumlamasının \\ dile özgü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-109">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="e53a0-110">Visual Basic `Chr$(13) & Chr$(10)` , satır başı ve satır besleme karakter bileşimi için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e53a0-110">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="e53a0-111">TextBox denetiminde birden çok satırı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="e53a0-111">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="e53a0-112"><xref:System.Windows.Forms.TextBox.Multiline%2A>Özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="e53a0-112">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="e53a0-113"><xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>İse `true` (varsayılan), denetimdeki metin bir veya daha fazla paragraf olarak görünür; Aksi takdirde, bazı satırların denetimin kenarında kırpıldığı bir liste olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e53a0-113">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="e53a0-114"><xref:System.Windows.Forms.TextBox.ScrollBars%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-114">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="e53a0-115">Değer</span><span class="sxs-lookup"><span data-stu-id="e53a0-115">Value</span></span>|<span data-ttu-id="e53a0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e53a0-116">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="e53a0-117">Bu değeri, metin neredeyse her zaman denetime uyan bir paragraf olacak şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-117">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="e53a0-118">Kullanıcı, metnin tek seferde görüntülenemeyecek kadar uzun olması halinde, denetimin içinde gezinmek için fare işaretçisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e53a0-118">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="e53a0-119">Bazıları denetimin genişliğinden daha uzun olabilecek bir satır listesini göstermek istiyorsanız bu değeri kullanın <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="e53a0-119">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="e53a0-120">Liste, denetimin yüksekliğinden daha uzun olabileceğinden bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-120">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="e53a0-121"><xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-121">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="e53a0-122">Değer</span><span class="sxs-lookup"><span data-stu-id="e53a0-122">Value</span></span>|<span data-ttu-id="e53a0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e53a0-123">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="e53a0-124">Denetimdeki metin otomatik olarak kaydırılmaz, bu nedenle bir satır sonuna ulaşıncaya kadar sağa kayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e53a0-124">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="e53a0-125">Bu değeri <xref:System.Windows.Forms.ScrollBars.Horizontal> , kaydırma çubukları <xref:System.Windows.Forms.ScrollBars.Both> ' nı veya üstünü seçtiyseniz kullanın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-125">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="e53a0-126">`true`varsayılanını</span><span class="sxs-lookup"><span data-stu-id="e53a0-126">`true` (default)</span></span>|<span data-ttu-id="e53a0-127">Yatay kaydırma çubuğu görünmez.</span><span class="sxs-lookup"><span data-stu-id="e53a0-127">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="e53a0-128"><xref:System.Windows.Forms.ScrollBars.Vertical> <xref:System.Windows.Forms.ScrollBars.None> Bir veya daha fazla paragraf göstermek için, kaydırma çubukları veya yukarıdaki ' u seçerseniz bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e53a0-128">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e53a0-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e53a0-129">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="e53a0-130">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e53a0-130">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e53a0-131">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="e53a0-131">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="e53a0-132">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e53a0-132">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e53a0-133">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e53a0-133">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="e53a0-134">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="e53a0-134">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="e53a0-135">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="e53a0-135">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e53a0-136">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="e53a0-136">TextBox Control</span></span>](textbox-control-windows-forms.md)
