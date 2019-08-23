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
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911684"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="26e18-102">Nasıl yapılır: Bir Şekli Resim Dokusuyla Doldurma</span><span class="sxs-lookup"><span data-stu-id="26e18-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="26e18-103">Bir kapalı şekli, <xref:System.Drawing.Image> sınıfını <xref:System.Drawing.TextureBrush> ve sınıfını kullanarak bir dokuyla doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e18-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26e18-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="26e18-104">Example</span></span>  
 <span data-ttu-id="26e18-105">Aşağıdaki örnek bir elipsi görüntüyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="26e18-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="26e18-106">Kod bir <xref:System.Drawing.Image> nesne oluşturur ve sonra bu <xref:System.Drawing.Image> nesnenin adresini bir <xref:System.Drawing.TextureBrush.%23ctor%2A> oluşturucuya bağımsız değişken olarak geçirir.</span><span class="sxs-lookup"><span data-stu-id="26e18-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="26e18-107">Üçüncü ifade resmi ölçeklendirir ve dördüncü ifade, elipsi ölçeklenmiş görüntünün yinelenen kopyalarıyla doldurur.</span><span class="sxs-lookup"><span data-stu-id="26e18-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="26e18-108">Aşağıdaki kodda, <xref:System.Drawing.TextureBrush.Transform%2A> özelliği, çizilmeden önce görüntüye uygulanan dönüştürmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="26e18-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="26e18-109">Orijinal görüntünün genişliği 640 piksel ve 480 piksel yüksekliğinde olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="26e18-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="26e18-110">Dönüştürme, yatay ve dikey ölçekleme değerlerini ayarlayarak görüntüyü 75 × 75 ' e küçültür.</span><span class="sxs-lookup"><span data-stu-id="26e18-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26e18-111">Aşağıdaki örnekte, görüntü boyutu 75 × 75 ve elips boyutu 150 × 250 ' dir.</span><span class="sxs-lookup"><span data-stu-id="26e18-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="26e18-112">Görüntü, doldurdukları elipsin daha küçük olduğundan, elips görüntüyle döşenir.</span><span class="sxs-lookup"><span data-stu-id="26e18-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="26e18-113">Döşeme, şeklin sınırına ulaşılana kadar görüntünün yatay ve dikey olarak yinelenme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26e18-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="26e18-114">Döşeme hakkında daha fazla bilgi için bkz [. nasıl yapılır: Görüntüyle](how-to-tile-a-shape-with-an-image.md)bir şekil döşeme.</span><span class="sxs-lookup"><span data-stu-id="26e18-114">For more information about tiling, see [How to: Tile a Shape with an Image](how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26e18-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="26e18-115">Compiling the Code</span></span>  
 <span data-ttu-id="26e18-116">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan gerektirir `e`.</span><span class="sxs-lookup"><span data-stu-id="26e18-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e18-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26e18-117">See also</span></span>

- [<span data-ttu-id="26e18-118">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="26e18-118">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
