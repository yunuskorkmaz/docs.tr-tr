---
title: Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: e56bc20eb55d694d19b25d9e94e5c9d9e3952628
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666442"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="77f4c-102">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="77f4c-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="77f4c-103"><xref:System.Drawing> Ad alanı sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve bu görüntüleri düzenleme için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="77f4c-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="77f4c-104">İçindeki görüntü Kodlayıcıları kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri bellekten diske yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77f4c-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="77f4c-105">Görüntü kod çözücüleri kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri diskten belleğe yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77f4c-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="77f4c-106">Verileri bir kodlayıcı çeviren bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> ayrılan disk dosya formatına nesne.</span><span class="sxs-lookup"><span data-stu-id="77f4c-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="77f4c-107">Bir kod çözücü tarafından gerekli biçime bir disk dosyasındaki verilerin çevirir <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="77f4c-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="77f4c-108">Yerleşik Kodlayıcıları ve aşağıdaki dosya türlerini destekleyen kod çözücüleri sahiptir:</span><span class="sxs-lookup"><span data-stu-id="77f4c-108">has built-in encoders and decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="77f4c-109">BMP</span><span class="sxs-lookup"><span data-stu-id="77f4c-109">BMP</span></span>  
  
- <span data-ttu-id="77f4c-110">GIF</span><span class="sxs-lookup"><span data-stu-id="77f4c-110">GIF</span></span>  
  
- <span data-ttu-id="77f4c-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="77f4c-111">JPEG</span></span>  
  
- <span data-ttu-id="77f4c-112">PNG</span><span class="sxs-lookup"><span data-stu-id="77f4c-112">PNG</span></span>  
  
- <span data-ttu-id="77f4c-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="77f4c-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="77f4c-114">Ayrıca, aşağıdaki dosya türlerini destekleyen yerleşik kod çözücüleri vardır:</span><span class="sxs-lookup"><span data-stu-id="77f4c-114">also has built-in decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="77f4c-115">WMF</span><span class="sxs-lookup"><span data-stu-id="77f4c-115">WMF</span></span>  
  
- <span data-ttu-id="77f4c-116">EMF</span><span class="sxs-lookup"><span data-stu-id="77f4c-116">EMF</span></span>  
  
- <span data-ttu-id="77f4c-117">SİMGESİ</span><span class="sxs-lookup"><span data-stu-id="77f4c-117">ICON</span></span>  
  
 <span data-ttu-id="77f4c-118">Aşağıdaki konular Kodlayıcıları ve kod çözücüleri daha ayrıntılı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="77f4c-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77f4c-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="77f4c-119">In This Section</span></span>  
 [<span data-ttu-id="77f4c-120">Nasıl yapılır: Yüklenen Kodlayıcıları listeleme</span><span class="sxs-lookup"><span data-stu-id="77f4c-120">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)  
 <span data-ttu-id="77f4c-121">Bir bilgisayar üzerinde sunulan kodlayıcılarda listesinde açıklar.</span><span class="sxs-lookup"><span data-stu-id="77f4c-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="77f4c-122">Nasıl yapılır: Yüklenen kod çözücüleri listeleme</span><span class="sxs-lookup"><span data-stu-id="77f4c-122">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)  
 <span data-ttu-id="77f4c-123">Bir bilgisayarda kullanılabilir kod çözücüleri listeleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="77f4c-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="77f4c-124">Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme</span><span class="sxs-lookup"><span data-stu-id="77f4c-124">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="77f4c-125">Liste açıklar <xref:System.Drawing.Imaging.EncoderParameters> bir kodlayıcı tarafından desteklenen.</span><span class="sxs-lookup"><span data-stu-id="77f4c-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="77f4c-126">Nasıl yapılır: BMP resmini PNG resmine dönüştürme</span><span class="sxs-lookup"><span data-stu-id="77f4c-126">How to: Convert a BMP image to a PNG image</span></span>](how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="77f4c-127">Farklı görüntü biçimi'nde bir görüntüsünü kaydetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="77f4c-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="77f4c-128">Nasıl yapılır: JPEG sıkıştırma düzeyini ayarlama</span><span class="sxs-lookup"><span data-stu-id="77f4c-128">How to: Set JPEG Compression Level</span></span>](how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="77f4c-129">Görüntü kalite düzeyini değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="77f4c-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="77f4c-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="77f4c-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="77f4c-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="77f4c-131">Related Sections</span></span>  
 [<span data-ttu-id="77f4c-132">GDI+ Yönetilen Kodu Hakkında</span><span class="sxs-lookup"><span data-stu-id="77f4c-132">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
  
 [<span data-ttu-id="77f4c-133">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="77f4c-133">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
