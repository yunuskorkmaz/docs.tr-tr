---
title: 'Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: ed129cd9487ba1416cd69b2e13f59747856cb598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522352"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="02ca1-102">Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="02ca1-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="02ca1-103"><xref:System.Drawing.Bitmap> Sınıfı (devralan <xref:System.Drawing.Image> sınıfı) ve <xref:System.Drawing.Imaging.ImageAttributes> sınıfı piksel değerleri ayarlama ve alma için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="02ca1-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="02ca1-104">Kullanabileceğiniz <xref:System.Drawing.Imaging.ImageAttributes> alfa değiştirmek için sınıf değerleri için tüm görüntü ya da çağırabilirsiniz <xref:System.Drawing.Bitmap.SetPixel%2A> yöntemi <xref:System.Drawing.Bitmap> tek tek piksel değerlerini değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="02ca1-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ca1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="02ca1-105">Example</span></span>  
 <span data-ttu-id="02ca1-106"><xref:System.Drawing.Imaging.ImageAttributes> Sınıfın görüntüleri işleme sırasında değiştirmek için kullanabileceğiniz birçok özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="02ca1-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="02ca1-107">Aşağıdaki örnekte, bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ne oldukları, yüzde 80 için tüm alfa değerleri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02ca1-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="02ca1-108">Bu renk matrisi başlatma ve 0,8 matrise değerinde ölçeklendirme alfa ayarlayarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="02ca1-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="02ca1-109">Renk Matrisi adresini geçirilir <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ve <xref:System.Drawing.Imaging.ImageAttributes> nesne iletilir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="02ca1-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="02ca1-110">İşleme sırasında yüzde 80'ne oldukları biri için bit eşlemde alfa değerleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="02ca1-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="02ca1-111">Bu, arka plan karıştırılan görüntüyü sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="02ca1-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="02ca1-112">Aşağıdaki çizimde gösterildiği gibi bit eşlem resmin saydam arar; düz siyah bir çizgi geçen görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02ca1-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="02ca1-113">![Alfa karıştırma bir matris kullanarak](../../../../docs/framework/winforms/advanced/media/image2.png "image2")</span><span class="sxs-lookup"><span data-stu-id="02ca1-113">![Alpha Blending Using a Matrix](../../../../docs/framework/winforms/advanced/media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="02ca1-114">Görüntü arka planı beyaz bölümü olduğunda, görüntü ile rengi beyaz karıştırılan.</span><span class="sxs-lookup"><span data-stu-id="02ca1-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="02ca1-115">Burada görüntü siyah bir çizgi kestiği görüntü rengi siyah karıştırılan.</span><span class="sxs-lookup"><span data-stu-id="02ca1-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02ca1-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="02ca1-116">Compiling the Code</span></span>  
 <span data-ttu-id="02ca1-117">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="02ca1-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ca1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02ca1-118">See Also</span></span>  
 [<span data-ttu-id="02ca1-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="02ca1-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="02ca1-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="02ca1-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
