---
title: "Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64384e3c283b6596e36d5b2bd583a304faf080b4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="05ef5-102">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="05ef5-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="05ef5-103"><xref:System.Drawing> Ad alanı sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve görüntüleri düzenleme için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="05ef5-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="05ef5-104">Görüntü Kodlayıcıları kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri bellekten diske yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05ef5-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="05ef5-105">Görüntü kod çözücüleri kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri diskten belleğe yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="05ef5-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="05ef5-106">Verileri bir kodlayıcı çeviren bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> ayrılan disk dosya biçimine nesnesi.</span><span class="sxs-lookup"><span data-stu-id="05ef5-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="05ef5-107">Bir disk dosyası gerekli biçime verilerde bir kod çözücü çevirir <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="05ef5-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="05ef5-108">Yerleşik Kodlayıcıları ve aşağıdaki dosya türlerini destekleyen kod çözücüleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="05ef5-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="05ef5-109">BMP</span><span class="sxs-lookup"><span data-stu-id="05ef5-109">BMP</span></span>  
  
-   <span data-ttu-id="05ef5-110">GIF</span><span class="sxs-lookup"><span data-stu-id="05ef5-110">GIF</span></span>  
  
-   <span data-ttu-id="05ef5-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="05ef5-111">JPEG</span></span>  
  
-   <span data-ttu-id="05ef5-112">PNG</span><span class="sxs-lookup"><span data-stu-id="05ef5-112">PNG</span></span>  
  
-   <span data-ttu-id="05ef5-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="05ef5-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="05ef5-114">Ayrıca, aşağıdaki dosya türlerini destekleyen yerleşik kod çözücüleri vardır:</span><span class="sxs-lookup"><span data-stu-id="05ef5-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="05ef5-115">WMF</span><span class="sxs-lookup"><span data-stu-id="05ef5-115">WMF</span></span>  
  
-   <span data-ttu-id="05ef5-116">EMF</span><span class="sxs-lookup"><span data-stu-id="05ef5-116">EMF</span></span>  
  
-   <span data-ttu-id="05ef5-117">SİMGESİ</span><span class="sxs-lookup"><span data-stu-id="05ef5-117">ICON</span></span>  
  
 <span data-ttu-id="05ef5-118">Aşağıdaki konular Kodlayıcıları ve kod çözücüleri daha ayrıntılı ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="05ef5-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05ef5-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="05ef5-119">In This Section</span></span>  
 [<span data-ttu-id="05ef5-120">Nasıl yapılır: yüklenen Kodlayıcıları listeleme</span><span class="sxs-lookup"><span data-stu-id="05ef5-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="05ef5-121">Bir bilgisayarda kullanılabilir kodlayıcılar listelemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="05ef5-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="05ef5-122">Nasıl yapılır: yüklenen kod çözücüleri listeleme</span><span class="sxs-lookup"><span data-stu-id="05ef5-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="05ef5-123">Bir bilgisayarda kullanılabilir kod çözücüleri listelemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="05ef5-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="05ef5-124">Nasıl yapılır: bir kodlayıcı tarafından desteklenen parametreleri belirleme</span><span class="sxs-lookup"><span data-stu-id="05ef5-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="05ef5-125">Liste açıklar <xref:System.Drawing.Imaging.EncoderParameters> bir kodlayıcı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="05ef5-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="05ef5-126">Nasıl yapılır: BMP resmini PNG resmine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="05ef5-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="05ef5-127">Farklı bir resim biçiminde bir görüntüsünü kaydetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="05ef5-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="05ef5-128">Nasıl yapılır: JPEG sıkıştırma düzeyini ayarlama</span><span class="sxs-lookup"><span data-stu-id="05ef5-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="05ef5-129">Bir görüntü kalite düzeyini değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="05ef5-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="05ef5-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="05ef5-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="05ef5-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="05ef5-131">Related Sections</span></span>  
 [<span data-ttu-id="05ef5-132">GDI + yönetilen kodu hakkında</span><span class="sxs-lookup"><span data-stu-id="05ef5-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="05ef5-133">Resimler, bit eşlemler ve meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="05ef5-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
