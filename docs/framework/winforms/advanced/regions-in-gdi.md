---
title: GDI+'daki Bölgeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: 31c0e4b1509c478786d075b127f0b181d5cdd1c6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724979"
---
# <a name="regions-in-gdi"></a><span data-ttu-id="07daa-102">GDI+'daki Bölgeler</span><span class="sxs-lookup"><span data-stu-id="07daa-102">Regions in GDI+</span></span>
<span data-ttu-id="07daa-103">Bir bölge, bir çıktı cihazına görüntü alanının bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="07daa-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="07daa-104">Bölgeler (tek bir dikdörtgen) basit veya karmaşık (çokgenler ve kapalı Eğriler birleşimi) olabilir.</span><span class="sxs-lookup"><span data-stu-id="07daa-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="07daa-105">Aşağıdaki resimde iki bölgeleri gösterir: bir bir dikdörtgen oluşturulur ve diğer bir yolu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="07daa-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="07daa-106">![Bölgeleri](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="07daa-106">![Regions](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="07daa-107">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="07daa-107">Using Regions</span></span>  
 <span data-ttu-id="07daa-108">Bölgeler, kırpma için sık kullanılan ve isabet sınaması.</span><span class="sxs-lookup"><span data-stu-id="07daa-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="07daa-109">Kırpma çizim ekran alanı, genellikle güncelleştirilmesi gerekiyor bölümü belirli bir bölgeye kısıtlama içerir.</span><span class="sxs-lookup"><span data-stu-id="07daa-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="07daa-110">İsabet sınaması bir fare düğmesine basıldığında imleci ekranın belirli bir bölgede olup olmadığını belirlemek için denetleme içerir.</span><span class="sxs-lookup"><span data-stu-id="07daa-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="07daa-111">Bir dikdörtgen ya da yolu bir bölgeden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07daa-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="07daa-112">Ayrıca, mevcut bölgelerimiz birleştirerek karmaşık bölgeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07daa-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="07daa-113"><xref:System.Drawing.Region> Sınıfı bölgeleri birleştirmek için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, ve <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="07daa-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="07daa-114">İki bölgeler kesişimini hem bölgelerine ait olan tüm noktaları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="07daa-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="07daa-115">Bir ya da diğer veya her iki bölgeleri ait tüm noktaları kümesini birleşimdir.</span><span class="sxs-lookup"><span data-stu-id="07daa-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="07daa-116">Bir bölge tümleme bölgede değil tüm noktaları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="07daa-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="07daa-117">Aşağıdaki resimde, önceki resimde gösterilen iki bölgeleri birleşimini ve kesişimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="07daa-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="07daa-118">![Bölgeleri](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="07daa-118">![Regions](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="07daa-119"><xref:System.Drawing.Region.Xor%2A> Bölge çiftine uygulanan yöntemi, tek bir bölge veya diğer, ancak ikisini birden ait tüm noktaları içeren bir bölge üretir.</span><span class="sxs-lookup"><span data-stu-id="07daa-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="07daa-120"><xref:System.Drawing.Region.Exclude%2A> Bölge çiftine uygulanan yöntem, ilk bölgeye ikinci bir bölgede değil tüm noktaları içeren bir bölge üretir.</span><span class="sxs-lookup"><span data-stu-id="07daa-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="07daa-121">Uygulamasını neden bölgeler aşağıda gösterilmektedir <xref:System.Drawing.Region.Xor%2A> ve <xref:System.Drawing.Region.Exclude%2A> yöntemleri için bu konunun başında gösterilen iki bölgeleri.</span><span class="sxs-lookup"><span data-stu-id="07daa-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="07daa-122">![Bölgeleri](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="07daa-122">![Regions](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="07daa-123">Bir bölge doldurmak için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi bir <xref:System.Drawing.Brush> nesnesi ve bir <xref:System.Drawing.Region> nesne.</span><span class="sxs-lookup"><span data-stu-id="07daa-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="07daa-124"><xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.FillRegion%2A> yöntemi ve <xref:System.Drawing.Brush> nesneyi dolgu rengini veya desenini gibi özniteliklerini depolar.</span><span class="sxs-lookup"><span data-stu-id="07daa-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="07daa-125">Aşağıdaki örnek, bir bölgeye düz renk ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="07daa-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="07daa-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07daa-126">See also</span></span>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="07daa-127">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="07daa-127">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="07daa-128">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="07daa-128">Using Regions</span></span>](using-regions.md)
