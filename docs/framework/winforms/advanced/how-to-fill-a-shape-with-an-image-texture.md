---
title: 'Nasıl yapılır: Bir Şekli Resim Dokusuyla Doldurma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 099bc9f5359f19439f308f28a6766d470956daea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177326"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="9a547-102">Nasıl yapılır: Bir Şekli Resim Dokusuyla Doldurma</span><span class="sxs-lookup"><span data-stu-id="9a547-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="9a547-103">Kullanarak kapalı şekil bir doku ile doldurabilirsiniz <xref:System.Drawing.Image> sınıfı ve <xref:System.Drawing.TextureBrush> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9a547-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a547-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a547-104">Example</span></span>  
 <span data-ttu-id="9a547-105">Aşağıdaki örnek, bir elips görüntü ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="9a547-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="9a547-106">Kod oluşturur bir <xref:System.Drawing.Image> nesnesi ve ardından, söz konusu adreslerinde <xref:System.Drawing.Image> nesne bağımsız değişkeni olarak bir <xref:System.Drawing.TextureBrush.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="9a547-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="9a547-107">Üçüncü deyim görüntüyü ölçeklendirir ve dördüncü deyimi yinelenen kopyaları Ölçeklendirilen görüntünün bir elips doldurur.</span><span class="sxs-lookup"><span data-stu-id="9a547-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="9a547-108">Aşağıdaki kodda, <xref:System.Drawing.TextureBrush.Transform%2A> çizildiğinde önce görüntüye uygulanan dönüşüm özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="9a547-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="9a547-109">Özgün resmin 640 piksel genişliği ve yüksekliği 480 piksel sahip olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="9a547-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="9a547-110">Dönüştürme, görüntü yatay ve dikey ölçekleme değerleri ayarlayarak 75 × 75 küçültür.</span><span class="sxs-lookup"><span data-stu-id="9a547-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a547-111">Aşağıdaki örnekte, 75 x 75 görüntü boyutu olduğundan ve 150 × 250 elips boyutudur.</span><span class="sxs-lookup"><span data-stu-id="9a547-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="9a547-112">Görüntü doldurma elipsin daha küçük olduğu için üç nokta ile görüntü döşenir.</span><span class="sxs-lookup"><span data-stu-id="9a547-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="9a547-113">Görüntüyü yatay ve dikey olarak şekli sınırına kadar yinelenir, anlamına gelir döşeme ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="9a547-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="9a547-114">Döşeme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir şekli bir görüntüyle döşeme](how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="9a547-114">For more information about tiling, see [How to: Tile a Shape with an Image](how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a547-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9a547-115">Compiling the Code</span></span>  
 <span data-ttu-id="9a547-116">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9a547-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a547-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a547-117">See also</span></span>

- [<span data-ttu-id="9a547-118">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="9a547-118">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
