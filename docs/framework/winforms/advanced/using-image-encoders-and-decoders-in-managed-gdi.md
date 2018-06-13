---
title: Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524507"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="4eeaf-102">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="4eeaf-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="4eeaf-103"><xref:System.Drawing> Ad alanı sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve görüntüleri düzenleme için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="4eeaf-104">Görüntü Kodlayıcıları kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri bellekten diske yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="4eeaf-105">Görüntü kod çözücüleri kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri diskten belleğe yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="4eeaf-106">Verileri bir kodlayıcı çeviren bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> ayrılan disk dosya biçimine nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="4eeaf-107">Bir disk dosyası gerekli biçime verilerde bir kod çözücü çevirir <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4eeaf-108"> Yerleşik Kodlayıcıları ve aşağıdaki dosya türlerini destekleyen kod çözücüleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4eeaf-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="4eeaf-109">BMP</span><span class="sxs-lookup"><span data-stu-id="4eeaf-109">BMP</span></span>  
  
-   <span data-ttu-id="4eeaf-110">GIF</span><span class="sxs-lookup"><span data-stu-id="4eeaf-110">GIF</span></span>  
  
-   <span data-ttu-id="4eeaf-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="4eeaf-111">JPEG</span></span>  
  
-   <span data-ttu-id="4eeaf-112">PNG</span><span class="sxs-lookup"><span data-stu-id="4eeaf-112">PNG</span></span>  
  
-   <span data-ttu-id="4eeaf-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="4eeaf-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4eeaf-114"> Ayrıca, aşağıdaki dosya türlerini destekleyen yerleşik kod çözücüleri vardır:</span><span class="sxs-lookup"><span data-stu-id="4eeaf-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="4eeaf-115">WMF</span><span class="sxs-lookup"><span data-stu-id="4eeaf-115">WMF</span></span>  
  
-   <span data-ttu-id="4eeaf-116">EMF</span><span class="sxs-lookup"><span data-stu-id="4eeaf-116">EMF</span></span>  
  
-   <span data-ttu-id="4eeaf-117">SİMGESİ</span><span class="sxs-lookup"><span data-stu-id="4eeaf-117">ICON</span></span>  
  
 <span data-ttu-id="4eeaf-118">Aşağıdaki konular Kodlayıcıları ve kod çözücüleri daha ayrıntılı ele alınmıştır:</span><span class="sxs-lookup"><span data-stu-id="4eeaf-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4eeaf-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4eeaf-119">In This Section</span></span>  
 [<span data-ttu-id="4eeaf-120">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="4eeaf-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="4eeaf-121">Bir bilgisayarda kullanılabilir kodlayıcılar listelemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="4eeaf-122">Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme</span><span class="sxs-lookup"><span data-stu-id="4eeaf-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="4eeaf-123">Bir bilgisayarda kullanılabilir kod çözücüleri listelemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="4eeaf-124">Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme</span><span class="sxs-lookup"><span data-stu-id="4eeaf-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="4eeaf-125">Liste açıklar <xref:System.Drawing.Imaging.EncoderParameters> bir kodlayıcı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="4eeaf-126">Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="4eeaf-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="4eeaf-127">Farklı bir resim biçiminde bir görüntüsünü kaydetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="4eeaf-128">Nasıl Yapılır: JPEG Sıkıştırma Düzeyini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4eeaf-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="4eeaf-129">Bir görüntü kalite düzeyini değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4eeaf-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4eeaf-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="4eeaf-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4eeaf-131">Related Sections</span></span>  
 [<span data-ttu-id="4eeaf-132">GDI+ Yönetilen Kodu Hakkında</span><span class="sxs-lookup"><span data-stu-id="4eeaf-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="4eeaf-133">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4eeaf-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
