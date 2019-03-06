---
title: WPF Uygulama Performansını İyileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: c1dd2587fb3642fb930fb7d5d6855a6e48c2ad2b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356396"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="0e99b-102">WPF Uygulama Performansını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="0e99b-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="0e99b-103">Bu bölüm için bir başvuru olarak hazırlanmıştır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama geliştiriciler ait uygulamaların performansını artırmanın yollarını arıyoruz.</span><span class="sxs-lookup"><span data-stu-id="0e99b-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="0e99b-104">Microsoft .NET Framework için yeni bir geliştirici olup olmadığını ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], önce her iki platform ile planladığınızdan.</span><span class="sxs-lookup"><span data-stu-id="0e99b-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="0e99b-105">Bu bölümde her ikisinde de bilgili varsayar ve uygulamalarıyla çalışmaya başlamak için bildiklerinizi programcılar için yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e99b-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e99b-106">Bu bölümde sağlanan performans verileri dayalı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] RAM ve ATI Radeon 9700 2,8 GHz PC 512 ile çalışan uygulamalar grafik kartı.</span><span class="sxs-lookup"><span data-stu-id="0e99b-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e99b-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0e99b-107">In This Section</span></span>  
 [<span data-ttu-id="0e99b-108">Uygulama Performansını Planlama</span><span class="sxs-lookup"><span data-stu-id="0e99b-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="0e99b-109">Donanımdan Yararlanma</span><span class="sxs-lookup"><span data-stu-id="0e99b-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="0e99b-110">Düzen ve Tasarım</span><span class="sxs-lookup"><span data-stu-id="0e99b-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="0e99b-111">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0e99b-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="0e99b-112">Nesne Davranışı</span><span class="sxs-lookup"><span data-stu-id="0e99b-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="0e99b-113">Uygulama Kaynakları</span><span class="sxs-lookup"><span data-stu-id="0e99b-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="0e99b-114">Metin</span><span class="sxs-lookup"><span data-stu-id="0e99b-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="0e99b-115">Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="0e99b-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="0e99b-116">Denetimler</span><span class="sxs-lookup"><span data-stu-id="0e99b-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="0e99b-117">Diğer Performans Önerileri</span><span class="sxs-lookup"><span data-stu-id="0e99b-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="0e99b-118">Uygulama Başlangıç Zamanı</span><span class="sxs-lookup"><span data-stu-id="0e99b-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e99b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e99b-119">See also</span></span>
- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="0e99b-120">Grafik İşleme Katmanları</span><span class="sxs-lookup"><span data-stu-id="0e99b-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="0e99b-121">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e99b-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="0e99b-122">Düzen</span><span class="sxs-lookup"><span data-stu-id="0e99b-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="0e99b-123">WPF İçinde Ağaçlar</span><span class="sxs-lookup"><span data-stu-id="0e99b-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="0e99b-124">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e99b-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="0e99b-125">DrawingVisual Nesnelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e99b-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="0e99b-126">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e99b-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="0e99b-127">Freezable Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e99b-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="0e99b-128">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="0e99b-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="0e99b-129">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="0e99b-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="0e99b-130">Biçimlendirilmiş Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="0e99b-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="0e99b-131">WPF'de Tipografi</span><span class="sxs-lookup"><span data-stu-id="0e99b-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="0e99b-132">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e99b-132">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="0e99b-133">Gezintiye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0e99b-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="0e99b-134">Animasyon İpuçları ve Püf Noktaları</span><span class="sxs-lookup"><span data-stu-id="0e99b-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="0e99b-135">İzlenecek yol: Bir WPF uygulamasında uygulama verilerini önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="0e99b-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
