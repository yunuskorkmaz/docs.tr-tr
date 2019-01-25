---
title: GDI+'da Görüntü Çizme, Konumlandırma ve Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: afd5be1fd56382ba0dcbb2938a7e466d1584ae7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548225"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="5b001-102">GDI+'da Görüntü Çizme, Konumlandırma ve Kopyalama</span><span class="sxs-lookup"><span data-stu-id="5b001-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="5b001-103">Kullanabileceğiniz <xref:System.Drawing.Bitmap> sınıfı yüklemek ve ızgara görüntüleri ve görüntülemek için kullanabileceğiniz <xref:System.Drawing.Imaging.Metafile> yüklemek ve vektör görüntüleri görüntülemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5b001-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="5b001-104"><xref:System.Drawing.Bitmap> Ve <xref:System.Drawing.Imaging.Metafile> sınıfları <xref:System.Drawing.Image> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5b001-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="5b001-105">Bir vektör resim görüntülemek için örneği gerekir. <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="5b001-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="5b001-106">Izgara resim görüntülemek için örneği gerekir. <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="5b001-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="5b001-107">Örneğini <xref:System.Drawing.Graphics> sağlar sınıfını <xref:System.Drawing.Graphics.DrawImage%2A> alan yöntemi <xref:System.Drawing.Imaging.Metafile> veya <xref:System.Drawing.Bitmap> bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="5b001-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="5b001-108">Dosya türleri ve kopyalama</span><span class="sxs-lookup"><span data-stu-id="5b001-108">File Types and Cloning</span></span>  
 <span data-ttu-id="5b001-109">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Drawing.Bitmap> Climber.jpg dosyasından ve bit eşlem görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5b001-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="5b001-110">Sol üst görüntünün hedef noktasının (10, 10), ikinci ve üçüncü parametre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5b001-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="5b001-111">Aşağıdaki çizimde, görüntüyü gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b001-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="5b001-112">![Görüntü örnek](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="5b001-112">![Image Sample](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="5b001-113">Oluşturulabilir <xref:System.Drawing.Bitmap> nesneleri grafik çeşitli dosya biçimleri: BMP, GIF, JPEG, EXIF, PNG, TIFF ve SİMGE.</span><span class="sxs-lookup"><span data-stu-id="5b001-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="5b001-114">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir <xref:System.Drawing.Bitmap> nesneleri çeşitli dosya türlerinin ve bit eşlemler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5b001-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="5b001-115"><xref:System.Drawing.Bitmap> Sağlar sınıfını bir <xref:System.Drawing.Bitmap.Clone%2A> varolan bir kopyasını oluşturmak için kullanabileceğiniz yöntem <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="5b001-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="5b001-116"><xref:System.Drawing.Bitmap.Clone%2A> Yöntemi kopyalamak istediğiniz özgün bit eşlem bölümünü belirlemek için kullanabileceğiniz bir kaynak dikdörtgenin parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="5b001-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="5b001-117">Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Drawing.Bitmap> varolan üst kısmında kopyalayarak <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="5b001-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="5b001-118">Ardından, her iki çizilir.</span><span class="sxs-lookup"><span data-stu-id="5b001-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="5b001-119">Aşağıdaki çizimde, iki görüntü gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b001-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="5b001-120">![Kırpma](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="5b001-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b001-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b001-121">See also</span></span>
- [<span data-ttu-id="5b001-122">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5b001-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="5b001-123">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b001-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="5b001-124">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="5b001-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
