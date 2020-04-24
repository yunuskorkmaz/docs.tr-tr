---
title: Uygulama performansını optimize edin
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 54d69e87ef2a9c5318e394422e3bcfcabcc76210
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646255"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="b662a-102">WPF Uygulama Performansını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="b662a-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="b662a-103">Bu bölüm, uygulamalarının [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] performansını artırmak için yollar arayan uygulama geliştiricileri için bir başvuru olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b662a-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="b662a-104">Microsoft .NET Framework'de yeni bir geliştiriciyseniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ve öncelikle her iki platforma da alışmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b662a-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="b662a-105">Bu bölüm, her ikisinin de çalışma bilgisini varsayar ve uygulamalarını çalışır hale getirmek için yeterli bilgiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b662a-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b662a-106">Bu bölümde sağlanan performans verileri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 512 RAM ve ATI Radeon 9700 ekran kartı na sahip 2,8 GHz PC'de çalışan uygulamalara dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b662a-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b662a-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b662a-107">In This Section</span></span>  
 [<span data-ttu-id="b662a-108">Uygulama Performansını Planlama</span><span class="sxs-lookup"><span data-stu-id="b662a-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="b662a-109">Donanımdan Yararlanma</span><span class="sxs-lookup"><span data-stu-id="b662a-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="b662a-110">Düzen ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="b662a-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="b662a-111">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b662a-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="b662a-112">Nesne Davranışı</span><span class="sxs-lookup"><span data-stu-id="b662a-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="b662a-113">Uygulama Kaynakları</span><span class="sxs-lookup"><span data-stu-id="b662a-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="b662a-114">Metin</span><span class="sxs-lookup"><span data-stu-id="b662a-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="b662a-115">Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="b662a-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="b662a-116">Denetimler</span><span class="sxs-lookup"><span data-stu-id="b662a-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="b662a-117">Diğer Performans Önerileri</span><span class="sxs-lookup"><span data-stu-id="b662a-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="b662a-118">Uygulama Başlangıç Zamanı</span><span class="sxs-lookup"><span data-stu-id="b662a-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="b662a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b662a-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="b662a-120">Grafik İşleme Katmanları</span><span class="sxs-lookup"><span data-stu-id="b662a-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="b662a-121">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b662a-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="b662a-122">Düzen</span><span class="sxs-lookup"><span data-stu-id="b662a-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="b662a-123">WPF İçinde Ağaçlar</span><span class="sxs-lookup"><span data-stu-id="b662a-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="b662a-124">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b662a-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="b662a-125">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="b662a-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="b662a-126">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b662a-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="b662a-127">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b662a-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="b662a-128">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="b662a-128">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="b662a-129">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="b662a-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="b662a-130">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="b662a-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="b662a-131">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="b662a-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="b662a-132">Veri Bağlama Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b662a-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="b662a-133">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b662a-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="b662a-134">Animasyon İpuçları ve Püf Noktaları</span><span class="sxs-lookup"><span data-stu-id="b662a-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="b662a-135">İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="b662a-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
