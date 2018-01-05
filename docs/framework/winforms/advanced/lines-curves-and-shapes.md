---
title: "Çizgiler, Eğriler ve Şekiller"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [Windows Forms], filling
- splines [Windows Forms], drawing
- shapes. drawing
- lines [Windows Forms], drawing
- curves [Windows Forms], drawing
ms.assetid: ace6e8d4-4e94-486b-9681-758a6667dc7f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04d93203f98c91b0d5bbed5f833745a9bb9ab1d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lines-curves-and-shapes"></a><span data-ttu-id="4290d-102">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="4290d-102">Lines, Curves, and Shapes</span></span>
<span data-ttu-id="4290d-103">Vektör grafikleri kısmı [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgiler çizme, eğriler, çizmek çizme ve şekilleri doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4290d-103">The vector graphics portion of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is used to draw lines, draw curves, and to draw and fill shapes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4290d-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4290d-104">In This Section</span></span>  
 [<span data-ttu-id="4290d-105">Vektör Grafiklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4290d-105">Vector Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)  
 <span data-ttu-id="4290d-106">Vektör grafikleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4290d-106">Discusses vector graphics.</span></span>  
  
 [<span data-ttu-id="4290d-107">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="4290d-107">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 <span data-ttu-id="4290d-108">Çizgiler ve dikdörtgenler çizme açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4290d-108">Discusses drawing lines and rectangles.</span></span>  
  
 [<span data-ttu-id="4290d-109">GDI+'da Elipsler ve Yaylar</span><span class="sxs-lookup"><span data-stu-id="4290d-109">Ellipses and Arcs in GDI+</span></span>](../../../../docs/framework/winforms/advanced/ellipses-and-arcs-in-gdi.md)  
 <span data-ttu-id="4290d-110">Yaylar ve üç nokta tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4290d-110">Defines arcs and ellipses and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4290d-111">GDI+'daki Çokgenler</span><span class="sxs-lookup"><span data-stu-id="4290d-111">Polygons in GDI+</span></span>](../../../../docs/framework/winforms/advanced/polygons-in-gdi.md)  
 <span data-ttu-id="4290d-112">Çokgenler tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4290d-112">Defines polygons and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4290d-113">GDI+'daki Ana Eğri Cetvelleri</span><span class="sxs-lookup"><span data-stu-id="4290d-113">Cardinal Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cardinal-splines-in-gdi.md)  
 <span data-ttu-id="4290d-114">Ana Eğriler tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4290d-114">Defines cardinal splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4290d-115">GDI+'daki Bézier Eğrileri</span><span class="sxs-lookup"><span data-stu-id="4290d-115">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 <span data-ttu-id="4290d-116">Bezier eğrileri tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4290d-116">Defines Bezier splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4290d-117">GDI+'da Grafik Yolları</span><span class="sxs-lookup"><span data-stu-id="4290d-117">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)  
 <span data-ttu-id="4290d-118">Yolları ve nasıl oluşturulacağını ve çizerken açıklar.</span><span class="sxs-lookup"><span data-stu-id="4290d-118">Describes paths and how to create and draw them.</span></span>  
  
 [<span data-ttu-id="4290d-119">GDI+'da Fırçalar ve Dolgulu Şekiller</span><span class="sxs-lookup"><span data-stu-id="4290d-119">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 <span data-ttu-id="4290d-120">Fırça türlerini ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4290d-120">Describes brush types and how to use them.</span></span>  
  
 [<span data-ttu-id="4290d-121">GDI+'da Açık ve Kapalı Eğriler</span><span class="sxs-lookup"><span data-stu-id="4290d-121">Open and Closed Curves in GDI+</span></span>](../../../../docs/framework/winforms/advanced/open-and-closed-curves-in-gdi.md)  
 <span data-ttu-id="4290d-122">Açık ve kapalı eğriler ve çizmek ve onları doldurmak nasıl tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4290d-122">Defines open and closed curves and how to draw and fill them.</span></span>  
  
 [<span data-ttu-id="4290d-123">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="4290d-123">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 <span data-ttu-id="4290d-124">Bölgeleri ile ilişkili yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4290d-124">Describes the methods associated with regions.</span></span>  
  
 [<span data-ttu-id="4290d-125">GDI+'da Çizim Yüzeyini Sınırlandırma</span><span class="sxs-lookup"><span data-stu-id="4290d-125">Restricting the Drawing Surface in GDI+</span></span>](../../../../docs/framework/winforms/advanced/restricting-the-drawing-surface-in-gdi.md)  
 <span data-ttu-id="4290d-126">Kırpma ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4290d-126">Describes clipping and how to use it.</span></span>  
  
 [<span data-ttu-id="4290d-127">Nasıl yapılır: Çizgiler ve Eğrilerle Düzgünleştirme</span><span class="sxs-lookup"><span data-stu-id="4290d-127">Antialiasing with Lines and Curves</span></span>](../../../../docs/framework/winforms/advanced/antialiasing-with-lines-and-curves.md)  
 <span data-ttu-id="4290d-128">Düzgünleştirme ve çizim sırasında düzgünleştirme kullanma satırları ve eğriler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4290d-128">Defines antialiasing and how use antialiasing when drawing lines and curves.</span></span>
