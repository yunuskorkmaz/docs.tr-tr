---
title: RichTextBox Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
ms.openlocfilehash: 2b1a6604df3979e83e4a815cdb4a9397ab4e67ad
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716986"
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="41a9c-102">RichTextBox Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="41a9c-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="41a9c-103">Windows Forms `RichTextBox` denetimi görüntüleme, girerek ve biçimlendirme metin düzenleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41a9c-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="41a9c-104">`RichTextBox` Netimi her şeyi <xref:System.Windows.Forms.TextBox> denetimi yapar, ancak ayrıca yazı tiplerini, renkleri ve bağlantılar görüntülemek; bir dosya; geri al ve Yinele düzenleme işlemleri; yük metin ve katıştırılmış görüntüler ve belirtilen karakter bulun.</span><span class="sxs-lookup"><span data-stu-id="41a9c-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="41a9c-105">`RichTextBox` Denetimi genellikle metin düzenlemesini sağlar ve Microsoft Word gibi bir sözcük işleme uygulamalarını benzer özellikleri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41a9c-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="41a9c-106">Gibi <xref:System.Windows.Forms.TextBox> denetimi `RichTextBox` denetimi, kaydırma çubukları; görüntüleyebilir ancak tersine <xref:System.Windows.Forms.TextBox> denetimi, yatay ve dikey kaydırma çubukları varsayılan olarak görüntüler ve ek kaydırma çubuğu ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="41a9c-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41a9c-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="41a9c-107">In This Section</span></span>  
 [<span data-ttu-id="41a9c-108">RichTextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41a9c-108">RichTextBox Control Overview</span></span>](richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="41a9c-109">Genel konseptlerini tanıtan `RichTextBox` girmesini sağlayan bir denetimi görüntüleme ve biçimlendirme seçenekleri ile metin düzenleme.</span><span class="sxs-lookup"><span data-stu-id="41a9c-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="41a9c-110">Nasıl yapılır: Windows Forms RichTextBox denetiminde biçimlendirme öznitelikleri belirlerken</span><span class="sxs-lookup"><span data-stu-id="41a9c-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="41a9c-111">Yazı tipi ve paragraf biçimlendirme değişiklikleri izlemek açıklanmaktadır `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="41a9c-112">Nasıl yapılır: Kaydırma çubukları görüntüleme Windows Forms RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="41a9c-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="41a9c-113">Kaydırma çubukları için kullanılabilir çok sayıda seçeneğiniz açıklar `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="41a9c-114">Nasıl yapılır: Windows Forms RichTextBox denetimi ile Web stili bağlantılar görüntüleme</span><span class="sxs-lookup"><span data-stu-id="41a9c-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="41a9c-115">Web sitelerinden bağlantı açıklanmaktadır `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="41a9c-116">Nasıl yapılır: Windows Forms RichTextBox denetimi ile sürükle ve bırak işlemleri etkinleştir</span><span class="sxs-lookup"><span data-stu-id="41a9c-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="41a9c-117">Verileri sürükleyerek için yönergeler sağlar `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="41a9c-118">Nasıl yapılır: Windows Forms RichTextBox denetimine dosyaları yükleme</span><span class="sxs-lookup"><span data-stu-id="41a9c-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="41a9c-119">Varolan bir dosyaya yüklemek için yönergeler sağlar `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="41a9c-120">Nasıl yapılır: İle Windows Forms RichTextBox denetimi dosyaları kaydetme</span><span class="sxs-lookup"><span data-stu-id="41a9c-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="41a9c-121">İçeriği kaydetmek için yönergeler sağlar `RichTextBox` dosyaya denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="41a9c-122">Nasıl yapılır: Windows Forms RichTextBox denetimi için yazı tipi özniteliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="41a9c-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="41a9c-123">Yazı tipi ailesi, boyut, stil ve metin rengi ayarlama işlemi açıklanmaktadır `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="41a9c-124">Nasıl yapılır: Girintileri, asılı girintileri ve madde işaretli paragrafları Windows Forms RichTextBox denetimi ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="41a9c-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="41a9c-125">Paragrafları biçimlendirme açıklar `RichTextBox` denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41a9c-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="41a9c-126">Reference</span></span>  
 <span data-ttu-id="41a9c-127"><xref:System.Windows.Forms.RichTextBox> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="41a9c-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="41a9c-128">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="41a9c-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41a9c-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="41a9c-129">Related Sections</span></span>  
 [<span data-ttu-id="41a9c-130">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="41a9c-130">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="41a9c-131">Windows Forms denetimlerini, tam bir listesi, kullanımları hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="41a9c-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="41a9c-132">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="41a9c-132">TextBox Control</span></span>](textbox-control-windows-forms.md)  
 <span data-ttu-id="41a9c-133">Genel konseptlerini tanıtan <xref:System.Windows.Forms.TextBox> düzenlenebilir, çok satırlı kullanıcı girişi sağlayan bir denetimi.</span><span class="sxs-lookup"><span data-stu-id="41a9c-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
