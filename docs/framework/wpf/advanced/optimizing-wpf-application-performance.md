---
title: Uygulama performansını iyileştirme
description: Bu kaynakları kullanın, performansı planlama ve donanımdan yararlanma gibi Windows Presentation Foundation uygulamaların performansını geliştirir.
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166331"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="cb541-103">WPF Uygulama Performansını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="cb541-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="cb541-104">Bu bölüm, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarının performansını artırmanın yollarını arayan uygulama geliştiricileri için başvuru olarak hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb541-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="cb541-105">Microsoft .NET Framework 'Ün yeni bir geliştiricisiyseniz ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ilk olarak her iki platformda de kendinizi öğrenmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb541-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="cb541-106">Bu bölüm, her ikisinin de bilgi sahibi olduğunu varsayar ve uygulamalarını çalışır duruma getirmek için yeterince bildiğiniz programcılar için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb541-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb541-107">Bu bölümde belirtilen performans verileri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 512 RAM ve bır ATI Radeon 9700 grafik kartı ile 2,8 GHz bilgisayar üzerinde çalışan uygulamalara dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb541-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb541-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cb541-108">In This Section</span></span>  
 [<span data-ttu-id="cb541-109">Uygulama Performansını Planlama</span><span class="sxs-lookup"><span data-stu-id="cb541-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="cb541-110">Donanımdan Yararlanma</span><span class="sxs-lookup"><span data-stu-id="cb541-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="cb541-111">Düzen ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="cb541-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="cb541-112">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cb541-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="cb541-113">Nesne Davranışı</span><span class="sxs-lookup"><span data-stu-id="cb541-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="cb541-114">Uygulama Kaynakları</span><span class="sxs-lookup"><span data-stu-id="cb541-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="cb541-115">Metin</span><span class="sxs-lookup"><span data-stu-id="cb541-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="cb541-116">Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="cb541-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="cb541-117">Denetimler</span><span class="sxs-lookup"><span data-stu-id="cb541-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="cb541-118">Diğer Performans Önerileri</span><span class="sxs-lookup"><span data-stu-id="cb541-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="cb541-119">Uygulama Başlangıç Zamanı</span><span class="sxs-lookup"><span data-stu-id="cb541-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb541-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb541-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="cb541-121">Grafik İşleme Katmanları</span><span class="sxs-lookup"><span data-stu-id="cb541-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="cb541-122">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb541-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="cb541-123">Düzen</span><span class="sxs-lookup"><span data-stu-id="cb541-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="cb541-124">WPF İçinde Ağaçlar</span><span class="sxs-lookup"><span data-stu-id="cb541-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="cb541-125">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb541-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="cb541-126">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb541-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="cb541-127">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb541-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="cb541-128">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb541-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="cb541-129">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="cb541-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="cb541-130">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="cb541-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="cb541-131">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="cb541-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="cb541-132">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="cb541-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="cb541-133">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb541-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="cb541-134">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb541-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="cb541-135">Animasyon İpuçları ve Püf Noktaları</span><span class="sxs-lookup"><span data-stu-id="cb541-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="cb541-136">İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="cb541-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
