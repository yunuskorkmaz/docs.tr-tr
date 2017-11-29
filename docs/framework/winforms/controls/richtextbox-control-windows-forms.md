---
title: RichTextBox Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80621a12a4ccd5008a0331af005629d45f60abdf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="dcacb-102">RichTextBox Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="dcacb-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="dcacb-103">Windows Forms `RichTextBox` denetimi görüntüleme, girme ve biçimlendirme metin düzenleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dcacb-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="dcacb-104">`RichTextBox` Denetimi her şeyi yapar <xref:System.Windows.Forms.TextBox> denetimi yapar, ancak bunu ayrıca yazı tiplerini, renk ve bağlantıları görüntüleyebilir; metin ve katıştırılmış görüntüler bir dosya; geri alma ve düzenleme işlemleri; Yinele yüklemek ve belirtilen karakterleri bulmak.</span><span class="sxs-lookup"><span data-stu-id="dcacb-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="dcacb-105">`RichTextBox` Denetimi metin düzenleme sağlamak ve Microsoft Word gibi sözcük işleme uygulamaları benzer özellikleri görüntülemek için genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dcacb-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="dcacb-106">Gibi <xref:System.Windows.Forms.TextBox> denetimi `RichTextBox` denetim kaydırma çubukları; görüntüleyebilir ancak aksine <xref:System.Windows.Forms.TextBox> denetim, varsayılan olarak yatay ve dikey kaydırma çubukları görüntülenir ve ek scrollbar ayarlara sahip.</span><span class="sxs-lookup"><span data-stu-id="dcacb-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dcacb-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dcacb-107">In This Section</span></span>  
 [<span data-ttu-id="dcacb-108">RichTextBox denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="dcacb-108">RichTextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="dcacb-109">Genel kavramlarını tanıtır `RichTextBox` girmesini sağlar, Denetim görüntülemek ve metin biçimlendirme seçenekleri ile değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="dcacb-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="dcacb-110">Nasıl yapılır: zaman biçimlendirme öznitelikleri değiştiğinde Windows Forms RichTextBox denetimi belirleme</span><span class="sxs-lookup"><span data-stu-id="dcacb-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="dcacb-111">Yazı tipi ve içinde paragraf biçimlendirme yapılan değişiklikleri izlemek açıklanmaktadır `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="dcacb-112">Nasıl yapılır: görüntü kaydırma çubukları Windows Forms RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="dcacb-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="dcacb-113">Kaydırma çubukları mevcut seçeneklerle açıklar `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="dcacb-114">Nasıl yapılır: Görüntü Web stili bağlantılar Windows Forms RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="dcacb-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="dcacb-115">Web sitelerinden bağlantı açıklanmaktadır `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="dcacb-116">Nasıl yapılır: etkinleştir sürükle ve bırak işlemleri Windows Forms RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="dcacb-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="dcacb-117">Verileri sürükleme için yönergeler sağlar `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="dcacb-118">Nasıl yapılır: yük dosyalarıyla Windows Forms RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="dcacb-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="dcacb-119">Varolan bir dosyaya yüklenmesi için yönergeler sağlar `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="dcacb-120">Nasıl yapılır: dosyaları kaydetme Windows Forms RichTextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="dcacb-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="dcacb-121">İçeriği kaydetmek için yönergeler sağlar `RichTextBox` bir dosyaya denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="dcacb-122">Nasıl yapılır: Windows Forms RichTextBox denetimi için yazı tipi özniteliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="dcacb-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="dcacb-123">Yazı tipi ailesi, boyutu, stil ve içindeki metnin rengi nasıl ayarlanacağını açıklar `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="dcacb-124">Nasıl yapılır: girintileri, asılı girintileri ve madde işaretli paragrafları Windows Forms RichTextBox denetimi ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="dcacb-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="dcacb-125">İçinde paragraf biçimlendirme açıklar `RichTextBox` denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dcacb-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="dcacb-126">Reference</span></span>  
 <span data-ttu-id="dcacb-127"><xref:System.Windows.Forms.RichTextBox>sınıfı</span><span class="sxs-lookup"><span data-stu-id="dcacb-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="dcacb-128">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="dcacb-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dcacb-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dcacb-129">Related Sections</span></span>  
 [<span data-ttu-id="dcacb-130">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="dcacb-130">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="dcacb-131">Windows Forms denetimleri, tam bir listesi ile bunların kullanılması hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dcacb-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="dcacb-132">TextBox denetimi</span><span class="sxs-lookup"><span data-stu-id="dcacb-132">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)  
 <span data-ttu-id="dcacb-133">Genel kavramlarını tanıtır <xref:System.Windows.Forms.TextBox> kullanıcıdan düzenlenebilir, çok satırlı girdi sağlayan denetim.</span><span class="sxs-lookup"><span data-stu-id="dcacb-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
