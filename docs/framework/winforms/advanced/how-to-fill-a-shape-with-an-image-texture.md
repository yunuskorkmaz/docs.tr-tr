---
title: "Nasıl yapılır: Bir Şekli Görüntü Dokusuyla Doldurma"
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
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b5ef87762b08daa973237e7b3da1068640e08bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="fa82b-102">Nasıl yapılır: Bir Şekli Görüntü Dokusuyla Doldurma</span><span class="sxs-lookup"><span data-stu-id="fa82b-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="fa82b-103">Kullanarak bir dokuyla kapalı bir şekil doldurabilirsiniz <xref:System.Drawing.Image> sınıfı ve <xref:System.Drawing.TextureBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fa82b-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa82b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa82b-104">Example</span></span>  
 <span data-ttu-id="fa82b-105">Aşağıdaki örnek elips bir görüntü ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="fa82b-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="fa82b-106">Kod oluşturur bir <xref:System.Drawing.Image> nesne ve daha sonra adresini geçirir <xref:System.Drawing.Image> nesne bağımsız değişkeni olarak bir <xref:System.Drawing.TextureBrush.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="fa82b-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="fa82b-107">Üçüncü ifade görüntüyü ölçeklendirir ve dördüncü ifade Ölçeklendirilen görüntünün yinelenen kopyalarla elips doldurur.</span><span class="sxs-lookup"><span data-stu-id="fa82b-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="fa82b-108">Aşağıdaki kodda, <xref:System.Drawing.TextureBrush.Transform%2A> özelliği çizildiğinde önce görüntüye uygulanan dönüştürme içerir.</span><span class="sxs-lookup"><span data-stu-id="fa82b-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="fa82b-109">Özgün görüntüsüne 640 piksel genişliği ve yüksekliği 480 piksel sahip olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="fa82b-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="fa82b-110">Dönüştürme resmi yatay ve dikey ölçekleme değerlerini ayarlayarak 75 × 75 küçültür.</span><span class="sxs-lookup"><span data-stu-id="fa82b-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa82b-111">Aşağıdaki örnekte, görüntü boyutu 75 × 75'tir ve üç nokta boyutu 150 × 250'dir.</span><span class="sxs-lookup"><span data-stu-id="fa82b-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="fa82b-112">Görüntü, doldurma elips küçük olduğu için üç nokta görüntüyle döşenir.</span><span class="sxs-lookup"><span data-stu-id="fa82b-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="fa82b-113">Döşeme görüntü yatay ve dikey olarak şekli sınır kadar yinelenir, anlamına gelir erişilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa82b-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="fa82b-114">Döşeme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir şekli bir görüntüyle döşeme](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="fa82b-114">For more information about tiling, see [How to: Tile a Shape with an Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa82b-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fa82b-115">Compiling the Code</span></span>  
 <span data-ttu-id="fa82b-116">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="fa82b-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa82b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa82b-117">See Also</span></span>  
 [<span data-ttu-id="fa82b-118">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="fa82b-118">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
