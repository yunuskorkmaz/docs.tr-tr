---
title: TextBox denetiminde birden çok satırı görüntüleme
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
ms.openlocfilehash: 61ea671c1e86fa8254bfc1b043a46f3b7aa6af1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728277"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="96a9f-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="96a9f-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="96a9f-103">Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> denetim tek satırlık bir metin görüntüler ve kaydırma çubuklarını görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="96a9f-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="96a9f-104">Metin, kullanılabilir alandan uzunsa metnin yalnızca bir kısmı görünür olur.</span><span class="sxs-lookup"><span data-stu-id="96a9f-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="96a9f-105"><xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>ve <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliklerini uygun değerlere ayarlayarak bu varsayılan davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96a9f-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="96a9f-106">TextBox denetiminde bir satır başı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="96a9f-106">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="96a9f-107">Bir satır başını çok satırlı bir <xref:System.Windows.Forms.TextBox>göstermek için <xref:System.Environment.NewLine%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="96a9f-108">Kaçış karakterlerinin (\\) yorumlamasının dile özgü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="96a9f-109">Visual Basic, satır başı ve satır besleme karakter bileşimi için `Chr$(13) & Chr$(10)` kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a9f-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="96a9f-110">TextBox denetiminde birden çok satırı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="96a9f-110">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="96a9f-111"><xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="96a9f-112"><xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> `true` (varsayılan), denetimdeki metin bir veya daha fazla paragraf olarak görünür; Aksi takdirde, bazı satırların denetimin kenarında kırpıldığı bir liste olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="96a9f-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="96a9f-113"><xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliğini uygun bir değer olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="96a9f-114">Değer</span><span class="sxs-lookup"><span data-stu-id="96a9f-114">Value</span></span>|<span data-ttu-id="96a9f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96a9f-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="96a9f-116">Bu değeri, metin neredeyse her zaman denetime uyan bir paragraf olacak şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="96a9f-117">Kullanıcı, metnin tek seferde görüntülenemeyecek kadar uzun olması halinde, denetimin içinde gezinmek için fare işaretçisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="96a9f-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="96a9f-118">Bazıları <xref:System.Windows.Forms.TextBox> denetimin genişliğinden daha uzun olabilecek bir satır listesini göstermek istiyorsanız bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="96a9f-119">Liste, denetimin yüksekliğinden daha uzun olabileceğinden bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="96a9f-120"><xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliğini uygun bir değer olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="96a9f-121">Değer</span><span class="sxs-lookup"><span data-stu-id="96a9f-121">Value</span></span>|<span data-ttu-id="96a9f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96a9f-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="96a9f-123">Denetimdeki metin otomatik olarak kaydırılmaz, bu nedenle bir satır sonuna ulaşıncaya kadar sağa kayacaktır.</span><span class="sxs-lookup"><span data-stu-id="96a9f-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="96a9f-124">Yukarıdaki <xref:System.Windows.Forms.ScrollBars.Horizontal> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.Both>seçeneğini belirlediyseniz bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="96a9f-125">`true` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="96a9f-125">`true` (default)</span></span>|<span data-ttu-id="96a9f-126">Yatay kaydırma çubuğu görünmez.</span><span class="sxs-lookup"><span data-stu-id="96a9f-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="96a9f-127">Bir veya daha fazla paragraf göstermek için yukarıdaki <xref:System.Windows.Forms.ScrollBars.Vertical> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.None>seçeneğini belirlediyseniz bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a9f-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96a9f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96a9f-128">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="96a9f-129">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="96a9f-129">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="96a9f-130">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="96a9f-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="96a9f-131">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96a9f-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="96a9f-132">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96a9f-132">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="96a9f-133">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="96a9f-133">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="96a9f-134">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="96a9f-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="96a9f-135">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="96a9f-135">TextBox Control</span></span>](textbox-control-windows-forms.md)
