---
title: "Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53dc25d6a23c5cdbba1c640905eadbdc6b1acb71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="ec189-102">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="ec189-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ec189-103">sağlar `Bitmap` ızgara görüntüleri ile çalışmak için sınıf ve `Metafile` vektör görüntülerle çalışma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ec189-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="ec189-104">`Bitmap` Ve `Metafile` sınıflarının her ikisi de devral `Image` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ec189-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec189-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ec189-105">In This Section</span></span>  
 [<span data-ttu-id="ec189-106">Nasıl yapılır: ekrana mevcut bir bit eşlemi çizme</span><span class="sxs-lookup"><span data-stu-id="ec189-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="ec189-107">Yük ve bit eşlemler çizin açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec189-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="ec189-108">Nasıl yapılır: yükleme ve görüntüleme meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="ec189-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="ec189-109">Yük ve meta dosyaları çizin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec189-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="ec189-110">Görüntü kırpma ve GDI +'ÖLÇEKLENDİRME</span><span class="sxs-lookup"><span data-stu-id="ec189-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="ec189-111">Kırpma ve ölçeklendirme vektörü ve ızgara görüntüleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec189-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="ec189-112">Nasıl yapılır: döndürme, yansıtma ve eğme görüntüleri</span><span class="sxs-lookup"><span data-stu-id="ec189-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="ec189-113">Döndürülen, yansıtılan ve çarpık görüntüleri çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec189-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="ec189-114">Nasıl yapılır: ölçeklendirme sırasında görüntü kalitesini denetlemek için ilişkilendirme modunu kullanma</span><span class="sxs-lookup"><span data-stu-id="ec189-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="ec189-115">Nasıl kullanılacağını gösterir <xref:System.Drawing.Drawing2D.InterpolationMode> görüntü kalitesini değiştirmek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="ec189-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="ec189-116">Nasıl yapılır: küçük resimler oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec189-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="ec189-117">Küçük resimler oluşturma açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec189-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="ec189-118">Nasıl yapılır: otomatik ölçeklendirmeyi önleyerek performansı</span><span class="sxs-lookup"><span data-stu-id="ec189-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="ec189-119">Otomatik ölçekleme olmadan resim çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec189-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="ec189-120">Nasıl yapılır: görüntü meta verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="ec189-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="ec189-121">Bir görüntüden meta verileri okuyabilmesi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec189-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="ec189-122">Nasıl yapılır: çalışma zamanında bit eşlem oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec189-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="ec189-123">Çalışma zamanında bir bit eşlemi çizme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec189-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="ec189-124">Nasıl yapılır: Windows formlarında bir dosyayla ilişkili simgeyi çıkarma</span><span class="sxs-lookup"><span data-stu-id="ec189-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="ec189-125">Katıştırılmış bir kaynağı bir dosyanın bulunduğu bir simge ayıklamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec189-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec189-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ec189-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="ec189-127">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="ec189-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="ec189-128">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="ec189-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="ec189-129">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="ec189-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec189-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ec189-130">Related Sections</span></span>  
 [<span data-ttu-id="ec189-131">Resimler, bit eşlemler ve meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="ec189-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="ec189-132">Bit eşlemler ve uygulamalarınızda düzenleme farklı türlerde ele konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="ec189-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
