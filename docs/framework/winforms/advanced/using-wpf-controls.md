---
title: WPF Denetimlerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 149a2da1303e6b801a439494254a416a38b145a7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211308"
---
# <a name="use-wpf-controls"></a><span data-ttu-id="a2419-102">WPF denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a2419-102">Use WPF controls</span></span>

<span data-ttu-id="a2419-103">Windows Forms tabanlı uygulamalarınızı Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2419-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="a2419-104">Bu iki farklı görünümü teknolojileri olsa da, bunlar düzgün çalışmak.</span><span class="sxs-lookup"><span data-stu-id="a2419-104">Although these are two different view technologies, they interoperate smoothly.</span></span>

<span data-ttu-id="a2419-105">Windows Form Tasarımcısı'nda Visual Studio, Windows Presentation Foundation denetimleri barındırma için bir görsel tasarım ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2419-105">The Windows Forms Designer in Visual Studio provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="a2419-106">Adlı bir özel Windows Forms denetimi tarafından barındırılan bir WPF denetiminde <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="a2419-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="a2419-107">WPF denetimi form düzeninde katılmak ve klavye ve fare iletileri almak için bu denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2419-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="a2419-108">Tasarım zamanında düzenleyebilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> herhangi bir Windows Forms denetimi gibi denetim.</span><span class="sxs-lookup"><span data-stu-id="a2419-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>

<span data-ttu-id="a2419-109">WPF tabanlı uygulamalarınızı Windows Forms denetimleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2419-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="a2419-110">Daha fazla bilgi için [Visual Studio'da XAML tasarım](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a2419-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a2419-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a2419-111">In This Section</span></span>

<span data-ttu-id="a2419-112">[Nasıl yapılır: Tasarım zamanında bir ElementHost denetimini yapıştırın](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-112">[How to: Copy and Paste an ElementHost Control at Design Time](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)\\</span></span>
<span data-ttu-id="a2419-113">Bir Windows formunda Windows Presentation Foundation denetim kopyalama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a2419-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>

<span data-ttu-id="a2419-114">[İzlenecek yol: Tasarım zamanında WPF içeriğini Windows Forms'ta düzenleme](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-114">[Walkthrough: Arranging WPF Content on Windows Forms at Design Time](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)\\</span></span>
<span data-ttu-id="a2419-115">Sabitleme ve dayama çizgileri, gibi Windows Forms düzeni özellikleri Windows Presentation Foundation denetimleri düzenlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2419-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>

<span data-ttu-id="a2419-116">[İzlenecek yol: Windows Forms'ta tasarım zamanında yeni WPF içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-116">[Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)\\</span></span>
<span data-ttu-id="a2419-117">Windows Forms tabanlı uygulamalarda kullanmak için bir Windows Presentation Foundation denetim oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a2419-117">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>

<span data-ttu-id="a2419-118">[İzlenecek yol: Tasarım zamanında Windows Forms WPF içeriği atama](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-118">[Walkthrough: Assigning WPF Content on Windows Forms at Design Time](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)\\</span></span>
<span data-ttu-id="a2419-119">Formunuzda görüntülemek istediğiniz Windows Presentation Foundation denetim türlerini seçmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a2419-119">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>

<span data-ttu-id="a2419-120">[İzlenecek yol: WPF içeriği için stil oluşturma](walkthrough-styling-wpf-content.md)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-120">[Walkthrough: Styling WPF Content](walkthrough-styling-wpf-content.md)\\</span></span>
<span data-ttu-id="a2419-121">Windows Form Tasarımcısı arasındaki iş akışını gösterir ve [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] Windows Presentation Foundation denetimleri için stil uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="a2419-121">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>

## <a name="reference"></a><span data-ttu-id="a2419-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a2419-122">Reference</span></span>

<xref:System.Windows.Forms.Integration.ElementHost>\
<span data-ttu-id="a2419-123">Windows Forms tabanlı uygulamalarınızı ana bilgisayar Windows Presentation Foundation denetimler için kullanabileceğiniz bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2419-123">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>

<xref:System.Windows.Forms.Integration.WindowsFormsHost>\
<span data-ttu-id="a2419-124">Ana bilgisayar Windows Forms denetimlerine Windows Presentation Foundation tabanlı uygulamanızda kullanabileceğiniz bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2419-124">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a2419-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="a2419-125">Related sections</span></span>

<span data-ttu-id="a2419-126">[Geçiş ve birlikte çalışabilirlik](../../wpf/advanced/migration-and-interoperability.md)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-126">[Migration and Interoperability](../../wpf/advanced/migration-and-interoperability.md)\\</span></span>
<span data-ttu-id="a2419-127">Windows Presentation Foundation ve Windows Forms teknolojileri arasında birlikte çalışabilirliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2419-127">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>

<span data-ttu-id="a2419-128">[Visual Studio'da XAML tasarım](/visualstudio/designers/designing-xaml-in-visual-studio)\\</span><span class="sxs-lookup"><span data-stu-id="a2419-128">[Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)\\</span></span>
<span data-ttu-id="a2419-129">Visual Studio'da Windows Presentation Foundation denetimleri tasarım açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2419-129">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>
