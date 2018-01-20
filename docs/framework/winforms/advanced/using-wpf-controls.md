---
title: WPF Denetimlerini Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e616019d53648058d51a3d0df457b1380aaf3b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="using-wpf-controls"></a><span data-ttu-id="44dc1-102">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="44dc1-102">Using WPF Controls</span></span>
<span data-ttu-id="44dc1-103">Windows Forms tabanlı uygulamalarda Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44dc1-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="44dc1-104">Bu iki farklı görünüm teknolojileri olsa da, bunlar sorunsuz onunla birlikte çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="44dc1-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="44dc1-105">Windows Form Tasarımcısı Windows Presentation Foundation denetimleri barındırma bir görsel tasarım ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="44dc1-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="44dc1-106">WPF denetimi adlı bir özel Windows Formları denetimi tarafından barındırılan <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="44dc1-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="44dc1-107">Bu denetim formun düzende katılmak ve klavye ve fare iletileri almak için WPF denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="44dc1-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="44dc1-108">Tasarım zamanında düzenleyebilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> herhangi bir Windows Forms denetimi olarak denetleme.</span><span class="sxs-lookup"><span data-stu-id="44dc1-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="44dc1-109">WPF tabanlı uygulamalarınızda Windows Forms denetimleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44dc1-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="44dc1-110">Daha fazla bilgi için bkz: [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).</span><span class="sxs-lookup"><span data-stu-id="44dc1-110">For more information, see [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44dc1-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="44dc1-111">In This Section</span></span>  
 [<span data-ttu-id="44dc1-112">Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="44dc1-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="44dc1-113">Bir Windows formunda Windows Presentation Foundation denetimi kopyalama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44dc1-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="44dc1-114">İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="44dc1-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="44dc1-115">Windows Forms düzeni özellikleri sabitleme ve dayama çizgileri, gibi Windows Presentation Foundation denetimlerini düzenlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44dc1-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>  
  
 [<span data-ttu-id="44dc1-116">İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="44dc1-116">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 <span data-ttu-id="44dc1-117">Windows Form Tasarımcısı arasında iş akışı gösterir ve [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] WPF denetimleri özelliklerini değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="44dc1-117">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] for changing properties on WPF controls.</span></span>  
  
 [<span data-ttu-id="44dc1-118">İzlenecek yol: Windows Forms’ta Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma</span><span class="sxs-lookup"><span data-stu-id="44dc1-118">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="44dc1-119">Windows Forms tabanlı uygulamalarınızda kullanım için bir Windows Presentation Foundation denetimini oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44dc1-119">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>  
  
 [<span data-ttu-id="44dc1-120">İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Forms’a Kopyalama ve Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="44dc1-120">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 <span data-ttu-id="44dc1-121">Bir Windows Presentation Foundation denetimi bir Windows formundan kopyalama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44dc1-121">Shows how to copy a Windows Presentation Foundation control from one Windows Form to another.</span></span>  
  
 [<span data-ttu-id="44dc1-122">İzlenecek yol: Windows Forms’ta Tasarım Zamanında WPF İçeriği Atama</span><span class="sxs-lookup"><span data-stu-id="44dc1-122">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="44dc1-123">Windows Presentation Foundation denetim türlerini formunuzda görüntülemek istediğinizi seçmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44dc1-123">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="44dc1-124">İzlenecek yol: WPF İçeriği için Stil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="44dc1-124">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="44dc1-125">Windows Form Tasarımcısı arasında iş akışı gösterir ve [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] stilleri Windows Presentation Foundation denetimlerine uygulama için.</span><span class="sxs-lookup"><span data-stu-id="44dc1-125">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="44dc1-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="44dc1-126">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="44dc1-127">Windows Forms tabanlı uygulamalarda ana bilgisayar Windows Presentation Foundation denetimleri için kullanabileceğiniz bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44dc1-127">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="44dc1-128">Windows Presentation Foundation tabanlı uygulamanızda ana bilgisayar Windows Forms denetimleri için kullanabileceğiniz bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44dc1-128">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44dc1-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="44dc1-129">Related Sections</span></span>  
 [<span data-ttu-id="44dc1-130">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="44dc1-130">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="44dc1-131">Windows Presentation Foundation ve Windows Forms teknolojileri arasında birlikte çalışabilirlik açıklar.</span><span class="sxs-lookup"><span data-stu-id="44dc1-131">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="44dc1-132">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="44dc1-132">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 <span data-ttu-id="44dc1-133">Windows Presentation Foundation denetimlerinde tasarım açıklar [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="44dc1-133">Describes how to design Windows Presentation Foundation controls in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>
