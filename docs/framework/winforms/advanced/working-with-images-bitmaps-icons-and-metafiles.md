---
title: Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
ms.openlocfilehash: 6d2f0a2f4acebaac59f2d8180f2de4ccb88b2965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526842"
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="5ad5b-102">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="5ad5b-103"> sağlar `Bitmap` ızgara görüntüleri ile çalışmak için sınıf ve `Metafile` vektör görüntülerle çalışma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="5ad5b-104">`Bitmap` Ve `Metafile` sınıflarının her ikisi de devral `Image` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ad5b-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5ad5b-105">In This Section</span></span>  
 [<span data-ttu-id="5ad5b-106">Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme</span><span class="sxs-lookup"><span data-stu-id="5ad5b-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="5ad5b-107">Yük ve bit eşlemler çizin açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="5ad5b-108">Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5ad5b-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="5ad5b-109">Yük ve meta dosyaları çizin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="5ad5b-110">GDI+'da Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="5ad5b-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="5ad5b-111">Kırpma ve ölçeklendirme vektörü ve ızgara görüntüleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="5ad5b-112">Nasıl yapılır: Görüntüleri Döndürme, Yansıtma ve Eğme</span><span class="sxs-lookup"><span data-stu-id="5ad5b-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="5ad5b-113">Döndürülen, yansıtılan ve çarpık görüntüleri çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="5ad5b-114">Nasıl yapılır: Ölçeklendirme Sırasında Görüntü Kalitesini Denetlemek için İlişkilendirme Modunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="5ad5b-115">Nasıl kullanılacağını gösterir <xref:System.Drawing.Drawing2D.InterpolationMode> görüntü kalitesini değiştirmek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="5ad5b-116">Nasıl yapılır: Küçük Resimler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="5ad5b-117">Küçük resimler oluşturma açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="5ad5b-118">Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="5ad5b-119">Otomatik ölçekleme olmadan resim çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="5ad5b-120">Nasıl yapılır: Görüntü Meta Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="5ad5b-121">Bir görüntüden meta verileri okuyabilmesi açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="5ad5b-122">Nasıl yapılır: Çalışma Zamanında Bit Eşlem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="5ad5b-123">Çalışma zamanında bir bit eşlemi çizme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="5ad5b-124">Nasıl yapılır: Windows Forms’ta Bir Dosyayla İlişkili Simgeyi Çıkarma</span><span class="sxs-lookup"><span data-stu-id="5ad5b-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="5ad5b-125">Katıştırılmış bir kaynağı bir dosyanın bulunduğu bir simge ayıklamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ad5b-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="5ad5b-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="5ad5b-127">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="5ad5b-128">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="5ad5b-129">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ad5b-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5ad5b-130">Related Sections</span></span>  
 [<span data-ttu-id="5ad5b-131">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5ad5b-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="5ad5b-132">Bit eşlemler ve uygulamalarınızda düzenleme farklı türlerde ele konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="5ad5b-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
