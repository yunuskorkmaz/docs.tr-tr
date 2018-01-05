---
title: "Görüntüler, Bit Eşlemler ve Meta Dosyaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67f72847e5dca20acd623c566a882e0094e94f68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="fe755-102">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fe755-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="fe755-103">`Image` Sınıftır ızgara görüntüleri (bit eşlemler) ile çalışmak için yöntemler sağlayan bir soyut taban ve vektör (meta dosyaları) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe755-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="fe755-104">`Bitmap` Sınıfı ve <xref:System.Drawing.Imaging.Metafile> her ikisi devral sınıfı `Image` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe755-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="fe755-105">`Bitmap` Sınıfını genişletir yeteneklerine `Image` yükleme, kaydetme ve ızgara görüntüleri düzenleme için ek yöntemleri sağlayarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe755-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="fe755-106"><xref:System.Drawing.Imaging.Metafile> Sınıfını genişletir yeteneklerine `Image` kaydetme ve vektör görüntüleri incelemek için ek yöntemleri sağlayarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fe755-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe755-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fe755-107">In This Section</span></span>  
 [<span data-ttu-id="fe755-108">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="fe755-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="fe755-109">Çeşitli görüntü biçimleri açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe755-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="fe755-110">GDI+'da Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fe755-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="fe755-111">Anlatılmaktadır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] meta dosyaları için destek.</span><span class="sxs-lookup"><span data-stu-id="fe755-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="fe755-112">GDI+'da Görüntü Çizme, Konumlandırma ve Kopyalama</span><span class="sxs-lookup"><span data-stu-id="fe755-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="fe755-113">Çizim vektör ve yönetilen kod ile ızgara görüntüleri için yöntemleri anlatır.</span><span class="sxs-lookup"><span data-stu-id="fe755-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="fe755-114">GDI+'da Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="fe755-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="fe755-115">Yönetilen kod ile vektör ve ızgara görüntü kırpma ve ölçeklendirme için yöntemleri anlatır</span><span class="sxs-lookup"><span data-stu-id="fe755-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fe755-116">Başvuru</span><span class="sxs-lookup"><span data-stu-id="fe755-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="fe755-117">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="fe755-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="fe755-118">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir</span><span class="sxs-lookup"><span data-stu-id="fe755-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fe755-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fe755-119">Related Sections</span></span>  
 [<span data-ttu-id="fe755-120">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="fe755-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="fe755-121">Görüntüleri, uygulamanızda kullanmak nasıl ekleyebileceğiniz gösterilmektedir konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="fe755-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
