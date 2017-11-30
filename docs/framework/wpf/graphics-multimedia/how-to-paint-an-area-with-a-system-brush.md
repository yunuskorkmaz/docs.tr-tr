---
title: "Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 355df3718d90768cdfa8bc9780c44c19eb4bf9bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="ee4ec-102">Nasıl yapılır: Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="ee4ec-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="ee4ec-103"><xref:System.Windows.SystemColors> Sınıfı sistem fırçaları ve renkler, erişim gibi sağlar <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, ve <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="ee4ec-104">Sistem Fırçası olan bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renk ile alanı boyar nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="ee4ec-105">Sistem Fırçası her zaman bir düz dolgu üretir; gradyan oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="ee4ec-106">Sistem fırçaları statik veya dinamik bir kaynak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="ee4ec-107">Uygulama çalışırken kullanıcı sistem fırçası değiştirirse otomatik olarak güncelleştirmek için fırça istiyorsanız, dinamik kaynak kullanın; Aksi halde, bir statik kaynak kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="ee4ec-108">SystemColors sınıfı çeşitli sıkı bir adlandırma kuralı izleyin statik özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="ee4ec-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="ee4ec-109">*\<SystemColor >*fırça</span><span class="sxs-lookup"><span data-stu-id="ee4ec-109">*\<SystemColor>*Brush</span></span>  
  
     <span data-ttu-id="ee4ec-110">Statik başvuru alır bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renginin.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="ee4ec-111">*\<SystemColor >*BrushKey</span><span class="sxs-lookup"><span data-stu-id="ee4ec-111">*\<SystemColor>*BrushKey</span></span>  
  
     <span data-ttu-id="ee4ec-112">Dinamik bir başvuru edinir bir <xref:System.Windows.Media.SolidColorBrush> belirtilen sistem renginin.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="ee4ec-113">*\<SystemColor >*rengi</span><span class="sxs-lookup"><span data-stu-id="ee4ec-113">*\<SystemColor>*Color</span></span>  
  
     <span data-ttu-id="ee4ec-114">Statik başvuru alır bir <xref:System.Windows.Media.Color> belirtilen sistem renginin yapısını.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="ee4ec-115">*\<SystemColor >*ColorKey</span><span class="sxs-lookup"><span data-stu-id="ee4ec-115">*\<SystemColor>*ColorKey</span></span>  
  
     <span data-ttu-id="ee4ec-116">Dinamik bir başvuru edinir <xref:System.Windows.Media.Color> belirtilen sistem renginin yapısını.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="ee4ec-117">Sistem rengi bir <xref:System.Windows.Media.Color> fırça yapılandırmak için kullanılan yapısı.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="ee4ec-118">Örneğin, sistem renkleri ayarlayarak kullanan bir gradyan oluşturabilirsiniz <xref:System.Windows.Media.GradientStop.Color%2A> özelliklerini bir <xref:System.Windows.Media.LinearGradientBrush> nesnesi gradyan duraklarının sistem renklerle.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="ee4ec-119">Bir örnek için bkz: [gradyan Sistem renklerini kullan](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="ee4ec-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee4ec-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee4ec-120">Example</span></span>  
 <span data-ttu-id="ee4ec-121">Aşağıdaki örnek, bir düğmenin arka planını ayarlamak için dinamik sistem fırçası başvurusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="ee4ec-122">Sonraki örnek bir düğmenin arka planını ayarlamak için bir statik sistem fırçası başvurusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="ee4ec-123">Bir sistem renginin bir gradyan içerisinde nasıl kullanılacağını gösteren bir örnek için bkz: [Sistem renklerini kullan gradyan](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="ee4ec-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4ec-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee4ec-124">See Also</span></span>  
 [<span data-ttu-id="ee4ec-125">Bir gradyan kullanım sistem renkleri</span><span class="sxs-lookup"><span data-stu-id="ee4ec-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="ee4ec-126">Boyama düz renklerle ve gradyan genel bakış</span><span class="sxs-lookup"><span data-stu-id="ee4ec-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
