---
title: "Genel ve Yerel Dönüştürmeler"
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
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e8d05bd0c3e76d643d56b652c8849eef1045ea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="c4713-102">Genel ve Yerel Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c4713-102">Global and Local Transformations</span></span>
<span data-ttu-id="c4713-103">Genel bir dönüşüm tarafından çizilmiş her öğe için geçerli bir dönüşümü gerçekleşir bir verilen <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c4713-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c4713-104">Buna karşılık, yerel bir dönüşüm çizilecek belirli bir öğeye uygulanan bir dönüşüm ' dir.</span><span class="sxs-lookup"><span data-stu-id="c4713-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="c4713-105">Genel dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="c4713-105">Global Transformations</span></span>  
 <span data-ttu-id="c4713-106">Genel dönüştürme oluşturmak için oluşturmak bir <xref:System.Drawing.Graphics> nesne ve sonra değiştirmek kendi <xref:System.Drawing.Graphics.Transform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c4713-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="c4713-107"><xref:System.Drawing.Graphics.Transform%2A> Özelliği bir <xref:System.Drawing.Drawing2D.Matrix> afin dönüşümler herhangi bir dizi tutabilir nesnesini.</span><span class="sxs-lookup"><span data-stu-id="c4713-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="c4713-108">Dönüştürme depolanan <xref:System.Drawing.Graphics.Transform%2A> özelliği, dünya dönüşümü çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c4713-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="c4713-109"><xref:System.Drawing.Graphics> Sınıfı bileşik dünya dönüşümü oluşturmaya yönelik birkaç yöntem sağlar: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, ve <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4713-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="c4713-110">Aşağıdaki örnekte iki kez elips çizilmiştir: Dünya dönüşümü ve sonra bir kez oluşturmadan önce bir kez.</span><span class="sxs-lookup"><span data-stu-id="c4713-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="c4713-111">Dönüştürme y yönünde 0,5 faktörüyle ilk ölçeklendirir sonra 50 birim x yönünde çevirir ve 30 derece döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4713-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="c4713-112">Aşağıdaki çizimde matrisleri dönüştürme katılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4713-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="c4713-113">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="c4713-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4713-114">Önceki örnekte, istemci alanını sol üst köşesinde olduğu koordinat sistemi kökeni hakkında elips döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4713-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="c4713-115">Bu, kendi Merkezi hakkında elips döndürme daha farklı bir sonuç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4713-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="c4713-116">Yerel dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c4713-116">Local Transformations</span></span>  
 <span data-ttu-id="c4713-117">Yerel bir dönüşüm çizilecek belirli bir öğeye uygular.</span><span class="sxs-lookup"><span data-stu-id="c4713-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="c4713-118">Örneğin, bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi bir <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> yol veri noktalarının dönüştürmenizi sağlar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4713-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="c4713-119">Aşağıdaki örnek, bir yol döndürme dönüşümü ve hiçbir dönüştürme bir dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="c4713-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="c4713-120">(Hiçbir dünya dönüşümü olduğu varsayılmaktadır.)</span><span class="sxs-lookup"><span data-stu-id="c4713-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="c4713-121">Dünya dönüşümü çeşitli sonuçlar elde etmek için yerel dönüşümleri ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4713-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="c4713-122">Örneğin, dünya dönüşümü koordinat sistemi gözden geçirin ve yerel dönüştürmeler döndürmek ve nesneler yeni koordinat sistemini çizilmiş ölçeklendirmek için kullanmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4713-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="c4713-123">Kendi kaynak 200 istemci alanını sol kenarından ve 150 pikseller yukarıdan istemci alanının sahip bir koordinat sistemi istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4713-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="c4713-124">Ayrıca, sağa ve yukarıyı y ekseni işaret eden x ekseni ile piksel olması ölçü istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4713-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="c4713-125">Varsayılan koordinat sistemi aşağıyı, y ekseni sahiptir, bu nedenle bir yansıma yatay eksende gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4713-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="c4713-126">Aşağıdaki çizimde, bu tür bir yansıma matris gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4713-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="c4713-127">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="c4713-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="c4713-128">Ardından, bir çeviri 200 birimleri sağa ve aşağı 150 birimleri yapmanız gereken varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c4713-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="c4713-129">Aşağıdaki örnek yeni dünya dönüşümü ayarı tanımlanan koordinat sistemi kurar bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c4713-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="c4713-130">Aşağıdaki kod (önceki örnekte sonunda yerleştirilmiş) kendi yeni koordinat sistemi kökeni sol alt köşede ile tek bir dikdörtgen oluşan bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4713-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="c4713-131">Dikdörtgen bir kez hiçbir yerel dönüştürme ve bir kez yerel dönüştürme ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="c4713-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="c4713-132">Bir yatay bir 30 derecelik döndürme ve ardından 2 faktörüyle ölçekleme yerel dönüştürme oluşur.</span><span class="sxs-lookup"><span data-stu-id="c4713-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="c4713-133">Aşağıdaki çizimde, yeni koordinat sistemi ve iki dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4713-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="c4713-134">![Dönüşümleri](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="c4713-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4713-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4713-135">See Also</span></span>  
 [<span data-ttu-id="c4713-136">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c4713-136">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="c4713-137">Yönetilen GDI+'da Dönüştürmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c4713-137">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
