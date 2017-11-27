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
ms.openlocfilehash: 2caa77285ebe327adc690b26baeb58aa800627fb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="lines-curves-and-shapes"></a><span data-ttu-id="4d49a-102">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="4d49a-102">Lines, Curves, and Shapes</span></span>
<span data-ttu-id="4d49a-103">Vektör grafikleri kısmı [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizgiler çizme, eğriler, çizmek çizme ve şekilleri doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d49a-103">The vector graphics portion of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is used to draw lines, draw curves, and to draw and fill shapes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d49a-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4d49a-104">In This Section</span></span>  
 [<span data-ttu-id="4d49a-105">Vektör grafiklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="4d49a-105">Vector Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)  
 <span data-ttu-id="4d49a-106">Vektör grafikleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4d49a-106">Discusses vector graphics.</span></span>  
  
 [<span data-ttu-id="4d49a-107">Kalemler, çizgiler ve dikdörtgenler GDI +'da</span><span class="sxs-lookup"><span data-stu-id="4d49a-107">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 <span data-ttu-id="4d49a-108">Çizgiler ve dikdörtgenler çizme açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4d49a-108">Discusses drawing lines and rectangles.</span></span>  
  
 [<span data-ttu-id="4d49a-109">Elipsler ve yaylar GDI +'da</span><span class="sxs-lookup"><span data-stu-id="4d49a-109">Ellipses and Arcs in GDI+</span></span>](../../../../docs/framework/winforms/advanced/ellipses-and-arcs-in-gdi.md)  
 <span data-ttu-id="4d49a-110">Yaylar ve üç nokta tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-110">Defines arcs and ellipses and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4d49a-111">GDI +'daki çokgenler</span><span class="sxs-lookup"><span data-stu-id="4d49a-111">Polygons in GDI+</span></span>](../../../../docs/framework/winforms/advanced/polygons-in-gdi.md)  
 <span data-ttu-id="4d49a-112">Çokgenler tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-112">Defines polygons and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4d49a-113">GDI +'daki ana eğri cetvelleri</span><span class="sxs-lookup"><span data-stu-id="4d49a-113">Cardinal Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cardinal-splines-in-gdi.md)  
 <span data-ttu-id="4d49a-114">Ana Eğriler tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-114">Defines cardinal splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4d49a-115">GDI +'daki Bézier eğrileri</span><span class="sxs-lookup"><span data-stu-id="4d49a-115">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 <span data-ttu-id="4d49a-116">Bezier eğrileri tanımlar ve bunları çizmek için gereken sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-116">Defines Bezier splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="4d49a-117">GDI +'da grafik yolları</span><span class="sxs-lookup"><span data-stu-id="4d49a-117">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)  
 <span data-ttu-id="4d49a-118">Yolları ve nasıl oluşturulacağını ve çizerken açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-118">Describes paths and how to create and draw them.</span></span>  
  
 [<span data-ttu-id="4d49a-119">Fırçalar ve dolgulu şekiller GDI +'da</span><span class="sxs-lookup"><span data-stu-id="4d49a-119">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 <span data-ttu-id="4d49a-120">Fırça türlerini ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-120">Describes brush types and how to use them.</span></span>  
  
 [<span data-ttu-id="4d49a-121">GDI +'da açık ve kapalı Eğriler</span><span class="sxs-lookup"><span data-stu-id="4d49a-121">Open and Closed Curves in GDI+</span></span>](../../../../docs/framework/winforms/advanced/open-and-closed-curves-in-gdi.md)  
 <span data-ttu-id="4d49a-122">Açık ve kapalı eğriler ve çizmek ve onları doldurmak nasıl tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-122">Defines open and closed curves and how to draw and fill them.</span></span>  
  
 [<span data-ttu-id="4d49a-123">GDI +'daki bölgeler</span><span class="sxs-lookup"><span data-stu-id="4d49a-123">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 <span data-ttu-id="4d49a-124">Bölgeleri ile ilişkili yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-124">Describes the methods associated with regions.</span></span>  
  
 [<span data-ttu-id="4d49a-125">GDI +'da çizim yüzeyini kısıtlama</span><span class="sxs-lookup"><span data-stu-id="4d49a-125">Restricting the Drawing Surface in GDI+</span></span>](../../../../docs/framework/winforms/advanced/restricting-the-drawing-surface-in-gdi.md)  
 <span data-ttu-id="4d49a-126">Kırpma ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-126">Describes clipping and how to use it.</span></span>  
  
 [<span data-ttu-id="4d49a-127">Çizgiler ve eğrilerle düzgünleştirme</span><span class="sxs-lookup"><span data-stu-id="4d49a-127">Antialiasing with Lines and Curves</span></span>](../../../../docs/framework/winforms/advanced/antialiasing-with-lines-and-curves.md)  
 <span data-ttu-id="4d49a-128">Düzgünleştirme ve çizim sırasında düzgünleştirme kullanma satırları ve eğriler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d49a-128">Defines antialiasing and how use antialiasing when drawing lines and curves.</span></span>
