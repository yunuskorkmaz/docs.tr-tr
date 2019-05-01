---
title: Resimler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
ms.openlocfilehash: 61d534f8299c920f656abe4280cc3ea5e609c0b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011924"
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="53604-102">Resimler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="53604-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="53604-103">sağlar `Bitmap` ızgara görüntüleri ile çalışmak için sınıf ve `Metafile` vektör görüntüleri ile çalışmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="53604-103">provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="53604-104">`Bitmap` Ve `Metafile` sınıflarının her ikisi de devralmanız `Image` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53604-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53604-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="53604-105">In This Section</span></span>  
 [<span data-ttu-id="53604-106">Nasıl yapılır: Ekrana mevcut bir bit eşlemi çizme</span><span class="sxs-lookup"><span data-stu-id="53604-106">How to: Draw an Existing Bitmap to the Screen</span></span>](how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="53604-107">Yük ve bit eşlemler çizin açıklar.</span><span class="sxs-lookup"><span data-stu-id="53604-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="53604-108">Nasıl yapılır: Yük ve görüntü meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="53604-108">How to: Load and Display Metafiles</span></span>](how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="53604-109">Yük ve meta dosyaları çizin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="53604-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="53604-110">GDI+'da Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="53604-110">Cropping and Scaling Images in GDI+</span></span>](cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="53604-111">Kırpma ve ölçeklendirme vektör ve ızgara görüntüleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53604-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="53604-112">Nasıl yapılır: Döndürme, yansıtma ve eğme görüntüleri</span><span class="sxs-lookup"><span data-stu-id="53604-112">How to: Rotate, Reflect, and Skew Images</span></span>](how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="53604-113">Döndürülen, yansıtılan ve dengesiz resimler çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="53604-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="53604-114">Nasıl yapılır: Ölçeklendirme sırasında görüntü kalitesini denetlemek için ilişkilendirme modunu kullanma</span><span class="sxs-lookup"><span data-stu-id="53604-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="53604-115">Nasıl kullanılacağını gösterir <xref:System.Drawing.Drawing2D.InterpolationMode> görüntü kalitesini değiştirmek için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="53604-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="53604-116">Nasıl yapılır: Küçük resimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="53604-116">How to: Create Thumbnail Images</span></span>](how-to-create-thumbnail-images.md)  
 <span data-ttu-id="53604-117">Küçük resimler oluşturma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="53604-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="53604-118">Nasıl yapılır: Otomatik ölçeklendirmeyi önleyerek performansı artırma</span><span class="sxs-lookup"><span data-stu-id="53604-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="53604-119">Otomatik ölçekleme olmadan bir görüntü çizin açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53604-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="53604-120">Nasıl yapılır: Okuma resim meta verileri</span><span class="sxs-lookup"><span data-stu-id="53604-120">How to: Read Image Metadata</span></span>](how-to-read-image-metadata.md)  
 <span data-ttu-id="53604-121">Bir görüntüden meta verileri okuyabilmesi açıklar.</span><span class="sxs-lookup"><span data-stu-id="53604-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="53604-122">Nasıl yapılır: Çalışma zamanında bir bit eşlem oluşturma</span><span class="sxs-lookup"><span data-stu-id="53604-122">How to: Create a Bitmap at Run Time</span></span>](how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="53604-123">Çalışma zamanında bir bit eşlemi çizme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="53604-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="53604-124">Nasıl yapılır: Windows Forms'ta bir dosyayla ilişkili simgeyi çıkarma</span><span class="sxs-lookup"><span data-stu-id="53604-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="53604-125">Bir dosyanın katıştırılmış bir kaynağı bir simgeyi ayıklanacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="53604-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="53604-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="53604-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="53604-127">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="53604-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="53604-128">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="53604-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="53604-129">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="53604-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53604-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="53604-130">Related Sections</span></span>  
 [<span data-ttu-id="53604-131">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="53604-131">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="53604-132">Bit eşlemler ve bunları uygulamalarınızda düzenleme farklı türleri açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="53604-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
