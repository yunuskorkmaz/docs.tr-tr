---
title: 'Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme'
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
ms.openlocfilehash: 47404f02a753fe143dd573bdf73143416872af9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012925"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="438f6-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="438f6-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="438f6-103">Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> denetimi tek satırlık metin görüntüler ve kaydırma çubukları görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="438f6-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="438f6-104">Metin boşluktan uzunsa, metnin yalnızca bir kısmını görülebilir.</span><span class="sxs-lookup"><span data-stu-id="438f6-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="438f6-105">Ayarlayarak bu varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, ve <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özellikleri uygun değerlere.</span><span class="sxs-lookup"><span data-stu-id="438f6-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="438f6-106">TextBox denetiminde başı görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="438f6-106">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="438f6-107">Bir çok satır başı görüntülenecek <xref:System.Windows.Forms.TextBox>, kullanın <xref:System.Environment.NewLine%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="438f6-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="438f6-108">Unutmayın, kaçış karakterleri yorumunu (\\) dile özgüdür.</span><span class="sxs-lookup"><span data-stu-id="438f6-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="438f6-109">Visual Basic kullanan `Chr$(13) & Chr$(10)` satır başı ve satır besleme karakter birleşimi.</span><span class="sxs-lookup"><span data-stu-id="438f6-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="438f6-110">Çok satırlı TextBox denetiminde görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="438f6-110">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="438f6-111">Ayarlama <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="438f6-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="438f6-112">Varsa <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> olduğu `true` (varsayılan), denetimdeki metin olarak bir veya daha fazla paragraflar sonra görünür; Aksi takdirde, bazı satırlar kırpılmış denetim ucuna, bir liste olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="438f6-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="438f6-113">Ayarlama <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="438f6-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="438f6-114">Değer</span><span class="sxs-lookup"><span data-stu-id="438f6-114">Value</span></span>|<span data-ttu-id="438f6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="438f6-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="438f6-116">Paragraf metni olacaksa, bu değeri kullanın, Denetim neredeyse her zaman uyar.</span><span class="sxs-lookup"><span data-stu-id="438f6-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="438f6-117">Kullanıcı, fare işaretçisini metnin tümünü tek seferde görüntülemek için çok uzun olursa denetim içinde hareket etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="438f6-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="438f6-118">Satırları, bazıları da olabilir genişliğini uzun bir listesini görüntülemek istiyorsanız, bu değeri kullanın <xref:System.Windows.Forms.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="438f6-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="438f6-119">Listenin denetimin yüksekliği uzun olması durumunda bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="438f6-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="438f6-120">Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="438f6-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="438f6-121">Değer</span><span class="sxs-lookup"><span data-stu-id="438f6-121">Value</span></span>|<span data-ttu-id="438f6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="438f6-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="438f6-123">Satır sonu ulaşılana kadar sağa doğru kayar şekilde metin denetiminde otomatik olarak, sarmalanır değil.</span><span class="sxs-lookup"><span data-stu-id="438f6-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="438f6-124">Seçerseniz, bu değeri kullanın <xref:System.Windows.Forms.ScrollBars.Horizontal> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.Both>, yukarıdaki.</span><span class="sxs-lookup"><span data-stu-id="438f6-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="438f6-125">`true` (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="438f6-125">`true` (default)</span></span>|<span data-ttu-id="438f6-126">Yatay kaydırma çubuğu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="438f6-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="438f6-127">Seçerseniz, bu değeri kullanın <xref:System.Windows.Forms.ScrollBars.Vertical> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.None>, bir veya daha fazla paragraflar görüntülemek için yukarıdaki.</span><span class="sxs-lookup"><span data-stu-id="438f6-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="438f6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="438f6-128">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="438f6-129">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="438f6-129">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="438f6-130">Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme</span><span class="sxs-lookup"><span data-stu-id="438f6-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="438f6-131">Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="438f6-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="438f6-132">Nasıl yapılır: Salt okunur metin kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="438f6-132">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="438f6-133">Nasıl yapılır: Dizeye tırnak işaretleri koyma</span><span class="sxs-lookup"><span data-stu-id="438f6-133">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="438f6-134">Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç</span><span class="sxs-lookup"><span data-stu-id="438f6-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="438f6-135">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="438f6-135">TextBox Control</span></span>](textbox-control-windows-forms.md)
