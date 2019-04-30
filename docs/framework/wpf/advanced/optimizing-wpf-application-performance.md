---
title: WPF Uygulama Performansını İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 53291a0e428b723cd7a6e7b1184639a7b3c3b972
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772989"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="e20be-102">WPF Uygulama Performansını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="e20be-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="e20be-103">Bu bölüm için bir başvuru olarak hazırlanmıştır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama geliştiriciler ait uygulamaların performansını artırmanın yollarını arıyoruz.</span><span class="sxs-lookup"><span data-stu-id="e20be-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="e20be-104">Microsoft .NET Framework için yeni bir geliştirici olup olmadığını ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], önce her iki platform ile planladığınızdan.</span><span class="sxs-lookup"><span data-stu-id="e20be-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="e20be-105">Bu bölümde her ikisinde de bilgili varsayar ve uygulamalarıyla çalışmaya başlamak için bildiklerinizi programcılar için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e20be-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20be-106">Bu bölümde sağlanan performans verileri dayalı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] RAM ve ATI Radeon 9700 2,8 GHz PC 512 ile çalışan uygulamalar grafik kartı.</span><span class="sxs-lookup"><span data-stu-id="e20be-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e20be-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e20be-107">In This Section</span></span>  
 [<span data-ttu-id="e20be-108">Uygulama Performansını Planlama</span><span class="sxs-lookup"><span data-stu-id="e20be-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="e20be-109">Donanımdan Yararlanma</span><span class="sxs-lookup"><span data-stu-id="e20be-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="e20be-110">Düzen ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="e20be-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="e20be-111">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e20be-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="e20be-112">Nesne Davranışı</span><span class="sxs-lookup"><span data-stu-id="e20be-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="e20be-113">Uygulama Kaynakları</span><span class="sxs-lookup"><span data-stu-id="e20be-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="e20be-114">Metin</span><span class="sxs-lookup"><span data-stu-id="e20be-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="e20be-115">Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="e20be-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="e20be-116">Denetimler</span><span class="sxs-lookup"><span data-stu-id="e20be-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="e20be-117">Diğer Performans Önerileri</span><span class="sxs-lookup"><span data-stu-id="e20be-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="e20be-118">Uygulama Başlangıç Zamanı</span><span class="sxs-lookup"><span data-stu-id="e20be-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="e20be-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e20be-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="e20be-120">Grafik İşleme Katmanları</span><span class="sxs-lookup"><span data-stu-id="e20be-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="e20be-121">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20be-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="e20be-122">Düzen</span><span class="sxs-lookup"><span data-stu-id="e20be-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="e20be-123">WPF İçinde Ağaçlar</span><span class="sxs-lookup"><span data-stu-id="e20be-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="e20be-124">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20be-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="e20be-125">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e20be-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="e20be-126">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20be-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="e20be-127">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20be-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="e20be-128">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="e20be-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="e20be-129">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="e20be-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="e20be-130">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="e20be-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="e20be-131">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="e20be-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="e20be-132">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20be-132">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="e20be-133">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e20be-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="e20be-134">Animasyon İpuçları ve Püf Noktaları</span><span class="sxs-lookup"><span data-stu-id="e20be-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="e20be-135">İzlenecek yol: Bir WPF uygulamasında uygulama verilerini önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="e20be-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
