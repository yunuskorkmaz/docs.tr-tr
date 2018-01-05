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
ms.workload: dotnet
ms.openlocfilehash: 29c8a4ef0a495d63c0263262857002f09d8c885a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="440ec-102">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="440ec-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="440ec-103">sağlar `Bitmap` ızgara görüntüleri ile çalışmak için sınıf ve `Metafile` vektör görüntülerle çalışma sınıfı.</span><span class="sxs-lookup"><span data-stu-id="440ec-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="440ec-104">`Bitmap` Ve `Metafile` sınıflarının her ikisi de devral `Image` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="440ec-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="440ec-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="440ec-105">In This Section</span></span>  
 [<span data-ttu-id="440ec-106">Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme</span><span class="sxs-lookup"><span data-stu-id="440ec-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="440ec-107">Yük ve bit eşlemler çizin açıklar.</span><span class="sxs-lookup"><span data-stu-id="440ec-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="440ec-108">Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="440ec-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="440ec-109">Yük ve meta dosyaları çizin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="440ec-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="440ec-110">GDI+'da Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="440ec-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="440ec-111">Kırpma ve ölçeklendirme vektörü ve ızgara görüntüleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="440ec-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="440ec-112">Nasıl yapılır: Görüntüleri Döndürme, Yansıtma ve Eğme</span><span class="sxs-lookup"><span data-stu-id="440ec-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="440ec-113">Döndürülen, yansıtılan ve çarpık görüntüleri çizmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="440ec-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="440ec-114">Nasıl yapılır: Ölçeklendirme Sırasında Görüntü Kalitesini Denetlemek için İlişkilendirme Modunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="440ec-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="440ec-115">Nasıl kullanılacağını gösterir <xref:System.Drawing.Drawing2D.InterpolationMode> görüntü kalitesini değiştirmek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="440ec-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="440ec-116">Nasıl yapılır: Küçük Resimler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="440ec-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="440ec-117">Küçük resimler oluşturma açıklar.</span><span class="sxs-lookup"><span data-stu-id="440ec-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="440ec-118">Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma</span><span class="sxs-lookup"><span data-stu-id="440ec-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="440ec-119">Otomatik ölçekleme olmadan resim çizme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="440ec-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="440ec-120">Nasıl yapılır: Görüntü Meta Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="440ec-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="440ec-121">Bir görüntüden meta verileri okuyabilmesi açıklar.</span><span class="sxs-lookup"><span data-stu-id="440ec-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="440ec-122">Nasıl yapılır: Çalışma Zamanında Bit Eşlem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="440ec-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="440ec-123">Çalışma zamanında bir bit eşlemi çizme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="440ec-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="440ec-124">Nasıl yapılır: Windows Forms’ta Bir Dosyayla İlişkili Simgeyi Çıkarma</span><span class="sxs-lookup"><span data-stu-id="440ec-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="440ec-125">Katıştırılmış bir kaynağı bir dosyanın bulunduğu bir simge ayıklamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="440ec-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="440ec-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="440ec-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="440ec-127">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="440ec-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="440ec-128">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="440ec-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="440ec-129">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="440ec-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="440ec-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="440ec-130">Related Sections</span></span>  
 [<span data-ttu-id="440ec-131">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="440ec-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="440ec-132">Bit eşlemler ve uygulamalarınızda düzenleme farklı türlerde ele konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="440ec-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
