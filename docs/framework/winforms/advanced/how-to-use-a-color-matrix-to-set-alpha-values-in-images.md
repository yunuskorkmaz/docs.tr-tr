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
ms.openlocfilehash: 79937f0801a790d4ff1ab327aaaf45ef1b881827
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954560"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="c66b4-102">Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="c66b4-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="c66b4-103"><xref:System.Drawing.Bitmap> Sınıfı (işlevinden devralan <xref:System.Drawing.Image> sınıfı) ve <xref:System.Drawing.Imaging.ImageAttributes> sınıfı piksel değerleri ayarlama ve alma işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c66b4-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="c66b4-104">Kullanabileceğiniz <xref:System.Drawing.Imaging.ImageAttributes> alfa değiştirmek için sınıf için görüntünün değerleri veya çağırabilirsiniz <xref:System.Drawing.Bitmap.SetPixel%2A> yöntemi <xref:System.Drawing.Bitmap> bağımsız piksel değerlerini değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c66b4-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c66b4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c66b4-105">Example</span></span>  
 <span data-ttu-id="c66b4-106"><xref:System.Drawing.Imaging.ImageAttributes> Sınıfı görüntüleri işleme sırasında değiştirmek için kullanabileceğiniz birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="c66b4-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="c66b4-107">Aşağıdaki örnekte, bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi 80 ne oldukları, yüzde olarak tüm alfa değerleri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c66b4-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="c66b4-108">Bu renk matrisi başlatma ve Alfa değerini 0,8 matrise ölçeklendirme ayarı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c66b4-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="c66b4-109">Renk Matrisi adresini geçirilir <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemi <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ve <xref:System.Drawing.Imaging.ImageAttributes> nesnesi <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="c66b4-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="c66b4-110">İşleme sırasında bit eşlem alfa değerleri 80 ne oldukları, yüzde olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c66b4-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="c66b4-111">Bu, bir arka plan ile karışık bir görüntü sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c66b4-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="c66b4-112">Aşağıdaki çizimde gösterildiği gibi bit eşlem resmi saydam arar; düz siyah bir çizgi geçen görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c66b4-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="c66b4-113">![Alfa karıştırma kullanarak bir matrise](./media/image2.png "image2")</span><span class="sxs-lookup"><span data-stu-id="c66b4-113">![Alpha Blending Using a Matrix](./media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="c66b4-114">Görüntü, arka plan üzerinde beyaz kısmında olduğunda, görüntü beyaz ile karışık.</span><span class="sxs-lookup"><span data-stu-id="c66b4-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="c66b4-115">Burada siyah bir çizgi görüntü aştığında görüntü rengi siyah harmanlanan.</span><span class="sxs-lookup"><span data-stu-id="c66b4-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c66b4-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c66b4-116">Compiling the Code</span></span>  
 <span data-ttu-id="c66b4-117">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c66b4-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66b4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c66b4-118">See also</span></span>

- [<span data-ttu-id="c66b4-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="c66b4-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c66b4-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="c66b4-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
