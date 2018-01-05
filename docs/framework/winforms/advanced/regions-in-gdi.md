---
title: "GDI+'daki Bölgeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d3805c2d67f5241425ef72d3802aba996d33cfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="regions-in-gdi"></a><span data-ttu-id="f39fb-102">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="f39fb-102">Regions in GDI+</span></span>
<span data-ttu-id="f39fb-103">Bir bölge, bir çıktı aygıtının görüntü alanını bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="f39fb-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="f39fb-104">Bölgeler (tek bir dikdörtgen) basit veya karmaşık (çokgenler ve kapalı Eğriler birleşimi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="f39fb-105">İki bölgede aşağıda gösterilmiştir: bir bir dikdörtgen oluşturulur ve başka bir yoldan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f39fb-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="f39fb-106">![Bölgeler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="f39fb-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="f39fb-107">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f39fb-107">Using Regions</span></span>  
 <span data-ttu-id="f39fb-108">Bölgeler kırpma için sık kullanılan ve isabet testi.</span><span class="sxs-lookup"><span data-stu-id="f39fb-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="f39fb-109">Belirli bir bölgeye görüntü alanının genellikle güncelleştirilmesi gerekiyor bölümü çizim kısıtlama kırpma içerir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="f39fb-110">İsabet testi fare düğmesine basıldığında imleci ekranın belirli bir bölgede olup olmadığını belirlemek için denetimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="f39fb-111">Dikdörtgene ya da bir yol bölgesinden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f39fb-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="f39fb-112">Varolan bölgeleri birleştirerek karmaşık bölgeler de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f39fb-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="f39fb-113"><xref:System.Drawing.Region> Sınıfı bölgeler birleştirmek için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, ve <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="f39fb-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="f39fb-114">İki bölgede kesişimi hem bölgelere ait olan tüm noktaları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="f39fb-115">UNION bir ya da diğer veya her iki bölgeden ait tüm noktalarının kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="f39fb-116">Bir bölge tamamlama bölgede değil tüm noktaları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="f39fb-117">Önceki çizimde gösterilen iki bölgede birleşimi ve kesişimi aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="f39fb-118">![Bölgeler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="f39fb-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="f39fb-119"><xref:System.Drawing.Region.Xor%2A> Bölgeler, çiftine uygulanan yöntem, tek bir bölge veya diğer, ancak ikisini ait tüm noktalarını içeren bir bölge üretir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="f39fb-120"><xref:System.Drawing.Region.Exclude%2A> Bölgeler, çiftine uygulanan yöntem, ilk bölgede ikinci bölgede değil tüm noktalarını içeren bir bölge üretir.</span><span class="sxs-lookup"><span data-stu-id="f39fb-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="f39fb-121">Aşağıdaki çizimde uygulanmasından neden bölgeleri gösterir <xref:System.Drawing.Region.Xor%2A> ve <xref:System.Drawing.Region.Exclude%2A> yöntemleri için bu konunun başında gösterilen iki bölgede.</span><span class="sxs-lookup"><span data-stu-id="f39fb-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="f39fb-122">![Bölgeler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="f39fb-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="f39fb-123">Bir bölge doldurmak için size gereken bir <xref:System.Drawing.Graphics> nesne, bir <xref:System.Drawing.Brush> nesnesi ve bir <xref:System.Drawing.Region> nesne.</span><span class="sxs-lookup"><span data-stu-id="f39fb-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="f39fb-124"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.FillRegion%2A> yöntemi ve <xref:System.Drawing.Brush> nesnesi dolgu rengini veya desenini gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="f39fb-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="f39fb-125">Aşağıdaki örnek, bir bölge düz renk ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="f39fb-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="f39fb-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f39fb-126">See Also</span></span>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="f39fb-127">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="f39fb-127">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="f39fb-128">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f39fb-128">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
