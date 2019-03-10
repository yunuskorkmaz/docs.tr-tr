---
title: 'Nasıl yapılır: Yeniden renk eşleme tablosu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 72965d6968aab256579929acc00e629bcd3c71f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707345"
---
# <a name="how-to-use-a-color-remap-table"></a><span data-ttu-id="a1e5f-102">Nasıl yapılır: Yeniden renk eşleme tablosu kullanma</span><span class="sxs-lookup"><span data-stu-id="a1e5f-102">How to: Use a Color Remap Table</span></span>
<span data-ttu-id="a1e5f-103">Yeniden eşleme yeniden renk eşleme tablosu göre görüntü renkleri dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-103">Remapping is the process of converting the colors in an image according to a color remap table.</span></span> <span data-ttu-id="a1e5f-104">Renk eşleme tablosu dizisidir <xref:System.Drawing.Imaging.ColorMap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-104">The color remap table is an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="a1e5f-105">Her <xref:System.Drawing.Imaging.ColorMap> dizi nesnesinde bir <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> özelliği ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-105">Each <xref:System.Drawing.Imaging.ColorMap> object in the array has an <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property and a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property.</span></span>  
  
 <span data-ttu-id="a1e5f-106">Zaman [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizer görüntü, her pikselin görüntünün bir diziye eski renk karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-106">When [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] draws an image, each pixel of the image is compared to the array of old colors.</span></span> <span data-ttu-id="a1e5f-107">Bir pikselin renk eski bir renk eşleşiyorsa rengini karşılık gelen yeni renge değişir.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-107">If a pixel's color matches an old color, its color is changed to the corresponding new color.</span></span> <span data-ttu-id="a1e5f-108">Renkleri işleme için yalnızca değiştirilen — görüntünün renk değerleri (depolanan bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> nesnesi) değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-108">The colors are changed only for rendering — the color values of the image itself (stored in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object) are not changed.</span></span>  
  
 <span data-ttu-id="a1e5f-109">Remapped resim çizmek için bir dizi başlatma <xref:System.Drawing.Imaging.ColorMap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-109">To draw a remapped image, initialize an array of <xref:System.Drawing.Imaging.ColorMap> objects.</span></span> <span data-ttu-id="a1e5f-110">Bu dizi için geçirmek <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> yöntemi bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi ve ardından geçirmek <xref:System.Drawing.Imaging.ImageAttributes> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-110">Pass that array to the <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> method of an <xref:System.Drawing.Imaging.ImageAttributes> object, and then pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1e5f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1e5f-111">Example</span></span>  
 <span data-ttu-id="a1e5f-112">Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Image> RemapInput.bmp dosyasından nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-112">The following example creates an <xref:System.Drawing.Image> object from the file RemapInput.bmp.</span></span> <span data-ttu-id="a1e5f-113">Kod bir tek oluşur yeniden renk eşleme tablosu oluşturur <xref:System.Drawing.Imaging.ColorMap> nesne.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-113">The code creates a color remap table that consists of a single <xref:System.Drawing.Imaging.ColorMap> object.</span></span> <span data-ttu-id="a1e5f-114"><xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Özelliği `ColorRemap` nesnedir kırmızı ve <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> özelliktir mavi.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-114">The <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> property of the `ColorRemap` object is red, and the <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> property is blue.</span></span> <span data-ttu-id="a1e5f-115">Yeniden eşleme ile yeniden eşleme olmadan çizilmiş bir kez de görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-115">The image is drawn once without remapping and once with remapping.</span></span> <span data-ttu-id="a1e5f-116">Yeniden eşleme işlemi, mavi ve kırmızı tüm pikselleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-116">The remapping process changes all the red pixels to blue.</span></span>  
  
 <span data-ttu-id="a1e5f-117">Aşağıdaki çizimde, sol taraftaki özgün görüntü ve remapped görüntü sağ tarafta gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-117">The following illustration shows the original image on the left and the remapped image on the right.</span></span>  
  
 <span data-ttu-id="a1e5f-118">![Renk eşleme](./media/colortrans7.png "colortrans7")</span><span class="sxs-lookup"><span data-stu-id="a1e5f-118">![Color ReMap](./media/colortrans7.png "colortrans7")</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1e5f-119">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a1e5f-119">Compiling the Code</span></span>  
 <span data-ttu-id="a1e5f-120">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-120">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e5f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1e5f-121">See also</span></span>
- [<span data-ttu-id="a1e5f-122">Görüntüleri Yeniden Renklendirme</span><span class="sxs-lookup"><span data-stu-id="a1e5f-122">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="a1e5f-123">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="a1e5f-123">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
