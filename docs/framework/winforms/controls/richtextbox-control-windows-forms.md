---
title: RichTextBox Denetimi
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
ms.openlocfilehash: 9d26ec7bfc4d75b304bbc9dc98dbbeaed64effe7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743128"
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="48b01-102">RichTextBox Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="48b01-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="48b01-103">Windows Forms `RichTextBox` denetimi, biçimlendirme ile metin görüntülemek, girmek ve işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48b01-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="48b01-104">`RichTextBox` denetimi <xref:System.Windows.Forms.TextBox> denetiminin yaptığı her şeyi yapar, ancak yazı tiplerini, renkleri ve bağlantıları da görüntüleyebilir; dosyadan metin ve katıştırılmış görüntüleri yükleme; işlemleri geri alma ve yineleme; ve belirtilen karakterleri bulur.</span><span class="sxs-lookup"><span data-stu-id="48b01-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="48b01-105">`RichTextBox` denetimi genellikle, Microsoft Word gibi Word işleme uygulamalarına benzer şekilde metin işleme ve görüntüleme özellikleri sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48b01-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="48b01-106"><xref:System.Windows.Forms.TextBox> denetimi gibi, `RichTextBox` denetimi de kaydırma çubuklarını görüntüleyebilir; Ancak <xref:System.Windows.Forms.TextBox> denetiminin aksine, varsayılan olarak hem yatay hem de dikey kaydırma çubuklarını görüntüler ve ek kaydırma çubuğu ayarlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="48b01-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48b01-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="48b01-107">In This Section</span></span>  
 [<span data-ttu-id="48b01-108">RichTextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="48b01-108">RichTextBox Control Overview</span></span>](richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="48b01-109">`RichTextBox` denetiminin genel kavramlarını tanıtır, bu, kullanıcıların biçimlendirme seçenekleriyle metin girmelerini, görüntülemesi ve işlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48b01-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="48b01-110">Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme</span><span class="sxs-lookup"><span data-stu-id="48b01-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="48b01-111">`RichTextBox` denetiminde yazı tipi ve paragraf biçimlendirmesinde yapılan değişikliklerin nasıl izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="48b01-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="48b01-112">Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="48b01-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="48b01-113">`RichTextBox` denetimindeki kaydırma çubukları için kullanılabilen birçok seçeneği açıklar.</span><span class="sxs-lookup"><span data-stu-id="48b01-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="48b01-114">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="48b01-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="48b01-115">`RichTextBox` denetiminden Web sitelerine nasıl bağlantı kurulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48b01-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="48b01-116">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="48b01-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="48b01-117">`RichTextBox` denetimine veri sürüklemek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="48b01-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="48b01-118">Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme</span><span class="sxs-lookup"><span data-stu-id="48b01-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="48b01-119">`RichTextBox` denetimine var olan bir dosyayı yüklemek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="48b01-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="48b01-120">Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme</span><span class="sxs-lookup"><span data-stu-id="48b01-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="48b01-121">`RichTextBox` denetiminin içeriğini bir dosyaya kaydetmek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="48b01-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="48b01-122">Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="48b01-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="48b01-123">`RichTextBox` denetimindeki metnin yazı tipi ailesinin, boyutunun, stilinin ve renginin nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="48b01-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="48b01-124">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama</span><span class="sxs-lookup"><span data-stu-id="48b01-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="48b01-125">`RichTextBox` denetimindeki paragrafları biçimlendirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="48b01-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="48b01-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="48b01-126">Reference</span></span>  
 <span data-ttu-id="48b01-127"><xref:System.Windows.Forms.RichTextBox> sınıfı</span><span class="sxs-lookup"><span data-stu-id="48b01-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="48b01-128">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="48b01-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="48b01-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="48b01-129">Related Sections</span></span>  
 [<span data-ttu-id="48b01-130">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="48b01-130">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="48b01-131">Windows Forms denetimlerinin tüm listesini, kullanımları hakkındaki bilgilerin bağlantılarıyla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="48b01-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="48b01-132">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="48b01-132">TextBox Control</span></span>](textbox-control-windows-forms.md)  
 <span data-ttu-id="48b01-133"><xref:System.Windows.Forms.TextBox> denetimin genel kavramlarını tanıtır ve bu, kullanıcının düzenlenebilir, çok satırlı girişine izin verir.</span><span class="sxs-lookup"><span data-stu-id="48b01-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
