---
title: 'Nasıl yapılır: Bir Şekli Bir Resimle Döşeme'
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
ms.openlocfilehash: a906db44a548361df2822efa24d1dd1849cb5a24
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063732"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="8a821-102">Nasıl yapılır: Bir Şekli Bir Resimle Döşeme</span><span class="sxs-lookup"><span data-stu-id="8a821-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="8a821-103">Dikdörtgen görüntüleri yalnızca kutucukları birbirinin yanına bir katı kapsayacak şekilde yerleştirilebilir gibi diğer yanındaki (döşeme) bir şekil doldurmak için yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8a821-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="8a821-104">Bir şeklin içinin döşeme için bir doku fırça kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a821-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="8a821-105">Oluşturduğunuzda bir <xref:System.Drawing.TextureBrush> nesnesi oluşturucusuna geçirmeniz bağımsız değişkenlerden biri olan bir <xref:System.Drawing.Image> nesne.</span><span class="sxs-lookup"><span data-stu-id="8a821-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="8a821-106">Bir şeklin içinin boyamak için doku fırça kullandığınızda, bu görüntüyü yinelenen kopyalarını şekli doldurulur.</span><span class="sxs-lookup"><span data-stu-id="8a821-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="8a821-107">Kaydırma modu özelliğini <xref:System.Drawing.TextureBrush> nesneyi belirleyen dikdörtgen bir kılavuzda yinelenen olarak nasıl yönlendirilmiş görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="8a821-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="8a821-108">Tüm kutucukları kılavuzunda aynı yönü hale getirebilir veya sonraki bir kılavuz konumundan Çevir görüntü yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a821-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="8a821-109">Çevirme yatay olabilir dikey ya da her ikisini de.</span><span class="sxs-lookup"><span data-stu-id="8a821-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="8a821-110">Aşağıdaki örnekler, farklı türde çevirme ile döşeme göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8a821-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="8a821-111">Resim kutucuğunda için</span><span class="sxs-lookup"><span data-stu-id="8a821-111">To tile an image</span></span>  
  
- <span data-ttu-id="8a821-112">Bu örnek, bir 200 × 200 dikdörtgen kutucuğa 75 × 75 aşağıda kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a821-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 ![Kırmızı bir ev ve bir ağaç gösteren kutucuk resim.](./media/how-to-tile-a-shape-with-an-image/rectangle-tile-200x200.gif)  
  
- <span data-ttu-id="8a821-114">Aşağıdaki çizim dikdörtgeni görüntünün ile nasıl döşenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a821-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="8a821-115">Tüm kutucuklar aynı yönü gerektiğini unutmayın; hiçbir çevirme yoktur.</span><span class="sxs-lookup"><span data-stu-id="8a821-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 ![İçin tüm kutucuklar aynı yönlendirmeyi kullanarak görüntüyle döşenmiş bir dikdörtgen.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-no-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="8a821-117">Görüntüyü döşeme sırasında yatay olarak çevrilip çevrilmediği</span><span class="sxs-lookup"><span data-stu-id="8a821-117">To flip an image horizontally while tiling</span></span>  
  
- <span data-ttu-id="8a821-118">Bu örnek, bir 200 × 200 dikdörtgen doldurmak için 75 × 75 görüntünün aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a821-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="8a821-119">Görüntüyü yatay olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a821-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="8a821-120">Aşağıdaki çizim dikdörtgeni görüntünün ile nasıl döşenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a821-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="8a821-121">Belirli bir satırda sonraki bir kutucuğunuz taşırken, görüntüyü yatay olarak çevrilmiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8a821-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 ![Görüntüyü yatay olarak çevrilmiş döşenmiş bir dikdörtgen.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="8a821-123">Görüntüyü dikey olarak döşeme sırasında ters çevirmek için</span><span class="sxs-lookup"><span data-stu-id="8a821-123">To flip an image vertically while tiling</span></span>  
  
- <span data-ttu-id="8a821-124">Bu örnek, bir 200 × 200 dikdörtgen doldurmak için 75 × 75 görüntünün aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a821-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="8a821-125">Görüntüyü dikey olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a821-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="8a821-126">Görüntü çalışırken döşeme Yatayda ve Dikeyde ters çevirmek için</span><span class="sxs-lookup"><span data-stu-id="8a821-126">To flip an image horizontally and vertically while tiling</span></span>  
  
- <span data-ttu-id="8a821-127">Bu örnek, bir 200 × 200 dikdörtgen kutucuğa 75 × 75 görüntünün aynısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a821-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="8a821-128">Görüntüyü yatay ve dikey olarak çevrilip çevrilmediği gerçekleştirilmeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a821-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="8a821-129">Aşağıdaki çizim dikdörtgeni görüntünün tarafından nasıl döşenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a821-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="8a821-130">Belirli bir satıra gelecek bir kutucuğunuz gitme, görüntüyü yatay olarak çevrilmiş ve sonraki belirli bir sütundaki bir kutucuğunuz taşırken, görüntüyü dikey olarak çevrilmiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8a821-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 ![Yatay ve dikey olarak çevrilmiş görüntüsüyle döşenmiş bir dikdörtgen.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-vertical-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="8a821-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a821-132">See also</span></span>

- [<span data-ttu-id="8a821-133">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="8a821-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
