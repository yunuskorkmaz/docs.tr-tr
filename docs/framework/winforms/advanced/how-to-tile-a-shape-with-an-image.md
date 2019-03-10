---
title: 'Nasıl yapılır: Bir şekli bir görüntüyle döşeme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: d873ba717fa94852692ce395ef7da30c512aba59
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719695"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="03989-102">Nasıl yapılır: Bir şekli bir görüntüyle döşeme</span><span class="sxs-lookup"><span data-stu-id="03989-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="03989-103">Dikdörtgen görüntüleri yalnızca kutucukları birbirinin yanına bir katı kapsayacak şekilde yerleştirilebilir gibi diğer yanındaki (döşeme) bir şekil doldurmak için yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="03989-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="03989-104">Bir şeklin içinin döşeme için bir doku fırça kullanın.</span><span class="sxs-lookup"><span data-stu-id="03989-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="03989-105">Oluşturduğunuzda bir <xref:System.Drawing.TextureBrush> nesnesi oluşturucusuna geçirmeniz bağımsız değişkenlerden biri olan bir <xref:System.Drawing.Image> nesne.</span><span class="sxs-lookup"><span data-stu-id="03989-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="03989-106">Bir şeklin içinin boyamak için doku fırça kullandığınızda, bu görüntüyü yinelenen kopyalarını şekli doldurulur.</span><span class="sxs-lookup"><span data-stu-id="03989-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="03989-107">Kaydırma modu özelliğini <xref:System.Drawing.TextureBrush> nesneyi belirleyen dikdörtgen bir kılavuzda yinelenen olarak nasıl yönlendirilmiş görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="03989-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="03989-108">Tüm kutucukları kılavuzunda aynı yönü hale getirebilir veya sonraki bir kılavuz konumundan Çevir görüntü yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03989-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="03989-109">Çevirme yatay olabilir dikey ya da her ikisini de.</span><span class="sxs-lookup"><span data-stu-id="03989-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="03989-110">Aşağıdaki örnekler, farklı türde çevirme ile döşeme göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="03989-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="03989-111">Resim kutucuğunda için</span><span class="sxs-lookup"><span data-stu-id="03989-111">To tile an image</span></span>  
  
-   <span data-ttu-id="03989-112">Bu örnek, bir 200 × 200 dikdörtgen kutucuğa 75 × 75 aşağıda kullanır.</span><span class="sxs-lookup"><span data-stu-id="03989-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="03989-113">![Döşeme 1](./media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="03989-113">![Tile 1](./media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="03989-114">Aşağıdaki çizim dikdörtgeni görüntünün ile nasıl döşenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="03989-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="03989-115">Tüm kutucuklar aynı yönü gerektiğini unutmayın; hiçbir çevirme yoktur.</span><span class="sxs-lookup"><span data-stu-id="03989-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="03989-116">![Döşeme 2](./media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="03989-116">![Tile 2](./media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="03989-117">Görüntüyü döşeme sırasında yatay olarak çevrilip çevrilmediği</span><span class="sxs-lookup"><span data-stu-id="03989-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="03989-118">Bu örnek, bir 200 × 200 dikdörtgen doldurmak için 75 × 75 görüntünün aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="03989-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="03989-119">Görüntüyü yatay olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="03989-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="03989-120">Aşağıdaki çizim dikdörtgeni görüntünün ile nasıl döşenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="03989-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="03989-121">Belirli bir satırda sonraki bir kutucuğunuz taşırken, görüntüyü yatay olarak çevrilmiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="03989-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="03989-122">![Döşeme 3](./media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="03989-122">![Tile 3](./media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="03989-123">Görüntüyü dikey olarak döşeme sırasında ters çevirmek için</span><span class="sxs-lookup"><span data-stu-id="03989-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="03989-124">Bu örnek, bir 200 × 200 dikdörtgen doldurmak için 75 × 75 görüntünün aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="03989-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="03989-125">Görüntüyü dikey olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="03989-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="03989-126">Görüntü çalışırken döşeme Yatayda ve Dikeyde ters çevirmek için</span><span class="sxs-lookup"><span data-stu-id="03989-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="03989-127">Bu örnek, bir 200 × 200 dikdörtgen kutucuğa 75 × 75 görüntünün aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="03989-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="03989-128">Görüntüyü yatay ve dikey olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="03989-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="03989-129">Aşağıdaki çizim dikdörtgeni görüntünün tarafından nasıl döşenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="03989-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="03989-130">Belirli bir satıra gelecek bir kutucuğunuz gitme, görüntüyü yatay olarak çevrilmiş ve sonraki belirli bir sütundaki bir kutucuğunuz taşırken, görüntüyü dikey olarak çevrilmiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="03989-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="03989-131">![Döşeme 5](./media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="03989-131">![Tile 5](./media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="03989-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03989-132">See also</span></span>
- [<span data-ttu-id="03989-133">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="03989-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
