---
title: WPF Denetimlerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: be925bdceea3dd01c568d85fe025d6e037066454
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170476"
---
# <a name="using-wpf-controls"></a><span data-ttu-id="f8402-102">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f8402-102">Using WPF Controls</span></span>
<span data-ttu-id="f8402-103">Windows Forms tabanlı uygulamalarınızı Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8402-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="f8402-104">Bu iki farklı görünümü teknolojileri olsa da, bunlar düzgün çalışmak.</span><span class="sxs-lookup"><span data-stu-id="f8402-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="f8402-105">Windows Form Tasarımcısı, Windows Presentation Foundation denetimleri barındırma için bir görsel tasarım ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8402-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="f8402-106">Adlı bir özel Windows Forms denetimi tarafından barındırılan bir WPF denetiminde <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="f8402-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="f8402-107">WPF denetimi form düzeninde katılmak ve klavye ve fare iletileri almak için bu denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8402-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="f8402-108">Tasarım zamanında düzenleyebilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> herhangi bir Windows Forms denetimi gibi denetim.</span><span class="sxs-lookup"><span data-stu-id="f8402-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="f8402-109">WPF tabanlı uygulamalarınızı Windows Forms denetimleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8402-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="f8402-110">Daha fazla bilgi için [Visual Studio'da XAML tasarım](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f8402-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8402-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f8402-111">In This Section</span></span>  
 [<span data-ttu-id="f8402-112">Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="f8402-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="f8402-113">Bir Windows formunda Windows Presentation Foundation denetim kopyalama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8402-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="f8402-114">İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f8402-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="f8402-115">Sabitleme ve dayama çizgileri, gibi Windows Forms düzeni özellikleri Windows Presentation Foundation denetimleri düzenlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8402-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>
  
 [<span data-ttu-id="f8402-116">İzlenecek yol: Windows Forms’ta Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8402-116">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="f8402-117">Windows Forms tabanlı uygulamalarda kullanmak için bir Windows Presentation Foundation denetim oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8402-117">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>
  
 [<span data-ttu-id="f8402-118">İzlenecek yol: Windows Forms’ta Tasarım Zamanında WPF İçeriği Atama</span><span class="sxs-lookup"><span data-stu-id="f8402-118">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="f8402-119">Formunuzda görüntülemek istediğiniz Windows Presentation Foundation denetim türlerini seçmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8402-119">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="f8402-120">İzlenecek yol: WPF İçeriği için Stil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8402-120">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="f8402-121">Windows Form Tasarımcısı arasındaki iş akışını gösterir ve [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] Windows Presentation Foundation denetimleri için stil uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="f8402-121">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f8402-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f8402-122">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="f8402-123">Windows Forms tabanlı uygulamalarınızı ana bilgisayar Windows Presentation Foundation denetimler için kullanabileceğiniz bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8402-123">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="f8402-124">Ana bilgisayar Windows Forms denetimlerine Windows Presentation Foundation tabanlı uygulamanızda kullanabileceğiniz bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8402-124">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f8402-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f8402-125">Related Sections</span></span>  
 [<span data-ttu-id="f8402-126">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f8402-126">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="f8402-127">Windows Presentation Foundation ve Windows Forms teknolojileri arasında birlikte çalışabilirliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8402-127">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="f8402-128">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="f8402-128">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 <span data-ttu-id="f8402-129">Visual Studio'da Windows Presentation Foundation denetimleri tasarım açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8402-129">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>
